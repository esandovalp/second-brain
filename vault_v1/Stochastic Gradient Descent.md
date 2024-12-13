#ml 
Técnica que en lugar de calcular el gradiente de todos los data points, va actualizando los parámetros usando uno o varios data points (los escoge estocasticamente).

How machines learn. 
**Cost function**: you tell the computer what the output should be. Output of the trash it initially got and the output you want it to be (take the difference and squared it) $(y-\hat{y})^2$
- Inputs: parameters (weights and biases)
- Output: 1 number (the cost)
- Parameters: training data

**Learning**: minimizing a cost function. That way the **weights** get adjusted to what you want them to be or how they should be. 
The magnitud of each of does weights in that cost function (**gradient of the cost function**) tells us how much the weights should change. This should be **negative** since we want to minimize it.