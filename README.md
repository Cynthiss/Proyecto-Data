# Predicción de Deserción de Empleados en una Empresa

## Descripción del Proyecto
Este proyecto tiene como objetivo predecir la **probabilidad de que un empleado abandone la empresa**. Utilizando un modelo de clasificación binaria, el proyecto busca identificar los factores que contribuyen a la decisión de un empleado de dejar la empresa. La predicción de la rotación de empleados ayuda a la empresa a optimizar los procesos de contratación, formación y retención de talento, mejorando la eficiencia y reduciendo costos.

## Caso de Uso
La empresa busca saber qué empleados tienen una alta probabilidad de dejar la empresa, con el fin de tomar medidas proactivas para retenerlos. Este modelo permite a la empresa:
- Mejorar la planificación de los recursos humanos.
- Reducir costos asociados con la rotación de personal.
- Identificar factores clave que influyen en la rotación.

## Características del Proyecto

### Dataset Utilizado
El dataset utilizado proviene de la competencia **IBM HR Analytics - Employee Attrition & Performance**, disponible en Kaggle.  
- https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset?resource=download

#### Características Principales
- **Cantidad de Observaciones**: 1,470 registros.
- **Cantidad de Features**: 35 características originales, de las cuales se seleccionaron 20 características relevantes mediante análisis y selección.

#### Target de Predicción
El **target** de predicción es la variable **Attrition** que tiene un valor binario:  
- **0**: El empleado no dejó la empresa.  
- **1**: El empleado dejó la empresa.

---

## Estructura de Notebooks

### 1. `1_data_loading_cleaning.ipynb`
- Carga del dataset original.
- Limpieza inicial y eliminación de columnas irrelevantes.
- Codificación binaria del target.
- Análisis general de variables y tipos.

### 2. `2_baseline_model.ipynb`
- Construcción del modelo baseline utilizando variables numéricas seleccionadas a simple vista.
- Evaluación inicial con métricas: accuracy, precision, recall y KS.
- Matriz de confusión y análisis de desempeño.

### 3. `3_feature_engineering_encoding.ipynb`
- Transformación de variables categóricas mediante one-hot encoding.
- Ingeniería de características: transformación logarítmica del ingreso mensual.
- Preparación del dataset para modelos iterativos.

### 4. `4_feature_selection.ipynb`
- Análisis de correlación entre variables.
- Cálculo de importancia de features por coeficientes del modelo.
- Aplicación de WoE e IV para selección rigurosa de variables.
- Selección de tres conjuntos de variables para las siguientes iteraciones de modelos.

### 5. `5_model_iterations.ipynb`
- Entrenamiento de tres modelos con diferentes conjuntos de variables seleccionadas.
- Evaluación de cada modelo con métricas clave.
- Comparación con el baseline.
- Visualización de la matriz de confusión y distribución de probabilidades para evaluar separación de clases.

### 6. `6_model_final_evaluation.ipynb`
- Selección del modelo final basado en balance óptimo entre métricas.
- Evaluación completa del modelo final con matriz de confusión, métricas y visualizaciones.
- Comparación detallada con el modelo baseline.
- Interpretación y conclusiones finales.

---

## Modelo Final Seleccionado

El modelo final (Modelo 1) fue seleccionado por lograr el mejor balance entre precisión y recall, con una capacidad superior para separar las clases (KS):

### Features utilizadas en el Modelo Final

- **OverTime_Yes** (trabaja horas extra)  
- **BusinessTravel_Travel_Frequently** (viaja frecuentemente por trabajo)  
- **Log_MonthlyIncome** (ingreso mensual transformado logarítmicamente)  
- **YearsSinceLastPromotion** (años desde la última promoción)  
- **MaritalStatus_Single** (estado civil soltero)  
- **NumCompaniesWorked** (número de empresas anteriores)  
- **EnvironmentSatisfaction** (satisfacción con el ambiente laboral)  
- **YearsAtCompany** (años en la empresa)  
- **YearsWithCurrManager** (años con el manager actual)  
- **JobSatisfaction** (satisfacción laboral)

### Rendimiento del Modelo Final

| Métrica   | Valor  |
|-----------|---------|
| Accuracy  | 0.855   |
| Precision | 0.613   |
| Recall    | 0.268   |
| KS        | 0.545   |

La matriz de confusión muestra un mejor desempeño en la detección de empleados que rotan comparado con el modelo baseline, lo que permite una gestión más efectiva del talento.

---

## Conclusión

Este proyecto demuestra la utilidad de la ciencia de datos aplicada a recursos humanos para anticipar la rotación de personal. El modelo final proporciona una herramienta predictiva robusta para identificar empleados con alto riesgo de abandono, permitiendo a la empresa tomar medidas proactivas para su retención, optimizando costos y mejorando la planificación estratégica de recursos humanos.

---




