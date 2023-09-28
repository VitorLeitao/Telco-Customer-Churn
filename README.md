# Telco-Customer-Churn
## 🔍 Sobre o projeto
### Análise de Churn em Telecomunicações
Bem-vindo ao projeto de Análise de Churn em Telecomunicações! Neste projeto, exploramos o emocionante mundo dos dados para entender o que determina a permanência de um cliente em uma empresa de telecomunicações. Usando um dataset fascinante disponível no Kaggle(https://www.kaggle.com/datasets/blastchar/telco-customer-churn), Telco Customer Churn, mergulhamos fundo nos registros de clientes para buscar respostas para perguntas cruciais e extrair insights valiosos.
### Sobre o Dataset
O conjunto de dados Telco Customer Churn contém informações detalhadas sobre clientes de uma empresa de telecomunicações. Cada entrada no conjunto de dados representa um cliente, e as informações incluem uma variedade de características, como contrato, uso de serviços, cobrança e muito mais. Este dataset nos oferece uma janela para o comportamento do cliente e nos permite investigar o que pode estar impulsionando a decisão de um cliente de permanecer ou deixar a empresa.
![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/9be81c94-6a94-4a31-ab30-86eef33870f1)
### Objetivos do Projeto
1. **Entender o que Determina a Permanência**: Vamos explorar as características dos clientes e buscar entender quais fatores têm a maior influência na decisão de permanecer ou não na empresa de telecomunicações. Estaremos à procura de padrões e correlações significativas.

2. **Extrair Insights Valiosos**: A medida que exploramos os dados, pretendemos identificar insights valiosos que podem ser utilizados para melhorar a retenção de clientes e a experiência geral dos clientes.

3. **Prever o Churn**: Aplicaremos algoritmos de Machine Learning para desenvolver modelos de previsão de churn. Usaremos uma variedade de técnicas de aprendizado de máquina para determinar quando um cliente é mais propenso a deixar a empresa. Isso nos ajudará a tomar ações proativas para reter clientes em risco.


## 🗺️ Analise exploratória dos dados
### Variável Tenure: Tempo de permanencia na empresa
Principais insights: 
- A maioria das pessoas que permanecem por mais tempo na empresa são aquelas que possuem algum tipo de serviço adicional, como streaming, TV, etc. Isso foi descoberto a partir da analise de diversos boxplots e, posteriormente, foi criada uma nova feature que sintetizava as variaveis de "serviços adicionais" e informava se o usuario em questão tinha ao menos 1 desses serviços. Ao analisar o boxplot dessa variavel em conjunto com a tenure, ficou muito mais clara a diferença:
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/7f4f7774-1d6d-46a0-bac2-78d99a571da0)


### Variável Contract: Tempo de contrato do cliente
Principais Insights: 
- a maioria dos clientes que **NÃO** tem serviços adicionais preferem fazer contratos **MENORES**
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/d4e9ccf6-9c95-4245-9fd0-dfe3cf0b6139)
- Os clientes idosos preferem por fazer planos **menores**
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/ba8b57f7-fb6c-4643-bebb-3f6d3d115746)

## Variável Churn: Determina se o Usuario permacene ou não na empresa
Principais Insights:
- Há uma diferença gritante na quantidade de meses entre os clientes que dão Churn e aqueles que não o fazem, mostrando que os clientes que o fazem são aqueles que passam pouco tempo na empresa. Talvez isso aconteca por ele não se adaptar ou simplesmente não aprovar o serviço, isso indica que o ideal para a empresa é fazer um estudo sobre oferecimento de beneficio para membros novos
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/ad2abfa6-30fa-4e45-ad40-ecf18d653e82)
- Os clientes idosos tem uma taxa de Churn significativamente maior. Talvez a operadora não tenha um suporte de fácil adaptação para os mais velhos, que via de regra tem menos intimidade com ferramentas derivadas das novas tecnologias. Seria extremamente válido o estudo de políticas que melhoram a aceitação de usuários com idade mais avançada
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/cd9ff773-b417-4f41-99e2-48f56b1902cd)
- Clientes que não possuem parceiro também tem uma taxa significativamente maior de churn do que aquelas que o possuem, seria interessante uma análise sobre aplicações de benefícios aos planos individuais, uma vez que a maior parte dos clientes que não tem parceiro fazem esse tipo de plano
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/3dd4a7be-8157-4bd0-91c4-00795aee6d18)

- Os clientes fazem contratos curtos tem uma taxa absurdamente maior de churn do que aqueles que ficam um tempo maior
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/6cced326-9017-44e4-8ac7-08e0f4c397ad)

## Algumas correlações interessantes entre features

### OnlineBackup X OnlineSecurity X DeviceProtection
- Em todos os casos analisados, percebemos que geralmente quando o cliente recusa uma das formas de segurança ele recusa todas. Porem, no caso contrário, geralmente quando ele aceita uma há uma probabiidade muito maior de ele aceitar uma segunda, talvez valha a pena investir em planos promocionais que incluam os 3 serviços de segurança juntos
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/936c5a77-9692-41de-9af1-e3319e9b82ba)

### StreamingMovies X StreamingTV
- Percebemos que a grande maioria das pessoas que assinam o Streaming de TV também assinam o de Filmes, e geralmente quem não assina um também não assina o outro
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/42073cf0-a936-4f49-ab76-ba4a438106a7)

