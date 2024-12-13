#linealprogramming 
Nodos de origen $a$, nodos de demanda $d$. Los nodos que no tienen ninguna label. La diferencia con el [[Modelo de trasbordo]] es que los nodos no están definidos como de demanda o oferta, pueden ser lo que sea. 
# Modelo
Sea $x_{i,j}$ el número de unidades transportadas desde i, hasta j. La función objetivo: $$\min z=c_{1,2}(x_{1,2}+x_{2,1})+c_{1,4}(x_{1,4}+x_{4,1})+...+c_{i,j}(x_{i,j}+x_{j,i})$$
Restricciones, el modelo lo ve como un **control de flujo** (lo que entra tiene que ser igual a lo que sale para cada nodo):
1. $x_{2,1}+x_{4,1}+a_1=x_{1,2}+x_{1,4}$, aquí a es lo que entra en un nodo de oferta
2. $x_{3,2}+x_{1,2}=x_{2,3}+x_{2,1}+d_2$, aquí d es lo que sale de un nodo de demanda.
3. $e.t.c$
4. $x_{i,j}\geq 0$
## Ejercicio 
![[notas_myo_1-2 (dragged).pdf]]
$$\min z=c_{1,2}(x_{1,2}+x_{2,1})+c_{1,4}(x_{1,4}+x_{4,1})+...+c_{i,j}(x_{i,j}+x_{j,i})$$
1. Sea $x_1$: el paso de $p_1$ a $w_1$
2. Sea $x_2$: el paso de $p_1$ a almacén
3. Sea $x_3$: el paso de $p_1$ a $p_2$
4. Sea $x_4$: el paso de $p_2$ a $p_1$
5. Sea $x_5$: el paso de $p_2$ a almacén. 
6. Sea $x_6$: el paso de $w_1$ a $w_2$
7. Sea $x_7$: el paso de $w_2$ a $w_1$
8. Sea $x_8$: el paso de almacén a $w_2$
$$\min z=900x_1+400x_2+400x_3+400x_4+900x_5+200x_6+900x_7+100x_8$$
Restricciones:
1. $x_4+150=x_2+x_1+x_3$
2. $x_3+40=x_4+x_5$
3. $x_2+x_5=x_8$
4. $x_1+x_7=x_6+90$
5. $x_8+x_6=x_7+60$
6. $x_2+x_5\geq x_8+10$: restricción de que el almacén debe de tener 10 unidades guardadas.
7. $x_1\leq 20$