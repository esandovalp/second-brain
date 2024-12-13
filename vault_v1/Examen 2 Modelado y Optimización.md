# Ejercicio 1 
$$\begin{align*}\min z=3x_1+2x_2+3x_3\\x_1+4x_2+x_3\geq7\\2x_1+x_2+x_4\geq 10\\x_1,x_2,x_3,x_3\geq 0\end{align*}$$
- Resolver mediante M grande (1.0 puntos)
- Resolver mediante dos fases (1.0 puntos)
- Resolver mediante Dual Simplex (1.0 puntos)
- Resolver mediante Simplex revisado (1.0 puntos)
# Dual Simplex 
$$\begin{align*}\min z-3x_1-2x_2-3x_3=0\\-x_1-4x_2-x_3+u_1=-7\\-2x_1-x_2-x_4+u_2= -10\\x_1,x_2,x_3,x_3\geq 0\end{align*}$$
![[Pasted image 20241105151744.png]]
$$x_2=1.75,x_4=8.25,z=3.5$$
# Simplex revisado 
$$\begin{align*}\min z=3x_1+2x_2+3x_3\\x_1+4x_2+x_3-s_1+a_1=7\\2x_1+x_2+x_4-s_2+a_2= 10\\x_1,x_2,x_3,x_3\geq 0\end{align*}$$
Fase 1: $$\min w=a_1+a_2$$
![[Pasted image 20241105153809.png]]
Fase 2: $$\min z=3x_1+2x_2+3x_3$$
![[Pasted image 20241105154856.png]]
$$x_3=7,x_4=10,z=-21$$
![[Pasted image 20241105155527.png]]
# Ejercicio 2 
Gutchi Company fabrica bolsos de mano, bolsas para rasuradora y mochilas. La construcción de los tres productos requiere piel y materiales sintéticos, dado que la piel es la materia prima limitante. El proceso de producción utiliza dos tipos de mano de obra calificada: costura y terminado. La siguiente tabla da la disponibilidad de los recursos, su uso por los tres productos, y los precios por unidad:

| Recurso             | Requerimiento de recursos por unidad |                       |         | Disponibilidad diaria |
| ------------------- | ------------------------------------ | --------------------- | ------- | --------------------- |
|                     | Bolso de mano                        | Bolsa para rasuradora | Mochila |                       |
| Piel (ft²)          | 2                                    | 1                     | 3       | 42                    |
| Costura (hr)        | 2                                    | 1                     | 3       | 40                    |
| Terminado (hr)      | 1                                    | 0.5                   | 1       | 45                    |
| Precio de venta ($) | $24                                  | $22                   | $45     |                       |
Formule el problema como una programación lineal, y determine la solución óptima (0.5 pt). A continuación, indique si los siguientes cambios en los recursos mantendrán factible la solución actual. En los casos donde la factibilidad u optimalidad se pierden, determine la nueva solución óptima (valores de las variables y la función objetivo).
- La piel disponible se incrementa a 45 ft² (0.5 pt).
- La piel disponible se reduce en 1 ft² (0.5 pt)
- Las horas de costura disponibles se cambian a 38 (0.5 pt).
- Las horas de costura disponibles se cambian a 46 (0.5 pt).
- Las horas de terminado disponibles se reducen a 15 (0.5 pt).
- Las horas de terminado disponibles se incrementan a 50 (0.5 pt).
- Recomendaría contratar una costurera más a $15 la hora? (0.5 pt)
## Formulación del problema lineal 
$$\begin{align*}x_1,x_2,x_3:\text{no. a fabricar de bolsa de mano, de rasuradora, mochila}\\\max z=24x_1+22x_2+45x_3\\2x_1+x_2+3x_3\leq42\\2x_1+x_2+3x_3\leq40\\x_1+0.5x_2+x_3\leq45\\x_1,x_2,x_3\geq0\end{align*}$$
Resolviendo con simplex. 
$$\begin{align*}\max z=24x_1+22x_2+45x_3\\2x_1+x_2+3x_3+s_1=42\\2x_1+x_2+3x_3+s_2=40\\x_1+0.5x_2+x_3+s_3=45\\x_1,x_2,x_3,s_1,s_2,s_3\geq0\end{align*}$$
![[Pasted image 20241105163112.png]]
Tenemos que $$x_2=40$$
A) La piel disponible se incrementa a 45 ft² (0.5 pt)
![[Pasted image 20241105163230.png]]
Vemos que no hay cambios.
B) La piel disponible se reduce en 1 ft² (0.5 pt)
![[Pasted image 20241105163323.png]]
No hay cambio.
C) Las horas de costura disponibles se cambian a 38 (0.5 pt).
![[Pasted image 20241105163441.png]]
Cambia a $$x_2=38,z=836$$
D) Las horas de costura disponibles se cambian a 46 (0.5 pt).
![[Pasted image 20241105163651.png]]
Se vuelve **infactible** ya que hay s1 se vuelve negativo. 
E) Las horas de terminado disponibles se reducen a 15 (0.5 pt).
![[Pasted image 20241105164136.png]]
La solución es: $$x_3=10,x_2=10,z=670$$
F) Las horas de terminado disponibles se incrementan a 50 (0.5 pt).
![[Pasted image 20241105164351.png]]
No hay cambio
G) Recomendaría contratar una costurera más a $15 la hora? (0.5 pt)
Subiendole el precio a cada uno a (15/3=5) vemos que: 
![[Pasted image 20241105165233.png]]
La función objetivo sube sin que suba la cantidad de bolsa para rasuradora, por lo tanto sí es recomendable. 
Esta se sacaba con el dual, 