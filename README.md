# gnireenignEesreveR

Este repositorio trata de uma tarefa da disciplina de eletrônica de potencia 2 sobre engenharia reversa de uma fonte chaveada comercia de celular, onde há certos requisitos a serem comtemplados, 

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

## Análise

O gabinete é feito de plástico duro, com espessura suficiente para garantir uma boa resistência mecânica a choques. Para abri-lo, necessitei serrar a estrutura onde havia uma junção.

Na especificação do produto a entrada é 100~240 V e 0.6 A máx, com sáida de 5V e 4A máx, o que é bem elevado para a categoria de carregadores, sendo um produto vendido em 2017.

Obtendo o produto aberto, é possivel observar 4 capacitores eletroliticos, 1 CI, 1 Resistor, 1 Trafo e 1 conector USB na parte de cima da placa. É interessante notar que a potência de chaveamento é dissipada pelo CI na parte de cima, pois este esta conectado com um dissipador através de algum tipo de resina que deve ser condutora térmica, o trafo também está conectado a este dissipador pela mesma resina, a imagem a seguir mostra isso.

![](Imagens%20da%20placa/visao-lateral-1.jfif)

Na parte inferior da placa, é possivel observar 2 circuitos separados por uma faixa sem cobre, utilizado para isolar a entrada e saída elétricamente, isso também leva a crer que o trafo é isolado. É uma técnica muito utilizada na mitigação de problemas provindos de EMI que poderiam afetar o funcionamento do próprio circuito.

![](Imagens%20da%20placa/visao-inferior-1.jfif)

Observando o layout da placa, é possível observar que o fluxo de potência é da direita para a esquerda, de cima para baixo, o que é interessante pois é um produto chinês, devido ao padrão de escrita espelhado em relação aos ocidentais é da esquerda para a direita. O circuito foi dividido em algumas partes, cada uma tem uma especifidade interessante de se comentar, esses pedaços podem ser observados na figura a seguir, sendo nomeados de A até H.

Algo interessante de observar-se é na parte da extrema esquerda a região estanhada. Apenas está estanhado nas partes onde a trilha necessita ficar mais fina por algum motivo, aumentando através da espessura a capacidade de corrente que passa por essa trilha.

![](Imagens%20da%20placa/visao-inferior-2.jfif)

Baseando-se na placa de circuito impresso e utilizando-se um multimetro no modo de verificação de continuidade, foi feito um esquemático estimado, pois não há como ter certeza sobre a ligação dos nós, mas acredito que pelo 95% dos nós estão estimados de forma correta. O esquemático pode ser observador na figura a seguir, ele também foi separado pelas regiões pela qual a placa foi separada e há alguns comentários sobre cada parte.

![](Imagens%20da%20placa/esquemático.jfif)


## Comentários sobre cada parte do esquemático

Coisas que tenho que falar sobre,

Foto lateral, dissipação termica e maneira que foi conectado o CI no dissipador

Foto inferior, mostrar dois blocos principais, mostrar os blocos de cada bloco e falar um pouco sobre eles

Mostrar esquemático estimado\*

falar sobre o magnético em E duas metades.