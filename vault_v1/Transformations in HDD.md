#ml 
Existen tres tipos de transformaciones: 
# Translating the data
Es representada por una matriz de traducción $b$ que desplaza los puntos de datos añadiendo el vector $b_{d\times1}$.
#  Rotating the data 
Cambiar la orientación sin alterar la forma o tamaño. Es representada con una matriz de rotación $A_{k\times d}$.
# Transformación combinada: 
$$m_i=Ax_i+b$$
Donde: 
- $x_i$: el data point original
- $m_i$: data point transformado
## Mean and Covariance
Tras una transformación, se ven afectados de la siguiente manera: 
1. **Mean:**$$E[Ax_i+b]=A\cdot E[X]+b$$
2. **Covariance:**$$A\cdot Covmat(X)\cdot A^T$$
# Eigenvectors and eigenvalues:
1. Eigenvectors: tras sufrir una transformación, su dirección no cambia. Solamente cambia en escalar. $$Su=\lambda u$$
	Donde:
	1. $S$: matriz 
	2. $\lambda$: <mark style="background: #ABF7F7A6;">eigenvalor</mark>
	3. $u$: <mark style="background: #ABF7F7A6;">eigenvector.</mark>
En una matriz simétrica, los **eigenvectores** son **ortogonales** y se pueden arreglar en una matriz $U$ **ortonormal**, esta es, un conjunto de valores en los que son la identidad, e.g. $\{(1,0,0),(0,1,0),(0,0,1)\}$. 
Los **eigenvalores** están acomodados en orden descendente para priorizar a los componentes más importantes en la data transformada.
## Diagonalización
Una matriz $S$ simétrica puede ser descompuesta como $$ S = U \Lambda U^\top$$
Donde: 
- $\Lambda$: es una matriz diagonal que contiene **eigenvalores**
Esta es la técnica que se usa en PCA ([[Principal Component Analysis]]).
# Después de una transformación
1. Después de una **traducción:** $E[m]=0$, i.e. la media del dataset se hace 0.
2. Después de una **rotación:** $Covmat(r)=A\cdot Covmat(x)\cdot A^\top$
	1. Si la matriz de rotación $A$ es la matriz de **eigenvectores** $U^\top$, entonces $Covmat(r)=\Lambda$

