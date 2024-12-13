#ml 

La mayoría de algoritmos de ML tienen *hyperparametros* los cuales se deben de considera fuera de el algoritmos, es por eso que es complicado **finetunearlos**, no pueden ser elegidos por el algoritmo. 

Definición de ML por Tom M. Mitchell: *A computer program is said to learn from experience $E$ with respect to some class of tasks $T$ and performance measure $P$ if its performance at tasks in $T$, as measured by $P$, improves with experience $E$.*

# The Task $T$ 

Se define por como un sistema de ML procesa un **ejemplo**, vector $x \in \mathbb{R}^n$, donde $x_i$ es un **feature** y $n$ son el número de features.

Existen distintos tipos de tasks en ML: 

1. Classification 
2. Classification with missing inputs. 
3. Regression
4. Transcription 
5. Machine Translation 
6. Structured output 
7. Anomaly detection 
8. Synthesis and sampling 
9. Imputation of missing values 
10. Denoising 
11. Density estimation or probabiliy mass function estimation 

# The Performance Measure $P$ 

Es una medida cuantificable para medir el rendimiento del algoritmo. 
Para algoritmos como el 1, 2, 4 medimos la puntería **accuracy**.

Nos interesa en que tan bien el algoritmo lo hace con información que no ha visto antes, es por eso que se usa un **test set** diferente al que se usa para entrenar al algoritmo. 

# The Experience $E$

Es que tanto controlan a un algoritmo en su proceso de entrenamiento. 
Hay algoritmos supervisados y no supervisados.

## Unsupervised learning algorithms

**Experimenta** a un dataset que contiene muchas **features**, para luego usar propiedades útiles de la estructura de este data set. 

## Supervised algorithms 

**Experimenta** un data con features pero cada **ejemplo** es asociado con un **label** u **objetivo.** E.g. un algoritmo que estudió el Iris data set puede aprender a clasificar las plantas entre 3 especies basada en sus medidas. Ve features y trata de estimar su función de probabilidad. 

# Ejemplo: regresión lineal

$T$: predecir $y$ desde $x$, usando $\hat{y}=w^\top x$
Esta en: Página 105 


Su usa la lambda del validation 

