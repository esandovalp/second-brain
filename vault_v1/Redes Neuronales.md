#ai 

![[Pasted image 20240418160832.png]]

Características clave:

- ﻿﻿Las distintas intensidades de las señales recibidas en cada dendrita se modelan como  
    distintos pesos de las conexiones de entrada
- ﻿﻿Los valores de entrada y de salida suponemos que pueden valer únicamente 0 o 1
- ﻿﻿La neurona artificial actúa como un sumador, haciendo una suma ponderada de sus entradas, la cual, si rebasa cierto umbral, hace que se proporcione un 1 a la salida

Características de las redes neuronales artificiales:

- ﻿﻿Buenas para aprender asociaciones
- ﻿﻿Se entrenan mostrándoles ejemplos
- ﻿﻿Recuerdan ejemplos anteriores después de aprender ejemplos nuevos (no olvidan los  
    ejemplos anteriores)
- ﻿﻿Poco a poco aprenden una generalización de los ejemplos  
    La generalización que aprende una red queda distribuida entre los pesos finales de sus conexiones (los pesos generalmente se inicializan de forma aleatoria)
- ﻿﻿No son tan sensibles al ruido como otros algoritmos
- ﻿﻿Una red neuronal (artificial) típica tiene tres capas (una de entrada, una intermedia y una de salida) de neuronas como las que se mostraron anteriormente, pero hay variantes
- ﻿﻿Como algoritmo de entrenamiento se usa la retropropagación ("back propagation"): se comparan las salidas obtenidas con las deseadas, y se usa la diferencia para hacerle ajustes a los pesos de las conexiones, partiendo desde la capa de salida y avanzando capa por  
    capa hacia la capa de entrada

Se ajustan los pesos hasta llegar a cierto umbral de aceptabilidad, depende de nosotros definirlo.

![[Pasted image 20240418160942.png]]

Nosotros decidimos cuantas **Hidden Layer**.
El [[one hot encoding]] simplifica la implementación. Ha sido mucho prueba y error. 