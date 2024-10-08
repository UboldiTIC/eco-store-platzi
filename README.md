## Curso de Platzi - Fundamentos de Sass: Crea tu Primera Landing Page
Prof. Ana María Díaz Solorio

Este sitio fue desarrollado siguiendo los ejercicios del curso. No es un sitio responsive y tiene algunos inconvenientes en el tratamiento de las imágenes. Mejorar esos aspectos no formaba parte de los contenidos del curso, por ese motivo se dicidió dejarlo así. El objetivo del curso es comprender las ventajas de SASS y lograr el desarrollo de los estilos utilizando esa tecnología.

[Curso en Platzi](https://platzi.com/cursos/sass/)

# Qué es SASS

SASS (Syntactically Awesome Style Sheets) es un **preprocesador de CSS** que se utiliza para trabajar los estilos de tu proyecto agregandoo funcionalidades con las que no cuenta CSS. Está basado en Ruby.

## El proceso de Compilado

Para hacer uso de Sass dentro de nuestro proyecto tenemos que tener en cuenta 3 puntos importantes que forman parte del proceso de compilación.

* Input file (.scss) - donde vamos a escribir nuestros estilos usando la sintaxis de Sass.
* Output file (.css) - No se debe editar.
* Los comandos para ejecutar y compilar Sass.

### Tipos de instalación de SASS

* Instalación global en el S.O.
* Haciendo uso de Node js
* Dart Sass
* Javascript API

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

## La herencia

La herencia es un mecanismo mediante el cual un selector puede recibir estilos CSS que vienen de variables utilizadas previamente.

**¿Cómo se usa la herencia dentro de SASS?** 

Se usa con la directiva **@extend** de SASS que nos permite organizar código y crear CSS más limpio. 

~~~
.error {
        border: 1px;
        background-color: #fdd;

        &--serious {
                @extend .error; (trae todos los estilos de la clase .error y permite agregar nuevos abajo)
                border-width: 3px;
}
~~~

## Mixin

Los mixins permiten definir estilos que se pueden reutilizar en toda su hoja de estilos y facilitan evitar el uso de clases no semánticas.

**Uso de mixins en Sass**

Se declara con la regla **@mixin** seguido del nombre que queremos asignar y se invoca con **@include** seguido del nombre del mixin.

~~~
@mixin horizontal-list {
   li {
       display: inline-block;
       margin: {
          left: -2px;
          right: 2em;
        }
     }
}

//lo invocamos con:
nav ul {
   @include horizontal-list;
}       
~~~

**Mixins más complejos - Reciben argumentos**

* Un argumento es el nombre de una variallbe que está separada por una coma.
* La utilidad de los mixins no sería tal si no tuvieran la capacidad de recibir argumentos.

~~~
@mixin circle2 ($width,$height,$color) {
        width: $width;
        height: $height;
        background: $color;
}
~~~

## Funciones

Las funciones permite definir operaciones complejas en valores de Sass. 

Las funciones se definen usando la regla **@function**

Sass como preprocesador tiene una gran cantidad de funciones. Algunos de los ejemplos son:
* Funciones RGB
* Funciones HSL
* Funciones de opacidad
* Funciones sobre strings
* Funciones sobre números

Sass es compatible con una gran cantidad de operadores útiles para trabajar con diferentes valores. Estos incluyen los operadores matemáticos estándar y operadores para varios otros tipos, por ejemplo: **==** y **!=**.

**Jerarquía de operaciones**

1. Los operadores unarios **(not + -)**
2. **(* / %)**
3. (+ -)
4. (> >= < <=)
5. Operadores de comparación (== !=)
6. Operadores lógicos (and or)
7. El operador de asignación (=)

**Cómo se implementan las funciones**

Las funciones se llaman utilizando la sintaxis de función CSS normal.
~~~
@function pow($base, $exponent) {
   $result: 1;
   @for $_ from 1 through $exponent {
      $result: $result * $base;
   }
   @return $result;
}

.sidebar {
   float: left;
   margin-left: pow(4, 3) * 1px;
}
~~~

## Aprende a instalar y configurar Sass mediante Node.js

### Instrucciones para instalar y configurar Sass mediante Node.js

1. Abre una terminal y navega hasta la carpeta raíz de tu proyecto.

Asegúrate de tener Node.js instalado en tu sistema. Puedes verificarlo escribiendo node -v en la terminal. Si no lo tienes instalado, ve al [sitio web oficial](https://nodejs.org/en) de Node.js para descargarlo e instalarlo.

2. Ejecuta el siguiente comando para instalar Sass a nivel global:
~~~   
npm install -g sass
~~~

3. Ahora que tienes Sass instalado a nivel global, puedes compilar tus archivos Sass en CSS con el siguiente comando en la terminal:
~~~
sass input.scss output.css
~~~

4. Reemplaza “input.scss” con la ruta y el nombre de tu archivo Sass, y “output.css” con la ruta y el nombre de tu archivo CSS de salida. Por ejemplo:
~~~
sass styles/main.scss styles/main.css
~~~

5. Si quieres compilar automáticamente tus archivos Sass en CSS cada vez que hagas cambios, puedes usar la opción --watch:
~~~
sass --watch input.scss:output.css
~~~

6. Si estás utilizando Node.js en tu proyecto, también puedes usar un paquete de npm llamado sass para compilar tus archivos Sass en CSS. Para instalarlo, ejecuta el siguiente comando:
~~~
npm install sass
~~~

7. En tu archivo de configuración de Node.js (como package.json) agrega un script para compilar tus archivos Sass en CSS. Por ejemplo:
~~~
"scripts": {
  "build:css": "sass input.scss output.css"
}
~~~
8. Ahora puedes ejecutar el script con el siguiente comando:
~~~
npm run build:css
~~~

*Apuntes de clase: [Solmar Andrés Uboldi](https://www.linkedin.com/in/solmar-uboldi/)