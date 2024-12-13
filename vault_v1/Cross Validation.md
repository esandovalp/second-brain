#ml 

[[Normalize]]: es llevar al vector normal $[0,1]$ y más métodos como min-max, log transformation, etc. 

Es una técnica para validar tus hyperparámetros usando Training, Test, Validation sets. 

Se usa durante el training para estimar el generalization error. 
# how?

Se fijan los hiper-parámetros para después usar **k-fold** en el que $1$ es tu validation fold, y $k-1$ tu training fold. 
El accuracy se mide con el promedio del **testing accuracy**
Si tenemos $Q$ hiper-parámetros, con **k-folds** lo entrenamos $Q\times K$

# when to use

Nos sirve para sacar estadísticos del **error, accuracy**.

# results 

Nos sirve para escoger la $\lambda$ (hyperparemeter), podemos escoger la que da mínimo error por **cross validation**, o la más grande que no esté a más de 1 del error estándar del mínimo. 



