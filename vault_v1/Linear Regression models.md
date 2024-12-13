#ml 
Son modelos que asumen que existe una relación lineal entre las features y las labels, i.e. que una label puede ser representada por una función lineal de features. 

Ejemplo: 

$$y(\text{precio})=w_0+w_1\cdot x_1(\text{sqliving})$$
donde: 
- $w_0$ = es el bias, que puede ser algo se tiene que dar por hecho, en este caso, impuesto por comprar una casa.
- $w_1$: que tan importante es el sqliving para el precio, i.e. si cambia el sqliving cuanto sube el precio.

Tenemos que revisar la relación entre features cuando agregamos más, ya que por ejemplo, si $x_1$ es el tamaño de la casa y $x_2$ es el número de habitaciones, sabemos que si $x_2$ aumenta, el tamaño de la casa se reduce, por lo que su relación es negativa, ==esto puede aumentar la complejidad del modelo.==

**Objetivo:** encontrar una línea que sea el mejor fit para el modelo, i.e. minimizar la [[Loss function]]

![[AGV_vUfPKXORjroUQWAUzXqhYGZNa_s3kTEm_ITGO10NxnnUh9-hV4fv1BmRD8MRPw26cQIu3PoSdk2tv3h3PYozuNdPV5izc8lwolit4A5tD1LFvSXWF7zGneXB.png]]
La línea que va de un punto azul a la regresión lineal es el error o "vertical offset" o **residuals** ($e=y-\hat{y}$).

También podemos hacer una regresión lineal para problemas de clasificación binaria, para esto usamos una [[Logistic Regression]] en donde $x=w_0+w_1x_1+...+w_nx_n$, y usar una [[Log Loss]] para medir su performance.

La exploración es un poco a fuerza bruta, ya que se itera hasta que no haya mejoras, escogiendo una variable independiente, que no haya sido agregada al modelo o que no haya mejorado el modelo. Esta es una manera general, pero hay más métodos, además, tenemos bibliotecas que nos ayudan a realizar esto. 
En **backward stage regression** el working set tiene todas las variables independientes y las va quitando conforme decide cuales son importantes.

La importancia de la variable, no depende de su coeficiente, cada uno de ellos incide en la pendiente del plano, por lo que si quitas uno, el que sea, afectará a la línea. 

M-estimator: $\min \sum_i(r_i(x_i,\beta))^2$: estima parámetros para que se minimize el efecto de outliers. 

