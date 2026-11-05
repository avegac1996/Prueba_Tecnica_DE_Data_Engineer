# Prueba Técnica Data Engineer - Banco Pichincha

Candidato: Anthony Vega
Rol: Data Engineer

## Contenido del repositorio
Prueba_Tecnica_DE_Data_Engineer_Banco_Pichincha_Anthony_Vega.ipynb
CENTROS_EDUCATIVOS_MADRID.json
README.md


## Descripción

Notebook de Google Colab con la resolución de 6 preguntas, en dos secciones:

| Sección | Pregunta | Tema |
|---|---|---|
| SQL (SQLite) | 1 | Tabla de resultados por equipo (puntos y gol diferencia) a partir de la tabla `Partidos` |
| SQL (SQLite) | 2 | Los 2 equipos clasificados por grupo, con sede y fecha/hora de la siguiente ronda |
| SQL (SQLite) | 3 | Equipos Élite: quintil más alto en puntos acumulados |
| PySpark | 4 | Mejor jugador por país, nuevo ranking con goles por partido y exportación a JSON |
| PySpark | 5 | Centro educativo más céntrico por `centro_titularidad` (promedio, UDF de distancia euclidiana) |
| PySpark | 6 | Exportación del resultado a Parquet, JSON y CSV (separador `|`) en `/tmp`, y justificación del formato |

## Cómo ejecutarlo

1. Abrir el notebook en Google Colab.
2. Subir `CENTROS_EDUCATIVOS_MADRID.json` a la ruta `/content`.
3. Ejecutar las celdas en orden. La pregunta 6 usa el resultado `df_agr` de la pregunta 5.

## Decisiones de resolución

- **Pregunta 1:** se normalizan los nombres de los equipos (tildes, mayúsculas y puntos finales) para que cada equipo se cuente una sola vez.
- **Pregunta 3:** se usa `NTILE(5)` sobre los puntos. Si hay empate, se desempata por gol diferencia, igual que en la pregunta 2.
- **Pregunta 4:** los jugadores estrella son el mejor jugador de cada país según el ranking anterior o según el nuevo indicador (goles / partidos jugados).
- **Pregunta 5:** se excluyen 4 centros sin coordenadas, porque la distancia no se puede calcular con valores nulos.
- **Pregunta 6:** se recomienda Parquet por ser columnar, comprimido, con esquema incluido y base de Delta Lake en Databricks.

## Tecnologías

Python, SQLite, PySpark, Google Colab.
