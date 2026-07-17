# Detección temprana de riesgo académico — UNCAus

Trabajo Integrador — Introducción al Aprendizaje de Máquina  
Doctorado en Informática — UTN FRRe / UNNE / UNAM — Julio 2026

---

## Descripción

Aplicación de técnicas de aprendizaje automático supervisado para la predicción temprana del riesgo académico de estudiantes de primer año de Ingeniería en Sistemas de la Universidad Nacional del Chaco Austral (UNCAus). Se trabajó sobre un dataset real de 978 registros de las asignaturas Algoritmos y Estructuras de Datos y Sistemas y Organizaciones (cohortes 2024 y 2025), relevados mediante el sistema SIU-Guaraní.

Para el detalle completo de metodología, resultados y conclusiones ver `informe/Informefinal.pdf`.

---

## Integrantes

| Nombre | Notebooks a cargo |
|:-------|:------------------|
| Stella Maris Gerzel | 01_EDA |
| Juan Manuel Goya | 02_Preprocesamiento, 03_Modelado, 04_GridSearch |
| Gustavo Ebel | 05_Importancia, 06_Umbral, 00_Notebook_Final |

---

## Estructura del repositorio

```
main (rama)
└── ml_uncaus/
    ├── notebooks/
    │   ├── 00_Notebook_Final.ipynb
    │   ├── 01_EDA.ipynb
    │   ├── 02_Preprocesamiento.ipynb
    │   ├── 03_Modelado.ipynb
    │   ├── 04_GridSearch.ipynb
    │   ├── 05_Importancia.ipynb
    │   └── 06_Umbral.ipynb
    ├── informe/
    │   └── Informefinal.pdf
    └── README.md
```

> El dataset no se incluye en el repositorio por contener información institucional.
> Los datasets serán disponibilizados directamente a la cátedra.

---

## Herramientas

Python 3 · Google Colab · scikit-learn · XGBoost · pandas · matplotlib · seaborn

---

> Trabajo Integrador — Asignatura: Introducción al Aprendizaje de Máquina  
> Doctorado en Informática — UTN FRRe / UNNE / UNAM — 2026
