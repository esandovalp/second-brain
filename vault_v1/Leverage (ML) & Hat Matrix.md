#ml 

# Leverage (ML)

Esto nos dice cuanto afecta un punto individual al modelo completo. Es el elemento $h_{i,i}$ de la Hat Matrix, esto es, la diagonal.

# Hat Matrix 

Mapea la $y$ a la $\hat{y}$, i.e. la transforma. 

$$H=X(X^TX)^{-1}X^T$$
Donde: 
- $X$: es la design matrix (matriz de variables independientes o features)
- $(X^TX)^{-1}$: inversa de la design matrix. 
- $X^T$: transpuesta de la design matrix. 


