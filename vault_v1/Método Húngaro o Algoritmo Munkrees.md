#linealprogramming 

Para **problemas de asignación**, similar a un problema de transporte como se vio en [[Método esquina noroeste, costo mas bajo, Vogel]]

| Niñas / Niños | 1   | 2   | 3   | 4   | Oferta |
| ------------- | --- | --- | --- | --- | ------ |
| A             | 4   | 2   | 1   | 3   | 1      |
| B             | 1   | 4   | 3   | 2   | 1      |
| C             | M   | 2   | 1   | 3   | 1      |
| D             | 1   | 3   | 2   | M   | 1      |
| Demanda       | 1   | 1   | 1   | 1   |        |
Usando el método de costo más bajo, nos saldrá una con M, que es un número muy alto. 

# Método

1. Sacamos el min de cada renglón 

| Niñas / Niños | 1     | 2   | 3   | 4     | Min |
| ------------- | ----- | --- | --- | ----- | --- |
| A             | 4     | 2   | 1   | 3     | 1   |
| B             | 1     | 4   | 3   | 2     | 1   |
| C             | M=100 | 2   | 1   | 3     | 1   |
| D             | 1     | 3   | 2   | M=100 | 1   |
2. Se le resta a cada valor del renglón

| Niñas / Niños | 1   | 2   | 3   | 4   |
| ------------- | --- | --- | --- | --- |
| A             | 3   | 1   | 0   | 2   |
| B             | 0   | 3   | 2   | 1   |
| C             | 99  | 1   | 0   | 2   |
| D             | 0   | 2   | 1   | 99  |
3. Se saca el mínimo de cada columna 

| Niñas / Niños | 1   | 2   | 3   | 4   |
| ------------- | --- | --- | --- | --- |
| A             | 3   | 1   | 0   | 2   |
| B             | 0   | 3   | 2   | 1   |
| C             | 99  | 1   | 0   | 2   |
| D             | 0   | 2   | 1   | 99  |
| Minimo        | 0   | 1   | 0   | 1   |
4. Restarlo a la columna

| Niñas / Niños | 1   | 2   | 3   | 4   |
| ------------- | --- | --- | --- | --- |
| A             | 3   | 0   | 0   | 1   |
| B             | 0   | 2   | 2   | 0   |
| C             | 99  | 0   | 0   | 1   |
| D             | 0   | 1   | 1   | 98  |
5. Se asigna donde haya ceros, los que tengan una sola opción, en este caso el 4 con B.
	1. 1 solo tiene una opción, 1D
	2. 2 y 3 tienen dos, a escoger, 3A, C2
6. Se calcula el costo usando el original. 

## Ejercicio

|     | A   | B   | C   | D   | E   |
| --- | --- | --- | --- | --- | --- |
| 1   | 6   | 12  | 3   | 11  | 15  |
| 2   | 4   | 2   | 7   | 1   | 10  |
| 3   | 8   | 11  | 10  | 7   | 11  |
| 4   | 16  | 19  | 12  | 23  | 21  |
| 5   | 9   | 5   | 7   | 6   | 10  |

|     | A   | B   | C   | D   | E   | Min |
| --- | --- | --- | --- | --- | --- | --- |
| 1   | 6   | 12  | 3   | 11  | 15  | 3   |
| 2   | 4   | 2   | 7   | 1   | 10  | 1   |
| 3   | 8   | 11  | 10  | 7   | 11  | 7   |
| 4   | 16  | 19  | 12  | 23  | 21  | 12  |
| 5   | 9   | 5   | 7   | 6   | 10  | 5   |

|     | A   | B   | C   | D   | E   |
| --- | --- | --- | --- | --- | --- |
| 1   | 3   | 9   | 0   | 8   | 12  |
| 2   | 3   | 1   | 6   | 0   | 9   |
| 3   | 1   | 4   | 3   | 0   | 4   |
| 4   | 4   | 7   | 0   | 11  | 9   |
| 5   | 4   | 0   | 2   | 1   | 5   |

|     | A   | B   | C   | D   | E   |
| --- | --- | --- | --- | --- | --- |
| 1   | 3   | 9   | 0   | 8   | 12  |
| 2   | 3   | 1   | 6   | 0   | 9   |
| 3   | 1   | 4   | 3   | 0   | 4   |
| 4   | 4   | 7   | 0   | 11  | 9   |
| 5   | 4   | 0   | 2   | 1   | 5   |
| Min | 1   | 0   | 0   | 0   | 4   |

