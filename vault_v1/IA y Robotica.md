#ai

![[Pasted image 20240423165159.png]]

Sensores = térmicos, de proximidad (sonar, radar, láser), de presión, ópticos (cámaras)
Actuadores = ruedas, brazos manipuladores, patas “orguas”

# Enfoques de Al aplicada a la robótica:

- ﻿﻿Enfoque deliberativo: enfatiza razonamiento y procesamiento detallado de la información de los sensores para tomar decisiones y planear cuidadosamente las acciones. Requiere un mapa/modelo completo (lo más posible) y detallado del ambiente en el que va a moverse el robot. Enfoque apropiado para ambientes estáticos y conocidos con anticipación, y para realizar tareas con poca variabilidad. Ejemplo: robot Shakey desarrollado en Stanford (https://en.wikipedia.org/wiki/Shakey_the_robot) entre 1966 y  1972.
- ﻿﻿Enfoque reactivo: enfatiza conexión directa ("intuitiva", basada en "reflejos" pre-programados) entre sensores y actuadores, minimizando al máximo el razonamiento (incluyendo mapas/modelos del ambiente en el que se va a desenvolver el robot). Bueno para ambientes dinámicos y desconocidos, y para tareas que requieren mayor flexibilidad.  
Ejemplos: robots, insectoides, desarrollados por Rodney Brooks
(https://www.britannica.com/biography/Rodney-Allen-Brooks) en MIT en los años 80 y 90.
- Enfoques híbridos: combinan aspectos de los dos anteriores (por ejemplo, comienzan a actuar de forma reactiva pero poco a poco construyen un mapa/modelo mental, aunque sea parcial y sujeto a correcciones, para luego consultarlo cada vez más y más y poder  deliberar más). Arquitectura ARA basada en comportamientos


