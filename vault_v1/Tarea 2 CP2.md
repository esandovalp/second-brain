# Blitzstein 
## Chapter 7
### 67
A certain course has a freshmen, b sophomores, c juniors, and d seniors. Let X be the number of freshmen and sophomores (total), Y be the number of juniors, and Z be the number of seniors in a random sample of size n, where for Part (a) the sampling is with replacement and for Part (b) the sampling is without replacement (for both parts, at each stage the allowed choices have equal probabilities).
(a) Find the joint PMF of X,Y,Z, for sampling with replacement.
(b) Find the joint PMF of X,Y,Z, for sampling without replacement.

**PARTE A.**
Recordar la [[multinomial distribution]]: $$P(X_1=n_1,X_2=n_2,...,X_k=n_k)=\frac{n!}{n_1!n_2!...n_k!}p_1^{n_1}p_2^{n_2}...p_k^{n_k}$$
Podemos definir al conjunto de estudiantes como $\Omega=\{0,1,2,...,n\}$, donde $X,Y,Z\in \Omega$, donde $X+Y+Z=n$
Viendo la probabilidad de seleccionar cada grupo: 
- Probabilidad de seleccionar a un freshman o sophomore: $\mathbb{P}(X=x)=\frac{a+b}{a+b+c+d}$
- Probabilidad de seleccionar a un junior: $\mathbb{P}(Y=y)=\frac{c}{a+b+c+d}$
- Probabilidad de seleccionar a un junior: $\mathbb{P}(Z=z)=\frac{d}{a+b+c+d}$
Por lo tanto, podemos expresar la conjunta como: $$\mathbb{P}(X=x,Y=y,Z=z)=\frac{n!}{x!y!z!}(\frac{a+b}{a+b+c+d})^x(\frac{c}{a+b+c+d}^y)(\frac{d}{a+b+c+d}^z)$$
**PARTE B.**
Sabemos que una [[multinomial distribution]] no hay sampleo sin remplazo, por lo que usaremos una [[multivariate hypergeometric]], la cual modela similar a la multinomial, sólo que <mark style="background: #FFF3A3A6;">sin remplazo</mark>. 
$$\mathbb{P}(X_1=k_1,...,X_c=k_c)=\frac{\Pi_{i=1}^c\binom{K_i}{k_i}}{\binom{N}{n}}$$
Traduciéndolo a nuestro problema: $$\mathbb{P}(X=x,Y=y,Z=z)=\frac{\binom{a+b}{x}\binom{c}{y}\binom{d}{z}}{\binom{a+b+c+d}{n}}$$
Donde se tiene que cumplir: 
- $x + y + z = n$
- $0 \leq x \leq a + b$
- $0 \leq y \leq c$
- $0 \leq z \leq d$
### 70
Let X be the number of statistics majors in a certain college in the Class of 2030, viewed as an r.v. Each statistics major chooses between two tracks: a general track in statistical principles and methods, and a track in quantitative finance. Suppose that each statistics major chooses randomly which of these two tracks to follow, independently, with probability p of choosing the general track. Let Y be the number of statistics majors who choose the general track, and Z be the number of statistics majors who choose the quantitative finance track.
1. ﻿﻿﻿﻿Suppose that $X \sim Pois(\lambda)$. (This isn't the exact distribution in reality since a Poisson is unbounded, but it may be a very good approximation.) Find the correlation between X and Y.
2. ﻿﻿﻿﻿Let n be the size of the Class of 2030, where n is a known constant. For this part and the next, instead of assuming that X is Poisson, assume that each of the n students chooses to be a statistics major with probability r, independently. Find the joint distribution of Y, Z, and the number of non-statistics majors, and their marginal distributions.
3. ﻿﻿﻿﻿Continuing as in (b), find the correlation between X and Y.

**PARTE A.**
Recordemos la formula para la [[correlation]] como: $Corr=\frac{Cov(X,Y)}{\sqrt{var(x)var(y)}}$, donde la [[covariance]] $Cov=E[XY]-E[X]E[Y]$

Necesitamos la distribución de Y. Lo que sabemos es que la probabilidad de que se vayan al camino general es de p y que depende de los valores de X, por lo tanto, tenemos que $Y | X \sim Binomial(X, p)$.

Dado que X se distribuye **Poisson, su media y varianza son $\lambda$.**
Además, podemos obtener la esperanza de Y usando la [[law of total expectation]] y sabiendo que la <mark style="background: #FFF3A3A6;">media de una binomial es</mark> $np$**, en este caso, $n=X$: $$E[Y] = E[E[Y|X]] = E[pX] = pE[X] = p\lambda$$
Podemos obtener la varianza de Y usando [[law of total variance]] de las notas y usando la <mark style="background: #FFF3A3A6;">varianza de una binomial </mark>($npq$).
$$\begin{align*}
\text{Var}(Y) &= \text{Var}[E[Y|X]] + E[\text{Var}[Y|X]] \\
&= \text{Var}(pX) + E[Xp(1 - p)] \\
&= p^2 \text{Var}(X) + p(1 - p)E[X] \\
&= p^2 \lambda + p(1 - p)\lambda \\
&= [p^2 + p(1 - p)]\lambda \\
&= p\lambda \
\end{align*}$$Para $E[XY]$ podemos usar <mark style="background: #FFF3A3A6;">ley de esperanza total</mark> y propiedades de esperanza condicional:
$$\begin{align*}

E[XY] &= E[E[XY|X]] = E[X E[Y|X]] \\

&= E[X(pX)] = pE[X^2] \\

&= p[\text{Var}(X) + (E[X])^2] \\

&= p[\lambda + \lambda^2] = p\lambda(1 + \lambda)

\end{align*}$$
Por lo tanto, la covarianza:
$$\begin{align*}Cov&=E[XY]-E[X]E[Y]=p\lambda(1+\lambda)-\lambda(p\lambda)\\&=p\lambda(1+\lambda-\lambda)=p\lambda
\end{align*}$$
Finalmente, la correlación: $$\begin{align*}Corr(X,Y)&=\frac{Cov(X,Y)}{\sqrt{var(x)var(y)}}=\frac{p\lambda}{\sqrt{\lambda p\lambda}}\\&=\frac{p\lambda}{\lambda\sqrt{p}}=p(p)^{-1/2}=\sqrt{p}\end{align*}$$
**PARTE B.**
Let n be the size of the Class of 2030, where n is a known constant. For this part and the next, instead of assuming that X is Poisson, assume that each of the n students chooses to be a statistics major with probability r, independently. Find the joint distribution of Y, Z, and the number of non-statistics majors, and their marginal distributions.

Sea $W\sim Bin(n,1-r)$ la cantidad de estudiantes que no se van a estadística. 
Si X representa el número de estudiantes de estadística, donde n escoge estadística con probabilidad r, entonces se puede ver como un modelo binomial similar a como lo vimos con Y, por lo tanto: $X\sim Bin(n,r)$. Además, podemos ver que X es una multinomial dado que tenemos n objetos (estudiantes), y $k=3$ categorías (general, finanzas, no estadística) las cuales se distribuyen binomial con parámetros $(n,rp),(n,rq=r(1-p)),(n,1-r)$, respectivamente, los cuales suman a 1: $rp+r(1-p)+1-r=rp+r-rp+1-r=1$. 
Por lo tanto, podemos ver la conjunta de Y y Z como una multinomial (X): $$\mathbb{P}(Y=y,Z=z,W=w)=\frac{n!}{y!x!w!}(rp)^{y}(r-rp)^{z}(1-r)^w$$
**PARTE C.**
﻿﻿﻿﻿Continuing as in (b), find the correlation between X and Y.
﻿﻿﻿﻿
$Corr(X,Y)=\frac{Cov(X,Y)}{\sqrt{var(x)var(y)}}$
Hacer talacha.
$X\sim Bin(n,r),\quad Y\sim Bin(n,rp),\quad X=Y+Z$

$$\begin{align*}Cov(X,Y)=E[XY]-E[X]E[Y]\\E[XY]=E[(Y+Z)Y]=E[Y^2]+E[YZ]\\=_{ind}E[Y^2]+E[Y]E[Z]=(Var(Y)-E^2[Y])+(nrp)(nr(1-p))\\nrp(1-p)-(nrp)^2+(nrp)(nr(1-p))=nrp-nrp^2-2n^2r^2p^2+n^2r^2p\\Cov(X,Y)=nrp-nrp^2-2n^2r^2p^2+n^2r^2p-E[X]E[Y]\\=nrp-nrp^2-2n^2r^2p^2+n^2r^2p-(nr)(nrp)\\nrp-nrp^2-2n^2r^2p^2+n^2r^2p-n^2r^2p=nrp-nrp^2-2n^2r^2p^2=Cov(X,Y)\end{align*}$$
Por lo tanto, la correlación: $$Corr(X,Y)=\frac{Cov(X,Y)}{\sqrt{var(x)var(y)}}=\frac{nrp-nrp^2-2n^2r^2p^2}{\sqrt{nr(1-r)nrp(1-p)}}=\frac{nrp-nrp^2-2n^2r^2p^2}{\sqrt{n²r²(1-r)p(1-p)}}$$
### 71
In humans (and many other organisms), genes come in pairs. Consider a gene of interest, which comes in two types (alleles): type a and type A. The genotype of a person for that gene is the types of the two genes in the pair: AA, Aa, or aa (aA is equivalent to Aa).
According to the Hardy-Weinberg law, for a population in equilibrium, the frequencies of AA, Aa, aa will be $p^2, 2p(1-p), (1 -p)^2$, respectively, for some p with $0 < p < 1$.
Suppose that the Hardy-Weinberg law holds, and that n people are drawn randomly from the population, independently. Let $X_1, X_2, X_3$ be the number of people in the sample with genotypes AA, Aa, aa, respectively.
1. ﻿﻿What is the joint PMF of $X_1, X_2, X_3$?
2. ﻿﻿﻿﻿What is the distribution of the number of people in the sample who have an A?
3. ﻿﻿﻿﻿What is the distribution of how many of the $2n$ genes among the people are A's?
4. Now suppose that p is unknown, and must be estimated using the observed data $X_1, X_2, X_3$. The maximum likelihood estimator (MLE) of p is the value of p for which the observed data are as likely as possible. Find the MLE of p.
5. ﻿﻿﻿﻿Now suppose that p is unknown, and that our observations can't distinguish between AA and Aa. So for each person in the sample, we just know whether or not that person is an aa (in genetics terms, AA and Aa have the same phenotype, and we only get to observe the phenotypes, not the genotypes). Find the MLE of p.

**PARTE A.**
Parece que la conjunta será una multinomial, por lo que tenemos que ver que las probabilidades para cada una de las X´s sume a 1: $$p^2+ 2p(1-p)+(1 -p)^2=p^2+2p-2p^2+1-2p+p^2=1$$
Además, podemos ver que para cada una de las X's su distribución es una binomial con parámetros $(n,p^2),(n,2p(1-p)),(n,(1-p)^2)$, respectivamente. 
Por lo tanto, la conjunta: $$\mathbb{P}(X_1=x_1,X_2=x_2,X_3=x_3)=\frac{n!}{x_1!x_2!x_3!}(p^2)^{x_1}(2p(1-p))^{x_2}((1-p)^2)^{x_3}$$
**PARTE B.**
En $X_1,X_2$ están el tipo A, ya que en el primero son para los AA y el segundo para los Aa-aA, por lo tanto, podemos verlo como el número de personas que tienen AA o Aa, por lo ttano es una union, o suma dada su independencia: $$\mathbb{P}(X_1\cup X_2)=_i\mathbb{P}(X_1)+\mathbb{P}(X_2)=p^2+2p(1-p)=p^2+2p-2p^2=2p-p^2=p(2-p)$$
Sea $Y=X_1+X_2$. Su distribución, entonces: $$Y\sim Bin(n,p(2-p))$$
**PARTE C**
3. ﻿﻿﻿﻿What is the distribution of how many of the $2n$ genes among the people are A's?
Similar al inciso anterior, sin embargo, podemos verlo por cuantas A aporta cada división de la población: 
- AA aportan 2 A's.
- Aa aportan 1 A
- aa aportan 0 A's.
Por lo tanto, sea $Z=2X_1+X_2$, podemos obtener la distribución pedida a través de la esperanza de Z: $E[Z]=E[2X_1+X_2]=2E[X_1]+E[X_2]=2np^2+n2p(1-p)=2np^2+2np-2np^2=2np$, vemos que la distribución es $$Z\sim Bin(2n,p)$$
**PARTE D**
4. Now suppose that p is unknown, and must be estimated using the observed data $X_1, X_2, X_3$. The maximum likelihood estimator (MLE) of p is the value of p for which the observed data are as likely as possible. Find the MLE of p.
**PARTE E.**
Now suppose that p is unknown, and that our observations can't distinguish between AA and Aa. So for each person in the sample, we just know whether or not that person is an aa (in genetics terms, AA and Aa have the same phenotype, and we only get to observe the phenotypes, not the genotypes). Find the MLE of p.
### 73
Let the joint PDF of X and Y be $$f_{X,Y}(x,y)=ce^{(-\frac{x^2}{2}-\frac{y^2}{2})},\quad \forall x,y \quad c\in \mathbb{R}$$
1. Find c to make this a valid joint PDF. 
2. What are the marginal distributions of X and Y? Are X and Y independent?
3. Is (X,Y) Bivariate Normal?

**PARTE A.**
Para que se cumpla que sea una función de densidad se tiene que cumplir la condición: $$  \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f_{X,Y}(x,y) \, dx \, dy = 1$$ Ajustándola a el problema: $$  

\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} c e^{-\frac{x^2}{2} - \frac{y^2}{2}} \, dx \, dy = 1$$
Separando e: $$  

