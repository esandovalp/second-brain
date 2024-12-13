#ml 
# High Dimensional Datasets
$$x = \begin{bmatrix} x_1^{(1)} & x_2^{(1)} & \dots & x_d^{(1)} \\ x_1^{(2)} & x_2^{(2)} & \dots & x_d^{(2)} \\ \vdots & \vdots & \ddots & \vdots \\ x_1^{(N)} & x_2^{(N)} & \dots & x_d^{(N)} \end{bmatrix}$$
Son data sets donde hay $d$ número de features  y $N$ número de samples. Vemos que en la matriz los data points son los renglones y los features las columnas.
## The Curse of Dimensionality
Dice que si sube $d$, i.e. el número de features, aumenta la distancia entre los puntos, lo cual nos lleva a estas dificultades:
1. Es difícil encontrar relaciones importantes. 
2. Las **medias y covarianzas** son más difíciles de estima porque se necesita más data.
3. Es más costoso computacionalmente.
4. Los datos están muy esparcidos, lo cual lleva a que el modelo sea menos efectivo. 
## Representación de high dimensional data
Se utilizan matrices de **scatter plots** entre todos los pares de features para representarla.
## Media y Varianza
- La media se representa como un vector, y es la de cada **feature**.
	- Formula: $$E[X]=\frac{\sum_i\bf{x}_i}{N}$$
	- $E(\{\bf{x}− E({x})\}) = 0$: la media de la desviación de la media es 0.
- La covarianza se mide entre features y la matriz toma todos los posibles pares de features y los nos dice que tanto cambian de acuerdo a su media. 
	- Si es positiva: cambian en la misma dirección.
	- Si es negativa: cambian en dirección contraria. 
	- Formula: $$cov(\{x\},\{y\})=\frac{\sum_i[x_i-E[x]][y_i-E[y]]}{N}$$
**Propiedades de la matriz de covarianzas**
1. Eigenvalores son no negativos.
2. Es simétrica: $cov(x,y)=cov(y,x)$
3. Es definida positiva. 

$$\begin{align*}Cov&=E[XY]-E[X]E[Y]\\Corr(X,Y)&=\frac{Cov(X,Y)}{\sqrt{var(x)var(y)}}\\\sigma^2(X)&=E[X^2]-E^2[X]\\\sigma=\sqrt{\sigma^2}\end{align*}$$
# Blobs
Son la clusterización(agrupamiento) de datapoints en un espacio de muchas dimensiones.

Para comprender como se afectan las **medias, varianzas y blobs** veremos [[Transformations in HDD]]