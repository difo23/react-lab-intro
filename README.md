# Laboratorio Intro a React: Agregar React a un sitio web

### Que es React?

React Una biblioteca de JavaScript para construir interfaces de usuario. (Construida por Facebook)

### ¿Cuánto gana un React Developer?

Actualizado el 1 de nov. de 2021
Confianza muy alta

- El sueldo promedio nacional para el puesto de React Developer es $34,083 por mes en México. 
- El sueldo promedio de React Developer es CAD 69.235 por año en Montreal, área Canadá. Las estimaciones de sueldos se basan en 8 sueldos enviados anónimamente a Glassdoor por empleados con el cargo de React Developer en Montreal, área Canadá.
- El sueldo promedio de React Developer es US$ 65.245 por año en New York, NY. Las estimaciones de sueldos se basan en 12 sueldos enviados anónimamente a Glassdoor por empleados con el cargo de React Developer en New York, NY.

Pagina oficial de [React en Español](https://es.reactjs.org/). 

### Github starts vs otras tecnologias

![Vue Vs. Angular Vs. React: The Comparison of JS Frameworks in 2021](https://theappsolutions.com/images/articles/source/vue-vs-angular-vs-react/img-1.png)

### Utiliza sólo lo que necesites de React.

React fue diseñado desde el principio para que se pudiera adoptar de forma gradual, y **puedas utilizar sólo las cosas que necesites de React**. Quizás solo quieras agregar una “pizca de interactividad” a una página existente. Los componentes de React son una gran manera de hacer eso.

La mayoría de sitios web no son, y no necesitan ser, aplicaciones de una sóla página. Con **unas pocas líneas de código y sin herramientas de compilación**, puedes probar React en lugares pequeños de tu sitio web. Y de allí puedes expandir su presencia de forma gradual, o mantenerlo contenido a unos pocos en unos widgets dinámicos.

------

## Agrega React en un minuto

En esta sección, vamos a mostrarte como agregar un componente de React a una página HTML existente. Puedes seguir los pasos en tu sitio web, o crear un nuevo archivo HTML para practicar.

No habrá necesidad de usar herramientas complicadas u otros requerimientos para instalar — **para completar esta sección, sólo necesitas de una conexión a internet y un minuto de tu tiempo.**

Opcional: [Descargar el ejemplo completo (2KB comprimido)](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/f6c882b6ae18bde42dcf6fdb751aae93495a2275.zip)

### Paso 0: Organiza tu proyecto

Crea una carpeta `intro_react_cdn` ( para practicar hazlo por la terminal - Asegurarte de estar en la carpeta correcta con `pwd`)

```bash
cd ./Documentos/code
mkdir intro_react_cdn
cd ./intro_react_cdn
```

Agrega `git` a tu repo:

```bash
git init
```

Agrega tu  repo a `github`:

```bash
gh create repo
```

Sigue los pasos de practicas anteriores y automáticamente tendrás tu remoto agregado.

Agrega tus archivos base para el proyecto:

```bash
touch README.md
touch index.html
touch like_button.js
```

Agrega contenido a tu `README.md` una pequeña descripción sobre el proyecto o practica que vas hacer, en nuestro caso `Introduccion a React JS libreria mas popular para FrontEnd`.

Crea tu primer `commit`:

```bash
git add .
git commit -m "Feat: First commit setup project"
```

Enlaza tu rama main local con tu rama main remota:

```bash
git push -u oringin main
```

Listo! Ahora podemos continuar con nuestro laboratorio como todo un profesional.



### Paso 1: Agrega un contenedor del DOM al HTML

(Recuerda hacer commit con este paso)

Para iniciar, abre la página HTML que deseas editar. Agrega una etiqueta `<div>` vacía para marcar el lugar donde deseas visualizar algo con React. Por ejemplo:

```html
<!-- ... HTML existente dentro del body ... -->

<div id="like_button_container">
 	<!-- ... React trabaja dentro de un div vacio ... -->
</div>


<!-- ... HTML existente ... -->
```

A este `<div>` le agregamos un atributo HTML `id` que es único. Esto nos permitirá encontrarlo desde el código `Javascript` más adelante y visualizar un componente de React adentro de este.

> **Consejo**: Puedes agregar un “contenedor” `<div>` como este en **cualquier sitio** dentro de la etiqueta `<body>`. Puedes tener la cantidad de contenedores independientes en el DOM que desees. Por lo general éstos están vacíos — React reemplazará cualquier contenido existente dentro de los contenedores del DOM.

### Paso 2: Agrega las etiquetas de script

(Recuerda hacer commit con este paso)

Lo siguiente es agregar tres etiquetas `<script>` a la página HTML justo antes de cerrar la etiqueta `</body>`:

```html
<!-- ... debajo del div anterior, más HTML, justo al final antes del cierre del body ... -->

  <!-- Cargar React. -->
  <!-- Nota: cuando se despliegue, reemplazar "development.js" con "production.min.js". -->
  <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>

  <!-- Cargamos nuestro componente de React. -->
  <script src="like_button.js"></script>

</body>
```

Las primeras dos etiquetas cargan **React**. La tercera carga tu código del componente.

### Paso 3: Crea un componente de React 

(Recuerda hacer commit con este paso)

Crea un archivo llamado `like_button.js` en el mismo lugar donde tienes tu archivo HTML.

Abre **[este código inicial](https://gist.github.com/gaearon/0b180827c190fe4fd98b4c7f570ea4a8/raw/b9157ce933c79a4559d2aa9ff3372668cce48de7/LikeButton.js)** y pégalo en el archivo que acabaste de crear.

```js
// Archivo like_button.js junto con tu HTML
'use strict';

const e = React.createElement;

class LikeButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = { liked: false };
  }

  render() {
    if (this.state.liked) {
      return 'You liked this.';
    }

    return e(
      'button',
      { onClick: () => this.setState({ liked: true }) },
      'Like'
    );
  }
}
```



> Consejo
>
> Este código define un componente de React llamado `LikeButton`. No te preocupes si aún no lo entiendes — vamos a cubrir los elementos básicos de React luego en nuestro [tutorial práctico](https://es.reactjs.org/tutorial/tutorial.html) y [guía de conceptos principal](https://es.reactjs.org/docs/hello-world.html). Por ahora, ¡vamos a hacer que se muestre en la pantalla!

Después **[en el código inicial](https://gist.github.com/gaearon/0b180827c190fe4fd98b4c7f570ea4a8/raw/b9157ce933c79a4559d2aa9ff3372668cce48de7/LikeButton.js)**, agrega las siguientes dos lineas al final de `like_button.js`:

```js
// ... el código inicial que pegaste ...

const domContainer = document.querySelector('#like_button_container');
ReactDOM.render(e(LikeButton), domContainer);
```

Estas dos líneas de código encuentran el `<div>` que agregamos en nuestro HTML en el primer paso y muestran el componente de React para nuestro botón de “Like” dentro del mismo.

### Final: ¡Eso es todo! Sube el enlace a tu proyecto en GitHub como evidencia

Comprueba que tu código sea similar al ejemplo. Ejecuta tu `index.html` en el `live server` y Corrija errores que pueda ocurrir en la programación.  Cuando todo este funcionando ejecuta tu ultimo commit:

```bash
git commit -am "End intro to React from facebook"
git push 
```



No hay un cuarto paso. **Ya agregaste tu primer componente de React a tu sitio web.**

Dale un vistazo a las siguientes secciones para más consejos sobre como integrar React.

**[Mira el código fuente del ejemplo completo](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605)**

**[Descargar el ejemplo completo (2KB comprimido)](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/f6c882b6ae18bde42dcf6fdb751aae93495a2275.zip)**

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Add React in One Minute</title>
  </head>
  <body>

    <h2>Add React in One Minute</h2>
    <p>This page demonstrates using React with no build tooling.</p>
    <p>React is loaded as a script tag.</p>

    <!-- We will put our React component inside this div. -->
    <div id="like_button_container"></div>

    <!-- Load React. -->
    <!-- Note: when deploying, replace "development.js" with "production.min.js". -->
    <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>

    <!-- Load our React component. -->
    <script src="like_button.js"></script>

  </body>
</html>
```

```js
/* like_button.js */
'use strict';

const e = React.createElement;

class LikeButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = { liked: false };
  }

  render() {
    if (this.state.liked) {
      return 'You liked this.';
    }

    return e(
      'button',
      { onClick: () => this.setState({ liked: true }) },
      'Like'
    );
  }
}

const domContainer = document.querySelector('#like_button_container');
ReactDOM.render(e(LikeButton), domContainer);
```



