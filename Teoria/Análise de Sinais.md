PDF: [[ft2.pdf]]
Data: [[02-12-2022]]
Tags: #SoftwareEngineering #FCD 
Other notes: [[Espectro de um sinal]]

---

A análise espetral de sinais utiliza as séries e as transformadas de Fourier da análise matemática, formalismos que constituem uma das ferramentas fundamentais da engenharia de telecomunicações.

Estes formalismos permitem tratar grandes classes de sinais que possuam propriedades semelhantes no domínio da frequência **independentemente** dos detalhes que os distingam no domínio do tempo.

# Sinais periódicos: Espetros de Linhas

## Fasores e Espetros de Linhas

$$v(t)=A\cdot cos(w_{0}t+\phi)$$
Onde $A$ é o valor de pico ou amplitude, $w_{0}$ é a frequência angular, em radianos por segundo, e $\phi$ o ângulo de fase. Este ângulo tem a ver com o instante escolhido para origem dos tempo e representa o facto de o valor mais próximo estar **desviado** dessa origem de um valor $t=-\phi/w_{0}$. 
A equação significa que $v(t)$ se repete indefinidamente com um *período* de repetição $T_{0}=2\pi/w_{0}$.

![[Pasted image 20221202134404.png]]

O inverso do período é a frequência cíclica $$f_{0}=\frac{1}{T_{0}}=\frac{w_{0}}{2\pi}$$
medida em ciclos por segundo, ou Herts ($Hz$).
Evidentemente que nenhum sinal *real* existe indefinidamente mas esta equação constitui um *modelo* razoável para uma forma de onda sinusoidal com uma duração muito maior do que o seu período. 

Esta sinusoide pode ser representada no plano complexo por uma exponêncial ou *fasor*. Esta representação baseia-se no teorema de Euler segundo o qual $$e^{\pm j\theta}=cos(\theta)\pm j\cdot sen(\theta)$$
em que $j=\sqrt{-1}$ e $\theta$ é um ângulo arbitrário. Fazendo $\theta=w_{0}t+\phi$ pode representar-se qualquer sinusoide como sendo a parte real de uma exponencial complexa $$A\cos{(w_{0}t+\phi)}=A\cdot\mathfrak{R}\,[e^{j(w_{0}t+\phi)}]=\mathfrak{R}\,[Ae^{jw_{0}t}\cdot{e^{j\phi}}]$$
designada de *representação por fasor* (porque o termo dentro de parêntesis retos pode ser considerado como um vetor rotativo no plano complexo).

![[Pasted image 20221202140319.png]]

Na representação espetral adotaremos as seguintes convenções:
1. A variável independente é a frequência $f$. A frequência angular $w$ é uma notação sintética para o valor $2\pi f$
2. Os ângulos de fase são medidos relativamente a funções *cosseno*. Os senos serão convertidos a cosseno através da identidade $\sin(wt)=\cos(wt\pm180\degree)$ 
3. A amplitude é sempre uma quantidade positiva. Quando aparecerem sinais com amplitude negativa, esta será absorvida na fase, isto é, $-A\cos{(wt)}=A\cos{(wt\pm180\degree)}$. 
4. Os ângulos de fase são expressos em *graus* embora ângulos tais como $wt$ sejam inerentemente em radianos.

Uma outra representação espetral ainda mais valiosa, embora envolva frequências negativas,  é o espetro de linhas bilateral $$A\cos{(2\pi f_{0}t+\phi)}=\frac{A}{2}e^{j2\pi f_{0}t}\cdot e^{j\phi}=\frac{A}{2}e^{-j2\pi f_{0}t}\cdot e^{-j\phi}$$
![[Pasted image 20221202142112.png]]

![[Pasted image 20221202142125.png]]

![[Pasted image 20221202142136.png]]

## Sinais Periódicos e Potência Média

O *valor médio* de $v(t)$ ao longo de todo o tempo é definido por $$[v(t)]=\lim_{T\rightarrow\infty}\int_{-\frac{T}{2}}^{\frac{T}{2}}v(t)\;dt$$
No caso de um sinal periódico, o valor médio para todo o tempo é igual ao valor médio num periódo $$[v(t)]=\frac{1}{T_{0}}\int_{t_{1}}^{t_{1}+T_{0}}v(t)\;dt=\frac{1}{T_{0}}\int_{T_{0}}v(t)\;dt$$
![[Pasted image 20221202143246.png]]

> [!Note]
> O componente constante de amplitude $C(0)$ da série de Fourier é o valor médio de $v(t)$.

## Teorema da Potência

Este teorema relaciona a potência média S de um sinal periódico com os seus coeficientes de Fourier.
![[Pasted image 20221202143925.png]]

![[Pasted image 20221202144133.png]]

Tem-se portanto, $$S=\sum\limits^{+\infty}_{n=-\infty}{C_{n}\,C_{n}^{*}}=\sum\limits^{+\infty}_{n=-\infty}{{|C_{n}|}^{2}}$$

## Teorema da Energia

O teorema da energia (ou teorema de Rayleigh) de sinais não-periódicos é análogo ao teorema da potência de Parseval para sinais periódicos. Diz que a energia, E, de um sinal $v(t)$ está relacionada com o seu espetro, $V(f)$, por

![[Pasted image 20221202150557.png|300]]

o que significa que a energia total de um sinal pode ser calculada integrando o quadrado do espetro de amplitude no intervalo de menos infinito a mais infinito.

## Largura de Banda

A interpretação dada acima a $|V(f)|^2$ fornece uma justificação quantitativa à noção de largura de espetral no sentido em que a maior parte da energia de um dado sinal deverá estar contida no intervalo de frequência que se tomar como sendo *banda* do sinal, intervalo esse cuja amplitude define a *largura de banda* do sinal.

![[Pasted image 20221202150953.png]]

![[Pasted image 20221202151013.png]]

# Modulação

## Modulação de Amplitude

A multiplicação de um sinal $v(t)$ por uma onda sinusoidal dá origem a um novo sinal $v_{m}(t)$ cujo espetro é o de $v(t)$ transladado na frequência de um valor igual à frequência do sinal sinusoidal.
Demonstração do *Teorema da modulação*:
![[Pasted image 20221202154752.png]]