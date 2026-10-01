# 5. Apéndice: reproducibilidad

## 5.1 Archivos de la entrega

```text
MachineLearning/
├── Entregable1/
│   └── covertype.csv                  Base de datos (581.012 filas, 55 columnas)
└── jbook_ml_entregable1/
    └── docs/
        ├── _config.yml                Configuración del libro
        ├── _toc.yml                   Tabla de contenido
        ├── requirements.txt           Dependencias con versiones fijadas
        ├── references.bib             Referencias bibliográficas
        ├── _utils.py                  Carga, partición, pipelines y constantes
        ├── intro.md
        ├── 01_base_datos.md
        ├── 02_eda.md
        ├── 02b_fuga_estructura.md
        ├── 02c_preprocesamiento.md
        ├── 03_modelo_base.md
        ├── 04_conclusiones.md
        ├── 05_apendice.md
        └── bibliografia.md
```

La base de datos también puede descargarse del repositorio UCI: <https://archive.ics.uci.edu/dataset/31/covertype>. El archivo local `covertype.csv` corresponde al archivo original `covtype.data` con los nombres de las columnas agregados.

## 5.2 Entorno y semillas

- **Python:** 3.9, en el ambiente de conda `ml_venv`.
- **Dependencias:** fijadas en `requirements.txt` (scikit-learn 1.3.0, pandas 2.1.0, numpy 1.23.5, scipy 1.11.2, matplotlib 3.7.2, seaborn 0.12.2 y jupyter-book 0.15.1).
- **Semilla aleatoria:** `RANDOM_STATE = 42`, definida en `_utils.py` y usada en la partición entrenamiento/prueba, en todas las submuestras estratificadas, en los pliegues de validación cruzada, en el *bootstrap*, en Isolation Forest, en *k-means*, en t-SNE y en los modelos.

## 5.3 Código auxiliar

El archivo `_utils.py` centraliza la carga del dataset, la partición reproducible, la ingeniería de variables y la construcción de los *pipelines*, de modo que todos los capítulos usan exactamente la misma partición y el mismo preprocesamiento.

```{literalinclude} _utils.py
:language: python
```
