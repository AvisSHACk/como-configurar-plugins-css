# como-configurar-plugins de postcss en gulp
Aqui indico como configurar los plugins de post css----Es que luego me olvido xd

## UNCSS
Uncss es un plugin de postcss que permite quitar las clases que no usas en tu projecto, es decir en el .html, esto viene bien cuando por ejemplo trabajas con font-awesome donde te traen como 500 iconos cuando solo usaras unos cuantos

En la consola o terminal ejecutamos los comandos 

```
npm install --save--dev gulp gulp-postcss postcss-uncss uncss
```

Bien, con esto se habran instalado las dependencias en la carpeta node_modules
Ahora en el archivo gulpfile.js (Necesario para ejecutar gulp) colocaras esto, pasaremos a explicarlo

```js
const gulp = require('gulp');
const postcss = require('gulp-postcss');
const uncss = require('postcss-uncss');

gulp.task('default', function () {
    var plugins = [
        uncss({html: ['index.html']})
    ];
    return gulp.src('./css/*.css')
        .pipe(postcss(plugins))
        .pipe(gulp.dest('./dest'));
});
```

## Explicando paso a paso

- **Declaracion de variables** (gulp, postcss, uncss): Aqui cargamos las dependencias que necesitaremos
- **Tarea** (default): Configuramos la tarea que sera la que ejecute uncss
- **Variable dentro de la tarea** (plugins): Contendra los plugins, en este caso unscss
  ```js
      var plugins = [
          uncss({html: ['index.html']})
      ];
  ```
    ejecutamos la variable uncss donde pasamos como parametro `{html: ['index.html']}`.
    Aqui señalamos que archivo o archivos seran los que analizara las clases
- **return**: indicamos que archivo con extension .css analizara o comparara las clases con las de el earchivo HTML luego ejecutamos la funcion pipe pasando como parametro `postcss(plugins)` donde plugins es la variable que creamos lineas mas arriba y al final pondra el archivo devuelto en la carpeta dest
