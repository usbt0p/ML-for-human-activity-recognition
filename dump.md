# DUDAS

DUDA: usar también un mismo estado para reproducibilidad??
- si, si no puede parecer que hay cambios en los hiperpar´ametros o en otras cosas

DUDA: en que orden hacer normalización, reducción de dimensionalidad y selección de atributos??
- no hay un orden eespecifico: depende de los datos qu etengas: igual te interesa primero quitar dimensiones, o prmero cambiar la dostribuci´on para que ra reducci´on sea mejor...

[order between those stackoverflow](https://stackoverflow.com/questions/46062679/right-order-of-doing-feature-selection-pca-and-normalization)

[reddit normalize after pca](https://www.reddit.com/r/datascience/comments/15u6esb/feature_selection_normalization_before_or_after/?rdt=59437)

DUDA: como compruebo el overfitting tras hacer un proceso de CV con una busqueda de hiperparámetros? hace falta?
- es mejor comprobar el overfitting igual: usar el par´ametro `search.cv_results_`.
Puedo hacer la diferencia con todos, y hacer la media.

DUDA: para comprobar overfitting / underfitting uso solo accuracy o también puedo usar otras métricas??
- se pueden usar otras. Est´a bien explicar por qu´e se eligen varias, y qu´e representa cada una en el contexto del problema

DUDA: cómo sé cuando normalizar, cuando escalar, que escalado usar... tengo que estudiar los datos por ejemplo para ver la distribución y los outliers??
- Est´a bien hacer un estudio de los datos previo. Se pueden hacer plots de la diferencia entre datos, y es muy importante mirar los outliers.
Por otro lado, se pueden tomar la decisi´on en base a un estudio previo: puede ser que alguien haya estudiado ya las distribuciones de los datos que se usan y eso da info de qu´e utilizar

DUDA: cómo saber que técnica de reducción de dimensionalidad usar? alguinas van mejor para pocas dim, otras no...
también debería realizar un proceso de selección de atributos??
- De nuevo, depende de las distribuciones y caracter´isticas espec´ificas de los datos.


---

DUDA: hay que hacer los tests todos al final o puedo ir haciéndolos sobre la marcha


---

### TODO:

decidir la reducción de dimensionalidad a aplicar: PCA, NMF, etc. justificar por que

1. Descripción del conjunto de datos utilizado en este enfoque: atributos considerados, instancias, etc.
2. Preprocesamiento específico del enfoque.
3. Parte experimental: claridad + numero de experimentos
  - Deberán detallarse todos los datos relacionados con los
experimentos a realizar: porcentajes para la división del conjunto de
datos original, número de pliegues en validación cruzada…
  - probada con diferentes hiperparámetros
  - incluir los resultados de las métricas
  seleccionadas y una discusión y comparación de los modelos
  obtenidos.
  - otro material que pueda
apoyar las afirmaciones, como gráficos explicativos, matrices de
confusión…

### HACER HOY
- experimento: reducir AUN mas la dimensionalidad en el entrenamiento
- experimento:  hacer selección de atributos para optimizar a saco el tiempo d e entrenamiento, pero elegir en cuales

### OPCIONAL
- intentar cachear la pipeline y meter passthrough al modelo
- cachear knn
- PLOT: dimension final VS tiempo entrenamiento VS f1-score
  problema: el tiempo solo se mide para todas las ieraciones
- aproximar kernel polinomial
- plotear algunos hypp como en [este chisme de scikit](https://scikit-learn.org/1.5/auto_examples/svm/plot_rbf_parameters.html#train-classifiers)
- crear e implementar un metodo de random forest / ensemble que ejecute separando actividades en movimiento / estáticas o por sensores, o simplemente metiendo varios modelos distintos
- [hacer una funcion de pérdida propia con sklearn.make_scorer](https://stackoverflow.com/questions/32401493/how-to-create-customize-your-own-scorer-function-in-scikit-learn)

  [make your custom scoring object](https://scikit-learn.org/1.5/modules/model_evaluation.html#implementing-your-own-scoring-object)

```
def custom_scorer(estimator, X, y, pca_n_components=None):
  """
  Calcula un score personalizado que equilibra la reducción de dimensiones (penalizando más dimensiones)
  y el F1-score obtenido por el modelo."""

  # Predecir y calcular F1-score
  y_pred = estimator.predict(X_reduced)
  f1 = f1_score(y, y_pred, average='weighted')

  # Penalizar con el número de dimensiones. Cuanto menor sea pca_n_components, mejor.
  # Ajustar el peso de la penalización en función de la escala de F1-score.
  penalty = pca_n_components / X.shape[1] if pca_n_components else 1  # Penalización como proporción de dimensiones

  # Combinar ambas métricas: Maximizar f1 pero penalizar número de componentes
  score = f1 - 0.1 * penalty  # Ponderación de la penalización

  return score
```

- asi se imprimen [dos plots con eje x compartido](https://scikit-learn.org/1.5/auto_examples/compose/plot_digits_pipe.html#sphx-glr-auto-examples-compose-plot-digits-pipe-py)
