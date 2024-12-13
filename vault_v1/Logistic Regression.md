#ml

**Logistic:** Se refiere a la función logística de la forma $\frac{1}{1+e^{-x}}$. Esta función tiene una forma S, entre valores 0 y 1, por lo cual se usa para estimar probabilidades (no para dar probabilidades en sí). Transforma valores de una función lineal a valores entre $[0,1]$. También se le conoce como función **sigmoide**.
**Regression:** Relación entre variables, generalmente entre una dependiente (label) y otras independientes (features)

Es usada para clasificaciones entre dos categorías, esto por su forma de S, y su espacio entre $[0,1]$. Generalmente la notación que se usa para esto es: $P(y=1|x)$: dado input x pertenece a la clase 1. 

Para generalizarla a múltiples clases usamos: [[Softmax]]

