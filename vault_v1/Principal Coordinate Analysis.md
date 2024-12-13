#ml 
Es una técnica de reducción de [[High Dimensional Data]]. Es muy útil para preservar distancias entre pares en espacios de pocas dimensiones., entre 2 y 3.
Nos ayuda a **detectar patrones y blobs**. 
Dado un data set $X$ con media 0, la distancia entre sus datapoints se representa como: $$D_{i,j}(x)=(x_i-x_j)(x_i-x_j)^T$$
La matriz $D(x)$ contiene todas las distancias entre todos los pares posibles. 
**PCoA** busca **minimizar** la **distancia** entre los **datos transformados**, se usa **Low Rank Approximation.**
Antes de sacar esto, se busca centrar la matriz para su descomposición usando: $$A=\left ( I_{N\times N}-\frac{1}{N}I_{N\times 1}I^T_{N\times 1}\right)$$
## Low Rank Approximation 
Se usa [[SVD & NIPALS]], especificamente se descompone la matriz de covarianzas de X, como se usa en **SVD**. La matriz resultante $XX^T=US^2U^T$ es la rank-reduced para tener los componentes más importantes. 
Esto nos da la aproximación $Y=U_rS_r$, donde: 
- $U_T,S_T$: son matrices truncadas.
	- $U_r$ : tiene las primeras r columnas de U (**eigenvectores**), $S_R$ tiene los **eigenvalores**
# Transformación de matriz de distancias
$$XX^T\approx-\frac{1}{2}AD(X)A^T$$
La matriz $W=XX^T$ es la que tiene los **eigenvalues y eigenvectors** del dataset transformado. 