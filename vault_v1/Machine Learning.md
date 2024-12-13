#ml 
# Preguntas de Chatbots (conceptos a repasar - 07 Clasificación - slide 82)

1. **¿Qué es un parámetro y como lo estimamos?:** son valores que se aprenden de la data data una vez se corre el modelo, e.g. en regresión lineal son las ordenadas al origen y la pendiente. ==Automático==. Son ajustadas para minimizar el MSE de la [[Loss function]]. Una manera común de estimar los parametros es el [[Stochastic Gradient Descent]]. 
2. **¿Qué es un hyperparametro  y como lo estimamos? ¿Qué pasa si lo estimamos como el train o validation o con cross validation?**: es algo que definimos ==manualmente== antes de correr el modelo, e.g. el depth de un random forest. Una manera común de estimar estos números es [[Cross Validation]]
3. **Entender train, validation, cross validation y como se relaciona con el error de generalización:** [[Training, Validation, Test sets]], respectivamente, es el set que se usa para que el modelo aprenda los parámetros. El validation es el set que se usa para estimar hyperparametros, y el test es el que se usa para medir el performance del modelo en su fase final y con data que no ha visto. El [[Cross Validation]] ayuda para saber el performance del modelo dividiendo la data en distintos subsets o folds, e.g. en k-fold, se divide en k-1 para el training set y el último es el validation set, esto se hace k veces para que todos los folds sean el validation una vez. Se relacionan con el **error de generalización** en que este método nos ayuda a prevenir overfitting, esto es, que tenga un buen performance con data que no ha visto. Queremos minimizar el error de generalización. 
4. **¿Qué ventajas nos otorga Cross Validation? ¿qué podemos estimar?:** nos ayuda a que se use mejor toda la data, previene overfitting (baja varianza), y nos ayuda a estimar los hyperparametros. Podemos estimar el error de generalización, los hyperparametros.
5. **¿Cuál es la importancia del error de generalización o para qué nos sirve?** nos sirve para saber que tan malo será nuestro modelo con data que no ha visto. Esto a partir de la data que uso para su entrenamiento. 
6. **¿Qué pasa si al algoritmo le permitimos que elija el grado del polinomio usando los datos de train? Con validación y Con Cross Validation?**: Si se usa el training set entonces el modelo va a ==overfittiar==, lo mismo con validation set (es mejor), y si se usa con CV entonces es lo mejor, sin embargo, es más costoso. 
7. **Entender los tipos o fuentes de error y que se puede hacer en cada caso** (slide 84)
	1. **¿A qué se debe?**: 
		1. Overfitting: High variance, low bias. El modelo es muy complejo, en la parte de entrenamiento el modelo se ajusta mucho al training set.
		2. Underfitting: Low Variance, high bias. El modelo es muy simple.
		3. Noise: La data tiene mucha aleatoriedad, o data que no puede ser modelada. 
	2. **¿Cómo podemos solucionarlo con lo tenemos?**: 
		1. Overfitting: usando regularización, e.g. [[Ridge Regularization]], [[Lasso Regularization]], [[Cross Validation]], reducir complejidad del modelo.
		2. Underfitting: hacer el modelo más complejo, agregar features, feature engineering. 
		3. Noise: limpiar la data, usar modelos más simples. 
	3. **¿Cómo podemos solucionarlo si tuvieramos más tiempo y recursos?**
		1. Overfitting: Tomar más información, metodos de ensamblaje. 
		2. Underfitting: modelos más avanzados, tomar más features informativas. 
		3. Noise: mejorar la colección de información, fuentes de datos. 
8. **¿Qué es la regularización?**: Busca prevenir overfitting al ==penalizar== valores grandes de parametros. 
9. **¿Qué es la penalización?:** en la [[Loss function]] es este termino: $\lambda w^Tw$, es la representación matemática de la regularización. Es proporcional a la magnitud de los parámetros del modelo, e.g. el peso w. 
10. **¿Qué hace la penalización a una regresión lineal y como afecta a su lagrangiano?:** depende del tipo de regularización que se quiera hacer, primero este es el lagrangiano de regresión lineal: $$\mathcal{L}(\theta,\lambda)=\frac{1}{2}\sum_{i=1}^n(y_i-\hat{y}i)^2=1^n(y_i-X_i\theta)^2$$
	1. Con ==Ridge==: penaliza valores grandes de los parámetros. $$\mathcal{J}(\theta)=\frac{1}{2}\sum_{i=1}^n(y_i-\hat{y}i)^2+\lambda\sum_{j=1}^p\theta_j^2$$
	2. Con ==Lasso==: hace que haya más dispersión ya que pueden haber pesos 0. $$\mathcal{J}(\theta)=\frac{1}{2}\sum_{i=1}^n(y_i-\hat{y}i)^2+\lambda\sum_{j=1}^p|\theta_j|$$
	3. Su efecto en el lagrangiano es agregar a una $\lambda$ para las $\theta$, i.e. los parametros (pesos).
