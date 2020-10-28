# <center> **Prevendo a performance dos estudantes no ENEM 2019 utilizando os dados do Ministerio da Educação** </center>

<center> Erika Costa Aves - commanderclarice@gmail.com </center>

## **1. Resumo**
> Nessa pequeno trabalho será descrito como foi feita uma análise, baseada nos dados fornecidos pelo Ministerio da Educação, de como as escolas públicas estaduais falham em atender as necessidades educacionais da população, e como isso é notório baseado nas performances dos estudantes na prova do ENEM 2019.  Em seguida, com base na análise das escolas, é feito um modelo de aprendizado de máquina para prever a performance dos candidatos do ENEM 2019 baseada na educação que tiveram no ensino médio.

## **2. Introdução**

> Na constituição de 1988, especificamente o artigo 205, é dito: "Art. 205. A educação, direito de todos e dever do Estado e da família, será promovida e incentivada com a colaboração da sociedade, visando ao pleno desenvolvimento da pessoa, seu preparo para o exercício da cidadania e sua qualificação para o trabalho." [1], ou seja, **é dever do estado dar uma educação de qualidade para o indivíduo para que ele possa, futuramente, ter uma boa qualidade de vida**. Mas será que de fato o estado está cumprindo com seus deveres para com a sociedade? De acordo com uma pesquisa feita pelo IBGE (Instituto Brasileiro de Geografia e Estatística), a educação do Brasil ainda não é acessível para todos [2]: cerca de 40% dos adultos acima de 25 anos não tinham ensino fundamental, cerca de 30% das pessoas que faziam ensino médio possuiam defasagem em relação a idade/série, e **esses dados se tornavam piores em relação a pessoas negras**. 

> Uma grande questão é, se nem toda pessoa tem acesso a sequer uma educação, é de se questionar qual a qualidade do serviço educacional no Brasil. Por isso, esse pequeno trabalho surgiu com o objetivo de analisar a educação das pessoas que prestaram o ENEM 2019 (Exame nacional do Ensino Médio): O ENEM é uma prova que avalia os alunos do ensino médio de todo o Brasil para que possam posteriormente entrar em alguma universidade.

> Nesse trabalho será utilizado os dados referentes aos alunos que prestaram a prova do ENEM 2019 no Rio Grande do Norte, e posteriormente será feito um modelo de Machine Learning pra predizer as notas dos alunos baseando-se na origem socio-econômica do candidato e na escola que fez o ensino médio.

## **3. Base de dados utilizadas**

> Para esse pequeno trabalho foram utilizadas duas bases de dados diferentes: a primeira referente ao ENEM 2019 [3], em específico apenas os dados do Rio Grande do Norte. A segunda base de dados utilizada foi a do IDEB 2019, que é uma base de dados que analisa a educação básica no Brasil [4].


### 3.1 ENEM 2019

> Nesta base de dados há dados sobre cada candidato que prestou o ENEM 2019. Nela há as condições socio-econômicas e até mesmo dados sobre alguma dificuldade de aprendizado ou deficiência.

### 3.2 IDEB

> Na base de dados do IDEB 2019 há dados sobre a performance das escolas de ensino básico, ou seja, do ensino fundamental(anos iniciais e finais) e ensino médio. Para a análise desse trabalho será apenas utilizado a performance das escolas do ensino médio.

## **4. Analise Exploratoria dos Dados**

> Nesta seção iremos explorar os nossos bancos de dados para analisar a educação básica do RN(Rio Grande do Norte).

### 4.1 Proporção das escola publicas e privadas

> O primeiro gráfico que iremos analisar será um gráfico sobre as escolas que os candidatos vão se graduar no ensino médio, visualizando a proporção entre escolas públicas e particulares dos candidatos. Nos dados há quatro tipos de categorias: pública, privada, não respondeu e exterior. O número de pessoas de escolas do exterior é zero, logo foi desconsiderado na análise. Em relação aos que 'não responderam', julgamos ser aqueles que já terminaram o ensino médio e estão fazendo novamente o ENEM. Os resultados do gráfico podem ser vistos na **Figura 1**.

![Figura 1](1.png)

### 4.2 Relação das nota totais por tipo de Escola

> Neste tópico iremos fazer uma breve análise sobre a performace dos alunos em relação a sua escola do ensino médio. Além disso, iremos retirar os valores nulos das notas de cada candidato para obter um resultado mais conciso.

