---
id: 1756831260
created: 2025-09-02 13:41:00
updated: 2025-09-02 13:41:00
aliases:
tags:
---
# 1. Definição
#TODO: Explicar a função objetivo
# 2. Como funciona a função objetivo no [[aprendizado de máquina]]?
No [[Aprendizado de Máquina]], o sistema entende que está aprendendo quando a sua função objetivo, ou função de perda como muitas vezes é chamadas, é otimizada, ou seja, a função objetivo é quem orienta o aprendizado da máquina e portanto fundamental nesse processo.
Em contextos mais simples, ao desenvolver um projeto de [[Aprendizado de Máquina|ML]], muitas vezes podemos querer apenas minimizar o erro entre o que foi predito e a realidade (*ground truth*), podemos utilizar portanto nessa situação funções objetivos de erro simples como o erro quadrático médio (RMSE) ou MAE para problemas de regressão ou ainda *log loss* para problemas de classificação binária ou entropia cruzada para multiclasse.
Em contextos mais complexos, o modelador pode ainda querer minimizar mais de uma função objetivo. Imagine a seguinte situação:
Você está desenvolvendo um sistema de recomendação e deseja otimizar tanto a precisão das recomendações quanto a diversidade dos itens recomendados. Nesse caso, você pode definir múltiplas funções objetivo: uma para minimizar o erro de previsão das classificações dos usuários (por exemplo, RMSE) e outra para maximizar a diversidade das recomendações (por exemplo, utilizando uma métrica de similaridade entre os itens recomendados). O desafio aqui é encontrar um equilíbrio entre essas diferentes funções objetivo, o que pode exigir técnicas avançadas de otimização multi-objetivo.
Uma abordagem dentre várias seria estimar uma função objetivo composta, onde cada função objetivo individual é ponderada de acordo com sua importância relativa. Por exemplo, se a precisão for mais importante que a diversidade, você pode atribuir um peso maior à função de precisão na função objetivo composta.
$$
loss = \alpha \cdot \text{precision loss} + \beta \cdot \text{diversity loss}
$$