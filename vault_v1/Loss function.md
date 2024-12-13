
#statistics #ml 

$\mathbb{L}=(y_i-f(x_i, \theta))^2$

- $\mathbb{L}$ represents the loss function.
- $y_i$ is the actual (observed) value of the dependent variable for the i-th data point.
- $f(x_i, \theta)$ is the predicted value for the i-th data point:
    - $x_i$ is the input (independent variable) for the i-th data point
    - $\theta$ represents the model parameters
    - $f$ is the function that maps inputs to predictions using the parameters
- $(y_i - f(x_i, \theta))$ is the difference between the actual and predicted values, also known as the residual or error.
- The entire expression is squared, $(...)^2$, which means this is a squared error loss function.

Tenemos que aprender a leer los **errores.**

# Problema de optimización 

$$\min \frac{1}{m}\sum_{i=1}^m{(y-\hat{f}(x;\theta))^2} $$
ó:

$$\hat{\theta}=\arg \min \frac{1}{m}\sum_{i=1}^m{(y-\hat{f}(x;\theta))^2}$$

# Regularización 

$$\min \frac{1}{m}\sum_{i=1}^m{(y-\hat{f}(x;\theta))^2 + \lambda w^Tw}$$
- $m$: no. de data points
- $w$: pesos del modelo, que tan importante es una feature en el large context, pueden tomar valores $\mathbb{R}$
	- **Positive** $w$: el feature tiene mucho peso para el predicted value, e.g. en clasificación binaria, acerca el valor a 1. 
	- **Negative** $w$: reduce el predicted value del modelo.
	- **Magnitud:** indica que tan influyente es la presencia del feature en un modelo. 
- $\lambda$: parametro de regularización.
	- **Big** $\lambda$: minimiza pesos, que lleva a [[Underfitting]]
	- **Small** $\lambda$: o cero, se reduce regularización, lo que le da enfoque a minimizar el error. 
- $w^T w$: L2 norm, se usa para penalizar valores grandes de peso $w$. 

# cómo medir el error 

Podemos medir el el error dependiendo del promedio, si no converge a la media, está mal el modelo. 

Si vemos que entre más grande la $y$, más grande el error, significa que el modelo ya no es mejorable. 

Si el error se distribuye normal, vamos por un buen camino. 

El modelo no da probabilidad. 

Si el error es menor que el error de la media, esta muy bien. 

