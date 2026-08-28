# Plantilla de reportes FACSO en Quarto

Esta plantilla de Quarto permite generar reportes reproducibles combinando texto (en markdown), análisis de datos y visualizaciones. Está orientada a estudiantes que necesiten elaborar trabajos de cursos, informes académicos, tesis, entre otros. Incluye los logos de FACSO, pero puede adaptarse a otros contextos. 

El propósito del repositorio es proporcionar un punto de partida completo: estructura de capítulos, manejo de datos, estilos visuales coherentes y archivos auxiliares para la exportación a HTML y PDF. El repositorio se organiza siguiendo las prácticas reproducibles del  [protocolo IPO](https://lisacoes.com/protocolos/a-ipo-rep/), con carpetas diferenciadas para `input/`, `procesamiento/` y `output/`.

Puede revisar la versión publicada en [https://datasoc.github.io/ReportesFACSO_plantillaQuarto/](https://github.com/data-soc/ReportesFACSO_plantillaQuarto), donde también encontrará la opción para descargar el paquete ZIP listo para usar. 

Esta versión es una adaptación de la plantilla para reportes FACSO desarrollada por [Katherine Aravena](https://github.com/karavena), y es similar a la propuesta de [**tesisfacsodown**](https://jc-castillo.com/blog/posts/tesisfacsodown/index.html) que se basa en Rmarkdown/Bookdown, pero aprovecha las ventajas de Quarto para generar documentos HTML y PDF desde un mismo proyecto, con mayor flexibilidad en estilos y formatos. 

## Requisitos previos

- Quarto 1.5 o superior instalado en el sistema (https://quarto.org).
- Motor LaTeX disponible para la salida en PDF (TinyTeX, TeX Live o MiKTeX).
- Git para clonar y versionar (opcional, pero recomendado).
- R con los paquetes necesarios si se ejecutan análisis embebidos en los capítulos.

## Primeros pasos

1. Clonar el repositorio (Usar esta plantilla) o descargar el paquete ZIP desde la página publicada [aquí](https://datasoc.github.io/ReportesFACSO_plantillaQuarto/).
2. Abrir la carpeta del proyecto en VS Code o RStudio.
3. Revisar `_quarto.yml` para ajustar metadatos (título, autores, fecha, idioma, formato de salida).
4. Ejecutar `quarto render` desde la raíz del proyecto para generar los archivos en `docs/`.

## Estructura principal del repositorio

El repositorio organiza el contenido en capítulos base (`00–06`), apéndices, e includes para portadas y metadatos. La identidad visual se controla en `assets/styles.scss` y el diseño PDF en `reportes-facso-plantilla.tex`. La carpeta `refs/` aloja `apa.csl` y `referencias.bib`. Se sigue el [protocolo IPO](https://lisacoes.com/protocolos/a-ipo-rep/) con `input/` (datos), `procesamiento/` (scripts/notebooks) y `output/` (tablas/figuras listas).

La plantilla permite integrar tablas y gráficos que se actualizan al cambiar los datos. Las citas se gestionan con Pandoc usando claves de `refs/referencias.bib` (formato BibTeX/CSL JSON), con estilo APA por defecto (`refs/apa.csl`). Esto asegura consistencia entre texto, evidencias y bibliografía en ambas salidas (HTML y PDF).

El despliegue web se puede realizar mediante [**GitHub Pages**](https://www.youtube.com/watch?v=8IdBAysf-U4) desde `docs/`. 


- `00-prefacio.qmd` a `06-conclusiones.qmd`: capítulos base del informe.
- `apendices/`: archivos QMD de anexos (`A-encuestas.qmd`, `B-tablas.qmd`).
- `includes/`: fragmentos de HTML/TeX utilizados en cabeceras, portadas, botones y scripts.
- `reportes-facso-plantilla.tex`: plantilla personalizada para la salida en PDF.
- `_metadata.yml`: metadatos y opciones compartidas por los capítulos.
- `_freeze/`: resultados cacheados de ejecuciones previas de Quarto (pueden limpiarse con `quarto clean`).
- `docs/`: sitio resultante listo para publicación en GitHub Pages o servidores estáticos.
- `site_libs/`: librerías estáticas que Quarto copia al sitio final.
- `input/`, `procesamiento/`, `output/`: directorios para insumos, scripts de preparación y artefactos finales (ver README interno).
- `refs/`: estilos de citación (`apa.csl`) y base bibliográfica (`referencias.bib`).

## Personalización de contenido

- Actualizar portada, logo y enlaces de descarga editando los archivos en `includes/` (por ejemplo, `logo-link.html`, `title-html.html`, `title-pdf.tex`).
- Configurar las opciones de la portada PDF ajustando `includes/cover-config.tex`, donde se definen ciudad, contexto, profesor guía y otros metadatos visibles.
- Ajustar colores, tipografías o detalles visuales en `assets/styles.scss`; ejecutar `quarto render` para ver los cambios aplicados.
- Modificar el archivo `reportes-facso-plantilla.tex` si se requiere adaptar el diseño PDF (margenes, cabeceras, numeración).
- Agregar o quitar capítulos creando nuevos archivos `.qmd` y listándolos en `index.qmd` y en la sección `sidebar` de `_quarto.yml`.
- Incluir la bibliografía en `referencias.bib` y citar usando Pandoc (`@clave`).

## Flujo de trabajo sugerido

1. Organizar los datos brutos en `input/data-orig/` y documentarlos brevemente.
2. Procesar la información en `procesamiento/` usando scripts o notebooks; guardar los productos limpios en `input/data-proc/` o `output/`, según corresponda.
3. Referenciar tablas y gráficos listos de los capítulos usando rutas relativas (por ejemplo, `output/tables/tabla-01.html`).
4. Usar `freeze: auto` (configurado) para mantener resultados reproducibles y evitar reejecuciones innecesarias.
5. Antes de liberar una versión final, ejecutar `quarto render --to html pdf` para garantizar la paridad entre formatos.

## Recursos útiles

- Documentación Quarto: https://quarto.org/docs
- Guía de libros en Quarto: https://quarto.org/docs/books
- Referencia de estilos SCSS: https://sass-lang.com/documentation
- Herramientas TinyTeX (instalación rápida LaTeX): https://yihui.org/tinytex

Para dudas o mejoras sugeridas, abrir un issue en el repositorio o contactar al equipo de ([LISA](https://lisacoes.com/)) o de [datasoc](https://datasoc.cl/) .
