# Proyecto 1 - Modelos de Sistemas  
### Universidad de Antioquia - Ingeniería de Sistemas (Modalidad Virtual)

---

## Descripción  
Este repositorio corresponde al **Proyecto 1** de la asignatura *Modelos de Sistemas*.  

El proyecto consiste en desarrollar un modelo de Machine Learning para predecir el rendimiento académico en las **Pruebas Saber Pro de Colombia**, utilizando variables socioeconómicas y académicas de estudiantes universitarios.

**Competencia Kaggle:** [UDEA AI 4 - Pruebas Saber Pro Colombia](https://www.kaggle.com/competitions/udea-ai-4-eng-20252-pruebas-saber-pro-colombia)

---

## Integrantes del equipo  

| Nombre | Cédula | Programa |
|--------|--------|----------|
| **José David Henao Gallego** | 1002205747 | Ingeniería de Sistemas |
| **Juan Andrés Lema Tamayo** | 1001233264 | Ingeniería de Sistemas |

---

## Contenido del repositorio  
```
Proyecto-1-Modelos-de-Sistemas/
│
├── 01 - exploración.ipynb                                                        # Análisis exploratorio de datos
├── 02 - preprocesado.ipynb                                                       # Limpieza y transformación de datos
├── 03 - modelo con preprocesado LogisticRegression OneHot SimpleImputer.ipynb    # Modelo baseline (Score: 0.37137)
├── 04 - modelo con preprocesado Ensemble GradientBoosting XGBoost LightGBM OneHot.ipynb  # Ensemble inicial (Score: 0.43284)
├── 05 - modelo con preprocesado Stacking XGB LGBM GB meta LogReg OrdinalEncoder.ipynb    # Stacking optimizado (Score: 0.43770)
├── 06 - modelo con preprocesado LGBM optimizado OOF FeatEng Ordinal.ipynb        # LGBM optimizado (Score: 0.43835)
├── 07 - modelo_solución.ipynb                                                    # Modelo NOVA - Solución final (Score: 0.44355)
└── README.md                                                                     # Este archivo                 
```

---

## Entregables - Entrega 2

### 1. Video Explicativo (3-4 minutos)

**[Ver video](https://drive.google.com/file/d/1pVYYp-RLQFH_aEdL70CAZgdKqutwZ4ZT/view?usp=sharing)**

## Entregables - Final

### 2. Video Explicativo (4-5 minutos)

**[Ver video](https://youtu.be/TQ4SkwMqriA)**

---

## Evolución de los modelos

### **Notebook 01 - Exploración**
Análisis exploratorio del dataset de Pruebas Saber Pro:
- Estructura del dataset (692,500 registros de entrenamiento)
- Análisis de variables socioeconómicas y académicas
- Identificación de variables relevantes para predicción
- Distribución de la variable objetivo `RENDIMIENTO_GLOBAL`

---

### **Notebook 02 - Preprocesado**
Limpieza y transformación de datos aplicada como base para todos los modelos:

**Operaciones realizadas:**
- Manejo de valores faltantes (3-4% del dataset)
- Reemplazo de nulos por categoría `'no info'`
- Limpieza de categorías ambiguas (`'No sabe'`, `'No Aplica'`)
- Conversión de rangos numéricos (ej: `'Menos de 500 mil'` → 0.25)
- Codificación de variables categóricas

---

### **Notebook 03 - Modelo Baseline** 
**Score Kaggle: 0.37137**

**Configuración:**
- Modelo: `LogisticRegression`
- Encoding: `OneHotEncoder`
- Imputación: `SimpleImputer`

**Propósito:** Establecer un punto de referencia simple e interpretable.

---

### **Notebook 04 - Ensemble Inicial**
**Score Kaggle: 0.43284** (+16.5% mejora)

**Modelos implementados:**
- `GradientBoostingClassifier`
- `XGBoost`
- `LightGBM`
- Pequeño ensamble de los tres

**Técnicas:**
- One-Hot Encoding
- Comparación de rendimiento entre algoritmos
- Primera mejora significativa sobre el baseline

---

### **Notebook 05 - Stacking con Meta-Modelo**
**Score Kaggle: 0.43770** (+1.1% mejora)

**Arquitectura:**
- **Modelos base:** XGBoost, LightGBM, GradientBoosting
- **Meta-modelo:** Regresión Logística (heredada del Modelo 3)
- **Imputación:** SimpleImputer
- **Encoding:** `OrdinalEncoder`

**Objetivo:** Combinar fortalezas de múltiples modelos usando stacking.

---

### **Notebook 06 - LightGBM Optimizado**
**Score Kaggle: 0.43835** (+0.15% mejora)

**Simplificación estratégica:**
- Eliminación de la capa de Regresión Logística
- Concentración en un **único modelo LightGBM**
- **Optimización profunda de hiperparámetros**
- Uso de Out-of-Fold (OOF) predictions
- Ordinal Encoding optimizado

**Filosofía:** Menos complejidad, más optimización.

---

### **Notebook 07 - Modelo NOVA (Solución Final)**
**Score Kaggle: 0.44355** (+1.2% mejora) - **MEJOR RESULTADO**

**Configuración del ensemble ponderado:**
- `LightGBM`
- `XGBoost`
- `CatBoost`

**Técnica clave:**
- **Ensemble ponderado** con optimización de pesos
- Experimentación con múltiples combinaciones de pesos
- Selección de la mezcla con mejor desempeño en validación

**Resultado:** Este modelo representa nuestra mejor solución y combina las fortalezas de tres algoritmos de gradient boosting mediante ponderación optimizada.

---

## Progresión de resultados en Kaggle

| Notebook | Modelo | Score Kaggle | Mejora |
|----------|--------|--------------|--------|
| 03 | Logistic Regression | **0.37137** | Baseline |
| 04 | GB + XGB + LGBM Ensemble | **0.43284** | +16.5% |
| 05 | Stacking (XGB + LGBM + GB + LogReg) | **0.43770** | +1.1% |
| 06 | LightGBM Optimizado | **0.43835** | +0.15% |
| 07 | **Modelo NOVA** (LGBM + XGB + CatBoost) | **0.44355** | +1.2% |

**Mejora total: +19.4% sobre el baseline**

---

## Metodología de trabajo

El proyecto siguió un enfoque iterativo de mejora continua:

1. **Exploración** → Entender los datos
2. **Preprocesado** → Preparar datos de forma consistente
3. **Baseline** → Modelo simple como referencia
4. **Experimentación** → Probar algoritmos avanzados
5. **Optimización** → Ajustar hiperparámetros y simplificar
6. **Ensamblado** → Combinar mejores modelos

Cada iteración incorporó aprendizajes de la anterior, priorizando mejoras incrementales basadas en evidencia empírica.

---

## Tecnologías utilizadas

- **Python 3.10+**
- **Pandas** - Manipulación de datos
- **NumPy** - Operaciones numéricas
- **Scikit-learn** - Modelos baseline, preprocesamiento y validación
- **XGBoost** - Gradient boosting optimizado
- **LightGBM** - Gradient boosting ligero y rápido
- **CatBoost** - Gradient boosting con manejo nativo de categorías
- **Matplotlib / Seaborn** - Visualización

---

## Competencia Kaggle

**Posición en leaderboard:** Disponible en el [leaderboard oficial](https://www.kaggle.com/competitions/udea-ai-4-eng-20252-pruebas-saber-pro-colombia/leaderboard)

*Nota: La posición puede variar ya que la competencia continúa abierta al momento de esta entrega.*

---

## Licencia

Este proyecto es de carácter académico y pertenece a la Universidad de Antioquia.

---

**Universidad de Antioquia**  
*Ingeniería de Sistemas - Modalidad Virtual*  
*2025-2*
