#ai 
Generalización más específica que cubra un conjunto de ejemplos positivos de algún fenómeno expresado de una forma no distribuida.

![[Pasted image 20240418161415.png]]

La tabla es el espacio de instancias, con 8 valores posibles.
No es deseable darle todo el espacio de instancias a la computadora, la idea es que la computadora la vaya generando en base a los géneros que le damos.
- Su tamaño se determina en base a $2^{3}$:
	- $2$: número de valores posibles por variable
	- $3$: número de variables
También podemos darle un conjunto de restricciones, es más deseable dar está restricción. Cada restricción puede tomar una de las siguientes formas:
	- Var = val (es decir, la variable Var a fuerza debe tener el valor Val)
	- Var = ? (es decir, el valor de la variable Var es irrelevante--condición "don't care"--en la descripción del fenómeno que estamos queriendo aprender)
	- Var = $\varnothing$ (es decir, ningún valor para la variable Var es válido en el fenómeno que estamos queriendo aprender, lo cual se expresa utilizando el símbolo del conjunto vacío)
- La generalización más amplia es $(?,?,?)$
- La hipótesis más específica: $(\varnothing,\varnothing,\varnothing)$
	- Esto implica que el tamaño del espacio de búsqueda (el espacio de hipótesis) es $4^3=64$, porque hay $3$ variables y cada variable tiene $4$ valores posibles: los dos valores posibles que tiene en el espacio de instancias, más los valores "$?$" y "$\varnothing$". (En realidad, ésta es la cantidad de hipótesis sintácticamente distintas, pero como todas las hipótesis en las que cualquier variable—o combinación de variables—tiene un valor de "$\varnothing$" es equivalente a las demás-dado que en ese caso se sabe que el valor de la variable de salida "Contingencia Ambiental" automáticamente va a ser "No"-entonces la cantidad de hipótesis semánticamente distintas—lo cual es equivalente al tamaño del espacio de búsqueda de hipótesis-realmente es $3^3+1=28$).
		- El $+1$ es cualquier hipótesis que tiene cualquier cantidad de puntos vacíos
		- El $3^3$: valores posibles descartando el $\varnothing$ (i.e. val tiene $2 + ?$ y la potencia porque son número el de variables.

## Algoritmo

![[Pasted image 20240418165734.png]]

- Mostrándole los ejemplos $4$, $1$ y $7$ renglones de la tabla inicial 
	- $h:(\varnothing, \varnothing, \varnothing) \rightarrow (4)(\text{BAJA,BAJA,SI})\rightarrow(1)(\text{BAJA,BAJA,SI})\rightarrow(7)(\text{BAJA,?,?})$ 
		- Si no concuerda el valor con el del anterior, se sube un nivel de generalidad, si era $\text{BAJA}$ y luego era $\text{ALTA}$ ahora será $?$
- Mostrándole los ejemplos $2$, $8$ y $7$ renglones de la tabla inicial 
	- $h:(\varnothing, \varnothing, \varnothing) \rightarrow (2)(\varnothing, \varnothing, \varnothing)\rightarrow(8)(\text{BAJA,BAJA,NO})\rightarrow(7)(\text{BAJA,?,NO})$
		- Vemos que la hipótesis se ve diferente.
![[Pasted image 20240418161415.png]]