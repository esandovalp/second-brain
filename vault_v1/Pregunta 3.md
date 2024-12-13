Una empresa importa productos en dos puertos: Filadelfia y Nueva Orleans. Los embarques de uno de los productos se hacen a clientes de Atlanta, Dallas, Columbus y Boston. Para el periodo de planeación siguiente, los suministros en cada puerto, las demandas de los clientes y los costos de envío por caja desde cada puerto, a cada cliente, son los de la siguiente tabla.
![[Pasted image 20241105164752.png]]

- Obtener una solución factible por el método que desee (1.0 pts).
- Obtener o verificar la óptimalidad por medio del teorema de holguras complementarias (1.5 pts)

Vemos que la demanda y la oferta son iguales, por lo tanto podemos proceder.

|               | Cliente |        |          |        | Suministro en puerto |
| ------------- | ------- | ------ | -------- | ------ | -------------------- |
| Puerto        | Atlanta | Dallas | Columbus | Boston |                      |
| Filadelfia    | 2       | 6      | 6        | 2      | 5000                 |
| Nueva Orleans | 1       | 2      | 5        | 7      | 3000                 |
| Demanda       | 1400    | 3200   | 2000     | 1400   |                      |
Usando Vogel: 

|               | Cliente |        |          |              | Suministro en puerto |     |
| ------------- | ------- | ------ | -------- | ------------ | -------------------- | --- |
| Puerto        | Atlanta | Dallas | Columbus | Boston       |                      |     |
| Filadelfia    | 2       | 6      | 6        | **2** (1400) | 5000-1400=3600       | 0   |
| Nueva Orleans | 1       | 2      | 5        | **7**        | 3000                 | 1   |
| Demanda       | 1400    | 3200   | 2000     | 1400         |                      |     |
|               | 1       | 4      | 1        | **5**        |                      |     |

|               | Cliente |               |          | Suministro en puerto |     |
| ------------- | ------- | ------------- | -------- | -------------------- | --- |
| Puerto        | Atlanta | Dallas        | Columbus |                      |     |
| Filadelfia    | 2       | 6             | 6        | 3600                 | 4   |
| Nueva Orleans | 1       | **2** (3000)  | 5        | 3000-3000=0          | 1   |
| Demanda       | 1400    | 3200-3000=200 | 2000     |                      |     |
|               | 1       | **4**         | 1        |                      |     |

|            | Cliente |        |              | Suministro en puerto |     |
| ---------- | ------- | ------ | ------------ | -------------------- | --- |
| Puerto     | Atlanta | Dallas | Columbus     |                      |     |
| Filadelfia | 2       | 6      | **6 (2000)** | 3600-2000=1600       | 4   |
| Demanda    | 1400    | 200    | 2000         |                      |     |
|            | 2       | 6      | 6            |                      |     |

|            | Cliente |             | Suministro en puerto |     |
| ---------- | ------- | ----------- | -------------------- | --- |
| Puerto     | Atlanta | Dallas      |                      |     |
| Filadelfia | 2       | **6 (200)** | 1600-200=1400        | 4   |
| Demanda    | 1400    | 200-200=0   |                      |     |
|            | 2       | **6**       |                      |     |

|            | Cliente     | Suministro en puerto |
| ---------- | ----------- | -------------------- |
| Puerto     | Atlanta     |                      |
| Filadelfia | 2 (1400)    | 1400-1400=0          |
| Demanda    | 1400-1400=0 |                      |
Asignación: 
Desde Filadelfia  
- Atlanta: 1400x$2 = $2800  
- Dallas: 200x$6 = $1200  
- Columbus: 2000x$6 = $12000  
- Boston: 1400x$2 = $2800  
Desde Nueva Orleans  
- Dallas: 3000x$2 = $6000  
  
Coste total = 24800  

Para comprobar su factibilidad usando el [[Teorema de Holguras Complementarias]] tenemos que obtener su versión primal y dual: 

Sea xij = unidades enviadas desde el puerto i al cliente j  
- x11 = Filadelfia a Atlanta  
- x12 = Filadelfia a Dallas  
- x13 = Filadelfia a Columbus  
- x14 = Filadelfia a Boston  
- x21 = Nueva Orleans a Atlanta  
- x22 = Nueva Orleans a Dallas  
- x23 = Nueva Orleans - Columbus  
- x24 = De Nueva Orleans a Boston  

Función objetivo: Min Z = 2x11 + 6x12 + 6x13 + 2x14 + x21 + 2x22 + 5x23 + 7x24
Restricciones de Oferta:  
- x11 + x12 + x13 + x14 ≤ 5000 (Filadelfia)  
- x21 + x22 + x23 + x24 ≤ 3000 (Nueva Orleans)  
  
Restricciones de la demanda:  
- x11 + x21 = 1400 (Atlanta)  
- x12 + x22 = 3200 (Dallas)  
- x13 + x23 = 2000 (Columbus)  
- x14 + x24 = 1400 (Boston)  

Su versión dual: 
Max W = 5000u1 + 3000u2 + 1400v1 + 3200v2 + 2000v3 + 1400v4  
- u1 + v1 ≤ 2 (Filadelfia-Atlanta)  
- u1 + v2 ≤ 6 (Filadelfia-Dallas)  
- u1 + v3 ≤ 6 (Filadelfia-Columbus)  
- u1 + v4 ≤ 2 (Filadelfia-Boston)  
- u2 + v1 ≤ 1 (Nueva Orleans-Atlanta)  
- u2 + v2 ≤ 2 (Nueva Orleans-Dallas)  
- u2 + v3 ≤ 5 (Nueva Orleans-Columbus)  
- u2 + v4 ≤ 7 (Nueva Orleans-Boston)  

Sea u1 = 0 (referencia Filadelfia)  
A partir de la solución básica encontrada por el método de Vogel:  
x11 = 1400 (Phila-Atlanta): 2 = u1 + v1 -> v1 = 2  
x12 = 200 (Phila-Dallas): 6 = u1 + v2 -> v2 = 6  
x13 = 2000 (Phila-Columbus): 6 = u1 + v3 -> v3 = 6  
x14 = 1400 (Phila-Boston): 2 = u1 + v4 -> v4 = 2  
x22 = 3000 (NOrl-Dallas): 2 = u2 + v2 -> u2 = -4  

Comprobando con las v.n.b
- Nueva Orleans-Atlanta: 1 > -4 + 2 = -2 , se cumple 
- Nueva Orleans-Columbus: 5 > -4 + 6 = 2 , se cumple
- Nueva Orleans-Boston: 7 > -4 + 2 = -2 , se cumple

Por lo tanto es óptimo, ya que es factible en el dual y factible en el primal. 