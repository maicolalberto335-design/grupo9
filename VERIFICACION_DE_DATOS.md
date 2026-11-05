# Auditoría reproducible de datos — 4 de noviembre de 2026

## ECV 2024

Se ejecutó `python scripts/calcular_indicadores_ecv_2024.py` sobre `datos/ECV_2024_original.xlsx` y se compararon los seis porcentajes con `datos/indicadores_ecv_2024.csv`. **Los seis valores coinciden exactamente a dos decimales**.

| Indicador | San Javier | El Poblado | Diferencia (pp) |
|---|---:|---:|---:|
| Alfabetismo (15+) | 97,73 | 99,06 | 1,33 |
| Asistencia educativa (5–24) | 66,47 | 85,73 | 19,26 |
| Formación superior (25+) | 15,34 | 74,12 | 58,78 |

Variables de entrada: `A.7` comuna, `B.6` edad, `E.1` alfabetismo, `E.2` asistencia, `E.6` título, `FEP` factor de expansión. Código fuente en `scripts/calcular_indicadores_ecv_2024.py`. Esta auditoría comprueba la reproducción **del algoritmo y sus valores**, no la pertinencia de todas las categorías ni la representatividad estadística.

## IMCV 2023

`datos/indicadores_2023.csv` conserva la transcripción de los resultados seleccionados del archivo de socialización y dimensiones. Para replicar el cotejo, abrir `datos/socializacionIMCV2023 (1).xlsx` y `datos/DimensionesIMCV2023.xlsx`. Los indicadores individuales no son puntajes dimensionales completos.

## Pendientes que no se deben declarar cumplidos

- Contrastar cada definición educativa y sus exclusiones contra el cuestionario y diccionario originales.
- Verificar las ponderaciones oficiales y dos referencias locales del marco teórico.
- Ejecutar `Rscript scripts/grafica_educacion_2024.R` y `quarto render paper_g9.qmd --to pdf` en un entorno con R y Quarto.
- Publicar un repositorio privado de GitHub y comprobar clonación y compilación desde otra cuenta.
