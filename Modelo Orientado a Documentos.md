---
id: 1758229562
created: 2025-09-18 18:06:02
updated: 2025-09-18 18:06:02
aliases:
tags:
---
Fazendo uma analogia entre o modelo de dados orientado a documentos e os modelos relacionais que são mais comuns no dia a dia, uma coleção de documentos é relativa a tabelas. Dessa forma, imagine que temos uma `tabela livros`, conforme abaixo

| Autor          | Livro            | Editora | Ano  | Formato | Preço    |
| -------------- | ---------------- | ------- | ---- | ------- | -------- |
| J.K. Rowling   | Harry Potter     | x       | 2004 | Ebook   | R$ 20,00 |
| J.R.R. Tolkien | Senhor dos Anéis | y       | 1967 | Livro   | R$ 55,00 |
| J.K. Rowling   | Harry Potter     | x       | 2004 | Livro   | R$ 34,00 |
Em um banco de dados orientado a documentos, criaríamos uma coleção chamada `livros`, no qual cada linha da tabela relacional transformaria-se em um documento, normalmente em formato JSON, XML ou BSON (Binary JSON):
```json
{
	"Autor": "J.K Rowling",
	"Livro": "Harry Potter",
	"Editora": "x",
	"Ano": "2004",
	"Sold as": 
	{
		["Formato": "Ebook", "Preço": "R$ 20,00"],
		["Formato": "Livro", "Preço": "R$ 34,00"]
	}
}
```
Perceba que como diferentemente da tabela que precisamos duplicar a linha do livro "Harry Potter" para indicar os diferentes formatos e preços, no documento JSON podemos representar ela no mesmo documento, uma vez que é um modelo de dado *schemaless*. Apesar disso não ser inteiramente verdade, pois apesar do *schema* não ser definido na gravação, ele será necessário na leitura.
Por essa facilidade de conseguirmos representar todas as características do livro em um único documento, dizemos que ela tem melhor localidade. Entretanto, a desvantagem em relação aos [[Modelo Relacional|modelos relacionais]] é quando precisamos fazer comparações entre diferentes documentos, nesse caso, é muito difícil realizar *joins* entre diferentes documentos, o que não é verdade no [[modelo relacional]].