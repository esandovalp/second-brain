#linealprogramming 

Se usa para problemas de demanda y oferta en transporte.

1. Se ve la esquina superior izquierda (noroeste).
2. Si la demanda (su columna, ultimo renglon) no se cumple (oferta, mismo renglon ultima columna), entonces el siguiente renglon (se quita el renglón donde inicio) en la misma columna tendrá que dar lo que falta. 
3. Si se cumple se borra el renglón y la columna y se toma la esquina noroeste.

Se cancela la columna o renglón hasta que este cubierta la demanda o hasta que ya no podamos dar más en la oferta.
Nos da un costo, el cual es factible pero no sabemos si es óptimo.

# Método del costo más bajo

Es similar solo que toma la posición en la matriz que tenga el costo más bajo.

# Método de Vogel 

También se le llama Heurística de Vogel. 

1. Se saca la diferencia entre los dos costos más bajos entre columnas y renglones, estos son los costos de oportunidad.
2. Se toma el costo de oportunidad más grande, puede ser de toda una columna o de todo un renglón.
3. De la columna o renglón tomamos el costo más barato y hacemos lo mismo que en los métodos anteriores. 
4. Cambian los costos de oportunidad cuando no se puede usar una columna o renglón, se actualizan sacando la diferencia entre los nuevos costos de oportunidad.

# Solución del Método de Aproximación de Vogel's  
  
## Tabla Inicial  
```  
Atlanta Dallas Columbus Boston Suministro Penalización  
Phila 2 6 6 2 5000 0*  
N.Orl 1 2 5 7 3000 1  
Demanda 1400 3200 2000 1400  
Penalización 1 4 1 5  
```  
  
## Paso 1: Penalizaciones iniciales  
Penalizaciones de fila (la segunda más baja - la más baja):  
- Philadelphia: 2-2 = 0*  
- Nueva Orleans: 2-1 = 1  
  
Penalizaciones de columna (segunda más baja - más baja):  
- Atlanta: 2-1 = 1  
- Dallas: 6-2 = 4  
- Columbus 6-5 = 1  
- Boston: 7-2 = 5*  
  
*La penalización más alta es 5 (columna de Boston)  
  
## Paso 2: Primera Asignación  
Asignar al coste más bajo de la columna Boston (Filadelfia-Boston = 2)  
Asignar 1400 unidades (toda la demanda de Boston)  
  
Tabla actualizada:  
```  
Atlanta Dallas Columbus Boston Suministro Penalización  
Phila 2 6 6 - 3600 4  
N.Orl 1 2 5 - 3000 1  
Demanda 1400 3200 2000 -  
Penalización 1 4 1  
```  
  
## Continuar Proceso  
La siguiente penalización más alta es 4 (columna Dallas)  
Asignar a Nueva Orleans-Dallas (coste=2) = 3000 unidades  
200 unidades restantes de Filadelfia a Dallas  
  
Luego asignar:  
- Filadelfia a Atlanta 1400 unidades  
- Filadelfia a Columbus: 2000 unidades  
  
## Solución Final  
```  
Desde Filadelfia  
- Atlanta: 1400 × $2 = $2,800  
- Dallas: 200 × $6 = $1,200  
- Columbus: 2000 × $6 = $12.000  
- Boston: 1400 × $2 = $2.800  
  
Desde Nueva Orleans  
- Dallas: 3000 × $2 = $6.000  
  
Coste total = 24.800 $  
```  
  
## Verificación de la optimalidad mediante la holgura complementaria  
  
Sean ui y vj las variables duales.  
Para variables básicas (celdas con flujo positivo), tenemos:  
cij = ui + vj  
  
Fijando u1 = 0 (para Filadelfia):  
- De Filadelfia-Atlanta: 2 = u1 + v1 → v1 = 2  
- De Filadelfia a Dallas: 6 = u1 + v2 → v2 = 6  
- Desde Filadelfia-Columbus: 6 = u1 + v3 → v3 = 6  
- Desde Filadelfia-Boston: 2 = u1 + v4 → v4 = 2  
  
Desde Nueva Orleans-Dallas: 2 = u2 + v2 → u2 = -4  
  
Comprobación de variables no básicas:  
- Nueva Orleans-Atlanta: 1 > -4 + 2 = -2 (satisfecho)  
- Nueva Orleans-Columbus: 5 > -4 + 6 = 2 (satisfecho)  
- Nueva Orleans-Boston: 7 > -4 + 2 = -2 (se cumple)  
  
Se cumplen todas las condiciones, lo que confirma la optimalidad.