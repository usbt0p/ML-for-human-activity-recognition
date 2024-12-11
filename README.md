# ML-for-human-activity-recognition

[Original dataset for HAR](https://www.kaggle.com/datasets/uciml/human-activity-recognition-with-smartphones/data)

> Applying dataset data analysis, visualization, preprocessing, hyperparameter tuning and model evaluation to the HAR  by using SVM's, kNN and Decision trees.
> Achieved 96% accuracy and f1-score, equal to the one obtained by the dataset creators.

Este proyecto busca aplicar las técnicas de aprendizale automático supervisado aprendidas a lo largo del curso al dataset Human Activity Recognition database.

El dataset utilizado contiene lecturas 30 individuos, tomadas a un ratio de 50 kHz por los sensores embebidos de sus teléfonos móviles. Las medidas concretas son:

    Aceleración lineal triaxial del acelerómetro.
    Velocidad angular triaxial del giroscopio.

A partir de estas medidas base de acelerómetro y giroscopio, los creadores del dataset han aplicado una serie de preprocesamientos para crear nuevos atributos que faciliten la predición. Estos se especificarán con detalle más adelante.

El dataset se compone de 563 columnas, de las cuales 561 son un vector de atributos con distintas mediciones de variables de tiempo y frecuencia, y las otras 2 son la actividad y el ID del sujeto que la llevó a cabo. El número de instancias es de 10299, con un tamaño total de 26MB.

Cabe destacar que el conjunto de datos no contiene datos nulos, un gran desbalance de clases ni una alta presencia de outliers, y ha sido previamente particionado en conjuntos de entrenamiento y test, formados por el 70% y 30% de las personas participantes en la recogida de datos, respectivamente.

Sobre este dataset se entrenarán modelos de clasificación multiclase con el objetivo de clasificar las actividades realizadas independientemente del sujeto, dados los atributos de los sensores previamente mencionados. Las clases a predecir son:

    WALKING
    WALKING_UPSTAIRS
    WALKING_DOWNSTAIRS
    SITTING
    STANDING
    LAYING

Se han utilizado modelos de k-Nearest Neighbours, Support Vector Machine (con distintos kernels) y Árboles de decisión para la predicción, y se comprobará que modelo logra un mejor rendimiento sobre el conjunto de test.

Para la evaluación del modelo se han presentado matrices de confusión que permitan ver los resultados de cada modelo en cada clase, y se han utilizado las siguientes métricas:

    Exactitud (accuracy): aciertos sobre el total de muestras. Elegida ya que funciona correctamente con datasets balanceados, como es el caso en este.

    F1-score weighted: media harmónica de recall y precision calculada de forma independiente para cada clase, y luego se calcula la media ponderada.

    Indicada para situaciones con desbalandeo de clases. El balance de clases nunca es perfecto, y aunque en este dataset es bueno , se ha elegido esta métrica para comparar con los resultados de accuracy y ver si el desbalance presente afecta al rendimiento de los modelos.

# Conclusiones

Basándose en las métricas, el mejor modelo es SVM con kernel RBF, pero si tenemos en cuenta la complejidad y eficiencia en tiempo de entrenamiento es LinearSVC, ya que la diferencia entre el accuracy y f1-score de ambos es realmente pequeña.

Finalmente, y como se mencionó en las conclusiones de las SVM's, se ha conseguido alcanzar la métrica dada por los creadores originales del dataset:
96.30% de precisión, y 96.29% de f1-score.

Se ha demostrado que las SVM's superan a los modelos basados en k-NN y en árboles de decisión en este dataset.

También se ha realizado un proceso completo de análisis, preprocesado, entrenamiento, optimización, validación y evaluación de los modelos, y se han extraído conclusiones de cada una de estas fases.