![Figura 2](2.png)

### 4.3 Relação das notas totais em relação à dependência administrativa da escola

> É importante lembrar que no Brasil a educação pública é dividida por diferentes governos, sendo eles: o governo municipal, estadual, e federal. Para isso, vamos fazer a mesma análise anterior, sendo que para as dependências administrativas da escolas. O resultado é possível ser visto na **Figura 3**.

![Figura 3](3.png)

> É notório, a partir da **Figura 3**, que há uma baixa performace da educação estadual e municipal em relação às escolas federais e privadas. Vale lembrar que as escolas de ensino médio federais são os Institutos Federais.

### 4.4 Relação da quantidade de candidatos por renda

> Uma grande questão em relação as escolas é: **quem são candidatos que frequentam cada tipo de escola?** Quais são suas rendas, e será que todo mundo tem como pagar por uma escola privada pra ter acesso a uma boa educação?

> Infelizmente, no Brasil, de acordo com uma pesquisa do IBGE [5], cerca de 50% dos brasileiros vivem com apenas 413 reais por mês. Se a prioridade de do cidadão é comprar o básico para a sobrevivência (compra de alimentos e itens essenciais), será que esses brasileiros terão dinheiro para pagar por uma boa escola? Obviamente não.

> Para ficar mais claro a relação da renda dos candidados, na **Figura 4** foi criado um pequeno gráfico que expõe isso. Nos dados do ENEM 2019 a renda do candidato é categorizada de A até Q, onde:
* A : Não possui nenhuma renda.
* B : Até 988.00 reais 
* C : De 988.00 reais até 1497.00 reais
* D : De 1497.00 reais até 1996.00 reais
* E : De 1996.00 reais até 2495.00 reais 
* F : De 2495.00 reais até 2994.00 reais
* G : De 2994.00 reais até 3992.00 reais
* H : De 3992.00 reais até 4990.00 reais
* I : De 4990.00 reais até 5988.00 reais
* J : De 5988.00 reais até 6986.00 reais
* K : De 6986.00 reais até 7984.00 reais
* L : De 7984.00 reais até 8982.00 reais 
* M : De 8982.00 reais até 9980.00 reais
* N : De 9980.00 reais até 11976.00 reais
* O : De 11976.01 reais até 14970.00 reais
* P : De 14970.01 reais até 19960.00 reais
* Q : Mais de 19960.00 reais

![Figura 4](4.png)

### 4.5 Performance das notas dos candidatos com relação a dependência administrativa da escola e o tipo de renda.

> Para encerrar a análise em relação aos dados do ENEM 2019, será feito um gráfico que analisa tudo que foi visto anteriormente em uma só imagem, **Figura 5**. É possível observar que com o aumento da renda aumenta a performance do candidato, apesar de que há pouca pessoas de rendas mais altas em relação às mais baixas. Proporcionalmente e estatisticamente, vide **Figura 4**, era pra ter mais gente indo bem nas rendas mais baixas, mas como nem todo mundo tem acesso a uma boa educação isso não é possível.

* Na legenda do boxplot: 1 é federal, 2 é estadual, 3 é municipal, e 4 é privado.

![Figura 5](5.png)

### 4.6 Conclusão da análise dos dados do ENEM 2019

> Por fim, para finalizar essa análise do dados do ENEM 2019, podemos concluir que além do fato das escolas municipais e estaduais não possuírem uma qualidade boa baseado na performance dos candidatos do ENEM, e, no geral, os candidatos não possuem renda o suficiente para pagar por uma educação de qualidade(escolas privadas).

> Esses problemas geram uma grande desigualdade, porque há mais chances de alguém de renda alta entrar em uma universidade do que alguém de renda baixa, mesmo que haja mais gente de renda baixa do que alta.

### 4.7 Analisando o IDEB por depêndencia administrativa das escolas

> Neste topico iremos analisar a média das notas do IDEB em relação à dependência administrativa das escolas, **Figura 6**.

> É possivel ver claramente a partir do dados do IDEB que a performance das escolas do ensino médio federais e privadas são melhores que a estadual.

![Figura 6](6.png)

## **5. Processamento dos dados**

> Neste tópico iremos mostrar como fizemos o processamento dos dados para melhorar os resultados do nosso modelo.

> Para fazer o nosso modelo para prever a performance dos candidatos baseado nos dados sobre a renda e a escola que irá completar o ensino médio, os dados sobre a escola são relacionados à depêndencia administrativa e às notas do IDEB.

