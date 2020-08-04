# gnireenignEesreveR <!-- omit in toc -->

Este repositorio trata de uma tarefa da disciplina de eletrônica de potencia 2 sobre engenharia reversa de uma fonte chaveada comercia de celular, onde há certos requisitos a serem comtemplados, 

- [Sobre o produto](#sobre-o-produto)
- [Análise](#análise)
- [Comentários sobre cada parte do esquemático](#comentários-sobre-cada-parte-do-esquemático)
  - [A (Entrada)](#a-entrada)
  - [B (Snubber)](#b-snubber)
  - [C (Alimentação do CI de chaveamento)](#c-alimentação-do-ci-de-chaveamento)
  - [D (CI principal da entrada)](#d-ci-principal-da-entrada)
  - [E (Separação de entrada e saída)](#e-separação-de-entrada-e-saída)
  - [F (Diodo de potência)](#f-diodo-de-potência)
  - [G (CI controlador da USB)](#g-ci-controlador-da-usb)
  - [H (Referencia de tensão)](#h-referencia-de-tensão)
- [Considerações finais](#considerações-finais)
  
### Identificar:
- Características do produto
- Conectores, interface com o usuário, interface com a rede elétrica
- Análise do gabinete
- Indicativo de atendimento as normas do produto
- Circuitos de proteção na entrada
- Filtros de EMI
- Estrutura do retificador

### Analisar:
- Elementos magnéticos
- Placa de circuito impresso
- Semicondutores (transistores e diodos de potência)
- Dissipadores térmicos
- CIs dedicados
- Blocos conhecidos

**\* Se possível, obtenção do esquemático do circuito**

A avaliação será feita através de uma apresentação sobre o que foi citado anteriormente, em torno de 10 minutos.

## Sobre o produto

O produto escolhido foi o carregador de celular *DASH charge* da one plus, a seguir uma imagem do corpo do carregador.

![](Imagens%20da%20placa/inteiro.jpg)


O gabinete é feito de plástico duro, com espessura suficiente para garantir uma boa resistência mecânica a choques. Para abri-lo, necessitei serrar a estrutura onde havia uma junção.

Na especificação do produto a entrada é 100~240 V e 0.6 A máx, com sáida de 5V e 4A máx, o que é bem elevado para a categoria de carregadores, sendo um produto vendido em 2017.

## Análise

Obtendo o produto aberto, é possivel observar 4 capacitores eletroliticos, 1 CI, 1 Resistor, 1 Trafo e 1 conector USB na parte de cima da placa. É interessante notar que a potência de chaveamento é dissipada pelo CI na parte de cima, pois este esta conectado com um dissipador através de algum tipo de resina que deve ser condutora térmica, o trafo também está conectado a este dissipador pela mesma resina, a imagem a seguir mostra isso.

![](Imagens%20da%20placa/visao-lateral-1.jfif)

Na parte inferior da placa, é possivel observar 2 circuitos separados por uma faixa sem cobre, utilizado para isolar a entrada e saída elétricamente, isso também leva a crer que o trafo é isolado. É uma técnica muito utilizada na mitigação de problemas provindos de EMI que poderiam afetar o funcionamento do próprio circuito.

![](Imagens%20da%20placa/visao-inferior-1.jfif)

Observando o layout da placa, é possível observar que o fluxo de potência é da direita para a esquerda, de cima para baixo, o que é interessante pois é um produto chinês, devido ao padrão de escrita espelhado em relação aos ocidentais é da esquerda para a direita. O circuito foi dividido em algumas partes, cada uma tem uma especifidade interessante de se comentar, esses pedaços podem ser observados na figura a seguir, sendo nomeados de A até H.

Algo interessante de observar-se é na parte da extrema esquerda a região estanhada. Apenas está estanhado nas partes onde a trilha necessita ficar mais fina por algum motivo, aumentando através da espessura a capacidade de corrente que passa por essa trilha.

![](Imagens%20da%20placa/visao-inferior-2.jfif)

Baseando-se na placa de circuito impresso e utilizando-se um multimetro no modo de verificação de continuidade, foi feito um esquemático estimado, pois não há como ter certeza sobre a ligação dos nós, mas acredito que pelo 95% dos nós estão estimados de forma correta. O esquemático pode ser observador na figura a seguir, ele também foi separado pelas regiões pela qual a placa foi separada e há alguns comentários sobre cada parte. Pelo esquemático presume-se que é um circuito fly-back.

![](Imagens%20da%20placa/esquemático.jfif)


## Comentários sobre cada parte do esquemático

### A (Entrada)

A parte *A* mostra a entrada do circuito, que está conectada a tomada que passa por um resistor na parte de cima da placa, parece ser um resistor utilizado para segurança, e esta tomada está conectada em um CI com 4 terminais, parecendo muito uma ponte de diodos que causa a retificação da onda de tensão, deixando-a em tensão contínua. Logo após a ponte há um capacitor eletrolítico necessário para uma maior estabilidade do sinal de tensão e diminuição de ripple, sendo este um capacitor para 400V assume-se que a tensão nesses terminais é de 311 V. A polaridade do capacitor eletrolítico também sugere a polaridade da tensão nestes dois pontos.

<img src="Imagens%20da%20placa/esquemático%20-%20A.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20A.jfif" alt="drawing" height="400"/>

### B (Snubber)

A parte *B* refere-se a um snubber clássico colocado entre dois terminais do trafo, 3 e 4. Este circuito tem 2 utilidades, sendo para diminuir os surtos de tensão no chaveamento do trafo e também para diminuir a emissão de EMI.

<img src="Imagens%20da%20placa/esquemático%20-%20B.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20B.jfif" alt="drawing" height="400"/>

### C (Alimentação do CI de chaveamento)

Esta parte foi destacada por justamente mostrar uma solução muito boa para a alimentação de circuitos de baixa tensão conectados a rede. É adicionado um enrrolamento ao trafo, o qual rebaixa a tensão e um circuito grampeador para manter a tensão fixa. Tem alto rendimento em potência se comparado com um regulador linear e utiliza-se apenas de um diodo e um capacitor. O resistor "0" aparece em vários pontos do circuito, acredito que seja um resistor de proteção com resistência muito próxima de zero, atuando como um tipo de fusível.

<img src="Imagens%20da%20placa/esquemático%20-%20C.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20C.jfif" alt="drawing" height="400"/>

### D (CI principal da entrada)

Sendo o único CI da entrada, sugere-se que este controle o chaveamento. Outra coisa que pode-se assumir a respeito do mesmo é que ele é responsável pela dissipação de potência do circuito que fica claro pela imagem lateral do circuito mostrando que ele é conectado ao dissipador diretamente. Provávelmente ele deve ter um transistor interno responsável pelo chaveamento do trafo.

<img src="Imagens%20da%20placa/esquemático%20-%20D.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20D.jfif" alt="drawing" height="400"/>

### E (Separação de entrada e saída)

Esta seção mostra o rasgo no cobre, isolando a condução entre entrada e saída. Como conexão destas duas partes, além do trafo, há um opto acoplador para a realimentação do circuito e um capacitor que serve para unir uma provável referencia do circuito em CA, outra possível aplicação desse capacitor é para mitigação de problemas com EMI, para passar em normas regulatórias. Capacitor de baixa potência que em caso de surto pode abrir, isolando assim entrada e saída fazendo o produto ser mais seguro que um par sem isolamento, provávelmente feito desta forma por questões de norma.

<img src="Imagens%20da%20placa/esquemático%20-%20E.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20E.jfif" alt="drawing" height="400"/>

### F (Diodo de potência)

Primeira coisa a se notar nessa parte são os terminais do CI todos conectados de forma conjunta, levando a creer que é um componente de potência. Como o indutor do circuito é feito através do trafo, presume-se que este seja o diodo do conversor. Não consegui identificar a utilidade do terminal 4 do componente, imagine que seja para isolação de ruídos, confinando-os por este pino e capacitor. Há também ao lado um capacitor eletrolítico utilizado para o filtro de saída do fly-back, mantendo a tensão bastante estável pois o valor da capacitância é bem alto.

<img src="Imagens%20da%20placa/esquemático%20-%20F.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20F.jfif" alt="drawing" height="400"/>

### G (CI controlador da USB)

Com os pinos da saída USB conectados a este CI, sugere-se fortemente que este é o controlador da USB, controlando dados e corrente de saída provávelmente. O datasheet do mesmo não foi encontrado.

<img src="Imagens%20da%20placa/esquemático%20-%20G.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20G.jfif" alt="drawing" height="400"/>

### H (Referencia de tensão)

Ultimo mas não menos importante, esta parte parece ser uma referencia de tensão para a realimentação pelo opto, o 431 é um regulador e 2.5 V, porém não tenho certeza do 662k, acredito que deve agir em conjunto para criar uma referencia de tensão junto com o 431 para o circuito de controle da USB.

<img src="Imagens%20da%20placa/esquemático%20-%20H.jfif" alt="drawing" height="400"/>
<img src="Imagens%20da%20placa/visao-inferior-2%20-%20H.jfif" alt="drawing" height="400"/>

## Considerações finais

A engenharia reversa de produtos de mercado é bem cansativa, e é dificil de saber-se os componentes utilizados, pois os códigos nos CIs nem sempre são referentes a códigos comerciais, sendo impossível saber-se ao certo o funcionamento do componente. Todavia é possível identificar topologias conhecidas, além de poder-se inferir a funcionalidade do CI pelos terminais conectados ao mesmo.

Autor: Tarcis Becher