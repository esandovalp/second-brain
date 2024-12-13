#linealprogramming 
Su característica principal es que hay nodos entre a y 1, similar a lo visto en [[Metodo Dual]], los cuales no tienen ni demanda ni oferta.
# Planteación
Sea $x_{ik}=$ número de unidades transportadas desde el nodo de oferta $i$ al nodo de trasbordo $k$. Sea $y_{kj}=$ número de unidades transportadas desde el nodo de trasbordo $j$ al nodo de demanda $k$.
Función objetivo: $$\min z=c_{A,t_1}x_{A,t_1}+c_{A,t_2}x_{A,t_2}+c_{B,t_1}x_{B,t_1}+...+c_{t_1,1}y_{t_1,1}+...+$$
Restricciones:
1. $X_{A,t_1}+X_{A,t_2}\leq a_A$
	1. Así para asegurar que esté todo lo que sale desde cada nodo. 
	2. Representan los nodos de oferta.
2. $Y_{t_1,1}+Y_{t_2,1}\geq d_1$
	1. Representan los nodos de demanda
3. $X_{A,t_1}+X_{B,t_1}+X_{C,t_1} = Y_{t_1,1}+Y_{t_1,2}+Y_{t_1,3}$
	1. Representan el trasborde

Para pasarlo a un problema de transporte:
En cada celda hay un costo, y S es la suma de todo para cada uno (oferta y demanda)

| Origen \ Destino | $t_1$       | $t_2$ | 1           | 2     | 3     | 4     | Oferta |
| ---------------- | ----------- | ----- | ----------- | ----- | ----- | ----- | ------ |
| A                | $C_{A,t_1}$ |       | M           | M     | M     | M     | $a_1$  |
| B                |             |       | M           | M     | M     | M     | $a_2$  |
| C                |             |       | M           | M     | M     | M     | $a_3$  |
| $t_1$            | M           | M     | $C_{t_1,1}$ |       |       |       | S      |
| $t_2$            | M           | M     |             |       |       |       | S      |
| Demanda          | S           | S     | $d_1$       | $d_2$ | $d_3$ | $d_4$ |        |
# Problema 
Lead Shoes debe determinar cuántos pares de zapatos debe producir durante cada uno de los siguientes cuatro meses. La demanda de pares de zapatos en cada mes es como sigue: primer mes, 40 pares; segundo mes, 60 pares; tercer mes, 75 pares; cuarto mes, 25 pares. Lead Shoes debe satisfacer la demanda a tiempo. Al comienzo del primer mes, la empresa tiene un inventario de 10 zapatos. Al inicio de cada mes, Lead Shoes debe decidir cuántos pares debe producir durante el trimestre actual. Durante cada mes, produce hasta 40 pares a un costo de 400 pesos por par. Si los empleados trabajan horas extra en un mes, se pueden producir 20 pares más a un costo de 450 pesos cada uno. Al final de cada mes, después de satisfacer la demanda respectiva, se incurre en un costo de inventario de 20 pesos por cada par. Dar una estrategia que permita minimizar los costos de producción e inventarios durante los siguientes cuatro meses.

| Origen \ Destino | 1     | 2     | 3     | 4     | Oferta |
| ---------------- | ----- | ----- | ----- | ----- | ------ |
| 0                | (0)   | (20)  | (40)  | (60)  | 10     |
| 1 - normal       | (400) | (420) | (440) | (460) | 40     |
| 1 - extra        | (450) | (470) | (490) | (510) | 20     |
| 2 - normal       | (M)   | (400) | (420) | (440) | 40     |
| 2 - extra        | (M)   | (450) | (470) | (490) | 20     |
| 3 - normal       | (M)   | (M)   | (400) | (420) | 40     |
| 3 - extra        | (M)   | (M)   | (450) | (470) | 20     |
| 4 - normal       | (M)   | (M)   | (M)   | (400) | 40     |
| 4 - extra        | (M)   | (M)   | (M)   | (450) | 20     |
| Demanda          | 40    | 60    | 75    | 25    |        |