### Partner X Dependents
- As duas variaveis tem uma forte correlação, **Mostrando que a grande maioria das pessoas que tem dependente possuem também um parceiro**, indicando que a maioria das pessoas costuma colocar seu parceiro como dependente
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/66a3aaf9-aa4e-44e6-a3a0-747aab49c534)


## 💻 Modelagem do preditor de Churn
Em primeira mão, fizemos alguns pre-processamentos importantes para o funcionamento adequado do modelo, como transformar variáveis categóricas em numéricas e dividir a base em treino e teste.

### Modelagem preliminar
- Após o preprocessamento, tinhamos que escolher quais seriam os modelos a serem usados nesse projeto, pra isso, usamos Grid Search para determinar o melhor resultado do F1 de cada modelo(Random Forest, Naive bayes, Redes neurais, XGB, KNN, Regressão logistica)
- A escolha do F1 como metrica principal veio por se tratar de um dataset que tem como principal atributo o Churn, mais especificamente quando ele assume o valor 1(quando o cliente sai da empresa). Ao usar a acuracia, ela "mascarava" a real Eficácia do modelo, pois na maioria das vezes ele acertava muito mais quando o Churn assumia 0, o que é menos importante pra esse projeto
- Os modelos que se sariam melhor foram:
- 1: Naive bayes(acc: 0.76, F1: 0.61)
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/4e20bfab-0f6d-46d8-a503-2e3844ec7779)
- 2: Random Forest(acc: 0.87, F1: 0.57)
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/5c49219a-d223-4ef2-a813-e8e8a9c030be)
- **OBS**: esse era o caso citado anteriormente, onde o modelo de random forest teve uma acc muito maior que o nb, porem ao analisar a matriz de confusão fica nitido que o modelo de random fortest é pior para esse projeto, uma vez que erra muito mais quando o churn = 1, mas a acc é "mascarada" por sua taxa de acerto quando o churn=0, que é bem menor importante para esse projeto
- 3: Regressão logistica(acc: 0.82, F1: 0.60)
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/76ef14bf-e362-457d-a886-01677dedc130)

## Otimizando os modelos
Após a escolha dos modelos que serão usados ao decorrer do projeto, temos que tentar melhora-los. Como a otimização dos parametos ja foi feita quando rodamos o Grid Search, os metodos escolhidos para melhorar os modelos foram: Escalonar os dados, Analisar as Correlações, tratar Dados desbalanceados. 

### Otimizando o Random Forest
- Após testar todas as otimizações citadas acima, a unica que resultou em um ganho de desempenho foi balancear a base de dados por meio da tecnica SMOTE, que cria artificialmente alguns dados da classe que tem menos registros, que nesse caso, era o Churn=1.
- Contexto: Houve uma pequena queda da acuracia do Random Forest nesse processo, uma vez que ele passou a acertar mais o Churn=1, mas acertou um pouco menos no Churn=0, apos uma avaliação de o que a empresa mais precisava, essa mudança foi considerada eficiente para a empresa
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/327010f8-ecb1-4618-bded-d270d23afa23)

### Otimizando o Naive Bayes
- De maneira semelhante ao Random Forest, o Naive Bayes apresentou uma melhora siginificativa após o balanceamentos dos dados com SMOTE. Alem disso, também houve uma melhora quando retiramos a coluna TotalCharges, que tinha uma correlação de 0.82 com a coluna tenure:
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/6692a180-2918-4390-a481-913905d8a040)
- O resultado final também se assemelha ao random forest, com uma melhora consideravel na predição do Churn=1, pagando o preço da diminuição de acuracia do Churn=0, que se torna viável pelo teor do projeto e pelo o que a empresa exige
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/ef4deefa-6bb5-4e51-8b16-22e7cc53d30c)

  ### Otimizando a Regressão Logistica
  - As otimizações da regressão logistica seguiram os passos do random forest, com uma melhora ao balancear os dados, com o mesmo preço a ser pago, de diminuição da acuracia quando o Churn=0
  - ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/803d9f70-9d19-44ba-ae59-0e3cb5c514ac)
 
  ## Combinando os classificadores
  - Apos a escolha e otimização dos modelos de ML, decidimos juntar o resultado dos 3
  - Usamos o naive bayes como modelo com maior peso de decisão, uma vez que ele tinha a maior taxa de acerto de churn = 1. Fizemos com que sempre que o Naive Bayes tivesse uma certeza menor que 0.85 em sua predição, a classe seria decidida através do voto da maioria, fazendo com que pegassemos o melhor de cada modelo, encontrando um resultado bem melhor

## Conclusão
- Conseguimos unir os resultados de forma a mesclar de uma forma satisfatória a acurácia e o F1, uma vez que os primeiros modelos testados tinham uma acurácia muito boa, mas era péssimo em prever o churn =1. No modelo final consegui diminuir essa diferença, aumentando o F1 score, mas perdendo parte da acurácia no processo, o que é válido para esse caso específico, no qual a taxa de acerto do Churn = 1 é uma métrica de extrema importância, com isso, chegamos a esse resultado final:
- Acuracia: 0.795
- F1 Score: 0.657
- ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/df86d8b4-c87a-4a56-983c-e8aad8d219ea)




