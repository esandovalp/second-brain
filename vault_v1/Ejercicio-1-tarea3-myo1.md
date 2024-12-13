Usando el **Algoritmo de Prim** (empezando por el vértice 7):  
1. Empezar en el vértice 7  
2. Añadir arista 7-8 (19)  
3. Añadir arista 8-9 (18)  
4. Añadir arista 8-6 (21)  
5. Añadir arista 6-4 (19)  
6. Añadir arista 4-3 (14)  
7. Añadir arista 4-2 (17)  
8. Añadir borde 2-5 (23)  

Costo total = 13,100 pies  

Utilizando el **Algoritmo de Kruskal**:  
1. Ordena las aristas por peso y añádelas si no crean un ciclo:  
- 3-4 (14)  
- 2-4 (17)  
- 8-9 (18)  
- 7-8 (19)  
- 4-6 (19)  
- 4-5 (20)  
- 6-8 (21)  
- 5-7 (22)  
Costo total = 13,000 pies  
## Recomendación:  
Recomiendo utilizar el **algoritmo de Kruskal**, ya que proporciona una longitud total de cable ligeramente más corta de 13,000 pies en comparación con el algoritmo de Prim, que da 13,100 pies.
  
La ventaja del **algoritmo de Kruskal** en este caso es que considera todas las aristas globalmente desde la más corta a la más larga, mientras que el algoritmo de Prim crece a partir de un único vértice. Como estábamos obligados a iniciar el de Prim en el vértice 7 (que no está situado en el centro), esto llevó a una solución ligeramente menos óptima.  