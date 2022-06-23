# Métodos de ensamblaje en Python

**Nivel de dificultad : Difícil**

Ensemble significa un grupo de elementos vistos como un todo en lugar de individualmente. Un método Ensemble crea múltiples modelos y los combina para resolverlo. Los métodos Ensemble ayudan a mejorar la robustez/generalizabilidad del modelo. En este artículo, discutiremos algunos métodos con su implementación en Python. Para ello, elegimos un conjunto de datos del repositorio de la UCI.

# Métodos básicos de ensamblaje

1. Método de promediación: Se utiliza principalmente para problemas de regresión. El método consiste en construir múltiples modelos de forma independiente y devolver la media de la predicción de todos los modelos. En general, el resultado combinado es mejor que el resultado individual porque se reduce la varianza.

En el siguiente ejemplo, se entrenan tres modelos de regresión (regresión lineal, xgboost y bosque aleatorio) y se promedian sus predicciones. El resultado final de la predicción es pred_final.

2. Votación máxima: Se utiliza principalmente para problemas de clasificación. El método consiste en construir múltiples modelos de forma independiente y obtener su resultado individual llamado "voto". La clase con el máximo de votos se devuelve como salida. 

En el siguiente ejemplo, se combinan tres modelos de clasificación (regresión logística, xgboost y bosque aleatorio) utilizando el VotingClassifier de sklearn, se entrena ese modelo y se devuelve como salida la clase con más votos. La salida de predicción final es pred_final. Tenga en cuenta que es una clasificación, no una regresión, por lo que la pérdida puede ser diferente de otros tipos de métodos de conjunto.

# Métodos de conjunto avanzados

Los métodos de ensamblaje se utilizan ampliamente en el aprendizaje automático clásico. Ejemplos de algoritmos que utilizan bagging son random forest y bagging meta-estimator y ejemplos de algoritmos que utilizan boosting son GBM, XGBM, Adaboost, etc. 

Como desarrollador de un modelo de aprendizaje automático, es muy recomendable utilizar métodos ensemble. Los métodos ensemble se utilizan ampliamente en casi todos los concursos y trabajos de investigación.

1. Apilamiento: Es un método ensemble que combina múltiples modelos (de clasificación o de regresión) a través de un metamodelo (metaclasificador o metarregresión). Los modelos base se entrenan en el conjunto de datos completo y, a continuación, el metamodelo se entrena con las características devueltas (como salida) por los modelos base. Los modelos base en el apilamiento suelen ser diferentes. El metamodelo ayuda a encontrar las características de los modelos base para conseguir la mejor precisión.

2. Mezcla: Es similar al método de apilamiento explicado anteriormente, pero en lugar de utilizar todo el conjunto de datos para entrenar los modelos base, se mantiene un conjunto de datos de validación por separado para hacer predicciones. 

3. Ensacado: También se conoce como método de bootstrapping. Los modelos base se ejecutan en bolsas para obtener una distribución justa de todo el conjunto de datos. Una bolsa es un subconjunto del conjunto de datos junto con un reemplazo para que el tamaño de la bolsa sea el mismo que el del conjunto de datos completo. El resultado final se obtiene tras combinar los resultados de todos los modelos base. 

4. Boosting: El refuerzo es un método secuencial cuyo objetivo es evitar que un modelo base erróneo afecte al resultado final. En lugar de combinar los modelos base, el método se centra en construir un nuevo modelo que depende del anterior. El nuevo modelo intenta eliminar los errores cometidos por el anterior. Cada uno de estos modelos se denomina aprendiz débil. El modelo final (llamado aprendiz fuerte) se forma obteniendo la media ponderada de todos los aprendices débiles. 