|     | A   | B   | C   | D   | E   |
| --- | --- | --- | --- | --- | --- |
| 1   | 2   | 9   | 0   | 8   | 8   |
| 2   | 2   | 1   | 6   | 0   | 5   |
| 3   | 0   | 4   | 3   | 0   | 0   |
| 4   | 3   | 7   | 0   | 11  | 5   |
| 5   | 3   | 0   | 2   | 1   | 1   |
A-3, B-5, C-1, D-2.
Quitando renglones y columnas donde se ocupan esta asignación, vemos que que da E5, por lo que no es óptimo y hacemos slide 152 **preguntar**
# Problema 
Roscoe Davis, presidente del departamento de negocios de una universidad, ha decidido aplicar un método nuevo para asignar a profesores a los cursos del siguiente semestre. Como criterio para juzgar quién debe enseñar cada curso, el señor Davis revisa las evaluaciones de profesores (hechas por estudiantes) de los dos años anteriores. Como cada uno de los cuatro profesores ha enseñado los cuatro cursos en algún momento durante los dos años, Davis puede registrar una puntuación del curso para cada profesor.
Las puntuaciones se muestran en la tabla que sigue. Encuentre la mejor asignación de profesores para los cursos que maximice la puntuación general de enseñanza.

| Profesor/ Curso | Estadística | Administración | Finanzas | Economía |
| --------------- | ----------- | -------------- | -------- | -------- |
| Anderson        | 90          | 65             | 95       | 40       |
| Sweeney         | 70          | 60             | 80       | 75       |
| Williams        | 85          | 40             | 80       | 60       |
| McKinney        | 55          | 80             | 65       | 55       |
Usando el método húngaro para maximización (buscamos el número más grande de toda la matriz y se lo restamos, continuamos como un problema de minimización)

| Profesor/ Curso | Estadística | Administración | Finanzas | Economía | Min |
| --------------- | ----------- | -------------- | -------- | -------- | --- |
| Anderson        | 5           | 30             | 0        | 55       | 0   |
| Sweeney         | 25          | 35             | 15       | 20       | 15  |
| Williams        | 10          | 55             | 15       | 35       | 10  |
| McKinney        | 40          | 15             | 30       | 40       | 15  |

| Profesor/ Curso | Estadística | Administración | Finanzas | Economía |
| --------------- | ----------- | -------------- | -------- | -------- |
| Anderson        | 5           | 30             | 0        | 55       |
| Sweeney         | 10          | 20             | 0        | 5        |
| Williams        | 0           | 45             | 5        | 25       |
| McKinney        | 25          | 0              | 15       | 25       |
| Min             | 0           | 0              | 0        | 5        |

| Profesor/ Curso | Estadística | Administración | Finanzas | Economía |
| --------------- | ----------- | -------------- | -------- | -------- |
| Anderson        | 5           | 30             | 0        | 50       |
| Sweeney         | 10          | 20             | 0        | 0        |
| Williams        | 0           | 45             | 5        | 20       |
| McKinney        | 25          | 0              | 15       | 20       |
Hacemos la asignación (donde hay ceros): A-3, B-4, C-1, D-2
# Problema 
Minimizar

| Contratista / Edificio | 1   | 2   | 3   | 4   |
| ---------------------- | --- | --- | --- | --- |
| 1                      | 58  | 58  | 60  | 54  |
| 2                      | 66  | 70  | 70  | 78  |
| 3                      | 106 | 104 | 100 | 95  |
| 4                      | 52  | 54  | 64  | 54  |

| Contratista / Edificio | 1   | 2   | 3   | 4   | Min |
| ---------------------- | --- | --- | --- | --- | --- |
| 1                      | 4   | 4   | 6   | 0   | 54  |
| 2                      | 0   | 4   | 4   | 12  | 66  |
| 3                      | 11  | 9   | 5   | 0   | 95  |
| 4                      | 0   | 2   | 12  | 2   | 52  |

| Contratista / Edificio | 1   | 2   | 3   | 4   |
| ---------------------- | --- | --- | --- | --- |
| 1                      | 4   | 2   | 2   | 0   |
| 2                      | 0   | 2   | 0   | 12  |
| 3                      | 11  | 7   | 1   | 0   |
| 4                      | 0   | 0   | 8   | 2   |
| Min                    | 0   | 2   | 4   | 0   |

| Contratista / Edificio | 1     | 2     | 3     | 4      |
| ---------------------- | ----- | ----- | ----- | ------ |
| 1                      | 4     | 2     | 2     | **0**  |
| 2                      | **0** | **2** | **0** | **12** |
| 3                      | 11    | 7     | 1     | **0**  |
| 4                      | **0**     | **0**     | **8**     | **2**  |
No queda la asignación, saco el mínimo no cubierto y se los restas a los que no estén cubiertos, y se lo sumó a la columna que está cubierta. 