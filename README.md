## Curso de Fundamentos de Sass: Crea tu Primera Landing Page
Prof. Ana María Díaz Solorio

[Curso en Platzi](https://platzi.com/cursos/sass/)


## El proceso de Compilado

Para hacer uso de Sass dentro de nuestro proyecto tenemos que tener en cuenta 3 puntos importantes que forman parte del proceso de compilación.

* Input file (.scss) - donde vamos a escribir nuestros estilos usando la sintaxis de Sass.
* Output file (.css) - No se debe editar.
* Los comandos para ejecutar y compilar Sass.

**Para complilar Sass usaremos:**

Live Sass Compiler es una extensión de VSCode que nos permitirá trabajar con Sass de forma simple, además de compilar nuestros estilos en tiempo real sin la necesidad de ejecutar los comandos manualmente.

En VSCode estensiones buscamos:

* Sass - Idented Sass syntax Highlighthing, Autocomplete & For...
* Live Sass Compiler - Glenn Marks
* Live Server - Ritwick Dey

Una vez instaladas las extensiones debemos verificar en Settings -> buscamos "sass format" y entramos en "Live Sass Compile > Settings: Formats" y ahí verificamos:
~~~
        {
            "format": "expanded",
            "extensionName": ".css",
            "savePath": "/css",
        }
~~~
Corremos el servidor con "ctrl + shift + p" buscamos Live Sass: Watch Sass y damos enter.

## Estructura de la hoja de estilos

Algunos ***statements*** contienen bloques y se definen entre un par de llaves **{}**, son separados mediante punto y coma **;**

### Cómo se organizan:

* Top-level statements (van al comienzo de la hoja de estilos)
    - Imports
    - Definición de un Mixin
    - Definición de una Función
    - Módulos

* Universal statements (se pueden utilizar en cualquier parte de la hoja de estilos)
    - Variables, estructuras de control y las reglas @error, @warm y @debug.
    - Declaraciones CSS: Reglas de estilo, At-rules y Mixins.

### Variables

Se pueden declarar en cualquier parte de la hoja de estilos y comienzan con **$**:

~~~
$primary-color: blue;
~~~

