# Selección de Preguntas para el 1er Debate Presidencial INE 2024

Cuadernos de código desarrollados como parte del equipo de **Signa_Lab ITESO**,
para el proceso oficial de selección de preguntas ciudadanas del **1er Debate
Presidencial del INE 2024** ("La Sociedad que Queremos", 7 de abril de 2024).

## Mi participación

Formé parte del equipo de programación encargado de los cuadernos de código
para **limpieza, depuración y análisis exploratorio de datos, análisis
semántico y selección aleatoria**, según consta en el informe oficial
entregado por Signa_Lab ITESO al INE.

> Informe completo: *Informe sobre el Proceso de Selección de Preguntas de
> Redes Sociales para el 1er Debate Presidencial INE 2024 (Formato A)*,
> Signa_Lab ITESO, 10 de abril de 2024.
> [Ver documento oficial (INE)](https://centralelectoral.ine.mx/wp-content/uploads/2024/04/Signa_Lab-ITESO_Informe-Sobre-Metodologi%CC%81a-Debate-INE-Formato-A.pdf)

## Contexto del proyecto

El INE recopiló más de 24,000 preguntas ciudadanas a través de un formulario
digital, distribuidas en 6 temas (Combate a la corrupción, Educación, Salud,
Transparencia, Violencia contra las mujeres, y No discriminación y grupos
vulnerables) y 3 regiones del país. El objetivo era obtener una selección
final de 108 preguntas (18 por frecuencia y 90 aleatorias) para las personas
moderadoras del debate, garantizando representatividad, neutralidad y
cumplimiento de criterios de elegibilidad.

Los cuadernos de este repositorio documentan el pipeline aplicado:

1. **Depuración**: eliminación de preguntas por lenguaje ofensivo, sesgo
   partidista (diccionario de 519 términos proscritos) y duplicados exactos,
   de 24,000 a 21,219 preguntas.
2. **Muestra estratificada**: cálculo de una muestra representativa por
   tema y región (1,701 preguntas), con 99% de confianza y 3% de margen de error.
3. **Análisis semántico**: generación de embeddings (modelo
   `multilingual-e5-large-instruct`), clustering (UMAP + k-means) y
   lingüística de corpus (n-gramas, TF-IDF) para identificar los núcleos
   semánticos más frecuentes por tema.
4. **Selección**: extracción de 18 preguntas por frecuencia y 90 por
   selección aleatoria estratificada (con semilla fija para trazabilidad).
5. **Revisión**: apoyo al proceso de revisión manual y reemplazo de
   preguntas que no cumplían los criterios de elegibilidad del INE.

## Estructura del repositorio

```
notebooks/
├── 01_depuracion_aed.ipynb              <- Depuración y análisis exploratorio inicial (Cuaderno 01)
├── 02_generacion_embeddings.ipynb       <- Generación de embeddings semánticos (Cuaderno 02)
├── 03_analisis_semantico/               <- Análisis semántico y selección por tema (Cuaderno 03)
│   ├── corrupcion.ipynb
│   ├── educacion.ipynb
│   ├── salud.ipynb
│   ├── transparencia.ipynb
│   ├── violencia_mujeres.ipynb
│   └── no_discriminacion.ipynb
├── 04_revision_preguntas.ipynb          <- Revisión y sustitución de preguntas (Cuaderno 04)
└── 05_analisis_exploratorio_resultados.ipynb  <- Análisis exploratorio de resultados (Cuaderno 05)

reports/
├── anexo3_graficas_poblacion_depurada.pdf     <- Gráficas de la población depurada (21,219 preguntas)
└── anexo4_graficas_analisis_semantico.pdf     <- Gráficas del análisis semántico por tema
```

Esta numeración corresponde a los Cuadernos 01–05 documentados en el Anexo 13
del informe oficial.

## Cómo navegar el proyecto

1. `01_depuracion_aed.ipynb` — de dónde parte todo: limpieza de la base de datos.
2. `02_generacion_embeddings.ipynb` — vectorización semántica del corpus.
3. `03_analisis_semantico/` — el análisis desglosado, un notebook por tema.
4. `04_revision_preguntas.ipynb` y `05_analisis_exploratorio_resultados.ipynb`
   — cierre del proceso y hallazgos finales.
5. Los PDFs en `reports/` corresponden a los Anexos 3 y 4 del informe oficial.

