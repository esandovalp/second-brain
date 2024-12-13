#linealprogramming 
## Pasos a seguir: 
1. Las $\geq$ pasan a $\leq$, pero con $=$ y se multiplican por $-1$, si están inicialmente como $\leq$ entonces quedan igual
2. En la función objetivo, si es max, todos se pasan del lado de la $z$, y consecuentemente, se iguala a 0. 
3. Una vez esta planetado, se sigue para resolver los tablaeu: 
	1. Se escoge la que está más negativa en b como <mark style="background: #ADCCFFA6;">variable saliente</mark>. 
	2. Se escogen los negativos en ese renglón y dividimos el valor absoluto $z$ de su columna, entre el valor absoluto de el renglón de la variable saliente.
	3. Se resuelve normal como Gauss-Jordan.
	4. Es factible cuando las columnas de las $b$ son positivas, exceptuando $z$
	5. Es óptima cuando los coeficientes de las $z$ son positivos (si es max, si es min acaba cuando son negativos), exceptuando a las $b$ 
# Ejercicio 
Función objetivo: $\min z=x_1+2x_2+3x_3$
S.A:
$$\begin{align*}
2x_1-x_2+x_3\geq 2\\
3x_1+x_2+7x_3\leq 3 \\
x_1+4x_2+6x_3\leq 5 \\
x_1,x_2,x_3\geq 0
\end{align*}
$$
La condición de $\geq$ <mark style="background: #FF5582A6;">me obliga a usar Dual Simplex</mark>
## Dual simplex
Función objetivo: $\min z-x_1-2x_2-3x_3=0$
S.A:
$$\begin{align*}
-2x_1+x_2-x_3+u_1= -2\\
3x_1+x_2+7x_3+u_2 = 3 \\
x_1+4x_2+6x_3+u_3 = 5 \\
x_1,x_2,x_3\geq 0
\end{align*}
$$
![[Pasted image 20241010171323.png]]
El resultado es que $x_1=1$ y las demás 0. 
Si fuera maximizar el problema, entonces se seguiría después del 2do tableau siguiendo el método de simplex en su forma normal (sin tener que sacar valor absoluto, etc).