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
