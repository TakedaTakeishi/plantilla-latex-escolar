<div align="center">

# Plantilla LaTeX para documentos académicos

[![XeLaTeX](https://img.shields.io/badge/XeLaTeX-3D6117?style=flat-square&logo=latex&logoColor=white)](https://www.latex-project.org)
[![Alegreya](https://img.shields.io/badge/Font-Alegreya-8B4513?style=flat-square)](#font-alegreya--times-new-roman)
[![Times New Roman](https://img.shields.io/badge/Font-Times%20New%20Roman-1F4E79?style=flat-square)](#font-alegreya--times-new-roman)
[![Biber](https://img.shields.io/badge/Bibliography-Biber-6A0DAD?style=flat-square)](#compilación)
[![VS Code](https://img.shields.io/badge/VS%20Code-LaTeX%20Workshop-007ACC?style=flat-square&logo=visualstudiocode)](#vs-code-setup)

</div>

Plantilla unificada para trabajos académicos en LaTeX compatible con **Alegreya** (XeLaTeX) y **Times New Roman**. Un solo proyecto, dos fuentes, una configuración.

## Requisitos

- Instalación de [TeX Live](https://tug.org/texlive/) (o [MiKTeX](https://miktex.org/) en Windows)
- [Visual Studio Code](https://code.visualstudio.com/) con la extensión [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
- Las fuentes instaladas en el sistema:
  - **Alegreya**: incluidas en TeX Live (`texlive-fonts-extra` en Linux)
  - **Times New Roman**: preinstalada en Windows/macOS; en Linux instalar `fonts-liberation` o `freetds`

> [!NOTE]
> Esta plantilla compila exclusivamente con **XeLaTeX**. Si vienes de pdfLaTeX, no necesitas cambiar nada — el `.vscode/settings.json` ya incluye las recetas correctas.

## Primeros pasos

```bash
# 1. Clona o descarga la plantilla
git clone https://github.com/TakedaTakeishi/plantilla-latex-escolar nuevo-proyecto

# 2. Abre la carpeta en VS Code
code nuevo-proyecto

# 3. Compila (Ctrl+Shift+P → "LaTeX Workshop: Build with recipe")
#    o simplemente guarda el archivo y compila automáticamente
```

## Cómo usar

Edita únicamente estos dos archivos y tendrás tu documento listo:

### 1. `capitulos/portada.tex` — Datos del proyecto

Aquí van el título, autores, materia, profesor, logos, etc. Todo lo visible de la portada está en este archivo.

```latex
\newcommand{\titulo}{Título del proyecto}
\newcommand{\listaAutores}{
    Apellido1 Nombre1 \\
    Apellido2 Nombre2
}
```

### 2. `config/proyecto.tex` — Configuración técnica

Acá se elige la fuente y los tamaños de título.

```latex
\newcommand{\fuentePrincipal}{Alegreya}  % "Alegreya" o "TimesNewRoman"
\newcommand{\tamanoTituloUno}{16pt}
```

### 3. Tus capítulos

Crea archivos `.tex` en `capitulos/` y descoméntalos en `main.tex`:

```latex
\input{capitulos/01_introduccion}
\input{capitulos/02_desarrollo}
\input{capitulos/03_conclusiones}
```

### 4. Bibliografía

Agrega tus referencias en `referencias.bib` y cítalas con `\cite{clave}`.

## Guía de redacción

La plantilla incluye en `docs/consejos_redaccion.md` una **guía de
autoevaluación** pensada para ayudarte a mejorar la belleza y
fluidez de tus textos. Puedes usarla antes de cada entrega para
revisar tu redacción punto por punto: estructura de párrafos, uso
de prosa en lugar de viñetas, marcadores textuales, formato de
figuras, citas en IEEE, etc.

> [!TIP]
> Antes de cerrar tu documento, ábrela y revisa cada apartado
> marcando lo que ya cumplas. La forma es tan importante como el
> fondo: una buena redacción, apoyada en **prosa continua** y en
> **marcadores textuales** bien elegidos, marca la diferencia entre
> un trabajo aceptable y uno bien presentado.

La guía incluye, entre otras cosas:

- Reglas generales de redacción (párrafos, viñetas, glosarios).
- Un **catálogo de marcadores textuales** organizados por intención
  discursiva (introducir, añadir, ordenar, explicar, contrastar,
  concluir) para evitar las listas y dar fluidez al texto.
- Lineamientos específicos para cada sección (portada, resumen,
  índice, introducción, marco teórico, citas, figuras, tablas,
  conclusiones).
- Errores comunes de forma que conviene evitar.
- Mini-ejemplos concretos para cada punto, facilitando su aplicación.

> [!TIP]
> Al estar en formato **Markdown (.md)** —el formato estándar para
> el contexto de asistentes de IA—, puedes copiar el contenido de
> `docs/consejos_redaccion.md` y usarlo como parte del prompt o
> contexto de herramientas como ChatGPT, Claude, Gemini, etc. Esto
> hará que las respuestas de la IA sigan los mismos lineamientos
> de redacción académica que exige tu documento, ahorrándote tiempo
> de corrección manual.

## Estructura del proyecto

```
📁 plantilla-latex-escolar/
├── 📁 .vscode/              → Configuración LaTeX Workshop (no tocar)
├── 📁 capitulos/            → Portada y tus capítulos (editar aquí)
│   ├── portada.tex           → Datos del proyecto + diseño
│   └── ejemplo.tex           → Capítulo de referencia
├── 📁 common/                → Archivos estáticos (no tocar)
│   ├── anexos.tex            → Anexos del documento
│   ├── bibliografia.tex      → Formato bibliográfico
│   └── indices.tex           → Generación de índices
├── 📁 config/                → Configuración técnica
│   ├── proyecto.tex          → Fuente, tamaños (editar)
│   └── configuracion.tex     → Paquetes y estilos (no tocar)
├── 📁 docs/                  → Guías y recursos para el autor
│   └── consejos_redaccion.md → Guía de autoevaluación de redacción
├── 📁 imagenes/              → Imágenes del proyecto
│   └── 📁 logos/             → Logos institucionales
├── 📁 build/                 → Compilación (no se sube)
├── .gitignore                → Exclusiones de control de versiones
├── main.tex                  → Documento principal
└── referencias.bib           → Referencias bibliográficas
```


## Documentos grandes (varios capítulos)

Cuando el proyecto tiene 3+ capítulos, cada uno con su propio
marco teórico, implementación, resultados, conclusiones y anexos,
lo ideal es organizarlos en **subcarpetas independientes**.

### Estructura recomendada

```
📁 proyecto/
├── 📁 capitulos/
│   ├── portada.tex                → Datos y diseño de portada
│   ├── resumen.tex                → Resumen ejecutivo
│   ├── introduccion.tex           → Introducción general
│   │
│   ├── 📁 capitulo_1/            → Un capítulo = una carpeta
│   │   ├── capitulo_1.tex         →  Punto de entrada (\chapter + \inputs)
│   │   ├── 01_marco_teorico.tex   →   Sección: marco teórico
│   │   ├── 02_programacion.tex    →   Sección: implementación
│   │   ├── 03_analisis.tex        →   Sección: análisis
│   │   ├── 04_conclusiones.tex    →   Sección: conclusiones
│   │   ├── 05_referencias.tex     →   Referencias (opcional)
│   │   └── anexos.tex          →   Anexos específicos del capítulo
│   │
│   └── 📁 capitulo_2/
│       ├── capitulo_2.tex
│       └── ...
│
├── 📁 imagenes/
│   ├── 📁 cap_1/    → Imágenes del capítulo 1
│   ├── 📁 cap_2/    → Imágenes del capítulo 2
│   └── 📁 logos/    → Logos institucionales
│
├── 📁 codigos/     → Código fuente para listar
├── 📁 programa/    → Código compilable (ejecutables)
│   ├── 📁 cap_1/
│   └── 📁 cap_2/
│
├── common/
│   ├── anexos.tex        → Solo agrega \input{} de cada anexo por capítulo
│   ├── bibliografia.tex
│   └── indices.tex
│
├── config/
├── main.tex
└── referencias.bib
```

### Paso a paso

#### 1. Crea la carpeta del capítulo y su archivo principal

```
mkdir capitulos/capitulo_1
```

`capitulos/capitulo_1/capitulo_1.tex`:

```latex
% ==========================================
% CAPITULO 1 — TÍTULO DEL CAPÍTULO
% ==========================================

\chapter{Título del capítulo 1}
\label{chap:capitulo_1}

Texto introductorio del capítulo.

\input{capitulos/capitulo_1/01_marco_teorico}
\input{capitulos/capitulo_1/02_programacion}
\input{capitulos/capitulo_1/03_analisis}
\input{capitulos/capitulo_1/04_conclusiones}
\input{capitulos/capitulo_1/05_referencias}

% Los anexos se manejan en common/anexos
% \input{capitulos/capitulo_1/anexos}
```

#### 2. Agrégarlo desde `main.tex`

```latex
\input{capitulos/capitulo_1/capitulo_1}
\input{capitulos/capitulo_2/capitulo_2}
```

#### 3. Las imágenes van en `imagenes/cap_1/`, referéncialas desde cualquier archivo

```latex
\includegraphics[width=0.7\textwidth]{imagenes/cap1/diagrama.png}
```

> [!TIP]
> Las rutas de `\input{}` e `\includegraphics{}` son **relativas a main.tex**,
> no al archivo donde las escribes. Por eso las imágenes van en `imagenes/` de la raíz
> y no dentro de la carpeta del capítulo.

#### 4. Los anexos van por capítulo

Cada capítulo tiene su propio `anexos.tex` dentro de su carpeta.
Luego `common/anexos.tex` los reúne a todos:

`capitulos/capitulo_1/anexos.tex`:

```latex
% ==========================================
% ANEXOS DEL CAPÍTULO 1
% ==========================================

\chapter{Código fuente completo — Capítulo 1}
\label{anexo:cap1_codigo}

En este anexo se presenta el código completo del capítulo 1.

\IfFileExists{programa/cap1/mi_programa.c}{
  \lstinputlisting[language=C, style=mystyle,
    caption={Código completo. \propia{}},
    label={lst:cap1_codigo}]{programa/cap1/mi_programa.c}
}{
  \noindent\textbf{Nota:} El archivo aún no está disponible.
}
```

`common/anexos.tex` (solo agrega `\input{}` de cada capítulo):

```latex
\appendix
\renewcommand{\appendixname}{Anexo}
\renewcommand{\appendixtocname}{Anexos}
\addappheadtotoc
\appendixpage

\input{capitulos/capitulo_1/anexos}
\input{capitulos/capitulo_2/anexos}
```

#### 5. El código compilable va en `programa/`

Crea `programa/cap1/` con los archivos `.c`, Makefile, etc.
Así puedes compilar y ejecutar desde ahí, y referenciarlo desde
los anexos con `\lstinputlisting{programa/cap1/mi_programa.c}`.
Los fragmentos sueltos o capturas van en `codigos/`.

### Ventajas de este enfoque

- **Cada capítulo es autocontenido**: puedes copiarlo a otro proyecto entero.
- **Cada anexo vive con su capítulo**: no se mezclan, y sabes de qué capítulo viene cada anexo.
- **`main.tex` minimalista**: un `\input{}` por capítulo, sin cientos de líneas.
- **`common/anexos.tex` no se edita casi**: solo agregas un `\input{}` por capítulo nuevo.
- **Imágenes separadas por capítulo**: evitas conflictos de nombres y sabes a qué capítulo pertenece cada imagen.
- **Trabajo en equipo**: cada persona edita su carpeta sin pisar la de los demás.

## Fuente: Alegreya vs Times New Roman

La plantilla usa un selector en `config/proyecto.tex` que carga la fuente correspondiente automáticamente:

| Fuente | Característica | Ideal para |
|--------|---------------|------------|
| **Alegreya** | Serif con personalidad, Small Caps nativos, números oldstyle | Documentos con carácter, tesis, artículos |
| **Times New Roman** | Serif clásico, sobrio y profesional | Reportes técnicos, prácticas, entornos corporativos |

> [!TIP]
> Con Alegreya los títulos de sección usan **Alegreya SC** (versalitas); con Times New Roman se usa negrita estándar. Ambos se ven profesionales.


## Compilación

### Desde VS Code (recomendado)

Con LaTeX Workshop instalado, la plantilla ya incluye las recetas en `.vscode/settings.json`. Usa:

- **Compilación rápida** (xelatex simple) — para cambios rápidos
- **Compilación completa** (xelatex → biber → xelatex → xelatex) — cuando agregas o modificas citas

### Desde terminal

```bash
# Compilación rápida (sin bibliografía, una pasada de xelatex)
latexmk -pdf -outdir=build main.tex

# Receta completa (resuelve referencias cruzadas y bibliografía):
# Nota: Algunas configuraciones de latexmk solo ejecutan xelatex
# una vez, lo que deja las referencias como "??". Si pasa eso,
# usa la receta manual:

xelatex -output-directory=build main.tex
biber --output-directory build main
xelatex -output-directory=build main.tex
xelatex -output-directory=build main.tex

# Limpiar compilación
latexmk -C -outdir=build
```

## Características

- **Selector de fuente** — Cambia entre Alegreya y Times New Roman con una línea
- **XeLaTeX** — Fuentes del sistema, Unicode completo, sin problemas de codificación
- **Portada unificada** — Datos del proyecto y diseño en un solo archivo
- **Bibliografía con Biber** — Formato IEEE, orden de aparición
- **Código fuente** — Resaltado con `listings`, soporte UTF-8 para acentos
- **Índices automáticos** — Tabla de contenidos, figuras y tablas
- **Comandos útiles** — `\comillas{}`, `\codigo{}`, `\nota{}`, `\propia`
- **VS Code listo** — Recetas de compilación preconfiguradas
- **Git-friendly** — `.gitignore` que excluye build, PDFs y temporales
- **Domain-agnostic** — Sin datos personales ni referencias específicas

## FAQ

### ¿Puedo agregar otra fuente?

Sí. En `config/configuracion.tex`, agrega un nuevo `\newif` y su configuración. El patrón ya está hecho con Alegreya como ejemplo.

### ¿Cómo agrego un anexo?

Descomenta `\input{common/anexos}` en `main.tex`. Luego en
`common/anexos.tex` agrega el `\input{}` del capítulo al que
pertenece (o directamente el `\chapter{}` si es un anexo general).
Incluye ejemplos de todas las formas de adjuntar código.

### ¿Puedo tener código fuente en archivos separados?

Sí, es la forma recomendada. Crea una carpeta `codigos/` o
`programa/` y usa `\lstinputlisting` con `\IfFileExists`:

```latex
\IfFileExists{codigos/mi_archivo.c}{
  \lstinputlisting[language=C, style=mystyle,
    caption={Descripción. \propia{}},
    label={lst:etiqueta}]{codigos/mi_archivo.c}
}{
  \noindent\textbf{Nota:} El archivo aún no está disponible.
}
```

El anexo incluido en `common/anexos.tex` documenta todas las variantes.

### ¿Por qué XeLaTeX y no pdfLaTeX?

XeLaTeX permite usar cualquier fuente del sistema, maneja Unicode nativamente y es el estándar moderno. Times New Roman con `fontspec` se ve idéntico a `newtxtext`.

### Biber falla con un error críptico

Si `referencias.bib` está vacío y usas `\nocite{*}`, biber falla
con un error del tipo "No data found" o "Invalid format".
**Solución**: comenta `\nocite{*}` cuando no tengas referencias,
o agrega al menos una entrada real en `referencias.bib`.

### latexmk deja referencias como "??"

Algunas configuraciones de `latexmk -pdf` solo ejecutan xelatex
una vez. Si ves "??" en lugar de números de capítulo o figura,
usa la receta manual completa (xelatex → biber → xelatex → xelatex)
descrita en la sección de compilación.

### No encuentro la fuente Alegreya

En TeX Live: `sudo tlmgr install alegreya`. También puedes descargarla de [Google Fonts](https://fonts.google.com/specimen/Alegreya) e instalarla en tu sistema.
