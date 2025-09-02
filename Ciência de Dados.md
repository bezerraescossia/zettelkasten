---
id: 1756832036
created: 2025-09-02 13:53:56
updated: 2025-09-02 13:53:56
aliases:
  - data science
tags:
---
# 1. Definição
*Data Science* é o conhecimento aplicado aos dados que os transforma em informação, conhecimento e por fim auxilia na tomada de decisões. Essa ciência é a intersecção de diversos conhecimentos, dentre os principais: programação de códigos, matemática (estatística, probabilidade, álgebra linear, ...) e de negócios (do objeto de estudo).
Para exemplificar como acontece esse processo na prática, imagine que um fundo de investimentos está buscando tomar decisões mais acertas em seu gerenciamento. Para isso ela busca agregar os diversos dados a qual tem acesso, entendê-los, gerar insights valiosos e por fim acionar a tomada de ação. Nesse processo, ela necessita de um professional que tenha o conhecimento do negócio (investimentos), consiga trabalhar com os dados disponíveis (programação), além de conseguir interpretar, inferir e avaliar (matemática). Portanto o professional adequado para esse trabalho é o cientista de dados de investimentos.
# 1.1. Workflow
Existem diversas abordagens metodológicas para se desenvolver um projeto de ciência de dados, dentre elas, a mais comum é a CRISP-DM. Mas de uma maneira geral, existem fases que independente da metodologia, sempre será necessário no fluxo de trabalho da ciência de dados.
```mermaid

graph LR;

    1(Scoping a Project) --> 2(Gathering Data)

    2 --> 3(Cleaning Data)

    3 -->2

    3 --> 4(Exploring Data)

    4 -->3

    4 --> 5(Modeling Data)

    5 -->4

    5 --> 6(Sharing Insights)

```
# 1.2. Referências
- [Python Data Science: Unsupervised Machine Learning](https://ibm-learning.udemy.com/course-dashboard-redirect/?course_id=5930252)