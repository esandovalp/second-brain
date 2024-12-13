# 3
Una compañía que opera 10 horas al día fabrica 3 productos con 3 procesos. En la siguiente tabla se resumen los datos del problema. 

| Producto | Proceso 1 | Proceso 2 | Proceso 3 | Precio Unitario |
| -------- | --------- | --------- | --------- | --------------- |
| 1        | 10        | 6         | 8         | $4.5            |
| 2        | 5         | 8         | 10        | $5.0            |
| 3        | 6         | 9         | 12        | $4.0            |
## Determine la mezcla de productos óptima:
Sea $x_i$ el numero de unidades a productos $i=1,2,3$
$$\begin{align*}\max Z=4.5x_1+5.0x_2+4.0x_3\end{align*}$$
Restricciones: $$\begin{align*}10x_1+5x_2+6x_3\leq600\\6x_1+8x_2+9x_3\leq600\\8x_1+10x_2+12x_3\leq600\\x_1,x_2,x_3\geq0\end{align*}$$
Resolviendo con simplex obtenemos que la mezcla de productos óptima es: 
1. 50 unidades del producto 1 
2. 20 unidades del producto 2 
3. 0 unidades del producto 3
4. La ganancia total es de $325.0 al día
## ¿Cuál sería el precio más alto posible para conservar la misma mezcla de productos óptima del punto anterior? 
Realizando un análisis de sensibilidad tenemos que el precio es de $10.00.
# 6
Obtenga la solución de los siguientes programas lineales a partir de sus soluciones duales 
# 6.A
$$\begin{align*}\max Z=5x_1+2x_2\\-x_1+x_2\leq-2\\2x_1+3x_2\leq5\\x_1,x_2\geq0\end{align*}$$
Forma dual: $$\begin{align*}
\min & W = -2y_1 + 5y_2 \\
\text{Restricciones:} & \\
-y_1 + 2y_2 & \geq 5 \\
y_1 + 3y_2 & \geq 2 \\
y_1, y_2 & \geq 0
\end{align*}$$
Revisando los puntos de intersección: 
De la restricción 1: $y_1 = 2y_2 - 5$
A partir de la restricción 2: $y_1 = 2 - 3y_2$
Punto de intersección:$$\begin{align*} 2y_2-5 &= 2 - 3y_2\\5y_2 &= 7\\y_2 &= 7/5\end{align*}$$
Sustituyendo de nuevo: $y_1 = 2(7/5) - 5 = 14/5 - 5 = -11/5$
Pero como $y_1$ debe ser ≥ 0, este punto es infactible.

Observando la región factible y la función objetivo:
Explorando los vértices incluyendo la intersección con $y_1 = 0$:
Cuando $y_1 = 0:$
A partir de la restricción 1: $2y_2 ≥ 5$, por lo que $y_2 ≥ 5/2.$
La solución óptima para el dual parece ser $y_1^* = 0, y_2^* = 5/2$

Ahora usando el [[Teorema de Holguras Complementarias]] para la solución primal:

Dado que $y_1^* = 0$, la primera restricción de la primal puede ser floja
Dado que $y_2^* > 0$, la segunda restricción de la primal debe ser vinculante

Por lo tanto:
$2x_1 + 3x_2 = 5$ (restricción vinculante)
De la primera restricción primal:
$-x_1 + x_2 ≤ -2$
Resolviendo estas juntas:
$$\begin{align*}2x_1 + 3x_2 &= 5\\
-x_1 + x_2 &= -2\end{align*}
$$
Sumando ecuaciones:
$$\begin{align*}x_1 + 4x_2 &= 3\\
-x_1 + x_2 &= -2\\
\therefore\\
5x_2 &= 1 \\
x_2 &= \frac{1}{5}\\
x_1 &= \frac{11}{5}
\end{align*}
$$
Comprobación de la solución:

$x_1 = 11/5,\qquad x_2 = 1/5$
Ambos son positivos (satisface la no negatividad)
$-11/5 + 1/5 = -2$ (cumple la primera restricción)
$2(11/5) + 3(1/5) = 22/5 + 3/5 = 5$ (cumple la segunda restricción)
$Z = 5(11/5) + 2(1/5) = 11 + 2/5 = 12.4$

