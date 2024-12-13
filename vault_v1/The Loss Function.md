#ml 
# What is it 

Es una función que nos sirve que tan bien el modelo predice la información, nos sirve como una guía para ajustar los parámetros (los hiperparametros se ajustan con métodos como [[Cross Validation]]) para mejorar la **accuracy** del modelo.

Calcula el error tomando la diferencia entre la información real y la predicha por el modelo.
# What each term means 

$L = \mathbb{L}(y_i, f(x_i, \theta)) + \lambda \theta^\top \theta$
- $\mathbb{L}$: it could be Mean Squared Error: $\frac{1}{N}\sum_{i=1}^{N}{(y_i-\hat{y_i})^2}$ for regression, or Cross Entropy Loss: $H(p,q)=-\sum_{x\in \text{classes}}{\log q(x)}$ for classification.
	- La función está en términos de $y_i$ y $f(x_i,\theta)$
	- When to use **MSE**: Más fácil de usar, da más énfasis a los errores, más eficiente computacionalmente, más útil para feature selection.  
	- When the **RMSE** (Root MSE): mismas unidades que la variable, más sensible a outliers (penaliza más fuerte los errores), comparar entre data sets, se usa más para reportar errores, por eso **la vemos mucho más en representaciones visuales.**
		- $y_i$: es el actual value de la data. 
		- $\hat{y}$: son los valores predichos por el modelo.
		- $(y-\hat{y})$: error
	- $f(x_i, \theta)$
		- $x_i$: representa el $i$-ceavo valor
		- $\theta$: vector de parámetros.
		- $f(x_i, \theta)$: mapea el input $x_i$ a los parametros $\theta$.
		- Su objetivo es generar predicciones que puedan ser comparadas con los valores reales en $y_i$
	- $\lambda \theta^\top \theta$
		- Def: es un componente de **regularización**, 
		- $\lambda$: Es el parámetro de regularización, controla la fuerza del penalty. Si es alto, entonces el penalty se centra en parametros con valores altos, con lo cual $\theta$ disminuye. 
		- $\theta^\top \theta$: Es la norma 2 [[Eclidean norm]], del parámetro $\theta$. Se calcula usando $\theta=\theta^\top \theta=\sum_j{\theta}_j^2$
		- Su objetivo es prevenir [[Overfitting]] penalizando los valores grandes de $\theta$ 
# What do we want from it 

Queremos que nos de una medida de error ([[How to measure Error]]) que debe de ser minimizada, esto para que el modelo sea mejor prediciendo resultados. 
# Why use it 

Nos ayuda a mejor los parámetros y así mejorar las prediciones. 
# When to use it 

Se usa en la **parte de entrenamiento del modelo**, vimos en los **términos** que se usan distintos tipos de funciones de error dependiendo del **task**

