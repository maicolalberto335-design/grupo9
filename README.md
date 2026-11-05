# Proyecto Grupo 9 — abrir en RStudio y compilar

**Para abrir el documento en RStudio:** descomprime el ZIP, abre `Grupo9.Rproj` (doble clic), y desde RStudio selecciona **File > Open File > paper_g9.qmd**. Si Windows no reconoce el archivo `.qmd` con doble clic, ábrelo desde RStudio como archivo de texto. La extensión `.qmd` es un documento Quarto, no un archivo `.R`.

**Para ver el documento sin instalar LaTeX:** instala [Quarto](https://quarto.org/docs/get-started/), abre una terminal en la carpeta del proyecto y ejecuta `quarto render paper_g9.qmd --to html`. Luego abre `paper_g9.html` en el navegador. Alternativamente, en RStudio ejecuta `source("scripts/abrir_vista_en_RStudio.R")`. La vista HTML contiene el texto y la gráfica; algunos comandos de portada y formato son exclusivos de LaTeX y solo aplican al PDF.

**Para compilar el PDF:** instala Quarto y una distribución de LaTeX con XeLaTeX, y ejecuta `quarto render paper_g9.qmd --to pdf`. Los archivos `referencias.bib`, `apa.csl`, `formato_apa.tex` y `figuras/` deben mantenerse junto al QMD en la estructura suministrada. El PDF ya generado también se incluye para consulta.

**Para reproducir el análisis:** ejecuta `Rscript scripts/analisis_imcv.R` y `Rscript scripts/grafica_educacion_2024.R` desde la raíz del repositorio. Revisa en cada script los datos requeridos y su alcance. Este paquete ligero incluye indicadores procesados y no la base original completa ECV 2024.

**Alcance de verificación:** se verificaron la presencia de las dependencias locales, la estructura del archivo QMD y la sintaxis del encabezado YAML. No se pudo probar una compilación efectiva con Quarto ni la ejecución de R en este entorno, por lo que la primera compilación debe verificarse en un equipo con estas herramientas instaladas.

---

# Grupo 9 — Condiciones de vida en las comunas 13 y 14 de Medellín

Trabajo académico del Grupo 9. El manuscrito completo está en `paper_g9.qmd`; `paper_g9.pdf` es la versión de referencia.

## Requisitos para compilar

- [Quarto](https://quarto.org/docs/get-started/) instalado.
- Una distribución LaTeX con **XeLaTeX** (por ejemplo, TinyTeX), y la fuente **Tinos** instalada. Si no dispone de Tinos, cambie `mainfont: Tinos` por una fuente instalada antes de compilar.
- R y RStudio son recomendados para ejecutar los scripts, pero el manuscrito QMD no contiene bloques ejecutables de R obligatorios para compilar el PDF.

## Clonar y compilar

```bash
git clone URL_DEL_REPOSITORIO
cd NOMBRE_DEL_REPOSITORIO
quarto render paper_g9.qmd --to pdf
```

O en RStudio: `File > Open File > paper_g9.qmd` y luego **Render**. Ejecute el comando desde la raíz del repositorio para que las rutas relativas funcionen.

## Reproducir gráfica en R

Desde la raíz del proyecto:

```bash
Rscript scripts/grafica_educacion_2024.R
```

Este script lee `datos/indicadores_ecv_2024.csv` y genera `figuras/brechas_educacion_2024.png`. La figura incluida en el paper (`figuras/brechas_educacion_2024_verificada.png`) es la versión previamente verificada con Python. El script R reproduce la visualización de los indicadores tabulados, no recalcula la encuesta original.

`Rscript scripts/analisis_imcv.R` comprueba la matriz dimensional. Como no se dispone de los 20 puntajes oficiales homologables, `datos/dimensiones_2023_2024.csv` solo contiene encabezados y el script informa que faltan datos; no inventa resultados.

## Datos y limitaciones

La carpeta `datos/` contiene tablas utilizadas en el manuscrito y dos libros oficiales de IMCV 2023. **La base original ECV 2024 de aproximadamente 22 MB no está incluida en esta versión ligera**, por lo que no se puede reproducir desde cero el cálculo de microdatos ECV 2024 solo con este repositorio. Para esa auditoría se requiere la base original y el script de cálculo, disponible en el paquete de trabajo completo. Los CSV incluidos sí permiten reproducir la gráfica R y revisar los resultados tabulados.

## Herramientas y declaración de IA

Consulte `PROMPTS_Y_DECLARACION_IA.md`. El proyecto utiliza Quarto, BibTeX/CSL y R para el manuscrito y la visualización. Algunos indicadores fueron contrastados mediante un procedimiento complementario en Python, mientras que los scripts de análisis y visualización disponibles están en R.

## Estado de verificación

Se comprobaron la existencia de los archivos y las rutas relativas utilizadas por el QMD. **No se ejecutó Quarto ni RStudio en este entorno**, por lo que la compilación en otro equipo queda pendiente de verificación. La compilación puede requerir instalar LaTeX, fuentes o paquetes según el sistema operativo.


## Solución de problemas de compilación

Abre `Grupo9.Rproj` y luego `paper_g9.qmd` desde RStudio (File > Open File).
Para comprobar Quarto en la terminal: `quarto check`.
Para vista HTML: `quarto render paper_g9.qmd --to html`.
Para PDF: `quarto render paper_g9.qmd --to pdf`.
El PDF requiere XeLaTeX y la fuente Tinos instalada. Si no existe XeLaTeX, instala TinyTeX con `quarto install tinytex`.
La portada y los saltos de página están ahora en bloques LaTeX específicos para PDF, de modo que no interfieran con HTML.
El PDF preexistente `paper_g9.pdf` se conserva como referencia; solo una compilación local confirmará la equivalencia del nuevo PDF.
