#ai 
Sistema de diseño arquitectónico (oficinas, pisos de oficinas).
Estructura:
- Tres columnas: goal (descripción del problema que se intentó resolver), plan (plano arquitectónico, la solución) y outcome (Res exitoso o no exitoso).
- Cuatro renglones: organization (aspectos sobre la empresa que va a ocupar los casos), core (ideas principales detrás del diseño de las oficinas), partitions (divisiones móviles), furniture (muebles)
- Los nombres están como INICIAL_DE_RENGLÓN-NOMBRE COLUMNA
- Se creó un esquema general y por eso algunos valores están vacíos.

Comportamiento:
- Si se le dice que vars son relevantes a la iluminación y cosas parecidas entonces rápidamente puede buscar en su memoria de casos y determinar cuáles son relevantes para esa clase de outcome.**RETRIEVE**
- Esta clase de modelos es lo que le da al sistema la capacidad de **retrieve** los casos (indexarlos y buscarlos)
- Con los intereses del usuario nuevo puede llegar fácilmente el sistema a los casos que resultan relevantes
- Los modelos son para entregar casos relevantes de forma más flexible
- Esto permite hacer una agrupación de casos según el modelo de calidad de iluminación = clustering
- Esto responde a una de las preguntas de cómo se pueden organizar los casos dentro de la memoria del sistema: se pueden organizar con clasificaciones (iluminación es solo un ejemplo)

Archie solo es un **sistema de apoyo (recupera casos)** pero no toma decisiones, el sistema facilita el acceso a los casos, es por esto que no se considera un sistema inteligente ni experto. 