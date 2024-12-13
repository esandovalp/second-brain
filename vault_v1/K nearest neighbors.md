#ml 
Es un algoritmo de clasificación.

Clasifica de acuerdo a cual es su vecino más cercano. Esto lo hace calculando sus distancias. 

Se le considera un algoritmo "lazy", por lo que no se necesita entrenarlo, en este paso sólo tienes que guardar la info que será usada. 

El paso de predicción es a través de el calculo de distancias de sus vecinos. 
	_For each stored data point xᵢ in D: a. Calculate the distance d(x, xᵢ) using the chosen distance metric b. Store the pair (d(x, xᵢ), yᵢ)_

```python
import numpy as np
from collections import Counter

class KNN:
    def __init__(self, k=3):
        self.k = k
        self.X_train = None
        self.y_train = None

    def fit(self, X, y):
        """
        Training algorithm: Store the training data
        """
        self.X_train = np.array(X)
        self.y_train = np.array(y)

    def predict(self, X):
        """
        Prediction algorithm: Predict labels for given samples
        """
        return np.array([self._predict_single(x) for x in X])

    def _predict_single(self, x):
        """
        Predict label for a single sample
        """
        # Calculate distances
        distances = np.sqrt(np.sum((self.X_train - x)**2, axis=1))
        
        # Get indices of k nearest neighbors
        k_indices = np.argsort(distances)[:self.k]
        
        # Get labels of k nearest neighbors
        k_nearest_labels = self.y_train[k_indices]
        
        # Majority vote
        most_common = Counter(k_nearest_labels).most_common(1)
        return most_common[0][0]

# Example usage
if __name__ == "__main__":
    # Generate some random data
    np.random.seed(0)
    X_train = np.random.rand(100, 2)
    y_train = np.random.randint(0, 2, 100)
    X_test = np.random.rand(20, 2)

    # Create and train the model
    knn = KNN(k=3)
    knn.fit(X_train, y_train)

    # Make predictions
    predictions = knn.predict(X_test)

    print("Predictions:", predictions)
    ```

De aquí vimos [[Naive Bayes Classification]]