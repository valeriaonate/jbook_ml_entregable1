# Clasificación de la cobertura forestal a partir de variables cartográficas

**Curso:** Machine Learning  
**Entrega:** Primer entregable del proyecto de investigación  
**Autoras:** Ana Galván, Valeria Oñate y María José Ruiz  
**Fecha:** 30 de septiembre de 2026

## Resumen

Este libro documenta la primera etapa de un proyecto de aprendizaje supervisado: la selección de la base de datos, el análisis exploratorio de datos (EDA), la auditoría de fuga de información, el diseño del preprocesamiento y la construcción de un modelo base que sirva como referencia para las etapas siguientes.

El problema consiste en predecir el **tipo de cobertura forestal dominante** en celdas de 30 × 30 metros del Roosevelt National Forest (Colorado, Estados Unidos) usando únicamente variables cartográficas: elevación, orientación, pendiente, distancias a fuentes de agua, carreteras y puntos de incendio, índices de sombreado, área silvestre y tipo de suelo. Los datos provienen del conjunto *Covertype* del repositorio UCI {cite}`uci_covertype,blackard2000`.

Se trata de una tarea de **clasificación multiclase con siete categorías y un desbalance marcado**: la clase más frecuente (pino lodgepole) tiene 103 veces más observaciones que la menos frecuente (álamo/sauce). Esta característica orienta las decisiones de partición, las métricas y la interpretación de resultados a lo largo del documento.

## Pregunta de investigación

¿En qué medida las características topográficas, hidrológicas y edáficas de un sitio permiten identificar el tipo de cobertura forestal que lo ocupa, y qué tan lejos llega un clasificador lineal en esta tarea?

La relevancia práctica es directa: los inventarios forestales de campo son costosos y, en zonas remotas o protegidas, difíciles de realizar. Un modelo que infiera la cobertura a partir de información cartográfica disponible de forma sistemática permite apoyar la planificación del manejo forestal, la evaluación del riesgo de incendios y el seguimiento de ecosistemas.

## Ruta metodológica

Al tratarse de un problema de **clasificación** con componente espacial implícito y sin componente temporal, el trabajo se organiza en los siguientes pasos:

1. Reserva del conjunto de prueba mediante una partición estratificada antes de cualquier decisión basada en los datos.
2. EDA sobre el conjunto de entrenamiento: variable objetivo, análisis unidimensional, bidimensional y multivariado.
3. Auditoría de fuga de información y análisis de la estructura espacial de los datos.
4. Preprocesamiento implementado en un `Pipeline` de scikit-learn {cite}`pedregosa2011`, ajustado solo con entrenamiento.
5. Modelo base (regresión logística multinomial) comparado con clasificadores triviales (`DummyClassifier`), con validación cruzada estratificada, intervalos de confianza por *bootstrap* y diagnóstico de errores.

## Organización del documento

| Capítulo | Contenido |
|---|---|
| 1. Base de datos | Problema, justificación, fuente y licencia, diccionario de variables, estructura, tamaño de muestra, calidad de datos y consideraciones éticas |
| 2. Análisis exploratorio | Variable objetivo, análisis unidimensional, bidimensional y multivariado |
| 2.5–2.8 Fuga y estructura | Auditoría de fuga de información y componentes temporal, espacial y espacio-temporal |
| 2.9 Preprocesamiento | Decisiones de preprocesamiento y su justificación a partir del EDA |
| 3. Modelo base | Línea base trivial, regresión logística, validación cruzada, métricas, curvas, calibración y curva de aprendizaje |
| 4. Conclusiones | Hallazgos principales y limitaciones |
| 5. Apéndice | Archivos, dependencias, semillas y código auxiliar |

```{note}
Todos los resultados se generan al compilar el libro. La semilla aleatoria es `42` en todas las particiones, submuestras y modelos, y las versiones de las librerías están fijadas en `requirements.txt`.
```
