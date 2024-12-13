#noveno
# Distribución multinomial
Es la generalización de una binomial. 
Parametros: 
- N
- P
$$P(X_1=n_1,X_2=n_2,...,X_k=n_k)=\frac{n!}{n_1!n_2!...n_k!}p_1^{n_1}p_2^{n_2}...p_k^{n_k}$$
Para $n_1,n_2,...,n_k$ que satisface $n_1+n_2+...+n_k=n$
# Mezclas de normales
Es una combinación lineal de densidades, no de variables aleatorias. 
$$f_X(x)=\sum_{i=1}^{m}a_if_{x_i}(x;\mu_i,\sigma_i^2)$$
donde vemos que $a_i\geq 0, \forall i\in \{1,...,m\}$ (a puede ser la proporción de algo, e.g. de machos y hembras en una población), con  $\sum_{i=1}^{m}a_i=1$, y $f_{x_i}(\cdot,\mu_i,\sigma_i^2)$ es la densidad de una Normal con parámetros $\mu_i,\sigma_i^2$.

## Ejercicio

Sea Y una mezcla de normales con 
$$\begin{align*}
\mu_1=0,\quad \mu_2=1, \quad  \mu_3= 2\\
\sigma_1=1,\quad \sigma_2=1,\quad \sigma_3=1\\
a_1= \frac{1}{3},\quad a_2= \frac{1}{3},\quad a_3= \frac{1}{3}
\end{align*}$$
Calcule la esperanza y varianza.
$$E[Y]= E(E(Y|X))=E(\mu_x)$$
Donde  $X\sim M(1,(\frac{1}{3},\frac{1}{3},\frac{1}{3}))= \frac{1}{3}\cdot0+\frac{1}{3}\cdot1+\frac{1}{3}\cdot2=1$
$Var(Y)=E(Var(Y|X))+Var(E(Y|X))$
$Var(E(Y|X))=Var(\mu_x)=E((\mu_X-E(\mu_x))^2) = E((\mu_x-1)^2$
$=\frac{1}{3}(0-1)^2+\frac{1}{3}(1-1)^2+\frac{1}{3}(2-1)^2= \frac{2}{3}$
$E(Var(Y|X))=E(\sigma_x^2)=1$
Por lo tanto,  $Var(Y)=E(Var(Y|X))+Var(E(Y|X)) = 1 +\frac{2}{3}=\frac{5}{3}$
# Sumas aleatorias
Sea $\{X_1,X_2,...,X_n\}$ una sucesión de variables aleatorias i.i.d y sea N una variable independiente de dicha sucesión y tal que toma valores en $\{1,2,...\}$, definimos una suma aleatoria como: $Y=\sum_{i=1}^{N}X_i \quad$ nos interesa la distribución de Y y sus momentos. 

## Ejercicio 1
Se tira un dado honesto una vez. Una vez observado el número de puntos, se tira una moneda tantas veces como puntos fueron observados. Sea $p=\frac{1}{3}$ la probabilidad de observar águila y Y el número total de águilas observado.
1. ¿Qué valores puede tomar y?
2. ¿Cómo calcularía la distribución de y?
$$X=\sum_{i=1}^NY_i, \quad x\in\{0,1,..,6\}$$
Distribución de X: 
$$P(X=2)=\sum_{i=2}^6P(X=2|N=i)P(N=i)

=\sum_{i=2}^6{\binom{i}{2}(\frac{1}{3})^2(\frac{2}{3})^{i-2}}\frac{1}{6}$$
Por lo tanto,  $P(X=x)= \sum_{x=0}^{6}{}$

## Ejercicio 2

El monto de un siniestro individual es una v.a. con media $\mu$ y varianza $\sigma^2$. La distribución del número de siniestros en un intervalo de longitud $t\sim Poi(\lambda t)$. Sea $Y_t$ el monto total de siniestros en $(0,t]$.
1. Esperanza de Y
2. Varianza de Y

El truco aquí es ver con que condicionar. 
$$X=\sum_{i=1}^NY_i, \quad E(X)=E(E(X|N))

=

E(E(\sum_{i=1}^NY_i|N))

= E(N\mu)=\mu E(N)=\mu \lambda t$$
$Var(X)=E(Var(X|N))+Var(E(X|N))$
$Var(E(X|N))=Var(N\mu)=\mu^2Var(N)=\mu^2\lambda t$
$$E(Var(X|N))= E(Var(\sum_{i=1}^NY_i|N))

= E(\sigma^2N)=\sigma^2\lambda t$$
# Propiedades de la esperanza condicional

1. X y Y independientes  $\implies E(Y|X)=E(Y)$
2. Cualquier función  $h(\cdot),\quad E(h(X)Y|X)=h(X)E(Y|X)$
3. $E(Y_1+Y_2|X)=E(Y_1|X)+E(Y_2|X)$
4. $E(cY|X)=cE(Y|X),\quad \forall c \text{ cons}$
5. $Y-E(Y|X)$, tiene correlación 0 con respecto a $h(X) \quad \forall$ función h(X), i.e. $Cov(Y-E(Y|X),h(X))=0$

# Transformaciones 

En una función Uno a Uno, la transformación es básicamente un cambio de nombre. 
Ejemplo de uso, cuando sabemos que X se distribuye binomial.
$Y=X-(n-X)=2X-n$
$\mathbb{P}(Y=y)=\mathbb{P}(2X-n=y))=\mathbb{P}(X=\frac{y+n}{2})$

