#noveno 
**Revenue equivalence Theorem (RET):** it states that if certain assumptions hold, all standard auction formats will yield the same expected revenue for the seller and give bidders the same expected utility.
# Optimal auctions 
How to maximize over all the possible mechanisms. We can see the revenue in the y axis and the mechanisms in the x axis. 
- 1 bidder, $v\sim c.d.f. F$ 
- 1 item, the seller does not value it. 
- Fact: the optimal selling mechanisms is a posted price $p$, the seller posts the price and the buyer decides whether to buy it or not. 
If buyers valuation exceeds p then: $\max_p\{(1-F(p))\cdot p+F(p)\cdot 0)\}$
F.O.C: $$\frac{1}{p}-\frac{f(p)}{1-F(p)}=0\implies p^*=\frac{1-F(p^*)}{f(p^*)}$$where f is p.d.f. and $p^*$ 
**Example:** $$\begin{align*}F(v)=v,f(v)=1\\
p^*=\frac{1-p^*}{1};p^*=\frac{1}{2}\end{align*}$$
If the solution is unique then this is the global maximum. 
We can derive $(1-F(p))$ with respect to p: $$\frac{d}{dp}(1-F(p))=-f(p)p+1-F(p)=-f(p)[p-\frac{1-F(p)}{f(p)}]$$
**Proposition**. Suppose $v-\frac{1-F(v)}{f(v)}$ (<mark style="background: #ADCCFFA6;">virtual valuation</mark>) increasing in $v$ for all $v\in [0,1]$. Then, the expected revenue maximizing price $p^*$ is the unique solution to $p^*=\frac{1-F(p^*)}{f(p^*)}$
## The Revelation Principle 
When searching for an optimal mechanism, there is no loss of generality in restricting attention to direct, truthful mechanisms. 
- <mark style="background: #ADCCFFA6;">Direct mechanism:</mark> the participants reveal their private information or types.
- <mark style="background: #ADCCFFA6;">Truthful mechanisms:</mark> like a VCG 
- <mark style="background: #ADCCFFA6;">Optimal</mark>: whatever your objetive might be, any outcome that can be achieved at an equilibrium of some mechanism can be achieved at an equilibrium of some direct truthful mechanism.
### Example:
- $X:$ Allocation rule 
- $t:$ payment rule 
- $x(v)\in[0,1]$
- $t(v)\in \mathbb{R}$ 
$$\max_{\hat{v}\in[0,1]}\{x(\hat{v})v-t(\hat{v})\}$$
And $(x,t)$ are such that $\forall v$, $v \in \arg\max_{\hat{v}\in[0,1]}\{x(\hat{v})v-t(\hat{v})\}$
Then $V(v)=x(v)v-t(v)$ 
This can also be expressed in the Envelope Theorem and Myerson's Lemma. 
$$V(v)=V(0)+\int_0^vx(s)ds$$
We want voluntary participation: $V(v) \geq 0, \forall v$
Total payoff buyers payoff and sellers payoff: $x(v)v-t(v)+t(v)$
Revenue seller: $$t(v)=x(v)v-V(0)-\int_0^vx(s)ds$$
Expected revenue of the seller which they want to maximize. 
$$\begin{align*}Et(v)=\int_0^1t(v)f(v)dv\\
=-V(0)+\int_0^1x(v)vf(v)dv-\int_0^1\int_0^vx(s)f(v)dsdv
\end{align*}
$$
We can set $V(0)$ in order to be revenue maximizer. We can't maximize with respect to x because it has other implications.
$\max_x=-V(0)+\int_0^1x(v)vf(v)dv-\int_0^1\int_0^vx(s)f(v)dsdv$, subject to x is such that $(x,t)$ is truthful.
Integrating by parts we get: $\max_{x(\cdot)}\int_0^1x(v)(v-\frac{1-F(v)}{f(v)})f(v)dv$

Compare Total surplus: $\max_{x(\cdot)}\int_0^1x(v)vf(v)dv$, the x that maximizes is $x(v)=1, \forall v$

In a simpler allocation rule: 
$$x^*(v)=\begin{cases}
0,&\text{ if }v<p^*\\
1,&\text{ if }v\geq p^*
\end{cases}$$
The Revenue seller: $t(v)=x(v)v-V(0)-\int_0^vx(s)ds\implies 1(v)-\int_{p^*}^v1ds=p^*$
$$t^*(v)=\begin{cases}
0,&\text{ if }v<p^*\\
p^*,&\text{ if }v\geq p^*
\end{cases}$$
This is just for one agent. 
Another example, for point wise maximization, in the following function: **insert image of the function drawn by the professor**
$v\in[0,a]\implies x^*(v)=0,t^*(v)=0$
$v\in[a,b]\implies x^*(v)=1,t^*(v)=v1-\int_a^v1ds=a$
$v\in[b,c]\implies x^*(v)=0,t^*(v)=0-\int_a^b1ds=a-b<0$

> What's the revenue maximizing price $p^*$

# Revenue maximizing Theorem 
- Suppose that each $\mu_i$ is increasing. Then, an augmented voluntary mechanism maximizes the seller's expected revenue if and only if.
	1. Each $U_i(0)=0$ (no subsidies)
	2. The good is allocated if bidder $i$ of type $\theta_i$ when $$\mu_i(\theta_i)>\max_{j\in N\not\{0,i\}}\{0,\mu_j(\theta_j)\}.$$
	At least one such augmented mechanism exists. The maximum expected revenue is: 
$$\begin{align*}\mathbb{E}_\theta\left [max_{i\in N\not0}\{0,\mu_i(\theta_i)\}\right]\end{align*}$$
