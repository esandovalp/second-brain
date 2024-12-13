[[#Tarea 1]]
# Fundamentos de programación lineal 
Componentes principales: 
1. **Función objetivo:** expresión matemática a maximizar o minimizar.
2.  **Variables de decisión:** cantidades a determinar. 
3. **Restricciones:** limitaciones o requerimientos expresados como ecuaciones lineales o desigualdades. 
4. **Región factible:** set que contiene todas las posibles soluciones. 
5. **Solución óptima:** mejor solución en la **región factible.**
## Ejemplo
Más ejemplos en la sección de tareas.
  **Modelo:** 
  ```txt
  Max Z = 70x + 50y
  Subject to:
  4x + 3y ≤ 240 (Carpentry hours)
  2x + y ≤ 100 (Painting hours)
  x, y ≥ 0
  Where:
  x = number of tables
  y = number of chairs
  ```
  **Pasos para solución:**
  1. Graficar las restricciones.
  2. Identificar la región factible.
  3. Buscar puntos de esquina. (0,0), (50,0), (0,80), (30,40)
  4. Evaluar la función objetivo en cada punto. 
  5. Seleccionar el valor maximo. En (30,40), Z=4100
# Problemas de Transporte y Asignación
  Los **problemas de transporte** se enfocan en minimizar el costo de productos de una origen a un destino. 
  Los problemas de asignación buscan optimizar recursos entre uno a uno. 
  Ambos usan métodos como [[Método esquina noroeste, costo mas bajo, Vogel]], [[Método Húngaro o Algoritmo Munkrees]].
  **Términos clave:**
- Condición de balance: OFERTA = DEMANDA
- Una solución básica factible.
- Degeneración: Cuando el número de celdas ocupadas < m + n - 1
- Test para comprobar Optimalidad.
- Variable para balancear demanda y oferta.
## Ejemplo 
  ```txt
  From\To   W1  W2  W3  Supply
  Plant1    2   3   4   50
  Plant2    3   2   1   40
  Plant3    4   3   2   60
  Demand    30  50  70
  ```
  Se puede resolver con cualquiera de los algoritmos mencionados anteriormente.
# Optimización de redes
  Son problemas que se pueden representar usando grafos con nodos y vértices. Esto puede ser encontrar el camino más corto, árboles de expansión mínima, flujo máximo, y solución al Traveling Salesman Problem.
## Ejemplo
  ```txt
  A-B: 4  A-C: 2  A-D: 7
  B-C: 1  B-D: 3  C-D: 5
  ```
  Solución usando el [[algoritmo de Kruskal]]
  1. Ordenar vértices por costo ascendente. BC(1), AC(2), BD(3), AB(4), CD(5), AD(7)
  2. Agregarlos en orden si no crean ciclos. 
  3. Arbol final:BC, AC, BD.
# Métodos de solución
## Simplex
  Método algebraico para resolver problemas de programación lineal. [[Método simplex]]
## Dual Simplex
  [[Dual Simplex]]
# GUÍA RÁPIDA DE REFERENCIA PARA LA INVESTIGACIÓN OPERATIVA
## 1. Formas normales de problemas de programación lineal.
### Maximización
  ```
  MAX Z = c₁x₁ + c₂x₂ + ... + cⱼxⱼ
  Subject to:
  a₁₁x₁ + a₁₂x₂ + ... + a₁ⱼxⱼ ≤ b₁
  a₂₁x₁ + a₂₂x₂ + ... + a₂ⱼxⱼ ≤ b₂
  ...
  aᵢ₁x₁ + aᵢ₂x₂ + ... + aᵢⱼxⱼ ≤ bᵢ
  x₁, x₂, ..., xⱼ ≥ 0
  ```
### Minimización
  ```
  MIN Z = c₁x₁ + c₂x₂ + ... + cⱼxⱼ
  Subject to:
  a₁₁x₁ + a₁₂x₂ + ... + a₁ⱼxⱼ ≥ b₁
  a₂₁x₁ + a₂₂x₂ + ... + a₂ⱼxⱼ ≥ b₂
  ...
  aᵢ₁x₁ + aᵢ₂x₂ + ... + aᵢⱼxⱼ ≥ bᵢ
  x₁, x₂, ..., xⱼ ≥ 0
  ```
### Casos especiales
#### A. Problemas mixtos:
  ```
  Max Z = 4(xA1 + xB1 + xC1) + 3(xA2 + xB2 + xC2) + 2(xA3 + xB3 + xC3)
       - 3(xA1 + xA2 + xA3) - 2(xB1 + xB2 + xB3) - (xC1 + xC2 + xC3)
  
  Special Constraints:
  - Proportion constraints: xA1/(xA1 + xB1 + xC1) ≥ 0.8
  - Maximum content constraints: xC1/(xA1 + xB1 + xC1) ≤ 0.2
  ```
##### Ejemplo
  ```
  A soft drink manufacturer mixing 3 brands (A, B, C) to create 3 new products.
  
  Given:
  - Brand A: 2000 bottles available, cost €3/bottle
  - Brand B: 4000 bottles available, cost €2/bottle
  - Brand C: 1000 bottles available, cost €1/bottle
  
  Product Requirements:
  Product 1: At least 80% brand A, max 20% brand C
  Product 2: At least 20% brand A, max 80% brand C
  Product 3: Max 70% brand C
  
  Selling prices: Product 1: €4, Product 2: €3, Product 3: €2
  ```
  **Solución:**
  ```
  Variables: xij = quantity of brand i used in product j
  
  Maximize Z = 4(xA1 + xB1 + xC1) + 3(xA2 + xB2 + xC2) + 2(xA3 + xB3 + xC3)
           - 3(xA1 + xA2 + xA3) - 2(xB1 + xB2 + xB3) - (xC1 + xC2 + xC3)
  
  Subject to:
  Supply constraints:
  xA1 + xA2 + xA3 ≤ 2000
  xB1 + xB2 + xB3 ≤ 4000
  xC1 + xC2 + xC3 ≤ 1000
  
  Proportion constraints:
  xA1 ≥ 0.8(xA1 + xB1 + xC1)
  xC1 ≤ 0.2(xA1 + xB1 + xC1)
  xA2 ≥ 0.2(xA2 + xB2 + xC2)
  xC2 ≤ 0.8(xA2 + xB2 + xC2)
  xC3 ≤ 0.7(xA3 + xB3 + xC3)
  ```
#### B. Planes de producción
  ```
  Resource Limitations:
  - Time-based capacity constraints
  - Storage limitations
  - Inventory balance equations:
  xt - st = dt (production - storage = demand)
  ```
## 2. Formulas para problemas de transporte
### Modelo básico
  ```
  MIN Z = Σᵢ Σⱼ cᵢⱼxᵢⱼ
  
  Subject to:
  Supply constraints: Σⱼ xᵢⱼ = aᵢ
  Demand constraints: Σᵢ xᵢⱼ = bⱼ
  xᵢⱼ ≥ 0
  ```
### Balance Check
  ```
  Total Supply = Total Demand
  Σᵢ aᵢ = Σⱼ bⱼ
  ```
### Casos especiales
#### A. Problemas desbalanceados
  ```
  When Supply ≠ Demand:
  - If Supply > Demand: Add dummy destination
  - If Demand > Supply: Add dummy source
  Cost for dummy routes = 0
  ```
#### B. Degeneracion
  ```
  Condition: Number of basic variables < m + n - 1
  Solution: Add small quantity (ε) to maintain basis
  ```
## 3. Formulas de problemas de asignación
### Standard Form
  ```
  MIN Z = Σᵢ Σⱼ cᵢⱼxᵢⱼ
  
  Subject to:
  Σⱼ xᵢⱼ = 1 (one task per resource)
  Σᵢ xᵢⱼ = 1 (one resource per task)
  xᵢⱼ ∈ {0,1}
  ```
### Caso especial
#### A. Asignación desbalanceada
  ```
  When number of sources ≠ destinations:
  - Add dummy rows/columns
  - Set dummy costs = M (for minimization)
  - Set dummy costs = 0 (for maximization)
  ```
## 4. Formulas de problemas de redes
### Shortest Path
  ```
  MIN Z = Σ(i,j)∈A cᵢⱼxᵢⱼ
  
  Flow balance constraints:
  Σⱼ xᵢⱼ - Σⱼ xⱼᵢ = bᵢ
  where bᵢ = {1 for source, -1 for sink, 0 otherwise}
  ```
### Minimum Spanning Tree Properties
- Number of edges = n-1 (n = number of nodes)
- No cycles
- All nodes connected
### Casos especiales
#### A. Flow restringido
  ```
  Edge Capacity Constraints:
  0 ≤ xij ≤ uij
  where uij is the capacity of arc (i,j)
  ```
#### B. Multi-period networks.
  ```
  Time-layered networks:
  - Each node replicated for each time period
  - Arcs connect appropriate time periods
  - Storage represented by vertical arcs
  ```
##### Ejemplo
  ```
  Monthly fuel requirements (liters):
  Jan: 10333
  Feb: 25320
  Mar: 19370
  Apr: 14610
  
  Storage capacity: 25000 L
  Minimum stock: 7500 L
  Initial stock: 12000 L
  Storage cost: 0.0025 $/L/month
  ```
  **Solución:**
  ```
  Variables:
  xt = amount purchased in month t
  st = stock at end of month t
  
  Balance equations:
  st = st-1 + xt - dt
  where dt is demand in month t
  
  Constraints:
  7500 ≤ st ≤ 25000 (storage limits)
  s0 = 12000 (initial condition)
  ```
## 5. Reglas de conversión
### Inequality to Equality
  ```
  ≤ to =: Add slack variable (+s)
  ≥ to =: Subtract surplus variable (-s)
  ```
### Variable Sign Restrictions
  ```
  Unrestricted variable x = x⁺ - x⁻
  where x⁺, x⁻ ≥ 0
  ```
## 6. Condiciones de optimidalidad
### Simplex Method
- All coefficients in objective row ≥ 0 (MAX)
- All coefficients in objective row ≤ 0 (MIN)
- All right-hand side values ≥ 0
### Complementary Slackness
  ```
  If xⱼ > 0, then corresponding dual constraint is binding
  If slack > 0, then corresponding dual variable = 0
  ```
## 7. KEY CHECKS
### Feasibility Test
  ```
  All RHS values ≥ 0
  All constraints satisfied
  All non-negativity conditions met
  ```
### Optimality Test (Transportation)
  ```
  For each unoccupied cell:
  dᵢⱼ = uᵢ + vⱼ - cᵢⱼ ≤ 0 (MIN)
  dᵢⱼ = uᵢ + vⱼ - cᵢⱼ ≥ 0 (MAX)
  ```
## 8. Relaciones de dualidad
### Primal-Dual Correspondence
  ```
  Primal MAX ↔ Dual MIN
  ≤ constraint ↔ ≥ 0 variable
  ≥ constraint ↔ ≤ 0 variable
  = constraint ↔ unrestricted variable
  ```
### Teoremas de dualidad
  ```
  Weak Duality: Zₚ ≤ Zd (MAX)
  Strong Duality: Zₚ = Zd (at optimality)
  ```
## Casos especiales de programación entera
### Variable binaria
  ```
  AND Logic: y = x1 ∧ x2
  y ≤ x1
  y ≤ x2
  y ≥ x1 + x2 - 1
  
  OR Logic: y = x1 ∨ x2
  y ≥ x1
  y ≥ x2
  y ≤ x1 + x2
  
  XOR Logic: y = x1 ⊕ x2
  y ≤ x1 + x2
  y ≤ 2 - x1 - x2
  y ≥ x1 - x2
  y ≥ -(x1 - x2)
  ```
#### B. Restricciones condicionales. 
  ```
  If-Then Structure:
  If Σ a1jxj ≤ b1 → Σ a2jxj ≤ b2
  
  Transformation:
  Σ a1jxj - b1 ≥ (L1 - ε)y + ε
  Σ a2jxj - b2 ≤ U2(1 - y)
  Where y is binary
  ```
##### Ejemplo
  ```
  If x1 > 4 then x2 ≤ 6
  Where 0 ≤ x1, x2 ≤ 10
  ```
  **Solución**
  Convertir a restricciones lineales:
  ```
  x1 ≤ 4 + 6y
  x2 ≤ 10 - 4y
  Where y is binary
  ```
## Métodos de solución especiales
#### A. Variables limitadas
  ```
  For variables with upper bounds:
  lj ≤ xj ≤ uj
  
  Modified optimality conditions:
  If xj = uj, then corresponding reduced cost can be negative
  If xj = lj, then corresponding reduced cost can be positive
  ```
# Tarea 1
## Ejercicio 1 
  ![[Pasted image 20241209133015.png]]
  **Modelo**
- x1 = número de vitrinas provinciales francesas producidas al día
- x2 = número de vitrinas modernas danesas producidas al día
  ```
  Maximize z = 28x1 + 25x2
  
  Subject to:
  # Carpentry constraint
  3x1 + 2x2 ≤ 360
  
  # Painting constraint  
  1.5x1 + x2 ≤ 200
  
  # Finishing constraint
  0.75x1 + 0.75x2 ≤ 125
  
  # Minimum daily production constraints
  x1 ≥ 60
  x2 ≥ 60
  
  # Non-negativity
  x1, x2 ≥ 0
  ```
  Para la solución gráfica se hace un sistema de ecuaciones con las restricciones, se buscan los puntos de intersección, y se evalúan esos puntos en la función objetivo y la más grande es la óptima.
## Ejercicio 2
  ![[Pasted image 20241209133232.png]]
  **Modelo**
- x1 = número de bolsas de golf estándar producidas en 3 meses
- x2 = número de bolsas de golf de lujo producidas en 3 meses
  ```
  Maximize z = 10x1 + 9x2
  
  Subject to:
  # Cutting & Dyeing constraint (630 hours)
  0.7x1 + 1x2 ≤ 630
  
  # Sewing constraint (600 hours)
  0.5x1 + (5/6)x2 ≤ 600
  
  # Finishing constraint (708 hours)
  1x1 + (2/3)x2 ≤ 708
  
  # Inspection & Packaging constraint (135 hours)
  (1/10)x1 + (1/4)x2 ≤ 135
  
  # Non-negativity
  x1, x2 ≥ 0
  
  Note: Converting all fractions to decimals:
  5/6 ≈ 0.833
  2/3 ≈ 0.667
  1/10 = 0.1
  1/4 = 0.25
  
  Therefore the model can be rewritten as:
  
  Maximize z = 10x1 + 9x2
  
  Subject to:
  0.7x1 + 1.0x2 ≤ 630
  0.5x1 + 0.833x2 ≤ 600
  1.0x1 + 0.667x2 ≤ 708
  0.1x1 + 0.25x2 ≤ 135
  
  x1, x2 ≥ 0
  ```
Para encontrar la solución gráficamente, necesitamos resolver cada restricción para x2 para graficarlas:
- Corte y Teñido: x2 ≤ 630 - 0.7x1
- Costura: x2 ≤ 720 - 0.6x1
- Acabado: x2 ≤ 1062 - 1,5x1
- Inspección y embalaje: x2 ≤ 540 - 0,4x1
## Problema 3