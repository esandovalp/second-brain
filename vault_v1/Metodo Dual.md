#linealprogramming 
- Factible en el **primal** y **factible** dual es la única manera de obtener un **óptimo**
# Ejercicio 
 
- $x_1$: número de lbs a comprar del producto 1
- $x_2$: número de lbs a comprar del producto 2 

Función objetivo: $\min z=2(\frac{\$}{lbs}lbs)x_1+3x_2$
S.A:
$$\begin{align*}
5x_1+10x_2\geq 90\\
4x_1+3x_2\geq 48 \\
0.5x_1\geq 1.5 \\
x_1,x_2\geq 0
\end{align*}
$$
## Traduciéndolo a Dual:

- $y_i$: costo de cada onza del ingrediente $i$

Función objetivo: $\max z=90(oz\frac{\$}{oz})y_1+48y_2+1.5y_3, \text{ Así queda como dinero, igual que en la función original}$
S.A:
$$\begin{align*}
5y_1+4y_2+0.5y_3\leq 2\\
10y_1+3y_2\leq 3 \\
y_1,y_2,y_3\geq 0
\end{align*}
$$
Resolviendo obtenemos: $y_1=0.24, y_2=0.2,y_3=0$

Usando el [[Teorema de Holguras Complementarias]], vemos que entonces las primeras dos restricciones del problema original tienen que ser igualdades, por lo tanto, tenemos: 
$$\begin{align*}
5x_1+10x_2 = 90\\
4x_1+3x_2 = 48 
\end{align*}
$$
Esto se puede resolver fácilmente, de aquí tenemos que: $x_1=8.4,x_2=4.8$, que son las $u_1,u_2$, que salen en el último tableau del simplex del Dual.

# Ejercicio
![[IMG_0216.jpeg]]

1. Ver que se cumpla que la demanda y oferta sean igual.
2. Factible del primal con [[Método esquina noroeste, costo mas bajo, Vogel]]
3. Si la que tenemos es factible dual, bien
4. Si no, corregir hasta que este bien.

| Plantas | 1   | 2   | 3   | 4   | Oferta |
| ------- | --- | --- | --- | --- | ------ |
| A       | 9   | 15  | 18  | 21  | 550    |
| B       | 23  | 14  | 16  | 10  | 650    |
| Demanda | 200 | 250 | 400 | 350 |        |
$$\begin{align*}
\min z=9a_1+15a_2+18a_3+21a_4+23b_1+14b_2+16b_3+10b_4 \\
a_1+b_1\geq 200\\
a_2+b_2\geq 250\\
a_3+b_3\geq 400\\
a_4+b_4\geq 350\\
a_1+a_2+a_3+a_4\leq 550\\
b_1+b_2+b_3+b_4\leq 650
\end{align*}
$$

Usando **Método de Vogel** 

1. Se saca la diferencia entre los dos costos más bajos entre columnas y renglones, estos son los costos de oportunidad.
2. Se toma el costo de oportunidad más grande, puede ser de toda una columna o de todo un renglón.
3. De la columna o renglón tomamos el costo más barato y hacemos lo mismo que en los métodos anteriores. 
4. Cambian los costos de oportunidad cuando no se puede usar una columna o renglón, se actualizan sacando la diferencia entre los nuevos costos de oportunidad.

## Paso 1 y 2

| Plantas | 1      | 2   | 3   | 4   | Oferta |     |
| ------- | ------ | --- | --- | --- | ------ | --- |
| A       | 9      | 15  | 18  | 21  | 550    | 6   |
| B       | 23     | 14  | 16  | 10  | 650    | 4   |
| Demanda | 200    | 250 | 400 | 350 |        |     |
|         | **14** | 1   | 2   | 11  |        |     |
## Paso 3
| Plantas | 1       | 2   | 3   | 4   | Oferta          |
| ------- | ------- | --- | --- | --- | --------------- |
| A       | 9 (200) | 15  | 18  | 21  | 550 - 200 = 350 |
| B       | 23      | 14  | 16  | 10  | 650             |
| Demanda | 200     | 250 | 400 | 350 |                 |
Se quita la primer columna. 
## Paso 4
| Plantas | 2   | 3   | 4      | Oferta          |     |
| ------- | --- | --- | ------ | --------------- | --- |
| A       | 15  | 18  | 21     | 550 - 200 = 350 | 3   |
| B       | 14  | 16  | 10     | 650             | 4   |
| Demanda | 250 | 400 | 350    |                 |     |
|         | 1   | 2   | **11** |                 |     |
## Repetimos pasos
| Plantas | 2   | 3   | 4        | Oferta         |
| ------- | --- | --- | -------- | -------------- |
| A       | 15  | 18  | 21       | 350            |
| B       | 14  | 16  | 10 (350) | 650 -350 = 300 |
| Demanda | 250 | 400 | 350      |                |
Se quita la cuarta columna

