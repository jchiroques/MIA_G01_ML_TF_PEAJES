# Predicción de Flujo Vehicular - Red Vial Nacional (Perú) 

Este repositorio contiene el desarrollo de un sistema de predicción de tráfico vehicular para las **82 estaciones de peaje** de la Red Vial Nacional, orientado a proyectar el volumen de vehículos ligeros y pesados para los trimestres **2025-III y 2025-IV**.

El proyecto sigue la metodología **CRISP-DM** y utiliza algoritmos de **Aprendizaje Supervisado** con optimización de hiperparámetros.

## Estructura del Proyecto

Para una revisión efectiva del flujo de trabajo, se recomienda explorar los archivos en el siguiente orden:

### 1. [Notebook 01: Exploración de Datos](Notebooks/01_Exploracion.ipynb)
* **Ingesta Multifuente:** Consolidación de datos históricos (2014-2025) con variables exógenas como el **PBI Regional** y el calendario normativo de **feriados y días no laborables**.
* **Análisis de Estacionalidad:** Identificación de patrones cíclicos (picos en enero/diciembre y caídas en abril-junio).
* **Segmentación:** Diferenciación entre peajes de alta demanda (Lima) y rutas logísticas de menor flujo (Puno).

### 2. [Notebook 02: Preprocesamiento](Notebooks/02_Preprocesamiento.ipynb)
* **Tratamiento de la Pandemia:** Exclusión estratégica de los datos 2020-2021 para evitar el sesgo de la discontinuidad estructural por COVID-19.
* **Imputación Avanzada:** Uso de **Decision Trees** para completar valores nulos basados en el comportamiento específico de cada peaje.
* **Ingeniería de Características:** Transformación logarítmica para normalizar la asimetría de los datos y codificación categórica para la ubicación geográfica.

### 3. [Notebook 03: Modelado y Evaluación](Notebooks/03_Modelo.ipynb)
* **Algoritmos Evaluados:** Comparativa entre Regresión Lineal, Random Forest, Support Vector Regression (SVR) y **XGBoost**.
* **Optimización:** Implementación de **Grid Search CV** para la búsqueda de los mejores hiperparámetros y técnicas de escalado.
* **Validación:** Uso de métricas robustas (RMSE, MAE, R², MAPE) con una división de datos cronológica (Entrenamiento hasta 2024 / Test 2025).

## Resultados del Modelo

El análisis de rendimiento muestra que el **68% de los modelos desarrollados (581 casos)** alcanzan un coeficiente de determinación **$R^2$ superior a 0.7**, demostrando una alta capacidad de generalización.

| Rango $R^2$ | Cantidad de Modelos | MAPE Promedio | RMSE Promedio | MAE Promedio |
| :--- | :---: | :---: | :---: | :---: |
| **0.9 - 1.0** | 269 | 0.1461 | 658.73 | 462.66 |
| **0.8 - 0.9** | 142 | 0.1656 | 1596.83 | 967.14 |
| **0.7 - 0.8** | 81 | 0.1675 | 1939.84 | 1221.99 |

## Requisitos Técnicos

El entorno de ejecución requiere **Python 3.10+** y las siguientes librerías:
```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn