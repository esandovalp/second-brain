#ml 
Generalización de la [[Log Loss]]
Formula:  $$\text{Categorical Cross}-\text{Entropy}=-\frac{1}{n}\sum_{i=1}^n\sum_{j=1}^{K}y_{i,j}\log(p_{i,j})$$
Donde: 
- $y_{i,j}$: es la indicadora binaria de si el label $j$ es correcto para la instancia $i$
- $p_{i,j}$: probabilidad predicha de la clase $j$ para la instancia $i$
- $K$: es el número total de clases.
