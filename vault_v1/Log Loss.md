#ml 
También se le conoce como binary cross entropy loss (log loss), nos dice que tan bien las predicciones del modelo coinciden con las labels reales. Queremos minimizar esta función para mejorar las predicciones del modelo. 

$$\text{Binary Cross}-\text{Entropy}=-\frac{1}{n}\sum_{i=1}^{n}[y_i\log(p_i)+(1-y_i)\log(1-p_i)]$$
Donde: 
- $y_i$: es la label real $\{0,1\}$
- $p_i$: es la probabilidad predicha de la clase positiva (1)
- $n$: es el número de samples

Ejemplo de uso para clasificación binaria: 

$$\text{LogLoss}=-(y\cdot\log(p)+(1-p)\cdot\log(1-p))$$
donde:
- $y$: clase real $\in\{0,1\}$
- $p$: probabilidad de la clase. 

Sabemos que el modelo nos arroja un ==class score== no una probabilidad, entonces por ejemplo: 
> Si nos arroja $p=0.8$ y $y=1$, entonces tenemos un $\text{LogLoss}=0.22$, por lo tanto, nuestro modelo es bueno, así que queremos minimizarlo. 

