# Proyecto Final de Minería de Datos: Predicción de Supervivencia en Cáncer de Mama

Este repositorio contiene el código y la documentación del trabajo final de la asignatura de Minería de Datos. El objetivo principal del proyecto es desarrollar y comparar diversos modelos predictivos para determinar el pronóstico de supervivencia ("Vivo" o "Exitus") en pacientes diagnosticados con cáncer de mama.

## 📋 Descripción del Proyecto

El análisis se centra en un conjunto de datos clínicos (`exam_dataset_24.xlsx`) que incluye variables demográficas, patológicas y de tratamiento. A través de un flujo de trabajo riguroso de minería de datos, se busca identificar los factores más influyentes y el algoritmo más preciso para la clasificación clínica.

### Demo Interactiva
Se ha desplegado una aplicación Shiny para interactuar con los resultados del modelo:
[Ver Aplicación Shiny](https://z4u3qf-juan0ignacio-soriano0mu0oz.shinyapps.io/aplicacion/)

## Metodología

El flujo de trabajo abarca las siguientes etapas:

1.  **Preprocesamiento de Datos:**
    * Limpieza de valores erróneos y tratamiento de valores perdidos (NAs).
    * Transformación de variables: categorización de edad, extracción del año de diagnóstico, y binarización de la variable objetivo (`ESTADO_ACTUAL`).
    * Agrupación de estadios del cáncer para mejorar la generalización.

2.  **Análisis Exploratorio (EDA):**
    * Estudio de la distribución de variables clave como Ki-67, Ganglios, Histología y Estado Actual.

3.  **Selección de Características:**
    * Se probaron métodos de filtrado (**Chi-squared**), métodos **Wrapper** (StepAIC backward/forward) y fuerza bruta (limitada por coste computacional).

4.  **Balanceo de Clases:**
    * Implementación de técnicas de **Oversampling** y **Undersampling** para mitigar el desbalanceo en la variable objetivo.

5.  **Validación de Modelos:**
    * Uso de **Validación Cruzada 5x2** (5 repeticiones de 2-fold cross-validation) para asegurar la robustez de los resultados y evitar el sobreajuste.

## Modelos Evaluados

Se entrenaron y compararon los siguientes algoritmos de clasificación supervisada:

* **Redes Neuronales (Neural Networks):** Ajuste de tamaño de capa oculta y *weight decay*.
* **Máquinas de Vector Soporte (SVM):** Prueba con kernel radial, variando Costo y Gamma.
* **Árboles de Decisión (Decision Trees):** Optimización de parámetros de complejidad (cp) y profundidad.
* **k-Vecinos Más Cercanos (k-NN):** Búsqueda del *k* óptimo.
* **Naive Bayes:** Evaluación con y sin estimación de kernel.
* **Random Forest:** Ajuste de número de árboles (*ntree*) y variables por nodo (*mtry*).
* **AdaBoost:** Boosting sobre modelos lineales generalizados.

## Resultados Destacados

Tras la experimentación exhaustiva, se obtuvieron las siguientes conclusiones:

* **Mejor Desempeño:** Los modelos de **Random Forest** (AUC ~0.81) y **Naive Bayes** (AUC ~0.79) mostraron la mejor capacidad de discriminación.
* **Variables Relevantes:** Las variables que consistentemente mostraron mayor poder predictivo fueron: *Año de diagnóstico*, *Edad*, *Estadio*, *Fenotipo* y *Ganglios*.
* **SVM:** Logró un AUC competitivo (~0.75) utilizando un coste alto y un gamma bajo para controlar el sobreajuste.

## Tecnologías Utilizadas

* **Lenguaje:** R
* **Librerías Principales:** `caret`, `pROC`, `nnet`, `e1071`, `randomForest`, `mboost`, `FSelector`, `ggplot2`, `dplyr`.

## ✒️ Autor

* **Juan** - *Trabajo Final de Minería de Datos (2024)*
