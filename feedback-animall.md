# FeedBack Animall.

## Recomendaciones generales:

### Cierre de etiquetas
Cerrar las etiquetas que contengan otras etiquetas adentro. Esto ustedes lo están haciendo bien

### Acceso a rutas
Cualquier acceso a ruta, para que no tenga problemas al momento de subirse a un servidor, y no tenga problemas con otras carpetas, debe hacerse así 

```html
<a href="carpeta/archivo.html"></a>
```
Es igual que con las imágenes, esto se llama "ruta relativa" en lugar de la ruta absoluta.

Hay que hacer este cambio donde sea que se utilice una ruta. Esto ustedes lo están haciendo bien, **pero** hay un par de casos donde usan una nomenclatura que no existe

```html
<li class="l"><a href="/Changes/cuenta.html">Cuenta</a></li>
```
Esta carpeta no existe en la rama main/master, por lo que no se puede acceder a ella.

### Nombres de archivos
index significa índice, el índice de una página es la página de inicio, que nos lleva al resto de las páginas.
En otras palabras, sólo la página de inicio debe llamarse index, el resto deben tener nombres representativos de lo que se verá en la página, como "catalogo.html" o "login.html"

**index2.html** no es un nombre adecuado para un archivo. Tampoco lo es **style2.css**

Para el caso de las imágenes, ustedes cumplen con esto de manera correcta, pero para los archivos html, css y js, no del todo.

**Nota:**
Los archivos sólo deben contener puntos para denotar el tipo de archivo

* index.html
* readme.md
* estilos.css

Los nombres de archivos y carpetas no deben contener puntos entre medio del nombre.

## Modificaciones importantes:

### Uso de flexbox y grid
El uso de flexbox ayuda mucho, pero cuando usas margenes en conjunto con flexbox pueden haber errores, la idea es tener una estructura más o menos así:
![alt text](https://www.freecodecamp.org/news/content/images/2022/05/CSS-GRID-3.png)
Donde las columnas y las filas pueden tener otras columnas y filas dentro. **Por supuesto que puede variar dependiendo de su diseño.**

Tienen muchos casos en donde no utilizan flexbox y donde todo su código se facilitaría mucho si lo utilizaran. **Principalmente en la barra de navegación donde todos sus elementos están posicionados absolutamente.**
```css
.animall{
        position: absolute;
        margin-left: 150px;
        margin-top: -10px;
}
.lupa{
        position: absolute;
        margin-left: 908px;
        margin-top: 68px;
}
.carrito{
    position: absolute;
    left: 980px;
    top: 68px;
}
```
Son algunos ejemplos donde se podría utilizar flexbox en lugar de posición absoluta.
Si se fijan bien **el logo, el slogan, la barra de busqueda y el carito** son parte de la misma fila, por lo que deberían estar dentro de un contenedor que tenga display flex.

Los siguientes bloques de código son un buen punto de partida. **Nótese que realicé otras modificaciones que también son relevantes, como eliminar tags y lineas innecesarias**
```css
.container-logo-otros{
    position: absolute;
    top: 0;
    display: flex;
}
```
```html
<img class="tronco" src="MenuPrincipalIGM/tronco.png">
<div class="container-logo-otros">
    <img src="MenuPrincipalIGM/logo.png" alt="">
    <img src="MenuPrincipalIGM/animall.png">
    <input class="buscador">
    <img class="lupa" src="MenuPrincipalIGM/lupa.png">
</div>
```
**Falta (To Do)**
* Arreglar el tamaño del logo, el slogan y la lupa, estos si pueden ser valores fijos en términos de tamaño (px).
* Pasa algo parecido con los elementos de la barra de navegación y con el input del buscador que tampoco se está posicionando correctamente.


### Uso de padding, margin y tamaños de objetos
**Esto es una solicitud especial de parte de ustedes para solucionar el tamaño del tronco de la barra de navegación**

Por defecto, es buena práctida predeterminar el padding y el margin de todos los elementos a 0, para que no haya problemas con el tamaño  y la ubicación de los elementos.
**Esto se hace así:**
```css
*{
    margin: 0;
    padding: 0;
}
```
Hay ciertos elementos que están afectando con los márgenes del tronco, por eso es que ustedes estimaron necesario ponerle márgenes negativos. **Esto no es una buena práctica, pero hay casos donde es necesario.**

```css
.tronco{
        width: 1368px;
        margin-top: -300px; /*Esto lo mantenemos porque es necesario para el funcionamiento de su código*/
        margin-left: -20px; /*Esta parte sobra*/
}
```
Al predeterminar todos los margenes a 0 y eliminar el margen izquierdo de su tronco, el tronco se posiciona correctamente en la esquina superior izquierda.

**Lo otro que los aproblemaba** es el tamaño del tronco.

Sabemos que el tronco tiene cierto alto fijo, el cual dictaron también por medio del **margin-top** negativo. Y el ancho del tronco es el ancho de la página, por lo que no es necesario especificarlo.
Pero el ancho de la página, en otras palabras, es el 100% de la página, **por lo que el tronco debería tener un ancho de 100%.**
```css
.tronco{
        width: 100%;
        height: 800px; /*800px es un valor arbitrario, que se parece mucho al alto de la imágen, que por algún motivo era 758.969*/
        margin-top: -300px; /*Esto lo mantenemos porque es necesario para el funcionamiento de su código*/
        
}
```
En otras palabras, **el alto es fijo en su página, pero el ancho depende del tamaño de la página, por lo que debe ser un porcentaje. Y este porcentaje es siempre, el 100% en su caso**


