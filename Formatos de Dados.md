---
id: 1756851683
created: 2025-09-02 19:21:23
updated: 2025-09-02 19:21:23
aliases:
tags:
---
# 1. Definição
Os dados podem assumir diferentes formatos, também conhecidos como extensões, e esses formatos influenciam tanto o comportamento dos dados quanto a forma como são utilizados pelo usuário. Por isso, é importante conhecer os diferentes formatos e suas características.  
Na escolha de um formato, alguns fatores são especialmente relevantes: se o arquivo será orientado por linhas ou por colunas, e se será baseado em texto ou em binário. Nos tópicos a seguir, exploraremos melhor cada uma dessas dimensões e analisaremos as vantagens e desvantagens de cada abordagem.
# 2. Formato orientado a linha vs orientado a coluna
O processamento computacional tende a funcionar melhor de forma sequencial, ou seja, quando as informações estão fisicamente próximas no disco, elas podem ser acessadas mais rapidamente. Por isso, dependendo do caso de uso, é importante observar a qual paradigma de organização o formato de dado obedece.
Os dois paradigmas mais comuns são os **orientados a linha** e os **orientados a coluna**, embora também existam outros, como chave-valor, grafos, séries temporais e híbridos. Aqui, vamos focar nos dois primeiros, que são os mais utilizados. Seus principais representantes são o **CSV** (linha) e o **Parquet** (coluna).
## 2.1. Orientado a linha
Formatos orientados a linha são amplamente usados em sistemas **OLTP** (_Online Transactional Processing_). Isso porque armazenam todos os campos de um registro de forma sequencial em um único bloco de disco (ou memória). Essa organização torna a escrita de novos registros mais eficiente e facilita consultas que precisam recuperar linhas completas.
Para entender melhor, imagine um _dataset_ com **1 milhão de registros** e **10 atributos** — ou seja, 1 milhão de linhas e 10 colunas — representando as vendas de um _e-commerce_. Nesse cenário, é comum inserir novas linhas (novas vendas) e consultar registros inteiros (todas as colunas de uma venda específica).  
Quando ocorre uma nova venda, todos os campos desse registro são gravados juntos, de forma sequencial, em um único bloco. E, se for necessário consultar os 1 milhão de registros com todas as 10 colunas, o sistema consegue ler os dados na mesma ordem em que foram armazenados, garantindo eficiência.
## 2.2. Orientado a coluna
Você pode estar se perguntando: "e por que o formato orientado a coluna não seria tão eficiente nesse caso?"
Diferentemente do orientado a linha, esse modelo armazena os valores de cada **coluna** de forma sequencial, e não os de cada linha. Isso significa que, ao registrar uma nova venda, os campos do registro precisam ser gravados em blocos distintos (um para cada coluna), em vez de em um único bloco contínuo. Esse processo gera mais operações de I/O e, consequentemente, uma escrita menos eficiente.
Além disso, ao consultar uma venda completa, o sistema precisa acessar os blocos de todas as colunas e reconstruir a linha em memória, aumentando o custo da operação. Por outro lado, esse modelo é extremamente eficiente em cenários analíticos (**OLAP**), nos quais é comum ler milhões de registros, mas apenas algumas colunas. Um exemplo típico é calcular a receita média de vendas por produto.
Assim, em cenários transacionais (**OLTP**), com inserções frequentes e consultas de registros inteiros, o formato orientado a linha tende a ser mais eficiente. Já em cenários analíticos (**OLAP**), com consultas em larga escala e foco em poucas colunas, o formato orientado a coluna se destaca.
> No ecossistema _Python_, o **DataFrame** do Pandas — inspirado no _DataFrame_ da linguagem _R_ — segue uma lógica de dados colunares. Já o **ndarray** do NumPy, por padrão, adota uma organização orientada a linhas, a menos que o usuário especifique o contrário.
# 3. Formato de texto vs formatos binário
Um dado pode ser armazenado em **formato de texto** ou **formato binário**. Essa escolha geralmente envolve um _trade-off_ entre **legibilidade** e **tamanho de arquivo**.
Arquivos de texto, como **CSV** e **JSON**, são legíveis para humanos. Se você abrir um arquivo desse tipo em um editor simples, como o Notepad ou o VS Code, conseguirá visualizar facilmente as informações armazenadas.
Já arquivos binários, como o **Parquet**, se abertos em um editor de texto, exibem apenas valores hexadecimais correspondentes a bytes — incompreensíveis para humanos. Para interpretar seu conteúdo, é necessário utilizar uma aplicação ou biblioteca específica capaz de decodificar o formato.
Apesar de menos acessíveis, formatos binários como o **Parquet** ocupam menos espaço em disco quando comparados a formatos de texto que armazenam a mesma informação. Por isso, são especialmente indicados em aplicações com restrições de armazenamento ou que lidam com grandes volumes de dados.
# 4. Conclusão
Na hora de escolher o formato de dados para uma aplicação, é importante avaliar:
1. **O paradigma do sistema: OLTP ou OLAP.**
	- Sistemas **OLTP** geralmente demandam formatos orientados a linhas.
	- Sistemas **OLAP** se beneficiam de formatos orientados a colunas.
2. **A necessidade de legibilidade humana.**
    - Se for importante que os dados possam ser lidos diretamente por pessoas, formatos de texto, como CSV ou JSON, são os mais adequados.
3. **As restrições de espaço em disco.**
    - Quando o armazenamento é limitado e a legibilidade não é um requisito, formatos binários, como Parquet, são preferíveis, pois ocupam menos espaço que os formatos de texto.
Em resumo, a escolha do formato de dados deve equilibrar desempenho, legibilidade e eficiência de armazenamento, sempre de acordo com as necessidades específicas do projeto.