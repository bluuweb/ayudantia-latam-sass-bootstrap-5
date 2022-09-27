# Ayudantía LATAM Sass con Bootstrap 5.

- [preview práctica](https://teal-frangipane-5bb524.netlify.app/)

## Instalación
```sh
npm init -y
npm i -D sass
npm i bootstrap
```

.gitignore
```
node_modules
```

package.json
```json{6-8,12-17}
{
  "name": "sa-sa",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "dev": "sass --watch sass/custom.scss css/main.css"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "sass": "^1.55.0"
  },
  "dependencies": {
    "bootstrap": "^5.2.1"
  }
}
```

index.html
```html
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Sass ayudantía</title>
        <link rel="stylesheet" href="css/main.css" />
    </head>
    <body>
        <h1 class="text-center">Center?</h1>
    </body>
</html>
```

custom.scss
```scss
@import "../node_modules/bootstrap/scss/bootstrap";
```

## Fuentes
- [fonts.google.com](https://fonts.google.com/)

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
    href="https://fonts.googleapis.com/css2?family=Lato:wght@100;300;400;700;900&display=swap"
    rel="stylesheet"
/>

<link rel="stylesheet" href="css/main.css" />
```

custom.scss
```scss
$font-family-base: 'Lato', sans-serif;

@import "../node_modules/bootstrap/scss/bootstrap";
```

## Custom colors
```scss

// 1. Include functions first (so you can manipulate colors, SVGs, calc, etc)
@import "../node_modules/bootstrap/scss/functions";

// 2. Include any default variable overrides here
$font-family-base: 'Lato', sans-serif;

// 3. Include remainder of required Bootstrap stylesheets
@import "../node_modules/bootstrap/scss/variables";

// 4. Include any default map overrides here
// Create your own map
$custom-colors: (
  "rojo": #900,
  "primary": $indigo-800
);

// Merge the maps
$theme-colors: map-merge($theme-colors, $custom-colors);

// 5. Include remainder of required parts
@import "../node_modules/bootstrap/scss/maps";
@import "../node_modules/bootstrap/scss/mixins";
@import "../node_modules/bootstrap/scss/root";

// 6. Optionally include any other parts as needed
@import "../node_modules/bootstrap/scss/utilities";
@import "../node_modules/bootstrap/scss/reboot";
@import "../node_modules/bootstrap/scss/type";
@import "../node_modules/bootstrap/scss/images";
@import "../node_modules/bootstrap/scss/containers";
@import "../node_modules/bootstrap/scss/grid";
@import "../node_modules/bootstrap/scss/helpers";

// components
// Layout & components
@import "../node_modules/bootstrap/scss/tables";
@import "../node_modules/bootstrap/scss/buttons";
@import "../node_modules/bootstrap/scss/transitions";
@import "../node_modules/bootstrap/scss/dropdown";
@import "../node_modules/bootstrap/scss/button-group";
@import "../node_modules/bootstrap/scss/nav";
@import "../node_modules/bootstrap/scss/navbar";
@import "../node_modules/bootstrap/scss/card";
@import "../node_modules/bootstrap/scss/accordion";
@import "../node_modules/bootstrap/scss/breadcrumb";
@import "../node_modules/bootstrap/scss/pagination";
@import "../node_modules/bootstrap/scss/badge";
@import "../node_modules/bootstrap/scss/alert";
@import "../node_modules/bootstrap/scss/progress";
@import "../node_modules/bootstrap/scss/list-group";
@import "../node_modules/bootstrap/scss/close";
@import "../node_modules/bootstrap/scss/toasts";
@import "../node_modules/bootstrap/scss/modal";
@import "../node_modules/bootstrap/scss/tooltip";
@import "../node_modules/bootstrap/scss/popover";
@import "../node_modules/bootstrap/scss/carousel";
@import "../node_modules/bootstrap/scss/spinners";
@import "../node_modules/bootstrap/scss/offcanvas";
@import "../node_modules/bootstrap/scss/placeholders";

// 7. Optionally include utilities API last to generate classes based on the Sass map in `_utilities.scss`
@import "../node_modules/bootstrap/scss/utilities/api";

// 8. Add additional custom code here
```

## Navbar

Alinear verticalmente con icono:
```html
<a class="navbar-brand" href="#">
    <img
        src="img/icons/react.svg"
        alt="Bootstrap"
        width="30"
        height="24"
    />
    Navbar
</a>
```

```scss
// 8. Add additional custom code here
.navbar-brand {
  @extend .d-flex;
  @extend .align-items-center;
}
```

Cambiar icono hamburguer:
```scss
// 2. Include any default variable overrides here
$font-family-base: 'Lato', sans-serif;
$navbar-dark-toggler-icon-bg: url('../img/icons/burger-solid.svg');
$navbar-dark-toggler-border-color: transparent;
```

## header
```html
<header class="bg-header-img">
    <h1 class="text-white display-1 mb-5">Lorem ipsum dolor sit.</h1>
    <div class="d-flex gap-2">
        <button class="btn btn-outline-light">
            Mas información
        </button>
        <button class="btn btn-secondary">Comprar</button>
    </div>
</header>
```

```scss
// 4. Include any default map overrides here
$custom-colors: (
  "rojo": #900,
  "primary": $indigo-800,
  "secondary": $indigo-400
);
```

```scss
// 8. Add additional custom code here
.bg-header-img {
  background-image: url('../img/bg-hero.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: calc(100vh - 56px);
  @extend .d-flex;
  @extend .flex-column;
  @extend .align-items-center;
  @extend .justify-content-center;
}
```

## main
```html
<section class="grid-col-2 mb-5">
    <article class="card">
        <img src="img/montain-1.jpg" alt="" class="card-img-top" />
        <div class="card-body">
            <h5 class="card-text">Lorem ipsum dolor sit.</h5>
        </div>
    </article>
    <article class="card">
        <img src="img/montain-2.jpg" alt="" class="card-img-top" />
        <div class="card-body">
            <h5 class="card-text">Lorem ipsum dolor sit.</h5>
        </div>
    </article>
</section>
```

```scss
.grid-col-2 {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1rem;
}

@media (min-width: 576px){
  .grid-col-2 {
    grid-template-columns: repeat(2, 1fr);
  }
}
```

[Con mixins Bootstrap:](https://getbootstrap.com/docs/5.2/layout/breakpoints/#min-width)
```scss
@include media-breakpoint-up(sm) {
  .grid-col-2 {
    grid-template-columns: repeat(2, 1fr);
  }
}
```

## gallery
```html
<section class="gallery mb-5 container">
    <article class="photo">
        <img src="img/1.jpg" alt="" class="photo-img" />
        <div class="photo-body">
            <h2 class="lead">Lorem</h2>
        </div>
    </article>
    <article class="photo">
        <img src="img/2.jpg" alt="" class="photo-img" />
        <div class="photo-body">
            <h2 class="lead">Lorem</h2>
        </div>
    </article>
    <article class="photo">
        <img src="img/1.jpg" alt="" class="photo-img" />
        <div class="photo-body">
            <h2 class="lead">Lorem</h2>
        </div>
    </article>
    <article class="photo">
        <img src="img/2.jpg" alt="" class="photo-img" />
        <div class="photo-body">
            <h2 class="lead">Lorem</h2>
        </div>
    </article>
</section>
```

```scss
.photo {
  position: relative;
  
  &:hover {
    cursor: pointer;
  }
  
  .photo-img {
    transition: all 0.5s ease-out;
    width: 100%;
  }

  .photo-body {
    transition: all 0.5s ease-out;
    position: absolute;
    bottom: 0;
    left: 0;
    padding: 2rem;
    background-color: rgba(0, 0, 0, 0.5);
    color: $white;
    width: 100%;
    text-align: center;
    opacity: 0;
  }

  &:hover > .photo-img {
    transform: scale(1.1);
  }

  &:hover > .photo-body {
    opacity: 1;
  }

}
```

con ``&`` 100%:
```scss
.photo {
  position: relative;
  
  &:hover {
    cursor: pointer;
  }
  
  &-img {
    transition: all 0.5s ease-out;
    width: 100%;
  }

  &-body {
    transition: all 0.5s ease-out;
    position: absolute;
    bottom: 0;
    left: 0;
    padding: 2rem;
    background-color: rgba(0, 0, 0, 0.5);
    color: $white;
    width: 100%;
    text-align: center;
    opacity: 0;
  }

  &:hover > &-img {
    transform: scale(1.1);
  }

  &:hover > &-body {
    opacity: 1;
  }

}
```

## Optimización
```scss
// components
// Layout & components
// @import "../node_modules/bootstrap/scss/tables";
@import "../node_modules/bootstrap/scss/buttons";
@import "../node_modules/bootstrap/scss/transitions";
@import "../node_modules/bootstrap/scss/dropdown";
// @import "../node_modules/bootstrap/scss/button-group";
@import "../node_modules/bootstrap/scss/nav";
@import "../node_modules/bootstrap/scss/navbar";
@import "../node_modules/bootstrap/scss/card";
// @import "../node_modules/bootstrap/scss/accordion";
// @import "../node_modules/bootstrap/scss/breadcrumb";
// @import "../node_modules/bootstrap/scss/pagination";
// @import "../node_modules/bootstrap/scss/badge";
// @import "../node_modules/bootstrap/scss/alert";
// @import "../node_modules/bootstrap/scss/progress";
// @import "../node_modules/bootstrap/scss/list-group";
// @import "../node_modules/bootstrap/scss/close";
// @import "../node_modules/bootstrap/scss/toasts";
// @import "../node_modules/bootstrap/scss/modal";
// @import "../node_modules/bootstrap/scss/tooltip";
// @import "../node_modules/bootstrap/scss/popover";
// @import "../node_modules/bootstrap/scss/carousel";
// @import "../node_modules/bootstrap/scss/spinners";
// @import "../node_modules/bootstrap/scss/offcanvas";
// @import "../node_modules/bootstrap/scss/placeholders";

// 7. Optionally include utilities API last to generate classes based on the Sass map in `_utilities.scss`
@import "../node_modules/bootstrap/scss/utilities/api";
```

## Minificar css
```json
"scripts": {
    "dev": "sass --watch sass/custom.scss css/main.css --style=expanded",
    "build": "sass sass/custom.scss css/main.css --style=compressed"
},
```

