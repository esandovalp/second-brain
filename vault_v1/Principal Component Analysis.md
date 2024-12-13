#ml 
Es una técnica de reducción de dimensiones muy usada que usa **diagonalización**, trata de conservar varianza y la información más importante.
Usa traducciones y rotaciones vistas en [[Transformations in HDD]]. 
Dado que se busca reducir la dimensión, esto introduce un elemento de **error** el cual se busca **minimizar.**
# Después de transformación
- Después de traducción: el data set original y el transformado tienen una media de 0. 
- Después de rotación: la matriz de covarianza se hace diagonal, esto es $$Covmat(r)=U^\top\sum U=\Lambda$$
- La matriz de rotación $U^\top$ se usa para alinear la data a los ejes principales los cuales son los que tienen la mayor varianza.
# Feature selection
Los **eigenvalores** se acomodan en **descendente** ya que los que tiene mayor valor correponden a los principales componentes o **features** con mayor varianza, i.e. **capturan más** de los datos. Un **subset** de estos se escogen para **representar** la data denotados como **s**, los demás componentes se hacen 0. 
# Error
Es la varianza perdida al quitar dimensiones, se calcula como : $$\sum_{j=s+1}^d\lambda_j$$i.e. la suma de los eigenvalores que no entraron en el subset **s**
## Error relativo:
$$\frac{\sum_{j=s+1}^d\lambda_j}{\sum_{j=1}^d\lambda_j}$$
**Ratio** del error en los componentes seleccionados con la varianza total. 
Debe de ser **chico**.
# Transformación Inversa
Por cada datapoint $x_i$ la data transformada esta representada en terminos de los **eigenvectores** seleccionados y sus scores (varianza de los eigenvectores más la media).$$\sum_{j=1}^s[u_j^\top(x_i-E[X])u_j)+E[X]$$ 
El error es el mismo, si lo minimizamos se reduce el error en la reconstrucción.
$$\sum_{j=s+1}^d\lambda_j$$
# overview 
El data set original tiene $d$ features, representados por la matriz de covarianzas. 
Después de aplicar PCA, la matriz de covarianas se hace diagonal donde los mayores eigenvalores tiene representan los features. 
La representación con menos dimensiones se denota como $\hat{x}$ y se obtiene con la selección de los componentes $s$.

Otras técnicas de reducción de dimensiones son [[SVD & NIPALS]]
