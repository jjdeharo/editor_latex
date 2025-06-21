# Editor $\LaTeX$ online

## Descripción

Este proyecto es una herramienta gratuita pensada para que docentes puedan crear y editar fórmulas matemáticas fácilmente, sin necesidad de conocer a fondo el lenguaje LaTeX. Permite generar materiales educativos con notación matemática clara, profesional y bien presentada. Se puede utilizar en programas que admitan LaTeX como eXeLearning, Moodle, etc.
.

## 1. index.html → El editor de fórmulas


### Para qué sirve

* Escribir fórmulas fácilmente usando un menú visual de botones con símbolos matemáticos y estructuras comunes (fracciones, raíces, sumatorios, matrices, etc.).
* Ver en tiempo real cómo queda la fórmula, gracias a MathJax, sin necesidad de compilar.
* Copiar el código LaTeX ya listo para pegarlo en documentos, Moodle, Overleaf u otros entornos.
* Exportar la fórmula como imagen PNG para usar en presentaciones, apuntes, webs, etc.
* Buscar comandos por nombre o por código (por ejemplo, “raíz” o `\sqrt`).
* Cargar **menús personalizados** de fórmulas desde archivos locales o desde URLs externas.
* Acceder rápidamente a los últimos comandos usados desde una pestaña de "Recientes".

### Cómo se usa

1. Escribe o selecciona una fórmula usando los botones.
2. Visualiza el resultado al instante.
3. Copia el código o descarga la imagen.

---

## 2. editor_menu.html → Editor del menú del _Editor LaTeX online_ para crear menús personalizados

Este programa es un **editor visual de menús de fórmulas LaTeX**. Permite crear, editar, organizar y exportar colecciones de botones que insertan fórmulas matemáticas en LaTeX, todo de manera visual y sin necesidad de escribir código a mano.

### Para qué sirve

* Crear categorías de botones que contienen fórmulas LaTeX.
* Editar y reorganizar las fórmulas con solo arrastrar y soltar.
* Copiar el resultado como archivo JSON estructurado para integrarlo en otros editores.
* Exportar el archivo completo para su uso en proyectos compatibles.
* Cargar fácilmente archivos `.json` alojados en GitHub, pegarlos desde el portapapeles o subirlos deste tu dispositivo.
* Usar un asistente con inteligencia artificial que genera automáticamente categorías, elementos o archivos JSON completos con fórmulas.

### Cómo se usa

1. Añade una categoría o carga un archivo de ejemplo.
2. Dentro de cada categoría, añade elementos con su código LaTeX.
3. Previsualiza cómo se verán los botones.
4. Copia o exporta el archivo JSON generado para integrarlo en tu editor LaTeX. Puedes cargarlo desde tu ordenador o si lo colocas en Internet (por ejemplo en un repositorio de GitHub, usando el acceso raw) podrás escribir su dirección.


---

## Archivos de menús de fórmulas

Los archivos de menús están en formato JSON y definen colecciones de botones con fórmulas LaTeX organizadas por categorías. Estos archivos pueden ser cargados por el editor de menús (`editor_menu.html`) o por el editor de fórmulas (`index.html`).

Permiten al usuario trabajar con expresiones matemáticas sin necesidad de memorizar la sintaxis LaTeX, seleccionándolas directamente desde menús visuales.

## Archivo base

El archivo `formulas.json` actúa como menú base. Se carga siempre por defecto al iniciar el editor, y contiene una selección general de fórmulas organizadas por temas. A partir de este archivo se puede ampliar o modificar el contenido utilizando el editor visual.

## Estructura general de los archivos

Cada archivo contiene un objeto con una única propiedad `categorias`, que es una lista de categorías temáticas. Cada categoría incluye un conjunto de botones que representan fórmulas.

```json
{
  "categorias": [
    {
      "nombre": "string",
      "id": "string",
      "grid_template_columns": "string",
      "isCollapsed": false,
      "elementos": [
        {
          "type": "button",
          "latex": "string",
          "display": "string",
          "title": "string"
        }
      ]
    }
  ]
}
```

Hay un elemento especial con la propiedad `type: custom_matrix` que actualmente se encuentra en la categoría "matrices" de `formulas.json` que hace que el programa despliegue una serie de campos para crear matrices personalizadas, tanto en el número de filas y de columnas como de su contenido. 

### Descripción de los campos

* `categorias`: Lista de categorías temáticas (por ejemplo, fracciones, límites, álgebra...).

  * `nombre`: Nombre visible de la categoría.
  * `id`: Identificador único de la categoría (en minúsculas y sin espacios).
  * `grid_template_columns`: Valor CSS para organizar la rejilla de botones.
  * `isCollapsed`: Si es `false`, la categoría se muestra desplegada; si es `true`, aparece plegada al cargar.
  * `elementos`: Lista de botones de la categoría.

    * `type`: Siempre `"button"`.
    * `latex`: Código LaTeX que se insertará al hacer clic.
    * `display`: Fórmula que se muestra en el botón (puede coincidir con `latex`).
    * `title`: Descripción breve de la fórmula.

## Ubicación de los archivos

Los archivos de menús adicionales están ubicados en la carpeta `docs`. Pueden cargarse desde el editor visual o utilizarse directamente mediante URL para integrarlos en otros proyectos o editores personalizados.


## Licencia

Este proyecto tiene licencia Creative Commons BY-SA. Puedes usarlo, modificarlo y compartirlo libremente, siempre que cites al autor y mantengas la misma licencia en tus versiones.

---

**Autor**: Juan José de Haro
[https://bilateria.org](https://bilateria.org)
