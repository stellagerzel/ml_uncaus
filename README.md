# Detección temprana de riesgo académico en estudiantes de primer año — UNCAus

Trabajo Integrador — Introducción al Aprendizaje de Máquina  
Doctorado en Informática — UTN FRRe / UNNE / UNAM  
Julio 2026

---

## Descripción

Este trabajo aplica técnicas de aprendizaje automático supervisado para predecir el riesgo académico (desaprobación o abandono) de estudiantes de primer año de la carrera de Ingeniería en Sistemas de la Universidad Nacional del Chaco Austral (UNCAus).

Se trabajó sobre un dataset real de 978 registros correspondientes a dos materias (Algoritmos y Estructuras de Datos y Sistemas y Organizaciones) en sus cohortes 2024 y 2025, relevados mediante el sistema SIU-Guaraní.

Se definieron tres problemas de clasificación binaria independientes:

| Problema | Descripción | Filas |
|:---------|:------------|------:|
| P1 — Riesgo global | Aprobó (A) vs. Desaprobó o Abandonó (R+U) | 978 |
| P2 — Desaprobación | Aprobó (A) vs. Desaprobó (R) | 730 |
| P3 — Abandono | Aprobó (A) vs. Abandonó (U) | 527 |

---

## Integrantes

| Nombre | Notebooks a cargo |
|:-------|:------------------|
| Stella Gerzel | 01_EDA |
| Juan Manuel Goya | 02_Preprocesamiento, 03_Modelado, 04_GridSearch |
| Gustavo Ebel | 05_Importancia, 06_Umbral, 00_Notebook_Final |

---

## Resultados principales

Mejor modelo por problema (ROC-AUC en test):

| Problema | Mejor modelo | ROC-AUC | Umbral recomendado |
|:---------|:-------------|--------:|:------------------:|
| P1 Riesgo global | XGBoost ajustado | 0.602 | 0.40 |
| P2 Desaprobación | XGBoost ajustado | 0.650 | 0.45 |
| P3 Abandono | Random Forest ajustado | 0.776 | 0.35 |

Variable más consistente en los tres problemas: **procedencia_localidad**.  
Variable con mayor importancia individual: **materia** y **cohorte** en P3 (abandono).

---

## Estructura del repositorio

```
/
├── notebooks/
│   ├── 00_Notebook_Final.ipynb       ← entregable oficial
│   ├── 01_EDA.ipynb                  ← análisis exploratorio
│   ├── 02_Preprocesamiento.ipynb     ← limpieza y pipeline
│   ├── 03_Modelado.ipynb             ← entrenamiento y evaluación
│   ├── 04_GridSearch.ipynb           ← ajuste de hiperparámetros
│   ├── 05_Importancia.ipynb          ← importancia de variables
│   └── 06_Umbral.ipynb               ← ajuste de umbral de decisión
├── data/
│   └── dataset_unificado_UNCAus.xlsx ← dataset anonimizado (978 registros)
├── informe/
│   └── Informe_Final_ML_UNCAus.docx  ← informe complementario
└── README.md
```

---

## Herramientas y tecnologías

- **Lenguaje**: Python 3
- **Entorno**: Google Colab
- **Librerías principales**:
  - `pandas`, `numpy` — manipulación de datos
  - `scikit-learn` — modelos, validación cruzada, métricas, preprocesamiento
  - `xgboost` — modelo de boosting
  - `matplotlib`, `seaborn` — visualización
  - `scipy` — cálculo de V de Cramér

---

## Metodología

Se adoptó el marco **CRISP-DM** (Cross Industry Standard Process for Data Mining):

1. **Comprensión del problema** — definición del riesgo académico y los tres problemas de clasificación
2. **Comprensión y preparación de los datos** — EDA, limpieza, codificación, split estratificado 75/25
3. **Modelado** — entrenamiento de Regresión Logística, Random Forest y XGBoost con validación cruzada 5-fold y ajuste de hiperparámetros mediante GridSearchCV
4. **Evaluación** — métricas ROC-AUC, recall, precisión y F1-score; análisis de umbral de decisión; importancia de variables con dos métodos (importancia interna RF y permutation importance)
5. **Conclusiones** — interpretación institucional de los resultados y propuesta de líneas futuras

---

## Cómo ejecutar los notebooks

1. Abrir el notebook en [Google Colab](https://colab.research.google.com)
2. Ejecutar **Entorno de ejecución → Ejecutar todo** (`Ctrl+F9`)
3. Cuando aparezca el botón de carga de archivos, seleccionar los 4 archivos Excel originales
4. Los notebooks se ejecutan de forma independiente — cada uno carga los datos desde cero

> Los notebooks fueron desarrollados y probados en Google Colab con Python 3.12.

---

## Dataset

El dataset proviene de relevamientos institucionales de UNCAus mediante el sistema SIU-Guaraní.
El acceso fue provisto por Stella Gerzel en su carácter de docente de la institución.

Los datos fueron anonimizados antes de ser incorporados al repositorio:
el identificador de alumno (legajo numérico) fue reemplazado por un código hash unidireccional.
No se incluyen nombres, DNI ni ningún otro identificador personal directo.

---

## Limitaciones

- El modelo trabaja únicamente con variables relevadas al inicio del ciclo lectivo.
  No tiene acceso a notas de parciales, asistencia ni rendimiento durante la cursada,
  lo que limita el AUC máximo alcanzable.
- Las variables identificadas como relevantes representan asociaciones estadísticas,
  no relaciones causales.
- El dataset cubre dos materias y dos cohortes de una sola institución.
  Los modelos pueden no generalizarse a otros contextos sin reentrenamiento.

---

## Líneas de trabajo futuro

- Transformar `procedencia_localidad` en distancia kilométrica a la sede (ya identificado)
- Incorporar variables de desempeño durante la cursada (asistencia, notas de parciales)
- Ampliar el análisis a otras materias y cohortes
- Evaluar la integración del modelo en un sistema de alerta temprana institucional

---

## Referencia del curso

> Trabajo Integrador — Asignatura: Introducción al Aprendizaje de Máquina  
> Doctorado en Informática — UTN FRRe / UNNE / UNAM — 2026