c \int_{-\infty}^{\infty} e^{-\frac{x^2}{2}} \, dx \int_{-\infty}^{\infty} e^{-\frac{y^2}{2}} \, dy = 1$$
Cada integral es una **integral gaussiana**, por lo tanto, $$  

\int_{-\infty}^{\infty} e^{-\frac{x^2}{2}} \, dx = \sqrt{2\pi} \quad \text{y} \quad \int_{-\infty}^{\infty} e^{-\frac{y^2}{2}} \, dy = \sqrt{2\pi}$$
Por lo tanto:$$c (\sqrt{2\pi})(\sqrt{2\pi}) = 1 \implies c=\frac{1}{2\pi}$$
**PARTE B.**
Resolviendo para las marginales: $$\begin{align*}\mathbb{P}(X=x)&=\int_{-\infty}^{\infty} f_{X,Y}(x,y)dy = \int_{-\infty}^{\infty}\frac{1}{2\pi}e^{(-\frac{x^2}{2}-\frac{y^2}{2})}dy\\&=\frac{1}{2\pi}e^{-\frac{x^2}{2}}\int_{-\infty}^{\infty}e^{(-\frac{y^2}{2})}dy=\frac{1}{2\pi}e^{-\frac{x^2}{2}}\sqrt{2\pi}\\&=\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}\end{align*}$$
Análogamente para Y tenemos que: $$P(Y=y)=\frac{1}{\sqrt{2\pi}}e^{-\frac{y^2}{2}}$$
Revisando independencia: $$\begin{align*}\mathbb{P}(X=x,Y=y)&=\mathbb{P}(X=x)\mathbb{P}(Y=y)\\\frac{1}{2\pi}e^{(-\frac{x^2}{2}-\frac{y^2}{2})}&=\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}\cdot \frac{1}{\sqrt{2\pi}}e^{-\frac{y^2}{2}}\\&=\frac{1}{2\pi}e^{(-\frac{x^2}{2}-\frac{y^2}{2})}\end{align*}$$
Vemos que si son independientes.
**PARTE C.**
Is (X,Y) Bivariate Normal?
Si, ya que revisando la formula de normal bivariada: $$  

