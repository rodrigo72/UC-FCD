Data: [[14-10-2022]] (uniforme) e [[21-10-2022]] (não-uniforme)
Tags: #FCD #SoftwareEngineering #uni 

---
Acerca de amostragem: [[Teorema da Amostragem]]

![[Pasted image 20221014190727.png]]

## Quantização uniforme

Um *quantizador* divide o intervalo de variação das amplitudes das amostras, $x_{a}(t)$, em $q$ intervalos, ou níveis quânticos, e aproxima-as ao nível mais próximo $x_{q}(t)$. 
Se os níveis quânticos estão **igualmente espaçados entre si**, a quantização diz-se **uniforme**.

![[Pasted image 20221014191702.png]]

## Ruído de quantização

O erro de quantização de uma amostra, $e_{q}$, será a diferença $$e_{q}=x_{a}(t)-x_{q}(t)$$
Portanto, o erro varia no intervalo $\frac{-1}{q}<e_{q}<+\frac{1}{q}$ e dado tratar-se de um intervalo normalmente muito pequeno, no qual se pode considerar que as amostras do sinal $x_{a}(t)$ se distribuem uniformemente, pode supor-se também que possui média nula e se distribui uniformemente nesse intervalo.

Supondo que os valores do erro $e_{q}$  são independentes entre si, o seu valor quadrático médio ([[Variância]]) representa a podência do *ruído de quantização*, $N_{q}$. Assim, a potência do ruído de quantização é $$N_{q}=\frac{q}{2}\int_{-1/q}^{1/q}e_{q}^{2}p(e_{q}) \ \ de_{q}=(...)=\frac{1}{3q^{2}}$$
que mostra que o ruído de quantização **decresce** quando o número de níveis de quantização aumenta. A razão entre a potência do sinal e a potência do ruído de quantização é $$\frac{S}{N_{q}}=3q^2S$$ $$\frac{S}{N_{q}}\le 3q^2$$
pois como estamos a considerar $|x(t)|\le1$ também a sua potência média será **$S\le1$**. O resultado é usualmente expresso em decibéis e em função do número de dígitos binários utilizados nos números que representam as amplitudes das amostras quantizadas, ou seja, $$(\frac{S}{N_{q}})_{dB}\le 10log_{10}(3*2^{2k})\ \ dB$$ $$(\frac{S}{N_{q}})_{dB}\le 4.8+6.0k\ \ dB$$
No telefone digital utilizam-se oito dígitos para codificar cada amostra do sinal de voz, pelo que $k=8$ e portanto $(S/N_{q})\le 52.\text{8 dB}$ o que significa que a potência do ruído devido à quantização é cerca de 200 mil vezes inferior à do sinal, o que representa uma fidelidade muito boa quando o objetivo é manter a inteligibilidade e a identificação do interlocutor.

## Quantização não-uniforme

Verifica-se que os sinais analógicos de informação possuem elevados valores de crista, isto é, ao longo do tempo a sua amplitude situa-se mais frequentemente na zona das amplitudes baixas do que na zona das amplitudes altas, facto que pode ser descrito pela relação $x_{max}>>x_{ef}=\sqrt{x^2}$ .
Isto significa que a densidade das amplitudes perto do valor médio do sinal (normalmente o zero) decrescendo até aos valores de pico.


![[Pasted image 20221021134504.png]]

O valor médio de erro de quantização e portanto também a potência do ruído de quantização é mínima se os limiares de transição $\pm{x_{1}},\pm{x_{2}},\text{...},\pm{x_{q/2-1}}$ dos níveis quanticos estiverem menos espaçados para as amplitudes mais baixas e mais espaçados nas amplitudes mais altas o que significa uma quantização não-uniforme ou não-linear tal como se exemplifica na figura acima.  

Porém, a realização de um quantizador não-uniforme é mais complexa e dispendiosa do que a de um quantizador uniforme. 
O que se faz então na prática é utilizar um quantizador uniforme após uma *compressão* não-linear do sinal, em que as características do compressor são determinadas a partir de estudos experimentais com sinais representativos.

A partir de considerandos teórico-práticos chegou-se à conclusão que a característica do *compressor* que melhor *uniformiza* a densidade de probabilidade das amplitudes dos sinais que aparecem na prática (em especial os sinais de audio) é linear a partir da amplitude zero e até um certo valor ($1/A$) das amplitudes e depois logaritmica até ao seu valor máximo de acordo com a lei designada por *lei-A*:

![[Pasted image 20221021141317.png|500]]

![[Pasted image 20221021141827.png]]

Next: [[Conversão analógico a digital]]