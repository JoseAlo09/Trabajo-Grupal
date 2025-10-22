# Trabajo-Grupal
Este trabajo para el curso de Introducción A Ciencia De Datos Y Machine Learning Con Python | E2ICD9 | es un proyecto que explora cómo el nivel educativo de la madre se relaciona con el acceso a controles prenatales adecuados en el Perú, utilizando datos de la Encuesta Demográfica y de Salud Familiar (ENDES). A través de un análisis descriptivo, se investiga la hipótesis de que un mayor nivel educativo está asociado a una mejor atención prenatal, examinando también el papel de otros factores como la riqueza y la ubicación geográfica.


## 1. Descripción de Variables y Objetivo

El objetivo de la investigación es analizar los factores sociodemográficos y económicos que influyen en la probabilidad de que una madre reciba atención prenatal adecuada.

### 🎯 Variable Objetivo (`TARGET`)

| Variable | Tipo | Descripción |
| :--- | :--- | :--- |
| **`prenatal_adecuado`** | Binaria (0, 1) | **1** si la atención prenatal es considerada adecuada, **0** si es inadecuada. |

### 🔍 Variables Predictoras (`FEATURES`)

| Variable | Tipo | Descripción |
| :--- | :--- | :--- |
| **`educacion_grupo`** | Numérica (Ordinal) | Nivel educativo de la madre (1=Básico, 2=Medio, 3=Avanzado). |
| **`Edad`** | Numérica (Continua) | Edad de la madre en años. |
| **`Nivel_riqueza`** | Numérica (Ordinal) | Nivel de riqueza del hogar (1 a 5). |
| **`SREGION`** | Numérica (Categórica) | Región geográfica de residencia. |
| **`urbano`** | Binaria (0, 1) | **1** si reside en zona urbana, **0** si reside en zona rural. |

***

## 2. Versión de Python y Dependencias

### Versión de Python
El entorno de ejecución usado fue **Python 3.12**.

### Dependencias

Las librerías necesarias pueden instalarse usando `pip`:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels
LibreríaPropósito principalpandas, numpyManipulación de datos.matplotlib, seabornVisualización.scikit-learnModelos de predicción y Validación Cruzada.statsmodelsInferencia estadística (OLS y Logit).
 
## 3. Decisiones de Modelado

Se eligió la **Opción B: Comparar Regresión (OLS) vs. Clasificación (Logit)**, ya que la variable dependiente es binaria, buscando el enfoque más informativo para la inferencia y predicción.

### Modelo Base (Baseline)

El modelo ingenuo (Clase Mayoritaria) estableció un **Accuracy del 0.8910**. El modelo final debe superar este umbral.

### Modelo Ganador

El modelo elegido fue la **Regresión Logística (Logit)**.

* **Razón:** Es el método estadístico más apropiado para modelar la probabilidad de una variable binaria. Ofrece interpretación directa (Odds Ratios) sobre la relación de las variables con el evento.

### Rendimiento y Hallazgos Clave

| Métrica | Validación Cruzada (CV) | Evaluación Final (Test Set) |
| :--- | :--- | :--- |
| **Accuracy** | 0.8910 | 0.89 |
| **F1-Score (Clase 1)** | 0.9424 | 0.94 |
| **Precisión (Clase 0)** | N/A | 0.00 |

* **Conclusión:** El modelo generaliza bien, ya que el rendimiento en el Test Set es similar al CV.
* **Inferencial:** Los **factores socioeconómicos** (Educación y Riqueza) aumentan significativamente las probabilidades de atención adecuada.
* **Limitación:** La Precisión de 0.00 para la clase minoritaria (atención inadecuada) evidencia un problema de **desbalance de clases** (89% vs 11%) que impide al modelo identificar correctamente los casos negativos.

***
