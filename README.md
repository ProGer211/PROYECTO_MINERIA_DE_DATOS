# Clasificación de la Gravedad de Incidentes Migratorios

## Descripción del Proyecto

Este proyecto desarrolla un pipeline completo de **Machine Learning** para clasificar la gravedad de incidentes relacionados con la migración utilizando el **Global Missing Migrants Dataset**.

El objetivo es predecir el nivel de gravedad de un incidente (`Baja`, `Media`, `Alta`) a partir de características geográficas, temporales y contextuales.

El proyecto incluye:

* Comprensión de los datos
* Limpieza robusta de los datos
* Creación de la variable objetivo
* Prevención de fuga de información (*Data Leakage*)
* División estratificada de los datos en entrenamiento y prueba
* Entrenamiento y comparación de múltiples modelos de Machine Learning
* Evaluación estadística avanzada

---

## Dataset

El conjunto de datos contiene información histórica sobre incidentes relacionados con la migración, incluyendo:

* Número de fallecidos
* Número estimado de personas desaparecidas
* Región del incidente
* Año
* Causa del fallecimiento
* Coordenadas geográficas

**Variable objetivo original:**

`Total Number of Dead and Missing`

---

## Creación de la Variable Objetivo

El problema se transforma en una tarea de **clasificación multiclase**:

| Total de fallecidos y desaparecidos | Gravedad |
| ----------------------------------- | -------- |
| 0 – 2                               | Baja     |
| 3 – 10                              | Media    |
| > 10                                | Alta     |

---

## Limpieza de Datos

Incluye:

* Eliminación de duplicados
* Conversión segura de valores numéricos
* Corrección de valores negativos
* Procesamiento y validación de coordenadas
* Comprobaciones de consistencia en la reconstrucción del total
* Eliminación de registros inconsistentes

---

## Eliminación de Fuga de Información

Para evitar la fuga de información respecto a la variable objetivo, se eliminan las siguientes columnas:

* `Total Number of Dead and Missing`
* `Number of Dead`
* `Minimum Estimated Number of Missing`
* `Number of Survivors`
* `Number of Females`
* `Number of Males`
* `Number of Children`

---

## División de los Datos en Entrenamiento y Prueba

* **80 %** para entrenamiento
* **20 %** para prueba
* División estratificada por clase
* Validación de la estrategia de división desde un punto de vista académico

---

## ⚙️ Preprocesamiento

* Imputación sin fuga de información (mediana/moda calculada a partir del conjunto de entrenamiento)
* Reducción de cardinalidad
* Tratamiento de valores atípicos
* Codificación One-Hot
* Escalado de características (para modelos lineales y basados en distancia)
* Selección de características mediante `SelectKBest`

---

## Modelos Entrenados

Se entrenaron y compararon los siguientes modelos:

* Naive Bayes
* KNN
* SVM (Lineal, Polinomial y RBF)
* Árbol de Decisión
* Random Forest
* Extra Trees
* AdaBoost
* Bagging

Se realizó un ajuste de hiperparámetros mediante `GridSearchCV`, utilizando **F1 ponderado (*F1-weighted*)** como métrica de optimización.

---

## Resultados Finales

| Modelo        | Accuracy | F1 ponderado |
| ------------- | -------- | ------------ |
| SVM           | 0.808    | 0.7848       |
| Random Forest | 0.806    | 0.7900       |
| Extra Trees   | 0.792    | 0.7827       |
| AdaBoost      | 0.801    | 0.7632       |
| Decision Tree | 0.767    | 0.7667       |
| KNN           | 0.727    | 0.7520       |
| Naive Bayes   | 0.583    | 0.6426       |

**Random Forest y SVM muestran un rendimiento estable y competitivo.**

---

## Evaluación Estadística

* Test de McNemar (comparación entre modelos)
* Intervalos de confianza del 95 % (Wilson)
* Intervalos de confianza mediante Bootstrap para F1
* Curvas Precision-Recall
* Comparación de matrices de confusión

---

## Tecnologías Utilizadas

* Python
* Pandas
* NumPy
* Scikit-learn
* Imbalanced-learn
* Seaborn
* Matplotlib
* Statsmodels

---

## ▶️ Cómo Ejecutar el Proyecto

### 1. Instalar las dependencias

```bash
pip install -r requirements.txt
```

### 2. Ejecutar el notebook

Abre y ejecuta:

```text
PRACTICA_JESIKA_JIMENEZ_GERARD_CHAPARRO.ipynb
```

---

## Autores

* **Jesika Jiménez**
* **Gerard Chaparro**

---

## Estado del Proyecto

Proyecto completo con validación estadística y comparación robusta de diferentes modelos de Machine Learning.