> Metodos que foram aplicados, no notebook está detalhado essa parte;
* Retirando outliers
* One-Hot encoding
* Normalização

# **6. Criando o modelo de Machine Learning**

### 6.1 Modelo de SVR

> Primeiros vamos construir um modelo simples utilizando a teoria de Support Machine Vector para Regressão, que chamado de Support Vector Regressor. Para criar nosso modelo SVR foram utilizados três parâmetros que alteram os valores do modelo criado: **Epsilon**, **Kernel** e **Degree**.
* Degree : Ele vai dizer qual é o grau do nosso Kernel.
* Kernel : É tipo da curva do nosso modelo.
* Epsilon : Determina a penalidade dentro do epsilon-tube.

> Para criar o melhor modelo foram testadas várias possibilidades para os parâmetros mencionados anteriormente. Para avaliar se o modelo está bom, utilizaremos uma métrica chamada r squared. Na metrica r squared, quanto mais próximo de 1 melhor, sendo também possível ter números negativos que mostram o quão horrível é o modelo.

### 6.2 Modelo de Árvore de Decisão

> Em seguida iremos criar um modelo bastante utlizado que é o de Árvore de Decisão. Esse modelo tem como objetivo criar 'regras' para dizer qual  caminho que nossas amostras devem seguir até o valor a ser 'predizido'. Nesse modelo iremos utilizar também três parâmetros: **Criterion**, **Max_Deph** e **Random_State**.
* Criterion : É o critério de erro do modelo.
* Max_Deph : É o tamanho da nossa árvore, quanto maior for ela, maior serão as regras
* Random_State : Deixa os nosso dados mais 'randomizados' o possível, pois a aleatoriedade é importante na hora de fazer o modelo. Para avaliar se o modelo está bom, utilizaremos uma métrica chamada r squared. Na metrica r squared, quanto mais próximo de 1 melhor, sendo também possível ter números negativos que mostram o quão horrível é o modelo.

## **7. Avaliando o Modelo de Machine Learning**

> No primeiro modelo, SVR, é notório que quanto menor é o Epsilon melhor, e quanto maior o grau da curva polinomial melhor fica o nosso modelo. E no nosso segundo modelo, árvore de decisões, quanto maior é a nossa árvore, melhor é o nosso modelo.

> Entretanto, foi observado que toda vez que a gente alterava os dados de teste e de treino as métricas r squared dos modelos alteravam um pouco. Para não haver dúvidas se o modelo está tendo um **Overfitting ou um underfitting** iremos criar um algoritmo para gerar vários modelos para diferentes dados de treino e de teste.

> Para verificar a veracidade do modelo de árvore de decisão, será aplicado o **cross validation**.

![Figura 7](7.png)

## **8. Conclusão e Resultados**

> Baseados nos dados da educação disponibilizados pelo Ministério da Educação e no modelo criado para prever e correlacionar esses dados, é possível afirmar que a educação básica ainda é ruim dentro do Rio Grande do Norte. Poucos tem acesso a uma educação de qualidade, e os que tem acesso são aqueles que possuem renda o suficiente para pagar por uma boa educação.

> O modelo criado utilizando Machine Learning consegue, com uma performace razoável, predizer a nota total do candidato baseado na sua renda e na educação que teve no ensino médio. Entretanto ainda há muitos dados que possam ser estudados futuramente para poder melhorar esse modelo de previsão.

> Um dos grandes problemas nesse modelo criado foi a falta de dados: muitos dados relacionados ao IDEB estavam em falta, o que levou a uma grande redução dos dados, assim limitando o modelo.

## **9. Referências**

[1] Artigo 205 da constituição: https://www.senado.leg.br/atividade/const/con1988/CON1988_05.10.1988/art_205_.asp

[2] Pesquisa do IBGE: https://www.redebrasilatual.com.br/cidadania/2019/06/pesquisa-ibge-mostra-que-educacao-brasileira-ainda-nao-e-para-todos/

[3] ENEM 2019: http://inep.gov.br/microdados

[4] IDEB: https://www.gov.br/inep/pt-br/areas-de-atuacao/pesquisas-estatisticas-e-indicadores/ideb/resultados

[5] Pesquisa do IBGE: https://www.cut.org.br/noticias/metade-dos-brasileiros-vive-com-apenas-r-413-por-mes-diz-ibge-6de3