Para $X^2$: 
$$\begin{align*}
F_Y(y)=\mathbb{P}(Y\leq y)=\mathbb{P}(X^2\leq y)=\mathbb{P}(-\sqrt{y}\leq X \leq \sqrt{y}) \\
F_Y(y) = F_x(\sqrt{y})-F_x(-\sqrt{y})
\end{align*}$$
Diferenciando: 
$$f_Y(y)=f_x(\sqrt{y})\cdot(\frac{1}{2}\frac{1}{\sqrt{y}}) +f_x(-\sqrt{y})\cdot(\frac{1}{2}\frac{1}{\sqrt{y}})$$
## Teorema 

Suponga que $g(\cdot)$ monótona (creciente o decreciente) y diferenciable en x, entonces la v.a. Y definida por $Y=g(X)$ tiene función de densidad dada por: 
$$f_Y)(y)=\begin{cases}
f_X[g^{-1}(y)]|\frac{d}{dy}g^{-1}(y)|,&\text{Si y=g(x) para algún x}\\
0,&e.o.c
\end{cases}
$$
Dem.
$$\begin{align*}
F_Y(y)=P(Y\leq y)\\
=P(g(X)\leq y) \\
=P(X\leq g^{-1}(y))\\
=F_X(g^{-1}(y))
\end{align*}$$
Diferenciando $f_X(g^{-1}(y))\frac{d}{dy}[g^{-1}(y)]$

# Una función de dos variables aleatorias

$Z=g(X,Y)$
$$F_Z(z)=P(Z\leq z)=P(g(X,Y)\leq z)=P((X,Y)\in D_Z)=\iint_{x,y\in D_Z}f_{X,Y}(x,y)dxdy$$

