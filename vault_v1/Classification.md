#ml 

Se clasifican **variables categóricas**. Es difícil asignarles una etiqueta, e.g. $$\begin{cases}1 & cat \\
2 & dog\\
3 & spider\end{cases}$$
Porque los números implican un orden específico, además, el modelo arroja un **class score** el cual puede pensarse como una probabilidad. Es por eso que se usa [[Logistic Regression]] como medida de confiabilidad de un modelo, además de esto, también se usa la [[Calibration Curve]].
Para medir el error de la clase predicha y la clase real, se usa la [[Loss function]].

Es parte del [[Supervised Learning]], i.e. alimentamos al modelo con el par de features y labels. Los términos importantes que se usarán para discutir los tipos de clasificación son:
1. [[Bias & Variance]]
2. [[Overfitting]]
3. [[Underfitting]]

# Tipos de clasificación 

## Instance based 

Se toman decisiones basadas en el training data, no con las predefinidas por el modelo .

### K Nearest Neighbors 

[[K nearest neighbors]], clasifica midiendo la distancia entre los vecinos cercanos de un nuevo data point, y tomando la mayoría de las categorías entre estos vecinos, decide en que categoría entra este data point. La data ya tiene que tener **labels.** 

1. Escoger $K$, es un hiperparametro, si es muy chico puede ocurrir [[Overfitting]], y si es muy grande puede ocurrir [[Underfitting]]
2. Mide la distancia de los K nearest Neighbors y $x_c$, es decir el item a clasificar. Este paso puede ser costoso computacionalmente. 
3. Identifica los k nearest neighbors.
4. Clasifica. 

## Generative Classifiers

Se calcula la distribución conjunta de los **features** y los **labels** (class) para después clasificar usando el [[Bayes Theorem]].

### Naive Bayes Classifier 

[[Naive Bayes Classification]], definimos los términos para [[Machine Learning]]

$$

P(Y|X)=\frac{P(X|Y)P(Y)}{P(X)}

$$
- $P(Y|X)$: Posterior probability
- $P(X|Y)$: Likelihood
- $P(Y)$: Prior
- $P(X)$: Marginal likelihood

Es **naive** porque asume que $P(X_i|Y)$ son independientes, i.e. la likelihood de los features X dado los labels no dependen una de otra, cosa que raramente pasa en el mundo real. 
Primero estima la **prior probability** y la **likelihood** de cada $x_i$. Después predice usando el teorema de Bayes para finalmente usar la clase con la **posterior probability** más alta. Muy buena para high dimensional data, fácil de implementar, es competente. Se agrega el termino $\alpha$ para que no existan probabilidades con $0$. 
Se puede usar una transformación logaritmica para cambiar el producto a sumas, esto ayuda para preservar la diferencia entre clases. 

## Ensamble Methods

Combinan varios classifiers para mejorar el rendimiento. 

### Random forests

Es una composición de muchos [[Decision Trees]], ensamblados con un subset random de data points. Ayuda a reducir el **bias** y **overfitting** si hay muchos decision trees, sin embargo, esto puede ser muy costoso. Cada tree decide una clase, la clasificación va por votos. 

## Support Vector Machines 

Separa clases usando un plano o hiperplano, es un [[Supervised Learning]] method. 

Conceptos importantes: 

- **Hiperplano**: $w^Tx+b$
- **Support Vector**: son los data points cerca del **decision boundary**, i.e. hiperplano. Son los data points más difíciles de clasificar. 
- **Margen**: es la distancia entre los support vector y el hiperplano. Buscamos maximizarla. 
- **Linealidad**: si el espacio no es lineal hacemos un truco de **kernel**.
- **Cost Parameter o Regularization Constant** $C$: nos dice que tanto penaliza a puntos missclasified.
	- **High C**: el modelo trata de clasificar lo mejor posible, lo que puede llevar a [[Overfitting]] y a un margen pequeño.
	- **Low C**: el modelo se enfoca en maximizar el margen, lo que puede llevar a [[Underfitting]]

Dado que se busca maximizar el margen, y consecuentemente, minimizar el peso de los vectores, esto es un problema de optimización, por lo tanto se usa [[Stochastic Gradient Descent]] la cual es una técnica que en lugar de calcular el gradiente de todos los data points, va actualizando los parametros usando uno o varios data points (los escoge estocasticamente).

# Cross Validation 

[[Cross Validation]] es un método que nos ayuda a saber como dividir nuestros sets (training, test, validation). Existen varios tipos como **K fold**, **Ten fold**, que divide la data en 10 partes y testea cada una con distintos métodos de clasificación para finalmente decidir cual es el que tuvo mejor **performance**. **Leave one out** deja un set para el **test** en cada iteración o **split**.

Cada set tiene que tener la misma distribución SIEMPRE.

# What happens to the accuracy if the data are very unbalanced?

For example, if in the train and in the test 99% have tag 0 and only 1% have tag 1.

	El accuracy será el de la clase más común, en este caso, 0. Por lo que puede dar la ilusión de ser un buen modelo, aunque este no es el caso. 

How could you set up a naive (benchmark) model? 

	El naive model nos soltará la clase más común, 0. 

## What considerations do we have to have regarding classes to separate into train, validation, test (or CV)?

1. Misma distribución entre cada clase. 
	1. Si una categoría representa el 10% del data, entonces esa categoria en todos los sets debería de ser el 10% también.

## Why do we take the one with the highest probability and not apply softmax on the probabilities (OvR)?

Porque softmax funciona bien para funciones multinomiales, y One versus Rest es, en esencia, binaria , ya que compara una contra el resto. 

If we have 10 classes, how many logistic regressions do we do?

10, ya que se trata de comparar una contra las demás, para cada instancia, entonces, si hay 10, se va a comparar una contra 9, 10 veces. 

## Why do we assign the one with the majority vote and not apply softmax (OvO)?

Lo mismo que en OvR.

If we have 10 classes, how many logistic regressions do we do?

Todos los posibles pares, en este caso $\binom{10}{2}$