$\sum_i(w_i(\beta)(y_i-x_i^T\beta)(-x_i) = X^T[W(\beta)]y=X^T[W(\beta)]X\beta$

# Generalized Linear models 

Extienden la regresión para estimar las probabilidades de variables. 

## Regresión Logística 

[[Logistic Regression]]

$$g(\theta)=\log{[\frac{P(y=1|\theta|)}{P(y=0|\theta)}]}=\log[\frac{\theta}{1-\theta}]=x^T\beta$$
$$\frac{\theta}{1-\theta}=e^{x^T\beta}$$
$$P(y=1|x,\beta)=\frac{e^{x^T\beta}}{1 + e^{x^T\beta}}, \quad P(y=0|x,\beta)=\frac{1}{1 + e^{x^T \beta}}$$


Generalización (multi clase):
$$g_k(T)=\frac{e^{Tk}}{\sum_{l=1}^{K}{e^{Tl}}}$$
ó
$$g_k(T)=\frac{1}{1+\sum_{l=1}^{K}{e^{x^T\beta_l}}}$$
# Coeficiente de determinación

$$R^2=\frac{\sigma^2(X\beta)}{\sigma^2(y)}$$
Esto es: 
- $\sigma^2(X\beta)$: varianza de los valores predichos 
- $\sigma^2(Y)$: varianza de los valores reales

Si:
- $R^2 \to 1$: buen modelo
- $R^2 \to 0$: mal modelo 

# Limitantes de la Regresión Lineal 

- Afectada fuertemente por Outliers
- Que sea lineal puede llegar a no poder explicar data no lineal 
- Puede no tener features suficientes

Para poder tratar Outliers usamos [[Leverage (ML) & Hat Matrix]] ya que estos nos dicen cuanto afecta individualmente cada punto.

Otra manera de tratar Outliers es usando ==Residuales estandarizados== que nos dicen que tan diferente es un Outlier a toda la data. 

También usamos la ==distancia de Cook== para saber la influencia de un data point, esta usa los residuales y el leverage. 

# Transformaciones 
## BoxCox

La usamos cuando la data tiene varianza no constante, ya que la estabiliza. 
$$y_i^{bc}=\begin{cases}
\frac{y_i^\lambda-1}{\lambda},&\lambda\neq0\\
\ln y_i,&\lambda=0
\end{cases}
$$
Donde: 
- $y^{(\lambda)}$: la transformada de y
- $\lambda$: determina la fuerza de la tranformación
## Polynomial of explanatory variable. 

Nos ayuda a modelar la relación entre variables independientes y la variable dependiente, ya que muchas veces esta relación no es lineal. 
El grado del polinomio es un hyperparametro.
Modelo lineal para dos variables explanatorias o independientes:
$$y_i=\beta_2x_2^{(i)}+\beta_1x_1^{(i)}+\beta_0+e^{(i)}$$

# Regularización
## Ridge

Usamos [[Ridge Regularization]] cuando tenemos data con muchas features correlacionados, cuando las features son importantes, y nos ayuda a prevenir [[Overfitting]]
$$L_2: ||\beta||_2=\beta^T\beta$$
## Lasso

Usamos [[Lasso Regularization]] cuando queremos hacer el modelo más simple ya que puede mandar algunas features a 0 (i.e. feature selection), reducir complejidad.
$L_1=\sum_k|\beta_k|$

Para encontrar $\lambda$ es un poco a fuerza bruta, aunque se recomienda usar [[Cross Validation]] y agarrar la que tenga el menor error. 

## Elastic Net

Usamos [[Elastic Net]] como método para regularizar, que es una combinación de Ridge y Lasso. 
$$\frac{1}{N}(y-X\beta)^T(y-X\beta)+\lambda(\frac{1-\alpha}{2}||\beta||_2^2+\alpha||\beta||_1)$$
Donde $\alpha$ controla el penalty.
- Si $\alpha=1$: elastic net se comporta como **Lasso**.
- Si $\alpha=0$: se comporta como **Ridge.**

# Regression models 

Sabemos que no todas los parametros son importantes para el modelo, por lo que tenemos que saber cuales seleccionar. Para esto tenemos distintos métodos, además de conceptos importantes. 

- **Bias:** $(f-E[\hat{f}])^2$: esto es el la diferencia entre el valor real y el valor predicho al cuadrado. 
- **Variance:** $var(\hat{f})$, que tanto varia la predicción.

**Overfitting:** ocurre cuando hay mucha varianza y poco bias 
**Underfitting:** poca varianza mucho bias. 

**Akaike Information Criterion (AIC)** y **Bayes Information Criterion (BIC)** son criterios que nos ayuda a medir el performance del modelo. Penalizan la complejidad del modelo, esto es, el número de parámetros. 

También existen métodos como [[Cross Validation]] para encontrar los mejores parametros ya que usa distintas combinaciones de estos. 

**Forward and Backward Stagewise Regression** nos ayudan a encontrar features. 
**Forward:** empieza con un set vacio y va añadiendo variables
**Backward:** inicia con todas las variables y va quitando las menos importantes. 

# Robust Linear Regression 

Son modelos de regresión lineal que se usan para tratar **outliers**, que son puntos que pueden afectar mucho a regresión y tiene residuales grandes. Se intruden los **M-estimators** que cambian la función de perdida para tratar a estos outliers. 

## M-estimators

$$\sum_i\rho(u,\sigma)$$
Donde: 
- $u$: residual ($y-\hat{y}$)
- $\sigma$: parametro a escalar
- $\rho$: es el m estimator, un ejemplo que se da es **Huber Loss**
## Huber Loss

$$\rho(u,\sigma)=\begin{cases}
\frac{u^2}{2},&|u|<\sigma\\
\sigma|u|-\frac{\sigma^2}{2},&|u|\geq \sigma
\end{cases}$$
Lo que hace es dar más peso a puntos con poco residuals, y le quita peso a puntos con mucho residual (pueden ser outliers).

El proceso para usar m-estimators en regresión lineal es que iterativamente se van cambiando los pesos para poder ajustar el modelo lo mejor posible y reducir la influencia de outliers. 

# Generalized linear models 

Sabemos que la regresión predice valores, sin embargo, realmente predice probabilidades (**class score**), por lo que esto se puede mapear a función de densidad acumulada. 

Para esto, usamos modelos generalizados para poder adaptarlos a distintos tipos de data. Se menciona [[Logistic Regression]] y [[Softmax]]