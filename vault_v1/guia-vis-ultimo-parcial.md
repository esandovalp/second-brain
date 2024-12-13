#datavis
# Leaflet 
Se usa para integrar mapas interactivos en R.
<mark style="background: #BBFABBA6;">Características: </mark>
- Marcadores
- Polígonos
- Líneas
- GeoJSON
La idea es que sea lo más similar a `ggpplot2`
## Funciones 
- `addTiles()`: agrega <mark style="background: #ADCCFFA6;">mapas de base</mark>, el proveedor de base es OpenStreetMaps, pero también se puede especificar uno. Es lo que cambia como se ve un mapa, usando `addProviderTiles`decimos que otro proveedor queremos.  
- `setView()`: pide coordenadas de latitud y longitud, además se le puede ajustar el zoom. Es la que nos ayuda a especificar una región. 
- `<strong> </strong> <br>`: así agregamos leyendas, con el <mark style="background: #FFF3A3A6;">formato HTML </mark>.
## Notas
- El CRS tiene que ser WGS84, si no es, se usa `st_transform(dataset, cres=4326)`.
- Para el tipo de datos espaciales se pueden espicíficar: 
	1. matriz de columnas long lat. 
	2. df spatialpoints, spatiallines, spatialpolygons
	3. con un df de "maps".
# Shiny 
Arquitectura de Shiny, componentes: 
- Función `server`que hace, comportamiento.
- Función `ui`cómo se ve, características. 
## Ejemplo 
```R
library(shiny)
# Intefaz del usuario 
ui <- fluidPageg( 
	"Hola mundo"
)
#Servidor
server <- function(input, output, session) {
}
shinyApp(ui, server)
```
## Notas
- Una vez que se corre el proyecto o servidor, se queda en ejecución. 
- Cada proyecto necesita distintos directorios. 
- También usa formato HTML 
<mark style="background: #FF5582A6;">¿Entradas y salidas? </mark> *preguntar si vienen*
# Cuadros de mando 1 
Información más importante para alcanzar un objetivo en una sola pantalla <mark style="background: #ADCCFFA6;">Dashboards</mark>.
Tipos de cuadro de mando: 
1. Uso estratégico: largo plazo, no acciones inmediatas. No es interactivo.
2. Para análisis: entender que ha ocurrido, por qué. 
3. Uso operacional, monitorear operaciones. 
Recomendaciones:
- Simple 
- No mas de 7 widgets
- Pocas tonalidades
## Con Shiny 
### Shiny dashboard 
Paquete de R para crear plantillas de Dashboards. 
## Tablaeu 
Ventajas: 
- Cualquier fuente de datos 
- Rápido y eficiente con grandes volúmenes de datos
- Interfaz intuitiva
- Lenguaje VizQL 
Nomenclatura: 
- <mark style="background: #ADCCFFA6;">Dimensiones: </mark> variables categóricas. 
- <mark style="background: #ADCCFFA6;">Medidas: </mark> variables cuantitativas. 
- <mark style="background: #ADCCFFA6;">Continuo, discreto: </mark> tipo de número.

**Nota:** lo que sigue es un tutorial de Tableau, recomendable hacer la [[practica-tableau]]