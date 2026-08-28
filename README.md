# Plantilla de reportes FACSO

![Equipo LISA 2025](assets/sharing-default.png)

Esta plantilla Quarto permite crear informes profesionales para proyectos de investigacion, cursos y documentos institucionales de FACSO. El proposito del repositorio es entregar un punto de partida completo: estructura de capitulos, manejo de datos, estilos visuales coherentes y archivos auxiliares para exportar a HTML y PDF. El repositorio se organiza siguiendo las practicas reproducibles del  [protocolo IPO](https://lisacoes.com/protocolos/a-ipo-rep/), con carpetas diferenciadas para `input/`, `procesamiento/` y `output/`.

Puedes revisar la version publicada en [https://karavena.github.io/ReportesFACSO_plantillaQuarto/](https://karavena.github.io/ReportesFACSO_plantillaQuarto/), donde tambien encontraras la opcion para descargar el paquete ZIP listo para usar.

## Requisitos previos

- Quarto 1.5 o superior instalado en el sistema (https://quarto.org).
- Motor LaTeX disponible para la salida PDF (TinyTeX, TeX Live o MiKTeX).
- Git para clonar y versionar (opcional pero recomendado).
- R con los paquetes necesarios si se ejecutan analisis embebidos en los capitulos.

## Primeros pasos

1. Clonar el repositorio (Usar esta plantilla) o descargar el paquete ZIP desde la pagina publicada [Aquí](https://karavena.github.io/ReportesFACSO_plantillaQuarto/).
2. Abrir la carpeta del proyecto en VS Code o RStudio.
3. Revisar `_quarto.yml` para ajustar metadatos (titulo, autores, fecha, idioma, formato de salida).
4. Ejecutar `quarto render` desde la raiz del proyecto para generar los archivos en `docs/`.

## Estructura principal del repositorio


El repositorio organiza el contenido en capítulos base (`00–06`), apéndices, e includes para portadas y metadatos. La identidad visual se controla en `assets/styles.scss` y el diseño PDF en `reportes-facso-plantilla.tex`. La carpeta `refs/` aloja `apa.csl` y `referencias.bib`. Se sigue el [protocolo IPO](https://lisacoes.com/protocolos/a-ipo-rep/) con `input/` (datos), `procesamiento/` (scripts/notebooks) y `output/` (tablas/figuras listas).

La plantilla permite integrar tablas y gráficos que se actualizan al cambiar los datos. Las citas se gestionan con Pandoc usando claves de `refs/referencias.bib` (formato BibTeX/CSL JSON), con estilo APA por defecto (`refs/apa.csl`). Esto asegura consistencia entre texto, evidencias y bibliografía en ambas salidas (HTML y PDF).

El despliegue web se puede realizar mediante [**GitHub Pages**](https://www.youtube.com/watch?v=8IdBAysf-U4) desde `docs/`. 



- `00-prefacio.qmd` a `06-conclusiones.qmd`: capitulos base del informe.
- `apendices/`: archivos QMD para anexos (`A-encuestas.qmd`, `B-tablas.qmd`).
- `includes/`: fragmentos HTML/TeX utilizados en cabeceras, portadas, botones y scripts.
- `reportes-facso-plantilla.tex`: plantilla personalizada para la salida PDF.
- `_metadata.yml`: metadatos y opciones compartidas por los capitulos.
- `_freeze/`: resultados cacheados de ejecuciones previas de Quarto (pueden limpiarse con `quarto clean`).
- `docs/`: sitio resultante listo para publicacion en GitHub Pages o servidores estaticos.
- `site_libs/`: librerias estaticas que Quarto copia al sitio final.
- `input/`, `procesamiento/`, `output/`: directorios para insumos, scripts de preparacion y artefactos finales (ver README internos).
- `refs/`: estilos de citacion (`apa.csl`) y base bibliografica (`referencias.bib`).

## Personalizacion de contenido

- Actualizar portada, logo y enlaces de descarga editando los archivos en `includes/` (por ejemplo `logo-link.html`, `title-html.html`, `title-pdf.tex`).
- Configurar las opciones de la portada PDF ajustando `includes/cover-config.tex`, donde se definen ciudad, contexto, profesor guia y otros metadatos visibles.
- Ajustar colores, tipografias o detalles visuales en `assets/styles.scss`; ejecutar `quarto render` para ver los cambios aplicados.
- Modificar el archivo `reportes-facso-plantilla.tex` si se requiere adaptar el diseno PDF (margenes, cabeceras, numeracion).
- Agregar o quitar capitulos creando nuevos `.qmd` y listandolos en `index.qmd` y en la seccion `sidebar` de `_quarto.yml`.
- Incluir bibliografia en `referencias.bib` y citar usando Pandoc (`@clave`).

## Flujo de trabajo sugerido

1. Organizar datos brutos en `input/data-orig/` y documentarlos brevemente.
2. Procesar la informacion dentro de `procesamiento/` usando scripts o notebooks; guardar productos limpios en `input/data-proc/` o `output/` segun corresponda.
3. Referenciar tablas y graficos listos desde los capitulos usando rutas relativas (por ejemplo `output/tables/tabla-01.html`).
4. Usar `freeze: auto` (configurado) para mantener resultados reproducibles y evitar re-ejecuciones innecesarias.
5. Antes de liberar una version final, ejecutar `quarto render --to html pdf` para garantizar paridad entre formatos.

## Recursos utiles

- Documentacion Quarto: https://quarto.org/docs
- Guia de libros en Quarto: https://quarto.org/docs/books
- Referencia de estilos SCSS: https://sass-lang.com/documentation
- Herramientas TinyTeX (instalacion rapida LaTeX): https://yihui.org/tinytex

Para dudas o mejoras sugeridas, abrir un issue en el repositorio o contactar al equipo de la plantilla ([LISA](https://lisacoes.com/))  .