f_{X,Y}(x,y) = \frac{1}{2\pi \sigma_X \sigma_Y \sqrt{1 - \rho^2}} e^{-\frac{1}{2(1 - \rho^2)} \left( \frac{(x - \mu_X)^2}{\sigma_X^2} + \frac{(y - \mu_Y)^2}{\sigma_Y^2} - 2\rho \frac{(x - \mu_X)(y - \mu_Y)}{\sigma_X \sigma_Y} \right)},$$
En nuestro caso, las medias son 0 y las varianzas son 1, y dado que X y Y son independientes la correlación es 0, por lo tanto la formula queda como la conjunta de X y Y.
### 74
Let the joint PDF of X and Y be $$f_{X,Y}(x,y)=ce^{(-\frac{x^2}{2}-\frac{y^2}{2})},\quad xy>0$$
where c is a constant (the joint PDF is 0 for xy < 0).
1. ﻿﻿﻿﻿Find c to make this a valid joint PDF.
2. ﻿﻿﻿﻿What are the marginal distributions of X and Y? Are X and Y independent?
3. ﻿﻿﻿﻿Is (X, Y) Bivariate Normal?

**PARTE A.**
Similar al problema anterior, lo que cambia son los limites: $$\begin{align*}
\int_{0}^{\infty} \int_{0}^{\infty} c e^{-\frac{x^2}{2} - \frac{y^2}{2}} \, dx \, dy &= 1\end{align*}$$
Sin embargo, por simetría podemos calcular una de ellas y duplicar el resultado: $$\begin{align*}
2\int_{0}^{\infty} \int_{0}^{\infty} c e^{-\frac{x^2}{2} - \frac{y^2}{2}} \, dx \, dy &= 1\\  
2c \int_{0}^{\infty} e^{-\frac{x^2}{2}} \, dx \int_{0}^{\infty} e^{-\frac{y^2}{2}} \, dy &= 1\end{align*}$$
Vemos que tiene forma de Gamma, por lo que podemos usarla para facilitar el cálculo sustituyendo $$t=\frac{x^2}{2}\implies \sqrt{2t}=y$$Diferenciado ambos lados por y:$$\frac{dt}{dy}=y \iff\frac{dt}{y}=dy\implies\frac{dt}{\sqrt{2t}}=dy$$
$$\begin{align*}
\int_{0}^{\infty} e^{-\frac{x^2}{2}} \, dx = \int_{0}^{\infty} e^{-u} \frac{du}{\sqrt{2u}} &= \frac{1}{\sqrt{2}} \int_{0}^{\infty} u^{-\frac{1}{2}} e^{-u} \, du\\  