Por lo tanto, la solución óptima es

Primal: $x_1^* = 11/5, x_2^* = 1/5, Z^* = 12.4$
Dual: $y_1^* = 0, y_2^* = 5/2, W^* = 12.5$

Esta solución satisface todas las restricciones y condiciones de holgura complementarias.
## 6.b
$$\begin{align*}\min z&=6x_1+3x_2\\6x_1-3x_2+x_3&\leq-2\\3x_1+4x_2+x_3&\geq5\\x_1,x_2,x_3&\geq0\end{align*}
$$
Su forma estándar: $$\begin{align*}\min z&=6x_1+3x_2\\6x_1-3x_2+x_3&\leq-2\\-3x_1-4x_2-x_3&\leq-5\\x_1,x_2,x_3&\geq0\end{align*}$$
Por lo tanto, su dual: 
$$\begin{align*}
\max z&=-2y_1-5y_2\\6y_1-3y_2&\leq 6\\-3y_1-4y_2&\leq3\\y_1-y_2&\leq0\\y_1,y_2&\geq0
\end{align*}$$
Tenemos un sistema de 3 ecuaciones con dos variables, se puede resolver fácilito: $$\begin{align*}\text{De la restrc. 1: }& 2y_1-y_2\leq2\implies2y_1-2\leq y_2\\\text{De la restrc. 3: }&y_1-y_2\leq0\implies y_1\leq y_2\end{align*}$$

![[Pasted image 20241102104608.png]]

Vemos que en los puntos: 
$$\begin{align*}y_1=0,y_2=0&\implies z=0\\y_1=2,y_2=2&\implies z=-14\\y_1=1,y_2=1&\implies z=-7\\\end{align*}$$
El máximo está en 0,0, esto significa que $z=0,x_1=0,x_2=0$:
$$\begin{align*}x_3-s_1&\leq-2\implies x_3\leq-2+s_1\\x_3+s_2&\geq5\implies x_3\geq5-s_2\\5-s_2\leq x_3\leq-2+s_1&\implies 7\leq x_3\end{align*}$$
## 6.c
$$\begin{align*}\max z=x_1+x_2\\2x_1+x_2=5\\3x_1-x_2=6\\x_1,x_2\geq0\end{align*}$$
Su forma dual: $$\begin{align*}\min w=5y_1+6y_2\\2y_1+3y_2\geq1\\y_1-y_2\geq 1\end{align*}$$
Como está fácil, podemos sustituir $y_1=1+y_2$ en la primera restricción: $$\begin{align*}2(1+y_2)+3y_2=1\\2+5y_2=1\\y_2 = \frac{-1}{5}
\\\therefore y_1=\frac{4}{5}\end{align*}$$
Vemos que claramente las restricciones se cumplen co estos valores y que $w=\frac{14}{5}$.
Resolviendo el sistema de dos ecuaciones y dos variables en la forma primal tenemos que: $x_1=\frac{11}{5},x_2=5-2(\frac{11}{5})=\frac{3}{5}$, de donde $z=\frac{14}{5}$. Vemos que $w^*=z^*$, por lo tanto se cumple y es óptimo.
# 8
$$\begin{align*}\min z=6x_1+7x_2+3x_3+5x_4\\5x_1+6x_2-3x_3+4x_4\geq 12\\x_2-5x_3-6x_4\geq10\\2x_1+5x_2+x_3+x_4\geq8\\x_1,x_2,x_3,x_4\geq0\end{align*}$$
## Dual simplex
$$\begin{align*}\min z-6x_1-7x_2-3x_3-5x_4=0\\-5x_1-6x_2+3x_3-4x_4+s_1= -12\\-x_2+5x_3+6x_4+s_2=-10\\-2x_1-5x_2-x_3-x_4+s_3=-8\\x_1,x_2,x_3,x_4\geq0\end{align*}$$
 ![[Pasted image 20241102114738.png]]
 Vemos que $x_2=2, z=14$
