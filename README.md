# Telco-Customer-Churn
##🔍 Sobre o projeto
### Análise de Churn em Telecomunicações
Bem-vindo ao projeto de Análise de Churn em Telecomunicações! Neste projeto, exploramos o emocionante mundo dos dados para entender o que determina a permanência de um cliente em uma empresa de telecomunicações. Usando um dataset fascinante disponível no Kaggle(https://www.kaggle.com/datasets/blastchar/telco-customer-churn), Telco Customer Churn, mergulhamos fundo nos registros de clientes para buscar respostas para perguntas cruciais e extrair insights valiosos.
### Sobre o Dataset
O conjunto de dados Telco Customer Churn contém informações detalhadas sobre clientes de uma empresa de telecomunicações. Cada entrada no conjunto de dados representa um cliente, e as informações incluem uma variedade de características, como contrato, uso de serviços, cobrança e muito mais. Este dataset nos oferece uma janela para o comportamento do cliente e nos permite investigar o que pode estar impulsionando a decisão de um cliente de permanecer ou deixar a empresa.
![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/9be81c94-6a94-4a31-ab30-86eef33870f1)
### Objetivos do Projeto
1. **Entender o que Determina a Permanência**: Vamos explorar as características dos clientes e buscar entender quais fatores têm a maior influência na decisão de permanecer ou não na empresa de telecomunicações. Estaremos à procura de padrões e correlações significativas.

2. **Extrair Insights Valiosos**: A medida que exploramos os dados, pretendemos identificar insights valiosos que podem ser utilizados para melhorar a retenção de clientes e a experiência geral dos clientes.

3. **Prever o Churn**: Aplicaremos algoritmos de Machine Learning para desenvolver modelos de previsão de churn. Usaremos uma variedade de técnicas de aprendizado de máquina para determinar quando um cliente é mais propenso a deixar a empresa. Isso nos ajudará a tomar ações proativas para reter clientes em risco.


##🗺️ Analise exploratória dos dados
### Variável Tenure: Tempo de permanencia na empresa
Principais insights: 
- A maioria das pessoas que permanecem por mais tempo na empresa são aquelas que possuem algum tipo de serviço adicional, como streaming, TV, etc. Isso foi descoberto a partir da analise de diversos boxplots e, posteriormente, foi criada uma nova feature que sintetizava as variaveis de "serviços adicionais" e informava se o usuario em questão tinha ao menos 1 desses serviços. Ao analisar o boxplot dessa variavel em conjunto com a tenure, ficou muito mais clara a diferença:
  ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/7f4f7774-1d6d-46a0-bac2-78d99a571da0)


### Variável Contract: Tempo de contrato do cliente
Principais Insights: 
- a maioria dos clientes que **NÃO** tem serviços adicionais preferem fazer contratos **MENORES**
  ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/d4e9ccf6-9c95-4245-9fd0-dfe3cf0b6139)
- Os clientes idosos preferem por fazer planos **menores**
  ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/ba8b57f7-fb6c-4643-bebb-3f6d3d115746)

## Variável Churn: Determina se o Usuario permacene ou não na empresa
Principais Insights:
- Há uma diferença gritante na quantidade de meses entre os clientes que dão Churn e aqueles que não o fazem, mostrando que os clientes que o fazem são aqueles que passam pouco tempo na empresa. Talvez isso aconteca por ele não se adaptar ou simplesmente não aprovar o serviço, isso indica que o ideal para a empresa é fazer um estudo sobre oferecimento de beneficio para membros novos
  ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/ad2abfa6-30fa-4e45-ad40-ecf18d653e82)
- Os clientes idosos tem uma taxa de Churn significativamente maior. Talvez a operadora não tenha um suporte de fácil adaptação para os mais velhos, que via de regra tem menos intimidade com ferramentas derivadas das novas tecnologias. Seria extremamente válido o estudo de políticas que melhoram a aceitação de usuários com idade mais avançada
  ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/cd9ff773-b417-4f41-99e2-48f56b1902cd)
- Clientes que não possuem parceiro também tem uma taxa significativamente maior de churn do que aquelas que o possuem, seria interessante uma análise sobre aplicações de benefícios aos planos individuais, uma vez que a maior parte dos clientes que não tem parceiro fazem esse tipo de plano
  ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/3dd4a7be-8157-4bd0-91c4-00795aee6d18)

- Os clientes fazem contratos curtos tem uma taxa absurdamente maior de churn do que aqueles que ficam um tempo maior
  ![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/6cced326-9017-44e4-8ac7-08e0f4c397ad)

## Algumas correlações interessantes entre features

### OnlineBackup X OnlineSecurity X DeviceProtection
Em todos os casos analisados, percebemos que geralmente quando o cliente recusa uma das formas de segurança ele recusa todas. Porem, no caso contrário, geralmente quando ele aceita uma há uma probabiidade muito maior de ele aceitar uma segunda, talvez valha a pena investir em planos promocionais que incluam os 3 serviços de segurança juntos
![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/936c5a77-9692-41de-9af1-e3319e9b82ba)

### StreamingMovies X StreamingTV
Percebemos que a grande maioria das pessoas que assinam o Streaming de TV também assinam o de Filmes, e geralmente quem não assina um também não assina o outro
![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/42073cf0-a936-4f49-ab76-ba4a438106a7)

### Partner X Dependents
As duas variaveis tem uma forte correlação, **Mostrando que a grande maioria das pessoas que tem dependente possuem também um parceiro**, indicando que a maioria das pessoas costuma colocar seu parceiro como dependente
![image](https://github.com/VitorLeitao/Telco-Customer-Churn/assets/101846159/66a3aaf9-aa4e-44e6-a3a0-747aab49c534)