\int_{0}^{\infty} e^{-\frac{x^2}{2}} \, dx = \frac{1}{\sqrt{2}} \Gamma\left( \frac{1}{2} \right)&=  

\int_{0}^{\infty} e^{-\frac{x^2}{2}} \, dx \\= \frac{\sqrt{\pi}}{\sqrt{2}} &= \sqrt{\frac{\pi}{2}}\end{align*}$$
Sustituyendo: $$  

2c \left( \sqrt{\frac{\pi}{2}} \right) \left( \sqrt{\frac{\pi}{2}} \right) = 1\implies c=\frac{2}{\pi}$$
**PARTE B.**
2. ﻿﻿﻿﻿What are the marginal distributions of X and Y? Are X and Y independent?
Similar a como obtuvimos c, usamos la función Gamma.
$$\begin{align*}\mathbb{P}(X=x)&=\int_{0}^{\infty} \frac{2}{\pi} e^{-\frac{x^2}{2} - \frac{y^2}{2}} \, \, dy\\&=\frac{2}{\pi}e^{-\frac{x^2}{2}}\int_0^{\infty}e^{-\frac{y^2}{2}}\,\,dy\\&=\frac{2}{\pi}e^{-\frac{x^2}{2}}\sqrt{\frac{\pi}{2}}\\&=\sqrt{\frac{2}{\pi}}e^{-\frac{x^2}{2}}\end{align*}$$ Análogamente para Y: $$\mathbb{P}(Y=y)=\int_{0}^{\infty} \frac{2}{\pi} e^{-\frac{x^2}{2} - \frac{y^2}{2}} \, \, dx=\sqrt{\frac{2}{\pi}}e^{-\frac{y^2}{2}}$$
Podemos ver que claramente son independientes.
**PARTE C.**
Ya que ambas marginales son normales estándar, (X, Y) es una distribución normal bivariada pero con correlación 0 en los dominios restringidos donde $xy > 0$ , lo que indica independencia dependiente del cuadrante.
### 75
Let X, Y, Z be ii.d. $N(0, 1)$. Find the joint MGF of $(X + 2Y, 3X + 4Z, 5Y + 6Z)$
Sea $$\begin{align*}W&=X+2Y\\U&=3X+4Z\\V&=5Y+6Z\end{align*}$$
Usando la definición de F.G.M para normales multivariadas: $$\mathbb{E}(e^{t_1W+t_2U+t_3V})$$
Sin embargo, tenemos que poner todo en términos de las variables dadas. $$\begin{align*}t_1(X+2Y)+t_2(3X+4Z)+t_3(5Y+6Z)\\=(t_1+3t_2)X+(2t_1+5t_3)Y+(4t_2+6t_3)Z\end{align*}$$
Usando el **teorema visto en la página 98**: $$\begin{align*}\mathbb{E}(e^{t_1W+t_2U+t_3V})=exp{[(t_1+3t_2)E(X)+(2t_1+5t_2)E(Y)+(4t_2+6t_3)E(Z)]}\\+\frac{1}{2}Var((t_1+3t_2)X+(2t_1+5t_3)Y+(4t_2+6t_3)Z)\end{align*}$$
## Chapter 8: Transformaciones (p.407)
### 10 
Let $X\sim Pois(\lambda)$ and Y be the indicator of X being odd. Find the PMF of Y. Hint: Find $P(Y=0)-P(Y=1)$ by writing $P(Y=0)$ and $P(Y=1)$ as series and then using the fact that $(-1)^k$ is 1 if k is even and -1 if k is odd.
$$P(X=x)=\frac{\lambda^{x}e^{-\lambda}}{x!},\quad P_{Y|X}(Y=y|X)=\begin{cases}0&x\in\{2,4,6,...\}\\1&x\in\{1,3,5,...\}\end{cases}$$