| Plantas | 2            | 3   | Oferta          |       |
| ------- | ------------ | --- | --------------- | ----- |
| A       | **15**       | 18  | 350             | **3** |
| B       | 14           | 16  | 300             | 2     |
| Demanda | 250          | 400 |                 |       |
|         | 1            | 2   |                 |       |
|         |              |     |                 |       |
| Plantas | 2            | 3   | Oferta          |       |
| A       | **15** (250) | 18  | 350 - 250 = 100 | **3** |
| B       | 14           | 16  | 300             | 2     |
| Demanda | 250          | 400 |                 |       |
|         | 1            | 2   |                 |       |

| Plantas | 3               | Oferta        |        |
| ------- | --------------- | ------------- | ------ |
| A       | 18 (100)        | 100 - 100 = 0 | **18** |
| B       | 16 (300)        | 300           | 16     |
| Demanda | 400 - 100 = 300 |               |        |
|         | 3               |               |        |
Costo = 9(200) + 10(350) + 15(250) + 18(100) + 16(300) = 15,650
- $x_{A,1}=200$
- $x_{B,4}=350$
- $x_{A,2}=250$
- $x_{A,3}=100$
- $x_{B,3}=300$
## Dual
Version primal:
$$\begin{align*}
\min z=9a_1+15a_2+18a_3+21a_4+23b_1+14b_2+16b_3+10b_4 \\
a_1+b_1 = 200\\
a_2+b_2 = 250\\
a_3+b_3 = 400\\
a_4+b_4 = 350\\
a_1+a_2+a_3+a_4 = 550\\
b_1+b_2+b_3+b_4 = 650
\end{align*}
$$
Dual: 
$$\begin{align*}
\max z= 550u_A+650u_B+200v_1+250v_2+400v_3+350v_4\\
u_A+v_1\leq 9,\quad u_A+v_2\leq 15,\quad u_A+v_3\leq 18,\quad u_A+v_4\leq 21\\
u_B+v_1\leq 23,\quad u_B+v_2\leq 14,\quad u_B+v_3\leq 16,\quad u_B+v_4\leq 10\\
\end{align*}
$$
Tomando la solución factible del primal, tomamos las desigualdades del dual. Esto es, porque según el [[Teorema de Holguras Complementarias]], si la solución del primal no es cero, en el dual se cumple como igualdad, es una ventaja porque se hace un sistema de ecuaciones.
$$\begin{align*}
u_A+v_1= 9,\quad u_A+v_2= 15,\quad u_A+v_3=18\\
u_B+v_3= 16,\quad u_B+v_4= 10
\end{align*}
$$
5 ecuaciones, 6 variables. Como vimos en la slide 169, podemos tomar una como 0 aunque sea básica, tomando $u_A=0$, tenemos: 
$$\begin{align*}
u_A=0,\quad u_B= -2\\
v_1= 9,\quad v_2= 15,\quad v_3=18, \quad v_4=12
\end{align*}
$$
Ahora, revisando las no básicas, se debe cumplir, también por el THC:
$$\begin{align*}
u_A+v_4-21<0\\
0+12-21<0 \\
u_B+v_1-23<0,\quad u_B+v_2-14<0 \\
-2+9-23<0,\quad-2+15-14<0
\end{align*}
$$
Vemos que se cumplen como desigualdades estrictas. Por lo tanto, como es factible en el primal y factible en el dual, es óptimo. 
Nota: si se hace con método de costo más bajo, no se cumple una condición, por lo que se tiene que usar $\theta$


# Solución de problemas de transporte utilizando el análisis primal-dual  
  
## 1. Formulación del Problema Primal  
  
### Variables de Decisión  
xij = unidades enviadas desde el puerto i al cliente j  
- x11 = Filadelfia a Atlanta  
- x12 = Filadelfia a Dallas  
- x13 = Filadelfia a Columbus  
- x14 = Filadelfia a Boston  
- x21 = Nueva Orleans a Atlanta  
- x22 = Nueva Orleans a Dallas  
- x23 = Nueva Orleans - Columbus  
- x24 = De Nueva Orleans a Boston  
  
