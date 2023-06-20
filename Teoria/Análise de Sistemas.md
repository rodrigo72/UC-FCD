Data: [[22-12-2022]]
Tags: #FCD #SoftwareEngineering 

---

# Transmissão e filtragem de sinais

A *transmissão* de um sinal é o processo pelo qual uma forma de onda elétrica transita de uma fonte para um destino, desejavelmente, sem sofrer alteração na sua forma (distorção). Por outro lado a *filtragem* de um sinal é uma operação que, propositadamente e a fim de atingir determinado objetivo, altera o espetro do sinal, e, consequentemente, a sua forma, ou seja, introduz no sinal uma **distorção propositada**.

No entanto, tanto os *sistemas de transmissão* como os *filtros* são modelados de forma semelhante, normalmente por funções de relação entrada-saída.
O sinal que se obtém à saída de um sistema como resultado da introdução de um determinado sinal na sua entrada designa-se por *resposta* do sistema a esse sinal de entrada.

Assim, este capítulo caracteriza os *sistemas* em termos da função razão *resposta-entrada* designada por *função de transferência* do sistema utilizando-a depois para analisar os efeitos do sistema na transmissão ou filtragem dos sinais que por ele transitam.

# Sistemas lineares e invariantes no tempo (LIT)

No contexto das comunicações elétricas, o sistema é normalmente um circuito com dois pares de polos (ou portas). Na porta de entrada, é aplicado o sinal de entrada, de tensão ou de corrente, que dará origem a um sinal de saída também elétrico, na porta de saída.

![](https://i.imgur.com/09thmOW.png)

$$x(t)\rightarrow y(t)$$
Um sistema é linear se, quando $$x_{1}(t)\rightarrow y_{1}(t)$$ $$x_{2}(t)\rightarrow y_{1}(2)$$
então $$a\cdot x_{1}(t)\,+b\cdot x_{2}(t)\rightarrow a\cdot y_{1}(t)\,+b\cdot y_{2}(t)$$
em que $a$ e $b$ são constantes, independentes de $t$.
Um sistema é invariante no tempo se $$x(t-t_{1})\rightarrow y(t-t_{1})$$ em que $t_{1}$ é uma constante. A propriedade de invariância no tempo significa que as características do sistema permanecem *fixas* ao longo do tempo, ou seja, um mesmo sinal de entrada aplicado à entrada do sistema $t_{1}$ segundos mais tarde produz a mesma saída também $t_{1}$ segundos mais tarde.

# Função de transferência

A questão fundamental que se coloca é a seguinte: Quais os $x(t)$ que passam pelo sistema sem alteração de forma? Isto é, quais os $x(t)$ tais que $$y\,(t)=H\,\cdot\,x(t)$$em que $H$ é um escalar, independente de $t$.  
