#ml 

Es una combinación de [[Ridge Regularization]] y [[Lasso Regularization]], le quita el limitante de Lasso que es que puede mandar features a 0, quitándolas del modelo.

$$\frac{1}{N}(y-X\beta)^T(y-X\beta)+\lambda(\frac{1-\alpha}{2}||\beta||_2^2+\alpha||\beta||_1)$$
Donde $\alpha$ controla el penalty.
- Si $\alpha=1$: elastic net se comporta como **Lasso**.
- Si $\alpha=0$: se comporta como **Ridge.**