### Función Objetivo (Minimizar)  
Min Z = 2x11 + 6x12 + 6x13 + 2x14 + x21 + 2x22 + 5x23 + 7x24  
  
### Sujeto a:  
Restricciones de Oferta:  
- x11 + x12 + x13 + x14 ≤ 5000 (Filadelfia)  
- x21 + x22 + x23 + x24 ≤ 3000 (Nueva Orleans)  
  
Restricciones de la demanda:  
- x11 + x21 = 1400 (Atlanta)  
- x12 + x22 = 3200 (Dallas)  
- x13 + x23 = 2000 (Columbus)  
- x14 + x24 = 1400 (Boston)  
  
No negatividad: xij ≥ 0 para todos i,j  
  
## 2. Formulación del problema dual  
  
### Variables  
ui = variable dual para la restricción de oferta i  
vj = variable dual para la restricción de demanda j  
  
### Función Objetivo (Maximizar)  
Max W = 5000u1 + 3000u2 + 1400v1 + 3200v2 + 2000v3 + 1400v4  
  
### Sujeto a:  
- u1 + v1 ≤ 2 (Filadelfia-Atlanta)  
- u1 + v2 ≤ 6 (Filadelfia-Dallas)  
- u1 + v3 ≤ 6 (Filadelfia-Columbus)  
- u1 + v4 ≤ 2 (Filadelfia-Boston)  
- u2 + v1 ≤ 1 (Nueva Orleans-Atlanta)  
- u2 + v2 ≤ 2 (Nueva Orleans-Dallas)  
- u2 + v3 ≤ 5 (Nueva Orleans-Columbus)  
- u2 + v4 ≤ 7 (Nueva Orleans-Boston)  
  
## 3. Solución utilizando la holgura complementaria  
  
### Condiciones:  
1. Si xij > 0, entonces ui + vj = cij  
2. Si ui + vj < cij, entonces xij = 0  
3. Si hay holgura en la restricción de oferta, entonces ui = 0  
4. Si hay holgura en la restricción de demanda, entonces vj = 0  
  
### Fijación de valores:  
Sea u1 = 0 (referencia Filadelfia)  
  
A partir de la solución básica encontrada por el método de Vogel:  
```  
x11 = 1400 (Phila-Atlanta) → 2 = u1 + v1 → v1 = 2  
x12 = 200 (Phila-Dallas) → 6 = u1 + v2 → v2 = 6  
x13 = 2000 (Phila-Columbus) → 6 = u1 + v3 → v3 = 6  
x14 = 1400 (Phila-Boston) → 2 = u1 + v4 → v4 = 2  
x22 = 3000 (NOrl-Dallas) → 2 = u2 + v2 → u2 = -4  
```  
  
### Comprobación de la optimalidad:  
1. Comprobar variables no básicas:  
- Nueva Orleans-Atlanta: 1 > -4 + 2 = -2 ✓  
- Nueva Orleans-Columbus: 5 > -4 + 6 = 2 ✓  
- Nueva Orleans-Boston: 7 > -4 + 2 = -2 ✓  
  
2. Comprobar la viabilidad primaria:  
Restricciones de suministro:  
- Filadelfia: 1400 + 200 + 2000 + 1400 = 5000 ≤ 5000 ✓  
- Nueva Orleans: 0 + 3000 + 0 + 0 = 3000 ≤ 3000 ✓  
  
Restricciones de la demanda:  
- Atlanta: 1400 + 0 = 1400 ✓  
- Dallas: 200 + 3000 = 3200 ✓  
- Columbus: 2000 + 0 = 2000 ✓  
- Boston: 1400 + 0 = 1400 ✓  
  
3. Comprobar la viabilidad dual:  
Todas las restricciones duales se satisfacen con nuestros valores de u, v ✓  
  
4. Comprobar Dualidad Fuerte:  
Valor objetivo primal:  
= 2(1400) + 6(200) + 6(2000) + 2(1400) + 2(3000)  
= 2800 + 1200 + 12000 + 2800 + 6000  
= 24,800  
  
Valor del doble objetivo:  
= 5000(0) + 3000(-4) + 1400(2) + 3200(6) + 2000(6) + 1400(2)  
= 0 - 12000 + 2800 + 19200 + 12000 + 2800  
= 24,800  
  
Primal = Dual ✓  
  
Por lo tanto, hemos demostrado la optimalidad como:  
1. Se cumplen todas las condiciones de holgura complementarias  
2. La solución es primalmente factible  
3. La solución es factible dual  
4. Se cumple la dualidad fuerte (objetivo primario = objetivo dual)