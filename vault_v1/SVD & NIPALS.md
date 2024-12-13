#ml 
- <mark style="background: #ABF7F7A6;">SVD</mark>: singular value decomposition
- <mark style="background: #ABF7F7A6;">NIPALS:</mark>: non-linear iterative partial least squares. 
# SVD
Un método de **factorización** que representa una **matriz** en términos de **matrices ortonormales** y **valores singulares**. 
- <mark style="background: #ABF7F7A6;">Ortonormal</mark>: vectores que tienen **producto punto 0** o angulos rectos entre ellos, y tienen una magnitud o longitud de 0, i.e. **normalizados**.
Nos dice que cualquier matriz puede ser descompuesta en $$USV^T$$ donde: 
- $U$: matriz ortonormal, i.e. $UU^T=I$
- $V$: matriz ortonormal, i.e. $VV^T=I$
- $S$: matriz diagonal con valores singulares en orden descendente. 
Se usan librerias para computar.
## Covariance matrix 
Se puede representar así $$X^TX=VS^2V^T$$
Ya que es simétrica. Los **eigenvector y eigenvalues** son los valores singulares y columnas de $V$.
Esta composición nos ayuda a encontrar direcciones o componentes principales cuando la varianza se maximiza.
# NIPALS
**Algoritmo iterativo** para obtener el [[Principal Component Analysis]] cuando hay valores **NA's.**
Norma de **Frobenius**: $$||A||^2_F=\sum_{i,j}a_{i,j}^2$$
Función de costo a minimizar: $$C({\bf x,u})=||X-{\bf wu^T}||^2_F=\sum_{i,j}(x_{i,j}-w_iu_j)^2\quad||u||=1$$
Esta función nos ayuda a encontrar los componentes principales. 
El algoritmo hace pasos iterativos para actualizar los valores de $w,u$ con pasos de normalización para buscar convergencia. 
1. Se asigna un valor random a $u$ y se normaliza.
2. Repetir hasta encontrar convergencia para el PCA con $w,u$
	1. Este componente representa la dirección con la mayor varianza.
3. El resto de componentes se encuentran aplicando NIPALS al dataset residual

## NIPALS NA's
Las actualizaciones de valores se formulan como sumas en lugar de operaciones de matrices, lo que nos permite ignorar NA's. Esto nos ayuda a reducir el ruido Gaussiano pero suaviza señales reales.

Estos dos métodos se usan para obtener el **PCA** en menores dimensiones. 