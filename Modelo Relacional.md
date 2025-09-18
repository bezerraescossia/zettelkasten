---
id: 1758143231
created: 2025-09-17 18:07:11
updated: 2025-09-17 18:07:11
aliases:
tags:
---
O modelo relacional é uma forma de representar um dado de consiste em relações (tabelas) que são um conjunto de tuplas (linhas). Após sua difusão, essa é a forma mais cotidiana de encontrar um dado, bons representantes desse modelo é o CSV, Parquet e o banco de dados relacionais. Muitas vezes é desejável que esses dados sejam [[Normalização de Dados|normalizados]], a fim de reduzir a **redundância** e melhorar a **integridade**. Por outro lado, uma desvantagem dessa normalização é que são criados várias outras relações (tabelas), deixando, portanto, os dados mais espalhados, o que pode ser computacionalmente mais custoso para unir esses dados.
Bancos de dados relacionais precisam da intermediação de uma **linguagem de consulta** para que o sistema entenda quais dados o usuário está buscando. Atualmente a linguagem de consulta mais popularmente utilizada é o [[SQL (Structured Query Language)]]. Diferentemente do Python que segue um **paradigma imperativo**, no qual o usuário é responsável por indicar o plano de ação a serem tomados, e após executado esses passos o computador retorna o *output*. O [[SQL (Structured Query Language)|SQL]] é uma **linguagem declarativa**, nesse paradigma o usuário informa o *output* desejado e o computador é responsável pelo plano de ações necessárias para retornar esse *output*. Sendo extremamente importante e uma arte a parte desenvolver **otimização de consultas**.