Usando el truco: $$P(Y=0)=P(X\in\{2,4,6,...\})=\sum_{k\in X}^\infty P(X=k)=\sum_{k=0}^\infty\frac{\lambda^{2k}e^{-\lambda}}{(2k)!}$$
$$P(Y=1)=P(X\in\{1,3,5,...\})=\sum_{k\in X}^\infty P(X=k)=\sum_{k=0}^\infty\frac{\lambda^{2k+1}e^{-\lambda}}{(2k+1)!}$$
$$\begin{align*}P(Y=0)-P(Y=1)&=\sum_{k=0}^\infty\frac{\lambda^{2k}e^{-\lambda}}{(2k)!}-\sum_{k=0}^\infty\frac{\lambda^{2k+1}e^{-\lambda}}{(2k+1)!}\\&=\sum_{k=0}^\infty\frac{\lambda^{2k}e^{-\lambda}}{(2k)!}-\frac{\lambda^{2k+1}e^{-\lambda}}{(2k+1)!}\\&=e^{-\lambda}\sum_{k=0}^\infty\frac{\lambda^{2k}}{(2k)!}-\frac{\lambda^{2k+1}}{(2k+1)!}\\\text{hint}&=e^{\lambda}\sum_{k=0}^\infty\frac{\lambda^k}{k!}(-1)^k\\&=e^{-\lambda}e^{-\lambda}=e^{-2\lambda}\end{align*}$$
Además sabemos que $$P(Y=0)+P(Y=1)=1$$
Por lo tanto, sumando estas dos ecuaciones, tenemos que: $$\begin{align*}2P(Y=0)=1+e^{-2\lambda}&\implies P(Y=0)=\frac{1+e^{-2\lambda}}{2}\\2P(Y=1)=1-e^{-2\lambda}&\implies P(Y=1)=\frac{1-e^{-2\lambda}}{2}\end{align*}$$
### 11
Let T be a continuous r.v. and $V=1/T$. Show that their CDFs are related as follows: $$F_V(v)=\begin{cases}F_T(0)+1-F_T(\frac{1}{v})&\text{ for  }v>0,\\F_T(0)&\text{ for  }v=0,\\F_T(0)-F_T(\frac{1}{v})&\text{ for  }v<0.\end{cases}$$
$$\begin{align*}F_V(v)&=\mathbb{P}(V\leq v)=\mathbb{P}(\frac{1}{T}\leq v)=\mathbb{P}(T\geq\frac{1}{v})\\&=1-\mathbb{P}(T<\frac{1}{v})=1-F_T(\frac{1}{v})\end{align*}$$
Por casos: 
1. $v>0$:
$$\begin{align*}F_V(v)&=P(T\geq \frac{1}{v})=1-P(T<\frac{1}{v})\\\text{Si }v>0&\implies P(0\leq T<\frac{1}{v})=F_T(\frac{1}{v})-F_T(0)\\\therefore F_V(v)&=1-P(T<\frac{1}{v})=1-F_T(\frac{1}{v})+F_T(0)\end{align*}$$
2. $v<0$:
$$\begin{align*}F_V(v)&=P(T\geq \frac{1}{v})\\\text{Si }v<0&\implies P(\frac{1}{v}\leq T\leq0)=F_T(0)-F_T(\frac{1}{T})\end{align*}$$
3. $v=0$:
$$\begin{align*}F_V(v)&=P(T\geq \frac{1}{v})\\\text{Si }v=0&\implies F_T(0)\end{align*}$$
### 12
Let T be the ratio $X/Y$ of two i.i.d. $N(0,1)$ r.v.s X,Y. This is the Cauchy distribution and, P.D.F $$f_T(t)=\frac{1}{\pi(1+t^2)}$$
1. Use the result of the previous problem to find the CDF of $\frac{1}{T}$. Then use calculus to find the PDF of $\frac{1}{T}$. (Note that one-dimensional change of variables formula does not apply directly, since the function $g(t)=\frac{1}{t}$, even though it has $g'(t)<0$ for all $t\not= 0$ and is not a strictly decreasing function on its domain.)
2. Show that $\frac{1}{T}$ has the same distribution as T without using calculus, in 140 characters or fewer.

**PARTE A.**
Sea $V=\frac{1}{T}$
$$F_V(v)=\begin{cases}\frac{1}{2}-\frac{1}{\pi}\arctan(\frac{1}{v}),&v>0\\0,&v=0\\\frac{1}{2}+\frac{1}{\pi}\arctan(\frac{1}{2}),&v<0\end{cases}$$
Derivando para tener $f_V(v)$: $$f_V(v)=\frac{1}{\pi(1+v^2)},\quad v\not=0$$
**PARTE B.**
Como $T \sim \text{Cauchy}(0,1)$ es simétrico alrededor de $0, T$ y $\frac{1}{T}$ tienen la misma distribución debido a la estabilidad de Cauchy bajo inversión.
### 14
Let X and Y have joint PDF $f_{X,Y}(x,y)$ and transform $(X,Y)\mapsto(T,W)$ linearly by letting $$T=aX+bY \text{ and }W=cX+dY,$$ where a,b,c,d are constants such that $ad-bc\not=0$
1. Find the joint PDF $f_{T,W}(t,w)$ (in terms of $f_{X,Y}$, though your answer should be written as a function of t and w).
2. For the case where $T=X+Y,W=X-Y$, show that $$f_{T,w}(t,w)=\frac{1}{2}f_{X,Y}(\frac{t+w}{2},\frac{t-w}{2}).$$
**PARTE A.**
$$\begin{align*}f_{T,W}(t,w)&=P(T=t,W=w)=P(aX+bY=t,cX+dY=w)\\&=P(aX=t-bY,dY=w-cX)=P(X=\frac{t-bY}{a},Y=\frac{w-cX}{d})\\&=\end{align*}$$
**PARTE B**
$$\begin{align*}f_{T,W}(t,w)&=P(T=t,W=w)=P(X+Y=t,X-Y=w)\\&=P(X=t-Y,Y=X-w)\end{align*}$$
### 16
Let X and Y be i.i.d. N(0,1) r.v.s, T=X+Y, W=X-Y. We know that T and W are independent. Give another proof of this fact using the change of variables theorem (Let X be a continuous r.v. with PDF f_X, and let Y= g(X), where g is diﬀerentiable and strictly increasing (or strictly decreasing). Then the PDF of Y is given by$$f_Y(y)=f_x(x)|\frac{dx}{dy}|$$

	$$X = W Y = W \left( \dfrac{T}{W + 1} \right) = \dfrac{W T}{W + 1}$$
# Work

Find f_z(z) for Z=X+\frac{1}{2}Y, where X and Y independent Exp(\lambda) r.v.s
Let $X$ and $Y$ be independent exponential random variables with rate parameter $\lambda$.

We want to find the probability density function (PDF) of $Z = X + \frac{1}{2}Y$.

First, we know that the PDF of an exponential random variable $X$ with rate $\lambda$ is:
$$f_X(x) = \lambda e^{-\lambda x}, \quad x \geq 0$$

The PDF of $Y$ is also exponential with the same rate $\lambda$:
$$f_Y(y) = \lambda e^{-\lambda y}, \quad y \geq 0$$

Now, we can use the transformation method to find the PDF of $Z = X + \frac{1}{2}Y$. 

Let $u = X$ and $v = \frac{1}{2}Y$, so $z = u + v$. 

The Jacobian of the transformation is $J = \left|\frac{\partial (u, v)}{\partial (x, y)}\right| = \frac{1}{2}$.

The joint PDF of $U$ and $V$ is:
$$f_{U,V}(u, v) = f_X(u)f_Y(2v) \cdot \frac{1}{2} = \lambda^2 e^{-\lambda u - 2\lambda v}, \quad u \geq 0, v \geq 0$$

To find the PDF of $Z = X + \frac{1}{2}Y$, we integrate the joint PDF over the region where $u + v = z$:
$$f_Z(z) = \int_0^z f_{U,V}(u, z-u) du = \lambda^2 \int_0^z e^{-\lambda u - 2\lambda (z-u)} du$$

Evaluating the integral, we get:
$$f_Z(z) = \lambda^2 \cdot \frac{1}{3\lambda} e^{-3\lambda z/2}, \quad z \geq 0$$

Therefore, the probability density function of $Z = X + \frac{1}{2}Y$ is:
$$f_Z(z) = \frac{2\lambda^2}{3} e^{-\frac{3\lambda z}{2}}, \quad z \geq 0$$

# convolutiosn
Let's start with the PDFs of the independent exponential random variables $X$ and $Y$:

$$f_X(x) = \lambda e^{-\lambda x}, \quad x \geq 0$$
$$f_Y(y) = \lambda e^{-\lambda y}, \quad y \geq 0$$

Since $Z = X + \frac{1}{2}Y$, we can use the convolution integral to find the PDF of $Z$:

$$f_Z(z) = \int_{-\infty}^{\infty} f_X(z - \frac{1}{2}y) f_Y(y) dy$$

Substituting the exponential PDFs, we get:

$$f_Z(z) = \int_{0}^{\infty} \lambda e^{-\lambda (z - \frac{1}{2}y)} \lambda e^{-\lambda y} dy$$

Evaluating the integral, we arrive at:

$$f_Z(z) = \frac{2\lambda^2}{3} e^{-\frac{3\lambda z}{2}}, \quad z \geq 0$$

This is the same result as we obtained earlier using the transformation method. The convolution approach provides an alternative way to derive the PDF of $Z = X + \frac{1}{2}Y$ by directly combining the individual PDFs of $X$ and $Y$.
$$f_Z(z) = \frac{2\lambda^2}{3} e^{-\frac{3\lambda z}{2}}, \quad z \geq 0$$`