11. **Plantear el problema de optimización con los métodos que vimos, lagrangeano:** es lo de arriba. $$\mathcal{L}(\theta,\lambda)=\frac{1}{2}\sum_{i=1}^n(y_i-\hat{y}i)^2$$ Este es el método OLS (ordinary least squares), ridge o lasso agregan $\lambda$ 
12. **¿Qué hace lasso con las variables que no funcionan y por que?:** las hace 0, porque no contribuyen a la predicción, esencialmente las quita del modelo. 
13. **¿Por qué la lambda (o la alpha de la penalización) del lagrangiano es un hyperparametro?:** porque si es grande penaliza mucho más fuerte, e.g. en lasso puede poner más variables en 0, y si es muy chico se comporta como un ==OLS==. 
14. **¿Qué se esperaría que le pasara al error (train, test, validación, y cv) si aumentamos la penalización marginalmente o la regularización?**
	1. **Si tenemos baja regularización**: ==overfitting==
	2. **Si tenemos alta regularización**: ==underfitting==
	3. **Si estamos en un escenario intermedio**: modelo balanceado.
15. **En términos de regularización, ¿por qué es importante escalar las variables?**: porque si hay variables con valores grandes y otras con valores chicos, penalizará mucho a las grandes, sin importar que sean igualmente importantes. 
16. **¿Qué es overfitting?:** mucha varianza, poco sesgo, i.e. el modelo es muy bueno para predecir con lo que fue entrenado, pero si le das información nueva, es pésimo.
17. **¿Qué es underfitting?**: poca varianza, mucho sesgo, i.e. el modelo es muy simple, muy dumb, se pierden detalles importantes. 
18. **Como puedo detectar cada uno (usando train, test, validación o cross-validation) utilizando los errores.** 

|     | Escenario    | Training Error | Validation/Test error | Cross Validation Error         | Diagnosis                        |
| --- | ------------ | -------------- | --------------------- | ------------------------------ | -------------------------------- |
|     | Overfitting  | Bajo           | Alto                  | Alto (respecto a training)     | El modelo es complejo            |
|     | Underfitting | Alto           | Alto                  | Alto (con respecto a training) | Modelo es simple                 |
|     | Noise        | Muy bajo       | Alto (incosistente)   | Mucha varianza entre folds     | Modelo esta overfitted con ruido |
|     |              |                |                       |                                |                                  |
19. **¿Que es el bias del error y como puedo identificarlo (train, test validación y CV)?**: es cuando el modelo es muy simple, el modelo falla a entender las complejidades de la data. Se puede identificar porque hay mucho error en cualquiera de los sets. 
20. **¿Qué es la varianza del error y como puedo identificarlo (train, test validación y CV)?:** es que tanto varía el modelo con distintos subsets de data. Se identifica si hay muy poco error en el training pero mucho con el test o validation. 
21. **¿Cómo funciona un algoritmo de clasificación?**
	1. **Binario:** el modelo predice una de dos categorías, e.g. spam o no spam. 
	2. **Multiclase:** el modelo predice una de varias categorías, e.g. gato, perro, oso, abeja.
	3. Para más información ir a [[Classification]]
22. **¿Cómo podemos entrenar y evaluar estos algoritmos?** (slide 91)
	1. **Función de perdida:** para binaria [[Log Loss]] se busca minimizarla, si las probabilidades predichas se alinean con las reales, entonces es menor. Multiclase usamos [[Multinomial Log Loss]], esto es, la generalización de ==log loss==.
	2. **Otras métricas de Performance:** usar la matriz de confusión y tomar medidas como el ==accuracy, precision, sensitivity== o la buenísima [[AUC-ROC]]
23. **Qué pasa con las funciones de pérdida y de performance si…**
	1. **Las clases están balanceadas o desbalanceadas**: 
		- Una clase esta balanceada si tiene el mismo número de ejemplos. 
			- No se necesitan ajustar, para la loss function. 
			- Todas las medidas de performance funcionan bien. 
		- Si están desbalanceadas entonces habrá un ==bias== hacia el mayor número de ejemplos, por lo que se tienen que ajustar.
			- El ==accuracy== estará mal. 
	1. **Si hay varias clases:** estos métodos nos yudan a medir el performance en todas las clases
		1. **Micro:** suma la contribución de todas las clases, no hay efecto directo en la loss function y da el mismo peso a todas las clases, esto es bueno para el imbalance.
		2. **Macro:** calcula para cada clase y después les asigna el mismo peso a todas, en base a su media, bueno para tratar a todas las clases igual)
		3. **Weighted:** le da más peso a las clases con más instancias. Puede usar weighted loss en la función de pérdida. 
