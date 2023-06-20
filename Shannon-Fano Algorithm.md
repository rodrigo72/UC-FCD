Date: [[07-10-2022]]
Tags: #uni #SoftwareEngineering #FCD #C #algorithms 

# Code
Implementação simples sem blocos, ou fonte com memória.

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>

#define MAX_BOOL 50

typedef struct node {
	unsigned char ch;
	bool *code;
	unsigned int arr_len;
	unsigned int freq;
	float prob;
} Node;

float modulus(float f) {
	if (f >= 0) return f;
	return (f*(-1));
}

void shannon_fano(Node bytes[], int superior_limit, int inferior_limit) {

	if (inferior_limit <= superior_limit) {
		return;
	} else {
		int index = superior_limit;
		float total_prob = 0, ac = 0;
	
		for (int i = superior_limit; i <= inferior_limit; i++) total_prob += bytes[i].prob;
		total_prob = total_prob / 2;
	
		while (ac < total_prob && modulus(ac + bytes[index].prob - total_prob) < modulus(ac - total_prob)) {
			ac += bytes[index].prob;
			index++;
		}
		
		for (int i = superior_limit; i <= inferior_limit; i++) {
			if (i < index) {
				bytes[i].code[bytes[i].arr_len] = 0;
			} else {
				bytes[i].code[bytes[i].arr_len] = 1;
			}
			bytes[i].arr_len++;
		}
	
		shannon_fano(bytes, superior_limit, index-1);
		shannon_fano(bytes, index, inferior_limit);
	}
}

  
int main() {

	FILE *fileptr;	
	unsigned char *buffer; // (8 bits == 1 byte)	
	long filelen;	
	float total = 0;	
	int count = 0;	  
	
	fileptr = fopen("input.txt", "rb"); // Open the file in binary mode	
	fseek(fileptr, 0, SEEK_END); // Jump to the end of the file	
	filelen = ftell(fileptr); // Get the current byte offset in the file	
	rewind(fileptr); // Jump back to the beggining of the file
		
	buffer = (char *)malloc(filelen * sizeof(char)); // Enough memory for the file	
	fread(buffer, filelen, 1, fileptr); // Read the entire file, filelen bytes
		
	Node *bytes = malloc(sizeof(struct node) * filelen);	  
	
	for (int i = 0; i <= filelen; i++) {
		bytes[i].code = malloc(sizeof(bool) * MAX_BOOL);
		bytes[i].arr_len = 0;
		bytes[i].freq = 0;
		bytes[i].prob = 0;
	}
	
	for (int i = 0; i <= filelen; i++) {	
		for (int j = 0; j <= filelen - i; j++) {
			if (buffer[j] > buffer[j+1]) {
				unsigned char temp = buffer[j];
				buffer[j] = buffer[j+1];
				buffer[j+1] = temp;
			}
		}
	}  
	
	int j = 0;
	
	for (int i = 0; i <= filelen; i++) {
		bytes[j].ch = buffer[i];
		bytes[j].freq++;
		total++;
		if (buffer[i] != buffer[i+1]) j++;
	}
	
	  
	
	for (int i = 0; i <= filelen; i++) {
		if (bytes[i].freq == 0) {
			bytes[i].prob = 0;
		} else {
			bytes[i].prob = (float)(bytes[i].freq) / total;
			count++;
		}
	}
	
	for (int i = 0; i < count; i++) {
		for (int j = 0; j < count - i; j++) {
			if (bytes[j].prob < bytes[j+1].prob) {
				Node temp = bytes[j];
				bytes[j] = bytes[j+1];
				bytes[j+1] = temp;
			}
		}
	}
	
	shannon_fano(bytes, 0, count-1);
	
	for (int i = 0; i < count; i++) {
		printf("%d : %hhx : %u : %g : ", i, bytes[i].ch, bytes[i].freq, bytes[i].prob);
		for (int j = 0; j < bytes[i].arr_len; j++) {
			printf("%d", bytes[i].code[j]);
		}
		printf("\n");
	}
	
	fclose(fileptr);
	return 0;
}
```

