Data: [[21-10-2022]]
Tags: #FCD #uni #SoftwareEngineering 

---

(Acerca de quantização: [[Quantização]])

Uma vez quantizadas, as amostras constituem ainda uma amplitude analógica mas dado que se encontram discretizadas a $q$ valores, podem desde já ser consideradas valores digitais, isto é, representam números com apenas um dígito da base $q$. Na prática, porém, utilizam-se representações na base 2. É a conversão analógico-digital que executa esta conversão da base de numeração.

# Modulação de Impulso Codificada (MIC/ ou PCM)

PCM - Pulse Code Modulation.
![[Pasted image 20221021144244.png]]

Conversor analógico-digital para $q=8$ níveis de quantização uniforme.
O divisor de tensão é constituído pelas resitências de $\text{R }\Omega$. 

Uma tensão de $1V$ é dividida em quatro intervalos iguais com limites: $\frac{1}{4},\frac{2}{4},\text{ e, } \frac{3}{4}$ V, os quais são comparados com a amplitude das amostras retificadas. 

Os comparadores produzem uma saída de valor lógico 1 sempre que a tensão da amostra for superior à de referência correspondente, e o valor lógico 0 caso contrário.

Assim, consoante o valor absoluto da amplitude de uma amostra, o conjunto das saídas dos comparadores mostrará os valores (000), (001), (011) ou (111) representativos do nível do sinal e que são depois convertidos em números de dois dígitos binários, $a_0$ e $a_{1}$ pelo *codificador binário*

Número binário resultante:
$D = (a_{2}a_{1}a_{0})=(-1)^{a_{2}}(2a_{1}+a_{0})$ 

O código binário gerado por este conversor é designado de código *dobrado* pois os números são simetricos sendo representados sobre a forma de sinal algébrico e mantissa inteira.

Exemplo de um Código PCM:
![[Pasted image 20221021150143.png|500]]
![[Pasted image 20221021150319.png]]

Portanto, ritmo binário de um canal PCM codificado a $k$ bits por amostra é $$r_{c}=kf_{a}\ge2kB$$
E a largura de banda exigida de um canal para transmissão digital é $k$ vezes maior do que se a transmissão fosse feita analogicamente $$B_{T}\ge \frac{r_{c}}{2}\ge{kB}$$
O conversor digital-analógico recebe como entrada o número digital depois de paralelizado e produz uma tensão analógica de valor $$v_{0}=\frac{(-1)^{a_{2}}}{8}(4a_{1}+2a_{0}+1)$$
que reproduz a amplitude da amostra quantizada, isto é, $x_{q}(t)=v_{0}(t)$.

Existe $2^{k-1}$ comparadores, isto é, por cada dígito por amostra o número de comparadores duplica o que, mesmo para valores moderados de $k$, representa alguma complexidade e um custo significativo.

![[Pasted image 20221021152012.png]]

![[Pasted image 20221021152030.png]]
![[Pasted image 20221021152058.png]]