24. **¿Qué hace la curva ROC?:** nos dice que tan cercanas son las predicciones predichas a las reales, entre más cerca a la curva mejor. [[AUC-ROC]]
25. **Qué alternativas hay al under/over-sampling?**
	1. **MCC:** es una formula que toma en cuenta los valores de la matriz de confusión, nos ayuda al imbalanceo de clases. 
	2. **Weighted**: dar diferentes pesos a las clases, e.g. le puedes dar más peso a las clases con pocas instancias. 
26. **Como tenemos que dividir/samplear los sets de train, validation, cv y test de acuerdo a las clases.**
	1. **Piensa en multiclase y en datos balanceados y desbalanceados**: misma distribución para todos, tiene que representar la distribución del dataset.
27. **Como se comporta computacionalmente (memoria y cómputo) el train, validation, test y CV**:
		El ==Training set== es el que ocupa más memoria ya que tiene los features y labels, además, computacionalmente depende de la complejidad del modelo y del tamaño del set. 
		El ==Validation set==  tiene menos memoria ya que es más chico que el training, y es menos pesado computacionalmente.
		En ==Cross Validation==, en k fold, un fold esta en memoria cada iteración, sin embargo, en computation es pesado ya que se repite k veces. 
		En el ==Test set== se usa muy poco ya que sólo le usa una vez. 
	1. **Dependiendo del número de hyperparametros y de folds:** 
		El costo computacional aumenta proporcionalmente al numero de parametros y folds. 
28. **¿Qué técnica utilizas (val, CV)?**
	1. **Si tuvieras poca memoria**: train-validation-test split, porque solo hay un subset de validation en memoria. 
	2. **Si tuvieras poco tiempo**: val, o cv con pocos folds, que sería más robusto, aunque ambos aproaches no estarían refinados. 
	3. **Si tuvieras mucho computo**: CV, con varios folds, esto porque asegura que el modelo será evaluado múltiples veces. 
29. **Cuál es la diferencia entre...:**
	1. **Machine Learning:** es una rama de la IA, que se enfoca en aprender de la data, encontrar patrones de la data. 
	2. **Good Old Fashion AI:** [[Sistemas Expertos en IA]], [[Sistema basado en casos]].
	3. **Deep Learning:** es una rama de ML que se enfoca en redes neuronales profundas, un ejemplo son los LLM, AlphaGo.
	4. **AI:** hacer que una computadora sea capaz de hacer cosas que harían humanos, ==AGI==. 
30. **Cual es la diferencia entre modelos pre-entrenados (no supervisados) y modelos supervisados?**: ==modelos no supervisados== son aquellos que no se les dan labels, son buenos para conocer las features super bien. ==Modelos supervisados== son aquellos que si tienen labels, como clasificación. 
	1. **Como se pueden combinar?** para finetunear cualquiera de los dos. 
31. **Cómo puedes saber si tu error es grande o pequeño?**
	1. **En regresión**: si el MSE es grande entonces el error es grande, o si el baseline se acerca a la media de la targeted variable entonces es bueno. 
	2. **En clasificación**: Buena accuracy es que el error es pequeño, si se usa [[AUC-ROC]] entonces si se acerca a 1, i.e. se acerca a la curva ==ROC==.
32. **Si la diferencia entre tu error train y validación es muy grande que puedes hacer para mejorarlo?**: esto es una señal de ==overfitting==, podemos hacer varias cosas como reducir la complejidad del modelo, agregar una $\lambda$ de ==regularización==, [[Cross Validation]], métodos de ensamblaje como ==random forests==, usar más data. 
33. **Que pasa si un modelo tiene un error más bajo en general que otro, pero su varianza es más grande que los demás modelos (en términos de CV)?**: que está overfittiado a sus datos. 
34. **Qué podría estar pasando si para cierto hyperparametro el error es bajo en todos los folds (CV) menos en uno (que es especificamente alto)?**: los folds no están balanceados, hay outliers o ruido, overfittiado a ciertos folds, ==data leakage== (data del validation afecta al entrenamiento). 
35. **Qué pasa si en un algoritmo de clasificación queremos usar CV con 5 folds, pero para una clase sólo hay 3 observaciones?:** algunos folds no tendrán observaciones de esa clase, i.e. estarán desbalanceados.
	1. **Que harías o como lo podrías solucionar**: bajar los folds, o usar otro método como leave one out. 
36. **Qué tipo de modelos y técnicas (validación o CV) utilizamos en cada uno de los siguientes casos y por qué?**
	1. **Muchos datos, mucho tiempo y mucho computo**: CV, porque aseguramos que el modelo generalice bien sin overfittiar.
	2. **Pocos datos, mucho tiempo y mucho computo**:CV, con pocos folds para maximizar la training data en cada iteración.
	3. **Muchos datos, poco tiempo y poco computo**, CV pocos folds, o validación, cv con una iteración. 
	4. **Muchos datos, mucho tiempo y poco computo**, CV.