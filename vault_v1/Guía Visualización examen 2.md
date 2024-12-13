# Gráficas para redes 
Son grafos, nodos conectados por enlaces. 
<mark style="background: #FF5582A6;">Propiedades</mark>:
1. Generación
2. Distancia entre nodos
3. Alcanzabilidad
4. <mark style="background: #ADCCFFA6;">Conectividad: </mark> robustez en función del número de conexiones, e.g. una red débil es una con pocas conexiones.
5. <mark style="background: #ADCCFFA6;">Centralidad:</mark> influencia relativa de nodos individuales, e.g. cercanía, betweenness, influencia. 
6. <mark style="background: #ADCCFFA6;">Densidad</mark>: medida de la intensidad de interconexiones. 
7. <mark style="background: #ADCCFFA6;">Excentricidad</mark>: distancia maxima entre un nodo y los demás. 
8. <mark style="background: #ADCCFFA6;">Circunferencia:</mark> número de enlaces en el ciclo más largo. 
9. Difusión de información
10. Cooperación/colaboración
11. Tolerancia a fallas
## Random networks & Small Worlds
- Tienen pocos nodos que están conectados entre sí. 
	- Bajo coeficiente de agrupamiento.
- Lo común es que haya poca separación entre cosas (en el mundo). La más larga es de 19.
## Caracterísiticas
1. <mark style="background: #ADCCFFA6;">Grado:</mark> número de vértices adyacentes. Pueden tener dirección y se le dice como "indegree", "outdegree".
2. <mark style="background: #ADCCFFA6;">Dirigidos</mark>: A le dio un regalo a B
3. <mark style="background: #ADCCFFA6;">No dirigidos:</mark> A y B son amigos.
4. <mark style="background: #ADCCFFA6;">Enlaces</mark>: pueden tener propiedades como: peso, ranking, tipo, intermediación.
## Visualizaciones 
- <mark style="background: #ADCCFFA6;">Force-directed placement: </mark> nodos se repelan pero los enlaces los atraen. 
- Su ubicación final es contingente. 
- Poca escalibilidad.
# Grafos en R 
Se usan librerías como: 
- `ggraph`: similar a GGplot, con capacidad para añadir capas, modificar propiedades, como tamaño y tonalidad. 
- `igraph`: útil para estadísticas y métricas de grafos. 
# Árboles
Un grafo sin ciclos. 
- <mark style="background: #ADCCFFA6;">Visualizaciones Reingold-Tilford: </mark>Algoritmo para visualizar árboles 
## Treemap
- 2 atributos cuantitativos en cada hoja. 
- Contención, sólo hojas son visibles. 
- Tiene una estructura jerárquica.
- Consultar atributos a nivel de hojas. 
### Otras representaciones. 
- Sunburst: radial.
- icicle: rectos. 
# Datos espaciales
 - <mark style="background: #ADCCFFA6;">Polígonos:</mark> es con lo que se representan entidades geográficas.
	 - Sobre esto se despliegan capas que pueden tener etiquetas, puntos de interés, etc. También se despliegan cuantitativos, como coropletas.
## Coropletas
- Polígonos coloreados con paletas de colores secuenciales. Los valores son estadísticos. 
- Es importante definir los cortes o los bins en un histograma. 
## Clasificación 
- Se necesitan saber las categorías
	- Entre 5-10
## Sistemas de información geográfica (GIS)
Nos permite traducir datos espaciales en información y procesarlos, lo que se hace en Google Maps, Waze.
## Sistema de Referencia de Coordenadas (CRS) 
- <mark style="background: #ADCCFFA6;">Unidades angulares: </mark> latitud y longitud. CRS geográfico.
- <mark style="background: #ADCCFFA6;">Unidades lineales: </mark> basadas en una malla plana, e.g. Norte 25 metros, Este 32 metros. CRS proyectado. 
- <mark style="background: #ADCCFFA6;">DATUM: </mark> modelo de la forma de la superficie de la tierra, e.g. UTM, BNG.
- Proyecciones: se pueden conservar ángulos (Mercator) o áreas (Lambert)
### Tipos de datos: 
1. Dato espacial: tiene coordenadas geográficas
2. Vector: entidades o características discretas dentro del espacio, como puntos, lineas, polígonos. 
	- Se usa el paquete `sf` para representar datos vectoriales, i.e. con varios atributos. 
		- Se usan extensiones para guardarlos como `.shp,.geojson`
1. <mark style="background: #FFF3A3A6;">Raster: </mark> campo continuo a través del espacio, e.g. elevación, temperatura. Representados como una malla de celdas o pixeles. Tiene que ser un sólo atributo, cada celda tiene un valor diferente de este. 
	- Es el más eficiente para representar variables continuas. 
