# Graphs for networks   
They are graphs, nodes connected by links.   
<mark style=“background: #FF5582A6;”>Properties</mark>:  
1. Generation  
2. Distance between nodes  
3. Reachability  
4. <mark style=“background: #ADCCFFA6;”>Connectivity: </mark> robustness as a function of the number of connections, e.g. a weak network is one with few connections.  
5. <mark style=“background: #ADCCFFA6;”>Centrality:</mark> relative influence of individual nodes, e.g. closeness, betweenness, influence.   
6. <mark style=“background: #ADCCFFA6;”>Density</mark>: measure of the intensity of interconnections.   
7. <mark style=“background: #ADCCFFA6;”>Excentricity</mark>: maximum distance between a node and the others.   
8. <mark style=“background: #ADCCFFA6;”>Circumference:</mark> number of links in the longest cycle.   
9. Information diffusion  
10. Cooperation/collaboration  
11. Fault tolerance  
## Random networks & Small Worlds  
- Few nodes that are connected to each other.   
- Low clustering coefficient.  
- Commonly there is little separation between things (in the world). Longest is 19.  
## Characteristics  
1. <mark style=“background: #ADCCFFA6;”>Grade:</mark> number of adjacent vertices. They can have direction and it is said as “indegree”, “outdegree”.  
2. <mark style=“background: #ADCCFFA6;”>Directed</mark>: A gave B a gift.  
3. <mark style=“background: #ADCCFFA6;”>Nondirected:</mark> A and B are friends.  
4. <mark style=“background: #ADCCFFA6;”>Links</mark>: can have properties such as: weight, ranking, type, intermediate.  
## Visualizations   
- <mark style=“background: #ADCCFFA6;”>Force-directed placement: </mark> nodes repel but links attract them.   
- Their final location is contingent.   
- Low scalability.  
## Graphs in R   
Libraries are used such as:   
- `ggraph`: similar to GGplot, with ability to add layers, modify properties, such as size and hue.   
- igraph`: useful for graph statistics and metrics.   
# Trees  
A graph without cycles.   
- <mark style=“background: #ADCCFFA6;”>Reingold-Tilford visualizations: </mark>Algorithm to visualize trees.   
## Treemap  
- 2 quantitative attributes on each leaf.   
- Containment, only leaves are visible.   
- Hierarchical structure.  
- Query attributes at leaf level.   
### Other representations.   
- Sunburst: radial.  
- icicle: straight.   
# Spatial data  
- <mark style=“background: #ADCCFFA6;”>Polygons:</mark> is what geographic entities are represented with.  
- On top of this, layers are displayed that can have labels, points of interest, etc. Quantitative ones, such as choropleths, are also displayed.  
## Choropleths  
- Polygons colored with sequential color palettes. Values are statistical.   
- It is important to define the slices or bins in a histogram.   
## Classification   
- Need to know the categories  
- Between 5-10  
## Geographic Information Systems (GIS)  
Allows us to translate spatial data into information and process it, which is done in Google Maps, Waze.  
## Coordinate Reference System (CRS)   
- <mark style=“background: #ADCCFFA6;”>Angle units: </mark> latitude and longitude. Geographic CRS.  
- <mark style=“background: #ADCCFFA6;”>Linear units: </mark> based on a flat grid, e.g. North 25 meters, East 32 meters. Projected CRS.   
- <mark style=“background: #ADCCFFA6;”>DATUM: </mark> model of the shape of the earth's surface, e.g. UTM, BNG.  
- Projections: angles (Mercator) or areas (Lambert) can be retained.  
### Types of data:   
Spatial data: has geographic coordinates 2.  
2. Vector: discrete entities or features within space, such as points, lines, polygons.   
- The `sf` package is used to represent vector data, i.e. with various attributes.   
- Extensions are used to save them as `.shp, .geojson`.  
1. <mark style=“background: #FFF3A3A6;”>Raster: </mark> continuous field through space, e.g. elevation, temperature. Represented as a grid of cells or pixels. Must be a single attribute, each cell has a different value of this.   
- It is the most efficient for representing continuous variables.