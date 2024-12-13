# Markov Chains 
Models sequence of states, in a finite way. Transitions between states that happen between some probability. 
<mark style="background: #ADCCFFA6;">Markov property</mark>: the next state depends on the current state and the probability of the next one, similar to <mark style="background: #ADCCFFA6;">memory loss</mark> from an exponential distribution.
## Hidden Markov Models
They are used in processes that generate noisy sequences, like <mark style="background: #FF5582A6;">typos</mark>. <mark style="background: #FFF3A3A6;">Markov chain with outputs. </mark>
- <mark style="background: #ADCCFFA6;">Emission distribution</mark>, distributions of outputs given the states.
- They are also initial distribution of states.
# Markov chains: states and transitions between states
La transición entre estados está representada por una matriz $P$ con probabilidades.
- <mark style="background: #FFF3A3A6;">Las transiciones de salida tienen sumar 1.</mark>
- La probabilidad de transición se denota con p. 
Una aplicación de cadenas de markov son las [[M-GRAMS]], queremos que tengan estados finitos y tiempo homogeneo. 
- Nosotros les damos las probabilidades de transición, las estimamos por observaciones, experimentos. 
	- Se usa Bayes para poder manejar estas probabilidades. 
- Un <mark style="background: #ADCCFFA6;">Trellis</mark> es un grafo que, en donde cada una de las observaciones tiene una cadena de Markov, sólo tenemos los estados y construimos las transiciones. 