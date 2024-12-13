#ml 
Es un método estadístico que ayuda a encontrar la correlación entre dos datasets, esto lo hace proyectando vectores que maximicen su correlación. 
Un ejemplo de esto en la vida real son videos con captions. 
# Método 
Cada item $p_i$ del dataset tiene puntos de $x_i$ y $y_i$ de sus sets correspondients. 
El objetivo: projectar $\{x\}$ en el vector $u$ y $\{y\}$ en el vector $v$, tal que la correlación entre $u^Tx, v^Ty$ se **maximize**.
1. Matriz de covarianzas: se usa una matriz bloque $\Sigma$ que representa las covarianzas dentro y entre x, y.
2. Objetivo: $$\max Corr(u^Tx,v^Ty)=\sqrt{\lambda_1}\sqrt{\lambda_2}$$ Esto optimizando las **proyecciones** $u,v$
3. Solución: esto es encontrando **eigenvectores** en $\Sigma$, estos determinan las **proyecciones** para $x,y$. 
## Maximización 
Los **eigenvectores** están ordenados por sus **eigenvalores**, ya que los más grandes indican correlaciones más fuertes. 
## Como medirlas
Un método que se usa para medir las correlaciones es **Wilk's Lambda**: $$\Lambda(r)=\Pi_{i=1}^r(1-\rho_i^2)$$donde $\rho_i$ son las **correlaciones canónicas**. 
Interpretación: 
- $\Lambda(r)$ pequeños nos dicen que hay correlaciones fuertes dentro de los componentes seleccionados.
- Al aumentar $r$, Lambda reduce.
- Permutando el dataset y volviendo a sacar la Lambda nos ayuda a verificar que las correlaciones son significativas. 
# Resumen
1. CCa relaciona dos datasets encontrar proyecciones con la maxima correlación.
2. Pares de proyecciones se encuentran resolviendo para eigenvectores y maximizando su correlación 