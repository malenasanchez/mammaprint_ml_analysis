# mammaprint_ml_analysis
Flujo completo de Machine Learning sobre datos de expresión génica de MammaPrint

# MammaPrint_II

## Descripción
Este repositorio contiene un flujo de trabajo en **R** para el análisis de datos de expresión génica y predicción de riesgo de cáncer de mama usando el **panel MammaPrint**.  

El **script principal** realiza:

- Carga de datos clínicos y de expresión génica.
- Preprocesamiento de datos (normalización, filtrado de variables con baja varianza y alta correlación).
- Entrenamiento de modelos de **Machine Learning**:
  - Random Forest (RF)
  - Gradient Boosting Machine (GBM)
  - Regresión lineal (LM) para predicción de scores continuos.
- Evaluación de modelos con:
  - Curvas ROC y cálculo de AUC.
  - Matrices de confusión.
  - Métricas de regresión (RMSE, MSE, MAE, R²).
- Visualización de resultados: importancia de variables, gráficos de dispersión, boxplots y density plots.

El **script previo** permite explorar y filtrar las características más relevantes de la matriz de expresión, realizar análisis diferencial de genes y generar visualizaciones iniciales de los datos.

## Estructura del repositorio

MammaPrint_II/
├─ data/
│ ├─ raw/ # Datos originales (tsv, rds)
│ ├─ processed/ # Datos filtrados y transformados
├─ scripts/
│ ├─ 01_Preprocessing.R # Filtrado y visualización de genes
│ ├─ 02_ModelTraining.R # Entrenamiento y evaluación de modelos ML
├─ results/
│ ├─ plots/ # Gráficos generados
│ ├─ tables/ # Resultados de importancia de genes y métricas
├─ README.md

## Requisitos

- R >= 4.0  
- Paquetes R:
  - `caret`
  - `MLeval`
  - `pROC`
  - `limma`
  - `ggplot2`
  - `gbm`

## Instalación de paquetes:
```r
install.packages(c("caret", "MLeval", "pROC", "ggplot2", "gbm"))
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("limma")
```

## Uso
## Configurar el directorio de trabajo
```r
setwd("C:/Ruta/Al/Proyecto/MammaPrint_II")
```

## Ejecutar el script de preprocesamiento
```r
source("scripts/01_Preprocessing.R")
```

## Ejecutar el script de entrenamiento y evaluación de modelos
```r
source("scripts/02_ModelTraining.R")
```

## Visualizar resultados
Los gráficos y tablas se generarán en la carpeta results/. Se incluyen curvas ROC, importancia de genes y métricas de modelos.

## Resultados esperados
- Tablas de genes más relevantes por riesgo.
- Gráficos de dispersión, boxplots y density plots de genes seleccionados.
- Modelos entrenados de Random Forest, GBM y regresión lineal.
- Curvas ROC y AUC para modelos de clasificación.
- Matrices de confusión y métricas de rendimiento.
- Métricas de regresión (RMSE, MAE, R²) para modelos de predicción continua.


