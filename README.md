## Práctica Experimental de Minería de Datos
## Descripción del proyecto

Este proyecto corresponde a una práctica experimental de minería de datos aplicada al análisis y clasificación del rendimiento académico de estudiantes.
El estudio utiliza un conjunto de datos de 5.000 registros y 15 variables relacionadas con características demográficas, académicas, familiares y de participación de los estudiantes. El objetivo es analizar estas características y aplicar técnicas de minería de datos para clasificar el nivel de rendimiento académico mediante la variable GradeClass.

## Objetivo
Desarrollar y comparar modelos de minería de datos capaces de clasificar el nivel de rendimiento académico de los estudiantes a partir de sus características demográficas, académicas, familiares y de participación.

## Dataset
- El conjunto de datos utilizado contiene:
- 5.000 registros
- 15 variables
- Variable objetivo: GradeClass
- Identificador: StudentID
Las principales variables incluyen edad, género, etnia, educación de los padres, tiempo de estudio semanal, ausencias, tutorías, apoyo parental, actividades extracurriculares, deportes, música, voluntariado y GPA.

## Fuente del dataset
El dataset fue obtenido de Kaggle: https://www.kaggle.com/datasets/miadul/student-performance-dataset

## Exploración de los datos
Durante la exploración inicial se realizaron:
- Estadísticas descriptivas.
- Análisis de valores nulos.
- Análisis de registros duplicados.
- Identificación de posibles valores atípicos mediante el método IQR.
- Visualizaciones de la distribución del GPA.
- Comparación del GPA según GradeClass.
- Análisis de la relación entre tiempo de estudio semanal y GPA.
  
El conjunto de datos presentó 0 valores nulos y 0 registros duplicados.

## Preprocesamiento
Se realizaron las siguientes actividades:
- Verificación de valores nulos y duplicados.
- Exclusión de StudentID de las variables predictoras, debido a que funciona únicamente como identificador.
- Revisión de las variables categóricas y binarias codificadas numéricamente.
- Aplicación de estandarización mediante StandardScaler como parte de la preparación y análisis de los datos.
- Generación de dos variables mediante ingeniería de características:
StudyAbsenceRatio: relación entre el tiempo de estudio semanal y las ausencias.

ActivityCount: cantidad total de actividades extracurriculares, deportivas, musicales y de voluntariado.

## División de los datos y exclusión de GPA
Durante el desarrollo se realizó inicialmente una división de los datos incluyendo GPA entre las variables predictoras.
Posteriormente, durante el análisis se identificó que GPA presenta una relación directa con GradeClass. Utilizar GPA para predecir GradeClass podía generar fuga de información (data leakage) y producir resultados artificialmente elevados.
Por esta razón, se realizó una segunda división de los datos excluyendo GPA de las variables predictoras. Esta segunda configuración fue utilizada para el entrenamiento, evaluación y comparación final de los modelos.
La configuración final utilizó:
- 80 % de los datos para entrenamiento: 4.000 registros.
- 20 % de los datos para prueba: 1.000 registros.
- random_state=42.
- División estratificada mediante stratify=y.
La variable GradeClass se mantuvo como variable objetivo.

## Técnicas de minería de datos
Se implementaron tres técnicas de clasificación:
## Árbol de Decisión
Parámetros principales:
- criterion="gini"
- max_depth=5
- random_state=42

## Random Forest
Parámetros principales:
- n_estimators=100
- criterion="gini"
- max_depth=10
- random_state=42

## K-Nearest Neighbors (KNN)
Parámetros principales:
- n_neighbors=5
- weights="uniform"
- metric="minkowski"

## Evaluación
Los modelos fueron evaluados utilizando:
- Accuracy.
- F1-score ponderado.
- Validación cruzada de 5 folds.

## Resultados sobre el conjunto de prueba
| Modelo | Accuracy | F1-score |
|---|---:|---:|
| Árbol de Decisión | 0,4660 | 0,3757 |
| Random Forest | 0,4550 | 0,3700 |
| KNN | 0,4320 | 0,3967 |

## Validación cruzada
| Modelo | Accuracy CV (5 folds) |
|---|---:|
| Árbol de Decisión | 0,4646 |
| Random Forest | 0,4756 |
| KNN | 0,4244 |

Los resultados muestran diferencias en el comportamiento de los modelos según la métrica utilizada. La validación cruzada permitió complementar la evaluación realizada sobre el conjunto de prueba y analizar el comportamiento de los modelos en diferentes particiones de los datos.

## Tecnologías utilizadas
- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- GitHub

## Archivos del repositorio
Practica_Experimental_Mineria_Datos_Keyla_Merino.ipynb: notebook con el código, procesamiento, modelado y evaluación de la práctica.

## Ejecución
Para reproducir el análisis:
- Descargar o abrir el notebook Practica_Experimental_Mineria_Datos_Keyla_Merino.ipynb.
- Cargar el archivo synthetic_student_performance.csv.
- Ejecutar las celdas del notebook en orden.
- Verificar los resultados de exploración, preprocesamiento, modelado y evaluación.

Autora: Keyla Merino
