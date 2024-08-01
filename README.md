<h1 align="center"> Case: Qualidade do Ar </h1>

![Badge em Desenvolvimento](https://img.shields.io/static/v1?label=STATUS&message=COMPLETO&color=<COLOR>)

<h1 align ="center"> Objetivo do Case🤔</h1>

Utilizando Python, estatística e Machine Learning este case objetiva analisar dados de sensores químicos localizados numa cidade significativamente poluída, gerando conhecimento sobre o nível de concentração de monóxido de carbono na cidade e criando um modelo capaz de predizer o nível de concentração do gás na atmosfera. 


<h1 align ="center"> Compreensão do Problema</h1>

Monóxido de Carbono é um gás poluente e tóxico para saúde dos seres vivos. Ele é fruto de processos de combustão e por isso é encontrados cidades que passam por desmatamento, queimadas ou que tenham alto fluxo de veículos. Monóxido de carbono é um dos gases liberados por veículos a base de combustível, e seu nível de concentração pode depender de muitos fatores uma vez que a reação com outras substâncias é possível.  

Neste projeto é importante notar que:
1. O dia e a hora pode ser um fator importante para a concetração
2. Outros gases podem estar presentes e afetar a concentração do mesmo.
   
Em contexto de métrica de avaliação do modelo tem:
1. Raiz do erro médio quadrático
2. Coeficiente R²


<h1 align ="center"> Resumos das Etapas</h1>

<h2 align ="left"> Tratamento dos Dados</h2>

Realizei tratamento dos dados. Este processo contou as etapas de leitura dos dados, obtenção de informações básicas do dataset, buscando inconsistênicias como valores duplicados e faltantes. Correções foram feitas nas inconsitências encontradas, criando colunas que informam a existência de valores faltantes para levar para Análise Exploratória e para o Modelo de Regressão.


* Analisei os tipos de dados;
* Como Lidei com Valores Nulos:
  1. Todos os valores *-200* representavam dados faltantes, logo os troquei por *NaN*
  2. Criei de Novas colunas que informam se os dados eras faltantes.
  3. Usei do Simple Imputer para substituit os valores Nulos.
     
* Avaliei e retirei duplicatas;
* Criei novo arquivo para Análise Exploratória.

<h2 align ="left"> Análise Exploratória e Explanatória</h2>

Realizei análise estatística descritiva univariadas e bivariadas das features, observando sua distribuição e correlação entre features. Anotei quais eram as features com correlações acima de 0.95 para retirar na criação do modelo. Calculei quais eram as variáveis mais correlacionadas ao variáveis Target.

![Corr_target](https://github.com/user-attachments/assets/0f9553c7-7403-48d6-a4e3-5ba70ef428f5)

O gráfico de barras acima mostra quais as cincos features mais correlacionadas com a concentração de CO, todos são outras substâncias químicas indicando que geralmente a presença destas substâncias indica presença de monóxido de carbono também. 

Calculei qual dia da semana há a maior mediana na concetração de CO.

![dia_semana](https://github.com/user-attachments/assets/7d33b611-0476-416b-9118-6637f0d0d8e1)

Quinta-Feira é o dia com a maior mediana na concentração de monóxido de carbono. 

![download](https://github.com/user-attachments/assets/f28ac8c0-97cd-4fd0-9867-85c27c79ad82)

E na quinta-feira a concentração do gás tem pico as 8h da manhã e as 18h, horários que iniciam e terminam o período comercial. Desta forma os picos de Monóxidos podem estar relacionados com entrada e saída dos trabalhadores ao trabalho. 



**A análise exploratória envolveu:**

* Análise da variável target, visualização de distribuição
* Análise de dados qualitativos e quantitativos
* Análise bivariada entre grupos da variável target
* Data visualization
* Storytelling

 
<h2 align ="left"> Criação do Modelo Regressão</h2>

**O treinamento do modelo envolveu:**

* Análise de Correlação e retirada de features multicolineares;
* Category Encoder com BinaryEncoder;
* Padronização dos dados com StandardScaler;
* Definição da Baseline com *regressão linear* e  *RMSE*: 73.72%;
* Separação de dados de treino e teste; 
* Treinamento de modelos de regressão utilizando Validação Cruzada e KFold;
* Otimização por Hiperparâmetros do melhor modelo usando GridSearchCV;
* Teste do modelo otimizado.

 <h3 align ="left"> Sobre a escolha da métrica</h3>

 A métrica escolhida foi *Root Mean Squared Error* para representar o erro do modelo ao predizer um valor. A escolha desta métrica se deve aos fatos:

 1. RMSE é uma métrica que é afetada por valores outliers, assim utilizando ela é possível verificar se o modelo está conseguindo se adequar inclusive aos valores mais discrepantes.
 2. RMSE está na unidade correta para fazer a avaliação do modelo, diferente de MSE.

 
  
<h3 align ="left"> Resultados do Modelo</h3>

O modelo apresentou os seguintes resultados finais, após avaliação do ponto de threashold que maximiza os lucros:

| Métrica                             | Valor             |
|-------------------------------------|-------------------|
| RMSE                        | 45,62               |

Esta métrica mostra que o modelo consegue predizer bem os valores, como será mostrado nos gráficos a seguir.

![download](https://github.com/user-attachments/assets/e7e769ae-ed2f-41b2-a1df-ecbc154403ab)

O gráfico de resídios acima mostra que não há padrão presente nos erros e portante o modelo não está apresentando tendências nos erros. 

![download](https://github.com/user-attachments/assets/7f8717d9-25fd-4806-b18a-6f73a31b3d50)

O gráfico de Preditos em função dos Reais acima mostra que o modelo está tendo bom poder de predição já que existe correlação linear entres dados reais e de predição. 

Por fim, as features com mais importância ao modelo estão representadas abaixo:

![download](https://github.com/user-attachments/assets/bc999ea5-3511-4497-9ba6-f2cf80c69a07)

Top 10 features com mais importância para o modelo, que está seguindo o padrão das features mais correlacionadas mostradas na análise exploratória. 


<h2 align ="center"> Próximas Etapas</h2>

Os resultados finais apresentados foram obtidos com dados de validação do modelos, o que mostra que o modelo perfomaria bem no dia a dia. O próximo passo seria fazer o deploy do modelo, para ser utilizado pela empresa durante o dia a dia. 


<h2 align ="center"> Quais bibliotecas usei durante o Case?</h2>

1. Tratamento: Pandas 🐼, Sklearn.impute|
2. Análise Exploratória: Numpy, scipy, matplotlib, seaborn|
3. Criação do Modelo: Sklearn, category encoders, Pickle|

## Detalhes do projeto


Os dados deste case foram retirados do P.E.D, e você pode acessar o P.E.D [aqui](https://www.renatabiaggi.com/ped). 



<h2 align ="center">Autor 🚀</h2>
<a>
<img style = "border-radius: 50%;" src = https://github.com/KaueAbbe/Analise_ChurnRate/assets/68445400/bd4b5b79-4826-4d72-91e4-5fc7532ac19b width="250px;" alt=""/>

 <sub><b></b></sub></a> 

<h4> Feito com 💙 por Kaue Hermann Abbehausen 👋🏽 
<br/> 

 
 1.Cientista de Dados
 
 2. Formado em Física na Universidade Federal de Uberlândia
 
 3. Mestre em Física Estatística na Universidade de Brasília</h4>
<h4> Entre em contato por</h4>
<div align = "center"> 

<div align = "center"> 
   <a href="https://www.linkedin.com/in/kaue-abbehausen-5b1922165/" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
  <a href="https://www.instagram.com/kaue.hermann/" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
  <a href = "mailto:kaueabbehausen@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"></a>
</div>
