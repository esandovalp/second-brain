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
