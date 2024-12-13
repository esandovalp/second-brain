#parallelcomputing 
# Bag of Words with MPI 
Serán 6 archivos '.txt'
Estos son los requerimentos:
## Entrada
- ﻿﻿Listado de nombres de los archivos donde se encuentran las palabras a contar (los archivos se pueden encontrar en el mismo lugar que el ejecutable)
- ﻿﻿Nombre del archivo en donde se encuentra el vocabulario y su tamaño.
- ﻿﻿Número de procesos a utilizar que debe ser igual al número de archivos a introducir
## Salida
- Archivo con matriz de Bolsa de Palabras en formato CSV.
## Más requerimentos:
- Para simplificar el problema, el código debe poder trabajar exactamente para 6 libros, pero puede ser cualquier libro.
- ﻿﻿Para simplificar el problema, se puede asumir el vocabulario y su tamaño (se puede extraer de la libreta de python).
- ﻿﻿Implementar versión paralela con MPI y Versión Serial.
- ﻿﻿Calcular y gráficar speed-ups, i.e., comparar el tiempo de ejecución de la version paralela con la versión serial.
## Prueba que deberá pasar su Programa para determinar su calificación:

- **Paso 0**. A partir de una lista de nombres de libros, se debe extraer el vocabulario y el tamaño de este para cada uno de los libros. Este paso es el único que se puede hacer en otro lenguaje que no sea C/C++, por ejemplo, python. Este paso se puede realizar manualmente utilizando como base el código provisto por el profesor:
```python
# Libraries
import pandas as pd
import numpy as np
import re
import nltk
import matplotlib.pyplot as plt

# Labeled corpus
etiquetas = ["libro1", "libro2", "libro3", "libro4", "libro5", "libro6"]
corpus = []
  
for etiqueta in etiquetas:
	archivo = open(etiqueta + ".txt", "r")
	corpus.append(archivo.read())
	archivo.close()
  
etiquetas = ["dicke..", "sha...", "libro3", "libro4", "libro5", "libro6"]
corpus = np.array(corpus)
df_corpus = pd.DataFrame({"documento": corpus,
"categoria": etiquetas})
df_corpus
```
### Model for Bag of Words
```python
from sklearn.feature_extraction.text import CountVectorizer
# bolsa de palabras en matriz dispersa
count_vectorizer = CountVectorizer(min_df=0.0, max_df=1.0)
matriz_conteo = count_vectorizer.fit_transform(corpus)
matriz_conteo
# ver valores diferentes de cero en la matriz dispersa
print(matriz_conteo)
# ver la representación densa
matriz_conteo = matriz_conteo.toarray()
matriz_conteo
# obten todas las palabras únicas del corpus
vocabulario = count_vectorizer.get_feature_names_out()
# muestra los vectores de características del documento
pd.DataFrame(matriz_conteo, columns=vocabulario)
```
### Vocabulary (number of columns of the matrix)
```python
print(len(vocabulario), vocabulario)
np.savetxt("vocab.txt", vocabulario, fmt="%s", delimiter=",")
```

Ya en sus programas de C++, tanto en la versión serial como en la paralela:
- ﻿﻿**Paso 1**. Se incluirá una lista con los nombres de 6 libros diferentes. Estos nombres se deben poder pasar como parámetros en la consola.
- ﻿﻿**Paso 2**. Se extraerá automáticamente los datos de los archivos csv correspondientes a los libros en función de la lista definida en el paso 1.
- ﻿﻿**Paso 3**. La salida del programa será la matriz de Bolsa de Palabras en formato csv además del tiempo de ejecución.
- ﻿﻿**Paso 4**. Se deberá obtener un speed up con la versión paralela mayor a 1.2x.
## Hello world of dictionaries: 
```c++
#include <map>
#include < string>
#include <iostream> 
using namespace std;

int main (int argc, char *argvl]) {
	map<string, int> my _dictionary;
	my_dictionary.insert({"computo", 100}); my_dictionary.insert({"paralelo", 200});
	my_dictionary.insert({"curso", 300});
	//my_dictionary.at("paralelo") = 3;
	my_dictionaryl"paralelo"] = 4;
	cout < my_dictionary.at("paralelo") << "\n";
	cout << my_dictionary.at("computo") « "In"; cout << my_dictionaryl"paralelo"] << "\n"; cout << my_dictionary.count("inexistente") << "\n"; cout <my_dictionary.count("paralelo") « "\n";
	my_dictionary.erase("curso");
	
	for (auto iterator = my_dictionary.begin(); iterator != my_dictionary.end();++titerator) {
		cout « iterator->first <<""<< iterator->second << "|n";
	}
	return 0;
```
# Initial prompt to ChatGPT 
I want to create two versions for a Bag of Words that takes 6 books on '.txt' format, one is a serial version and the other is parallelized with MPI. Help me structure my approach and let's start doing it step by step. 
The requirements are: 
## Input
- List of file names where the words to be counted are located (the files can be found in the same place as the executable).
- Name of the file where the vocabulary is located and its size.
- Number of processes to be used, which must be equal to the number of files to be entered.
## Output
- File with Bag of Words matrix in CSV format.
## Further requirements:
- To simplify the problem, the code must be able to work for exactly 6 books, but it can be any book.
- To simplify the problem, the vocabulary and its size can be assumed (can be extracted from python notebook).
- Implement parallel version with MPI and Serial Version.
- Calculate and plot speed-ups, i.e., compare the execution time of the parallel version with the serial version.

In the next prompt I'm gonna tell you the test that the program must pass to determine its qualification. 
## Test the program must pass to determine its qualification:

- **Step 0**. From a list of book names, you must extract the vocabulary and vocabulary size for each of the books. This step is the only step that can be done in a language other than C/C++, e.g., python. This step can be done manually using the code provided by the teacher as a basis:
```python
# Libraries
import pandas as pd
import numpy as np
import re
import nltk
import matplotlib.pyplot as plt

# Labeled corpus
etiquetas = ["libro1", "libro2", "libro3", "libro4", "libro5", "libro6"]
corpus = []
  
for etiqueta in etiquetas:
	archivo = open(etiqueta + ".txt", "r")
	corpus.append(archivo.read())
	archivo.close()
  
etiquetas = ["dicke..", "sha...", "libro3", "libro4", "libro5", "libro6"]
corpus = np.array(corpus)
df_corpus = pd.DataFrame({"documento": corpus,
"categoria": etiquetas})
df_corpus
```
### Model for Bag of Words
```python
from sklearn.feature_extraction.text import CountVectorizer
# bolsa de palabras en matriz dispersa
count_vectorizer = CountVectorizer(min_df=0.0, max_df=1.0)
matriz_conteo = count_vectorizer.fit_transform(corpus)
matriz_conteo
# ver valores diferentes de cero en la matriz dispersa
print(matriz_conteo)
# ver la representación densa
matriz_conteo = matriz_conteo.toarray()
matriz_conteo
# obten todas las palabras únicas del corpus
vocabulario = count_vectorizer.get_feature_names_out()
# muestra los vectores de características del documento
pd.DataFrame(matriz_conteo, columns=vocabulario)
```
### Vocabulary (number of columns of the matrix)
```python
print(len(vocabulario), vocabulario)
np.savetxt("vocab.txt", vocabulario, fmt="%s", delimiter=",")
```
In the C++ programs, both in the serial and parallel versions:
- **Step 1**. A list with the names of 6 different books will be included. You must be able to pass these names as parameters in the console.
- **Step 2**. The data of the csv files corresponding to the books will be automatically extracted files corresponding to the books according to the list defined in step 1.
- **Step 3**. The output of the program will be the Bag of Words matrix in csv format in addition to the run time.
- **Step 4**. A speed up should be obtained with the parallel version greater than 1.2x.
### Hello world of dictionaries: 
```c++
#include <map>
#include < string>
#include <iostream> 
using namespace std;

int main (int argc, char *argvl]) {
	map<string, int> my _dictionary;
	my_dictionary.insert({"computo", 100}); my_dictionary.insert({"paralelo", 200});
	my_dictionary.insert({"curso", 300});
	//my_dictionary.at("paralelo") = 3;
	my_dictionaryl"paralelo"] = 4;
	cout < my_dictionary.at("paralelo") << "\n";
	cout << my_dictionary.at("computo") « "In"; cout << my_dictionaryl"paralelo"] << "\n"; cout << my_dictionary.count("inexistente") << "\n"; cout <my_dictionary.count("paralelo") « "\n";
	my_dictionary.erase("curso");
	
	for (auto iterator = my_dictionary.begin(); iterator != my_dictionary.end();++titerator) {
		cout « iterator->first <<""<< iterator->second << "|n";
	}
	return 0;
```

Having a longer `stopwords.txt` helped getting a more significant speed up.
Here: https://gist.github.com/larsyencken/1440509

# Traducir y explicar con mis palabras que está pasando en el código paralelo 

## Función loadVocab
```
	// Loads the vocabulary from a CSV file into a vector

vector<string> loadVocab(const string& filePath) {
	ifstream file(filePath);
	vector<string> vocab;
	string line, word;
	if (file.is_open()) {
	
		while (getline(file, line)) {
			istringstream stream(line);
			while (getline(stream, word, ',')) {
				vocab.push_back(word);
			}
		}
	} else {
		cerr << "Failed to open the vocabulary file." << endl;
		MPI_Abort(MPI_COMM_WORLD, EXIT_FAILURE);
	}
	return vocab;
}
```
## Función principal
```cpp
// Main execution of the word counting per book
void executeWordCount(const vector<string>& files, vector<string>& vocab, int rank, int size, double& totalTime) {
	const int iterations = 10;
	map<string, int> counts;
	vector<int> localCounts(vocab.size(), 0), allCounts(vocab.size() * size);
	  
	// Broadcasting vocabulary once
	int vocabSize = vocab.size();
	MPI_Bcast(&vocabSize, 1, MPI_INT, 0, MPI_COMM_WORLD);
	vocab.resize(vocabSize);
	for (string& word : vocab) {
		int length = word.size();
		MPI_Bcast(&length, 1, MPI_INT, 0, MPI_COMM_WORLD);
		word.resize(length);
		MPI_Bcast(&word[0], length, MPI_CHAR, 0, MPI_COMM_WORLD);
	}
	
	for (int i = 0; i < iterations; ++i) {
		double startTime = MPI_Wtime();
		// Process the book file
		ifstream bookFile(files[rank]);
		string line;
		while (getline(bookFile, line)) {
			istringstream lineStream(line);
			string token;
			while (getline(lineStream, token, ',')) {
				if (counts.find(token) != counts.end()) {
					counts[token]++;
				} else {
					counts[token] = 1;
				}
			}
		}
	
		// Prepare local counts for gathering
		for (size_t j = 0; j < vocab.size(); ++j) {
			localCounts[j] = counts[vocab[j]];
		}
		MPI_Gather(localCounts.data(), vocab.size(), MPI_INT, allCounts.data(), vocab.size(), MPI_INT, 0, MPI_COMM_WORLD);
	
		double endTime = MPI_Wtime();
		totalTime += endTime - startTime;
	}
	
	if (rank == 0) {
		cout << "Average execution time: " << totalTime / iterations << " seconds" << endl;
	}
}
```