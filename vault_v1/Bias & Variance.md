#ml 

# Bias

Es el error que trae el modelo, está asociado al [[Underfitting]] porque significa que el modelo es muy simplista, en [[K nearest neighbors]] hace que el modelo clasifique la clase más común, cosa que es muy básica. 

# Variance 

Estadísticamente, nos dice que tanto difiere algo de una media, en [[Machine Learning]] significa que el modelo es muy susceptible a cambiar drásticamente dados nuevos features, es por eso que está asociado a [[Overfitting]]. 

En términos del modelo: 
- **Mayor** capacidad menor **bias**, mayor **varianza**
- **Menor** capacidad mayor **varianza** menor **bias**
![[Pasted image 20240904202629.png]]

## Que pasa si nuestras variables X tienen diferentes escalas? Cómo afectaría esto la regularización?

En regularización se penaliza por igual a todas las features independientemente de su escala, por lo que si hay valores grandes el penalty será mayor al que en realidad debería ser. 

Por lo tanto, usamos [[Feature Scaling]], algoritmos de estandarización como minmax. 

