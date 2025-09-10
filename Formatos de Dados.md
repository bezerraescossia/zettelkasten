---
id: 1756851683
created: 2025-09-02 19:21:23
updated: 2025-09-02 19:21:23
aliases:
tags:
---
# 1. Definição
Os dados possuem formatos, popularmente extensões, esses formatos podem influenciar o comportamento do dado e a forma com a qual o usuário a utiliza. Portanto, é importante conhecer os diferentes formatos e suas características. Ao considerar um formato de dado para se trabalhar, é importante levar em consideração principalmente a legibilidade para humanos e se ela é baseada em binário ou texto. Por exemplo, o formato JSON é um formato de dado que é legível para humanos e baseado em texto, enquanto o arquivo Parquet é um arquivo binário que não é legível para humanos.
# 2. Formato orientado a linha vs orientado a coluna
O processamento computacional funciona melhor, por sua natureza de construção, de forma sequencial, ou seja, informações que estão fisicamente mais próximas uma da outra em seu disco são mais rapidamente acessadas. Com isso, dependendo do caso de uso, é importante observar a qual paradigma de orientação o formato de dado obedece. 
Os dois tipos de paradigmas mais comumente utilizados são os orientados a linha e coluna, embora existam outros como os orientados a chave-valor, grafo, série temporal e híbridos.
Abordaremos aqui principalmente os orientados a linha e coluna que são os dois tipos mais encontrados. Os dois grandes representantes desses paradigmas são o CSV (orientado a linha) e o Parquet (orientado a coluna).
Os formatos de dados orientados a linha são normalmente utilizados em sistemas OLTP (_Online Transactional Processing_), pois armazenam todos os campos de um registro de forma sequencial no em um único bloco do disco (ou memória). Isso torna a escrita de novos registros mais eficiente e também facilita consultas que precisam recuperar linhas inteiras.
Vamos tentar entender o motivo disso. Imagine que você tem um _dataset_ com 1 milhão de registros e 10 atributos — ou seja, 1 milhão de linhas e 10 colunas. Agora, suponha que esses dados representem as vendas do seu _e-commerce_. Nesse caso, é muito comum inserir novas linhas (novas vendas) e consultar registros completos (por exemplo, todas as colunas de uma venda específica).
Assim, quando ocorre uma nova venda, cada campo desse registro, ou seja, a linha inteira é gravada por inteira em um único bloco de forma sequencial. E se for necessário consultar os 1 milhão de registros com as 10 colunas, o sistema consegue ler os dados exatamente na ordem em que foram armazenados, de forma eficiente.
**E por que o paradigma orientado a coluna não seria tão eficiente nesse caso?**
Diferentemente do orientado a linhas, ele armazena os valores de cada **coluna** de forma sequencial no disco, e não os de cada linha. Isso significa que, ao registrar uma nova venda, os campos desse registro precisarão ser gravados em blocos distintos (um para cada coluna), em vez de em um único bloco sequencial. Esse processo gera muito mais operações de I/O e torna a escrita menos eficiente.
Além disso, ao consultar uma venda completa, o sistema precisa acessar os blocos de todas as colunas e depois reconstruir a linha em memória, o que também aumenta o custo. Esse modelo funciona muito bem em cenários analíticos (OLAP), nos quais é comum ler milhões de registros mas apenas algumas colunas — por exemplo, calcular a receita média de vendas por produto. Porém, em cenários transacionais (OLTP), em que há inserções frequentes e consultas de registros completos, a orientação a linha é claramente mais eficiente.
> Ao trabalhar com o *Python*, o *DataFrame* do Pandas, que é baseado no *DataFrame* do *R*, é um formato de dados colunar enquanto o *narray* do *NumPy*, por padrão assume um formato de dados orientado a linhas, caso não declarado o contrário pelo usuário.
# 3. Formato de texto vs formatos binário
