---
id: 1756828177
created: 2025-09-02 12:49:37
updated: 2025-09-02 12:49:37
aliases:
  - P.A.M
  - protocolo de aprendizado de máquina
  - protocolo de machine learning
tags:
---
# 1. Introdução
Desenvolver um projeto de ML é um processo **iterativo** e **interminável**. Iterativo pois possui um passo-a-passo não sequencial e não linear, que se necessário retorna as etapas anteriormente já realizadas, ou ainda avança para etapas futuras conforme a necessidade. E é interminável, pois é um processo que mesmo após colocado em produção, exige monitoramento e aprendizado contínuo.
Existem várias metodologias para se implementar um sistema de ML, dentre os mais conhecidos, o CRISP-DM ou o KDD. Entretanto, de uma maneira holística podemos resumidamente falar que o processo de desenvolvimento de um sistema de ML, passa pelos seguintes estágios:
1. Escopo do Projeto
2. [[Data Engineering]]
3. Desenvolvimento de Modelos de ML
4. Implementação
5. Monitoramento e Aprendizagem Contínua
6. Análise de Negócios
# 2. Escopo do projeto
É nessa etapa que se define metas, objetivos, estimasse alocação de recursos financeiros e humanos, monta-se uma equipe, defini-se um plano de ação com timelines e outras atividades dessa natureza. Segue o *checklist*:
- [ ] Delimite o problema
- [ ] Identifique a natureza do problema
- [ ] Defina os objetivos do projeto
- [ ] Estime os recursos necessários
- [ ] Monte a equipe do projeto
- [ ] Crie um plano de ação com timelines
## 2.1. Delimitando o problema
De uma maneira geral, um problema bem delimitado é um problema que tem o seu escopo claramente definido. Dessa forma, para os problemas de ML, ele será bem delimitado se for bem definido em termos de entradas, saídas e [[função objetivo]].
Ou seja, para que um problema de ML seja bem definido precisamos saber claramente quais são as entradas (dados), as saídas (resultados) e a [[função objetivo|funções objetivo]] (o que estamos tentando otimizar ou prever).
E uma das primeiras atividades ao delimitar um problema é traduzir um requisito de negócio em um requisito de ML. Isso envolve entender o que o negócio precisa e como isso se traduz em um problema que pode ser resolvido com técnicas de [[aprendizado de máquina]]. Imagine a seguinte situação:
Você é um cientista de dados em um banco e seu chefe ao observar uma empresa concorrente, percebe que a satisfação e retenção dos clientes melhoraram após a implementação de um sistema de ML. Portanto, seu chefe chega para você e solicita que desenvolva um sistema de ML que melhore a retenção de clientes, ou seja que diminua o *churn* na empresa.
Dessa forma, perceba que a solicitação do seu chefe não é um problema de ML bem delimitado, na verdade ele é um requisito de negócio: "melhore a retenção de clientes". Portanto, nesse estágio, a sua primeira missão é traduzir o requisito de negócio em requisito de ML, e as vezes poderá não ser tão direto assim.
Nesse caso, após investigação, imagine que percebeu que os clientes que ligaram ao SAC com reclamações, permaneceram bastante tempo na linha e suas demandas não foram atendidas, sendo esse o principal motivo de descontentamento com sua empresa. Um *insight* que foi possível retirar da análise exploratória é que esses clientes foram transferidos muitas vezes até serem redirecionados ao departamento correto. Nessa situação você percebe que poderia criar um modelo de ML que classifica o setor de atendimento ao cliente e direciona as chamadas para o departamento apropriado, melhorando assim a experiência do cliente e potencialmente reduzindo o churn.
Nesse contexto, chegamos enfim a um problema de ML bem delimitado: "classificar o setor de atendimento ao cliente". Sendo:
- **Entrada:** solicitação do cliente
- **Saída:** setor que atenderá o cliente
- **[[função objetivo|Função objetivo]]:** diminuir a diferença entre o setor de atendimento ao cliente previsto e o setor de atendimento ao cliente real.
## 2.2. Identificando a natureza do problema
#TODO
## 2.3. Definindo os objetivos do projeto
#TODO
## 2.4. Estimando os recursos necessários
#TODO
## 2.5. Montando a equipe do projeto
#TODO
## 2.6. Criando um plano de ação com timelines
#TODO
# 3. Data engineering
#TODO
# 4. Desenvolvimento de modelos de ML
#TODO
# 5. Implementação
#TODO
# 6. Monitoramento e aprendizagem contínua
#TODO
# 7. Análise de negócios
#TODO
# 8. Referências
1. Projetando Sistemas de [[Machine Learning]] - Chip Huyen