# 11 
Klein Chemicals, Inc. produce un material especial con una base de petróleo que actualmente esta escaso. Cuatro de los clientes de Klein ya han colocado pedidos que en conjunto exceden la capacidad combinada de sus dos plantas. La gerencia de la empresa enfrenta el problema de decidir cuántas unidades debe proveer a cada cliente. Debido a que los cuatro clientes pertenecen a diferentes sectores de la industria y existen varias estructuras de precios según la industria, se pueden asignar distintos precios. Sin embargo, los costos de producción son ligeramente diferentes en las 2 plantas y los costos de transporte entre las plantas y los clientes varían, por lo que una estrategia de "vender al mejor postor", no es aceptable. después de considerar el precio, los costos de producción, y de transporte, se establecieron las siguientes utilidades por unidad para cada alternativa de planta-cliente:

Cliente

| Planta                 | D1  | D2  | D3  | D4  |
| ---------------------- | --- | --- | --- | --- |
| Clifton<br><br>Springs | $32 | $34 | $32 | $40 |
| Danville               | $34 | $30 | $28 | $38 |

las capacidades de la planta y los pedidos de los clientes son los siguientes:

| Planta          | Capacidad (unidades) | Pedidos de distribuidor (unidades) |
| --------------- | -------------------- | ---------------------------------- |
| Clifton Springs | 5000                 | D_1: 2000<br>D_2: 5000             |
| Danville        | 3000                 | D_3: 3000<br>D_4: 2000             |

¿Cuántas unidades debe producir cada planta para cada cliente con el fin de maximizar las utilidades?
¿Cuáles demandas de los clientes no se cumplirán?

## Usando Vogel

| origen/destino | D1   | D2   | D3   | D4   | oferta | c.o. |
| -------------- | ---- | ---- | ---- | ---- | ------ | ---- |
| CS             | 32   | 34   | 32   | 40   | 5000   | [8]  |
| DV             | 34   | 30   | 28   | 38   | 3000   | [10] |
| demanda        | 2000 | 5000 | 3000 | 2000 | ---    | ---  |
| dif            | [2]  | [4]  | [4]  | [2]  | ---    | ---  |

Donde: CS = Clifton Springs, DV = Danville

| origen/destino | D1   | D2   | D3     | D4   | oferta | c.o. |
| -------------- | ---- | ---- | ------ | ---- | ------ | ---- |
| CS             | 32   | 34   | 32     | 40   | 5000   | [8]  |
| DV             | 34   | 30   | ~~28~~ | 38   | ~~0~~  | ---  |
| demanda        | 2000 | 5000 | ~~0~~  | 2000 | ---    | ---  |
| c.o.           | [2]  | [4]  | ---    | [2]  | ---    | ---  |

De aquí tomamos CS-D4 ya que tiene el costo de oportunidad más alto, y nos queda: 

| origen/destino | D1   | D2   | D3     | oferta | c.o. |
| -------------- | ---- | ---- | ------ | ------ | ---- |
| CS             | 32   | 34   | 32     | 3000   | [2]  |
| DV             | 34   | 30   | ~~28~~ | 0      | ---  |
| demanda        | 2000 | 5000 | ~~0~~  | ---    | ---  |
| c.o.           | [2]  | [4]  | ---    | ---    | ---  |

| origen/destino | D1   | D2     | oferta | c.o. |
| -------------- | ---- | ------ | ------ | ---- |
| CS             | 32   | ~~34~~ | 0      | ---  |
| DV             | 34   | 30     | 0      | ---  |
| demanda        | 2000 | 2000   | ---    | ---  |
| c.o.           | [2]  | [4]    | ---    | ---  |

### Resultado: 
1. DV→D3: 1000 
2. CS→D4: 2000 
3. CS→D2: 3000 
4. DV→D1: 2000 

### Tabla Final

| origen/destino | D1   | D2   | D3   | D4   | oferta |
| -------------- | ---- | ---- | ---- | ---- | ------ |
| CS             | 0    | 3000 | 0    | 2000 | 5000   |
| DV             | 2000 | 0    | 1000 | 0    | 3000   |
| demanda        | 2000 | 5000 | 3000 | 2000 | 12000  |

## Total:
- CS→D2: 3000 × $34 = $102,000
- CS→D4: 2000 × $40 = $80,000
- DV→D1: 2000 × $34 = $68,000
- DV→D3: 1000 × $28 = $28,000
Total = $278,000

## Demandas no cumplidas: 
- D2: 2000 (recibió 3000 de 5000)
- D3: 2000 (recibió 1000 de 3000)