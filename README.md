# **ESTIMACIÓN DE LA VELOCIDAD DE LOS POKÉMON MEDIANTE MODELOS SUPERVISADOS: REGRESIÓN Y VALIDACIÓN MEDIANTE CLASIFICACIÓN**
## Descripción
Este proyecto analiza la variable `speed` (velocidad) en un dataset de Pokémon y evalúa si es posible estimarla a partir de otras estadísticas. El objetivo principal es imputar valores faltantes de `speed` mediante modelos de regresión y comprobar si esa imputación afecta el desempeño de una clasificación binaria: identificar Pokémon legendarios (`is_legendary`).

## Dataset
Utilizamos el dataset de pokemon https://www.kaggle.com/datasets/hamzacyberpatcher/data-of-1010-pokemons con estadísticas base y atributos físicos, incluyendo variables como `hp`, `atk`, `def`, `spatk`, `spdef`, `speed`, `height` y `weight`, además de la etiqueta binaria `is_legendary`.

## Procesado y análisis inicial
- Revisión de calidad de datos y distribución de variables numéricas.
- Análisis exploratorio de `speed` y comparación con el resto de estadísticas.
- Estudio de correlaciones para entender qué variables se relacionan con la velocidad.
- Construcción de un escenario con valores faltantes simulados (~10%) en `speed` para replicar un caso realista.

## Modelos de regresión e imputación
Se implementan y comparan modelos para predecir `speed` a partir del resto de variables:
- Regresión lineal (baseline)
- Random Forest Regressor
- Optimización con Grid Search (comparación contra el modelo base no lineal)

La imputación se realiza utilizando el modelo seleccionado sobre las filas con `speed` faltante.

## Validación en clasificación
Para medir el impacto real de la imputación, se entrena un clasificador de `is_legendary` y se comparan tres escenarios:
- Dataset original (sin faltantes en `speed`)
- Dataset con `speed` faltante
- Dataset con `speed` imputado

## Resultados principales
La regresión permite aproximar `speed`, pero no determinarla completamente a partir de las demás variables, lo que sugiere que la velocidad depende también de factores no representados en el dataset. En la etapa de clasificación, el desempeño global se mantiene estable entre escenarios, por lo que la imputación completa el dataset sin generar mejoras consistentes en la detección de legendarios.

## Insight clave
La velocidad describe un estilo o rol de combate más que una regla deducible desde otras estadísticas: puede estimarse parcialmente con señales ofensivas, pero gran parte de su variación responde a factores no observados. Por eso, imputar `speed` es útil para completar datos, pero no cambia de manera sustancial la capacidad de distinguir legendarios.

## Tecnologías utilizadas
- Python
- pandas, numpy
- scikit-learn
- matplotlib / seaborn

## Autor
Sebastian Pelaez Villalba