Sea $X\sim Exp(\lambda),Y\sim Exp(\lambda)$ independientes. Sea $Z=X+Y$
$$\begin{align*}
f_Z(z)=\int_0^zf_X(z-y)f_y(y)dy\\
f_Z(z)=\int_0^z\lambda e^{-\lambda(z-y)}\lambda e^{-\lambda y}dy \\
f_Z(z)=\int_0^z\lambda^2 e^{-\lambda z} \\
=\frac{z^{2-1} \lambda^2e^{-\lambda z}}{\Gamma(2)}\mathbb{I}_{(0,\infty)}(z)
\end{align*}$$
# Convolusión 
$$f_Z(z)=\int f(z-y)f(y)dy$$
Los limites se determinan conforme al problema, ejemplos: 
## Ejemplo convolusión 1 
$$\begin{align*}z\in(0,1)&,\quad Z=X+Y\\F_Z(z)&=P(Z\leq z)=P(X+Y\leq z)= \frac{z^2}{2}\end{align*}$$
Esto es, porque Z está definido en la región entre 0 y 1, además: 
![[Pasted image 20241104144619.png]]
Ahora, si $$\begin{align*}z\in(1,2)&,\quad Z=X+Y\\F_Z(z)&=1-\frac{(2-z)^2}{2} \end{align*}$$
![[Pasted image 20241104144851.png]]
Nos interesa la región que está limitada entre x=1, y=1. $$F_Z(z)=1-\frac{(2-z)^2}{2} \implies f_Z(z)=2-z$$
![[Pasted image 20241104145153.png]]
A este método se le llama <mark style="background: #ADCCFFA6;">Imagen Inversa</mark>, y es muy general.
Haciendo <mark style="background: #FF5582A6;">Convolusión</mark>: 
$$\begin{align*}f_Z(z)=\int_0^zf(z-y)f_y(y)dy=\int_0^zdy=z\\f_Z(z)=\int_{z-1}^1f(z-y)f_ydy=\int_{z-1}^1dy=1-z+1=2-z\end{align*}$$
La formula de convolusión sale de derivar la intergral de adentro con respecto a z, y defines sus límites. En este caso es X la de adentro y sus limites son de $$(0,z-y),\quad \text{i.e. }Z=X+Y\implies X=Z-Y$$
## Otro ejemplo con Z=X-Y
Determine f(z)
Estamos poniendo a Y como variable libre, es por eso que sus límites de integración quedan como todo R. 
$$\begin{align*}F_Z(z)=P(X-Y\leq z)=\int_{-\infty}^{\infty}\int_{-\infty}^{z+y}f_{X,Y}(x,y)dxdy\\\implies f_Z(z)=\frac{dF_z(z)}{dz}=\int_{-\infty}^{\infty}f_{x,y}(z+y,y)dy\end{align*}$$
Hay distintos casos, dependiendo de la región que se busque, ejemplo donde z<0: ![[Pasted image 20241104160338.png]]
Vemos que $$\begin{align*}F_Z(z)=\int_{z}^{\infty}\int_{0}^{z+y}f(x,y)dxdy\\f_z(z)=\int_{-z}^\infty f(z+y,y)dy\end{align*}$$
## Otro ejemplo con Z=X/Y
$$\begin{align*}F_Z(z)&=P(Z\leq z)=P(\frac{X}{Y}\leq z)\\&=P(\frac{X}{Y} \leq z, Y>0)+P(\frac{X}{Y} \leq z, Y<0)\\&=\int_0^\infty\int_{-\infty}^{zY}f(x,y)dxdy+\int_{-\infty}^0\int_{zY}^{\infty}f(x,y)dxdy\end{align*}$$
Usando <mark style="background: #FF5582A6;">regla de Leibniz.</mark> $$\begin{align*}f_z(z)&=\frac{d}{dz}F(z)=\int_0^\infty y\cdot f(zY,y)dy+\int_{-\infty}^0 (-y)\cdot f(zY,y)dy\\&=\int_{-\infty}^\infty |y|\cdot f(zY,y)dy\end{align*}$$
## Ejemplo max(X,Y)
Sea Z=max(X,Y), tenemos que: $$\begin{align*}F_Z(z)=P(Z\leq z)=P(\max(X,Y)\leq z)=P(X\leq z, Y\leq z)\\f_z(z)=\frac{d^2}{dz^2}F_z(z,z)\end{align*}$$
Si X,Y son independientes entonces: $$\begin{align*}F_Z(z)=P(X\leq z, Y\leq z)=F_X(x)F_y(y)\\f_z(z)=F_x(z)f_y(y)+f_x(x)F_Y(y)\end{align*}$$
<mark style="background: #FF5582A6;">Takeaway: </mark> si es max, implica que ambos son más chicos que z.
# Estadisticos de orden
SI $$\min(X_1,X_2,...,X_n)\implies x_1\leq x_2\leq...\leq x_n$$
No son dependientes, ya que si sabemos X_1 sabemos el soporte de los demás. 
## Función de densidad acumulada Estadístico de Orden
$$F_{x_{(j)}}=\sum_{i=j}^n\binom{n}{i}(F_x(x))^i(1-F_x(x))^{n-i}$$
De este resultado tenemos que la función de densidad es: $$f_{x_{(j)}}(x)=n\binom{n-1}{j-1}f(x)[F_X(x)]^{j-1}[1-F_X(x)]^{n-j}$$
La densidad de cada uno es implemente $$f_{x_{(1),...,x_{(n)}}}(x_1,...,x_n)=n!f_x(x_1)...f_x(x_n)$$
