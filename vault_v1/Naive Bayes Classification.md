#ml 

Esta basado en el teorema de Bayes: 

$$ \mathbb{P}(A|B)=\frac{\mathbb{P}(B|A)\mathbb{P}(A)}{\mathbb{P(B)}} $$

Es **naive** porque asumimos que las features son independientes de una.

Implementación 

```python
import numpy as np
from scipy.stats import norm

class GaussianNaiveBayes:
    def __init__(self):
        self.classes = None
        self.mean = None
        self.var = None
        self.priors = None

    def fit(self, X, y):
        n_samples, n_features = X.shape
        self.classes = np.unique(y)
        n_classes = len(self.classes)

        # Initialize parameters
        self.mean = np.zeros((n_classes, n_features))
        self.var = np.zeros((n_classes, n_features))
        self.priors = np.zeros(n_classes)

        # Calculate mean, variance, and prior for each class
        for idx, c in enumerate(self.classes):
            X_c = X[y == c]
            self.mean[idx, :] = X_c.mean(axis=0)
            self.var[idx, :] = X_c.var(axis=0)
            self.priors[idx] = X_c.shape[0] / n_samples

    def predict(self, X):
        return np.array([self._predict(x) for x in X])

    def _predict(self, x):
        posteriors = []

        # Calculate posterior probability for each class
        for idx, c in enumerate(self.classes):
            prior = np.log(self.priors[idx])
            posterior = np.sum(np.log(self._pdf(idx, x)))
            posterior = prior + posterior
            posteriors.append(posterior)

        # Return the class with highest posterior probability
        return self.classes[np.argmax(posteriors)]

    def _pdf(self, class_idx, x):
        mean = self.mean[class_idx]
        var = self.var[class_idx]
        return norm.pdf(x, mean, np.sqrt(var))

# Example usage
if __name__ == "__main__":
    # Generate some random data
    np.random.seed(0)
    X = np.random.randn(100, 2)
    y = np.random.randint(0, 2, 100)

    # Split into train and test sets
    X_train, X_test = X[:80], X[80:]
    y_train, y_test = y[:80], y[80:]

    # Create and train the model
    nb = GaussianNaiveBayes()
    nb.fit(X_train, y_train)

    # Make predictions
    predictions = nb.predict(X_test)

    # Calculate accuracy
    accuracy = np.mean(predictions == y_test)
    print(f"Accuracy: {accuracy:.2f}")
    ```

Es muy robusto, que no es el caso de [[K nearest neighbors]]

