---
id: 1754942448
created: 2025-08-11 17:00:48
updated: 2025-08-11 17:00:48
aliases:
tags:
status: In Progress
---
# 1. Definição
O KMeans é um algoritmo de [[Aprendizado de Máquina|machine learning]] [[ML não Supervisionado|não supervisionado]] relativamente simples e que forma os grupos através dos passos que serão descritos abaixo. Para facilitar a explicação e o entendimento da técnica, vamos ilustrar um conjunto de pontos em uma única dimensão, conforme abaixo:
![[Pasted image 20250811185853.png]]
Nesse conjunto de pontos, podemos claramente identificar 3 clusters de forma visual. Entretanto, na maioria das vezes não é possível identificar *clusters* de forma tão fácil como a do exemplo acima, especialmente se estamos trabalhando com uma dimensão acima de 3. São exatamente nesses casos que o KMeans e outros algoritmos de *clusters* auxiliam na resolução do problema. Para o caso acima apresentado, o KMeans estabeleceria os *clusters* a partir dos seguintes passos:
1. Estabelecer aleatoriamente três pontos iniciais de centroide.
![[Pasted image 20250811191957.png]]
2. Calcular a distância euclidiana entre os pontos e os centroides, e então estabelecer o centroide mais próximo de cada ponto.
![[Pasted image 20250811192452.png]]
3. Calcular o novo centroide, a partir da média dos pontos pertencentes ao mesmo cluster.
![[Pasted image 20250811192653.png]]
4. Repetir os passos 2 e 3 até que o centroide não se altere muito, e esse *threshold* é normalmente é um parâmetro sugerido pelo usuário.
Note que no caso acima, o *cluster* estabelecido pelo KMeans na última imagem não é bem o *cluster* que esperávamos visualmente. Isso aconteceu especialmente pela localização inicial dos centroides. E, portanto, para mitigar esse problema, o algoritmo normalmente repete todo o processo algumas vezes, e compara a variância dos seus resultados, selecionando por fim o *cluster* que possui a menor variância. 
Além disso, é importante observar que o algoritmo tem como [[função objetivo]] a inércia, que nada mais é do que um cálculo com a distância euclidiana, e o tenta minimizá-lo. Entretanto o cálculo da inércia tem alguns pontos fracos:
5. A inércia tem como premissa de que os conjuntos são [[Conjunto Convexo|convexos]] e isotrópicos, o que nem sempre é o caso, entregando portanto resultados não muito satisfatórios para clusters alongados e com muitas irregularidades.
6. Inércia é uma métrica não normalizada, portanto para conjuntos de alta cardinalidade dimensional, tende-se obter distâncias euclidianas muito infladas, que é também conhecida como a maldição da dimensionalidade. Logo, rodar algoritmos de redução de dimensionalidade, como o PCA, pode ser benéficos nesses casos.
## 1.1. Referências
[^1]: https://scikit-learn.org/stable/modules/clustering.html
[^2]: https://www.youtube.com/watch?v=4b5d3muPQmA&ab_channel=StatQuestwithJoshStarmer