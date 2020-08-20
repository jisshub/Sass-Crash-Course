# Sass Intro

![image](./screenshots/screen1.png 'image')

- Browser doesnt read the sass files direclty, so compile them to css first

- Sass Compiler (live sass compiler extension)

---

## .sass vs .scss files

![image](./screenshots/screen2.png 'image')

- most preferable one is *.scss* type, since it has backward compatability with regualr css.
- it has curly braces like css
- *.scss* types are less prefered. not similar to regular css, 
- it not uses curly braces - instead uses intendation

---

## Sass features

### Variables

![image](./screenshots/screen3.png 'image')

- variable name begins with a **$**.

### Nesting

![image](./screenshots/screen4.png 'image')

- we can provide inner tags of nav in a nested manner.
- so we dint have to specify nav for each of tags while applying the styles.

### Modules

![image](./screenshots/screen5.png 'image')

- we can create different modules for sass file.

- later import one file into another file.

- here, v can see two scss file *_base.scss*
and *styles.scss*

- v import _base.scss file to *styles.scss* file.

- later called variable a from *_base.scss* file to *styles.scss* file. 

- thus v can have diff files for separate pages.eg: sass files for home page, about page, contact page. and import them to a main page

- but imported files should begins name with an underscore. if not, sass compiler will ignore it while compilation.

---

### Mixins and Functions

![image](./screenshots/screen6.png 'image')

- here in *sass* file, v include the transform function using *@include*.

- pass the **rotate(30deg)** as argument.

- **$property** parameter receives it as a value.

- later pass assigned the same for eaxg variables.

---

### Inheritance

![image](./screenshots/screen7.png 'image')

- For instance, a page might have diffrent buttns like success, warning, error buttons ...

- this message have similar styles in case of borders, padding, margin, font color..

- so v create a base styles for this at once. later v extend them to other class in sass using *@extend*.

---

### Conditionals

![image](./screenshots/screen8.png 'image') 

- we can provide conditions in sass unlike css.

- ie. here v suse a mixin called *triangle()*, which gets values on each parameter.

- include the *triangle* mixin on *next* class.

- pass the arguments to triangle mixin.

- later can check the direction, and based on that v set a border-color.

---

## Application Part

[CodePen For Reference](https://codepen.io/bradtraversy/pen/ExjmGdY?editors=1100)

```scss
$primary-color:#f4f4f4;
$font-stack: Arial, Helvetica, sans-serif;
*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
body{
    background-color: $primary-color;
    font-family: $font-stack;
    line-height: 1.5;
}

```

- to compile the file, we hasve two options,

1. using sass compiler of npm
2. using sass lve compiler

### Using Sass Compiler NPM

- install it and run the compiler to compile scss/sass to css,

```bash

npm i -g sass

sass --watch scss/style.scss css/style.css

```

- here changes made in sass file will also reflected in css file.

---

### Using VS Code extension Live sass compiler

> open settings > search for live sass > choose edit settings.json

> make changes as below,

**settings.json**

```json
"liveSassCompile.settings.formats": [
        {
            "format": "compressed",
             "extensionName": ".css",
            "savePath": "/css"
        }
    ],
    "liveSassCompile.settings.generateMap": false
```


```scss

.showcase{
    background-color: $primary-color;
    color: $light-color;
    height: 600px;
    
    nav{
        display: flex;
        justify-content: space-between;
        align-items: center;
        ul{
            display: flex;
            list-style-type: none;
        }
        li{
            padding: 15px;
        }
        a:hover{
            color: $secondary-color;
        }
    } 
    // links outside of nav also follow below styles
    a{
        color: $light-color;
        text-decoration: none;
    }

    &-content{
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        img{
            width: 50%;
        }
        h1{
            font-size: 50px;
            line-height: 1.2;            
        }
        p{
            margin: 20px 0;
        }
    }
```

- here, *&-content* pertains to *showcase-content* class.

---

## Using Partials in Sass

- partials are used to breakdown the scss file to multiple file and while compiling, it
compiles into one css file.

- partial files r begins with *underscore*. eg: _config.scss, _utilities.scss

- but the partial files r not compiled on its own like regular scss file.

- first create a partial file for configurations

**_config.scss**

```scss
$light-color:#f4f4f4;
$font-stack: Arial, Helvetica, sans-serif;
$primary-color: #3339FF;
$secondary-color: #FC7C00;
```

- import the config.scss file to style.scss file
- later v can use this configurations for all related files as well.

**style.scss**
```scss
@import "config";
```

**_utilities.scss**
```scss
.container{
    max-width: 1100px;
    padding: 0 30px;
    margin: 0 auto;
    overflow: hidden;
}
```

**style.scss**
```scss
@import "utilties";
```

**_button.scss**

```scss
%btn{
    display: inline-block;
    border-radius: 5px;
    padding: 8px 20px;
    margin: 3px;

    &:hover{
        transform: scale(.98);
    }
}

.btn-primary{
    @extend %btn;
    background-color: $primary-color;
}
.btn-secondary{
    @extend %btn;
    background-color: $secondary-color;
}
```

- here v extends the *btn* property to *btn-primary* and *btn-secondary* classes
---

## Lighten function

```scss

.btn-primary{
    @extend %btn;
    background-color: lighten($primary-color, 10%);
}

```
- lighten the color by 10%;

## Functions and Conditionals

**_config.scss**

```scss
// create a fcunction to set text color based on bg color
@function set-text-color($color){
    // if bg is lightcolor
    @if (lightness($color) > 70) {
        @return #333;
    }
    @else {
        @return #fff;
    }
}
```

**style.scss**
```scss

.showcase{
    background-color: $primary-color;
    // call function 
    color: set-text-color($primary-color);
    height: 600px;
    
    nav{
        display: flex;
        justify-content: space-between;
        align-items: center;
        ul{
            display: flex;
            list-style-type: none;
        }
        li{
            padding: 15px;
        }
        a:hover{
            color: $secondary-color;
        }
    } 
    // links outside of nav also follow below styles
    a{
        color: set-text-color($primary-color);
        text-decoration: none;
    }

```
- here v invoke the *set-text-color*() function in color property.

---

## Using mixin

- micxin is like a function that returns nothing.


**style.scss**
```scss

.showcase{
    background-color: $primary-color;
    // call function 
    color: set-text-color($primary-color);
}
```
- here v can use mixin to set baxckground color and font color  property.

**_config.scs**
```scss

@mixin set-bg-text-color($color){
    
    background-color: $color;
    // call function 
    color: set-text-color($color);
}

```

- then use this mixin in style.scss

**style.scss**

```scss

.showcase{

    // include the mixin here to set bg and text color
    @include set-bg-text-color($primary-color);
    height: 600px;
}
```

- thus v set the background and font color in one go.

---


## Using @each loop for automatically assiging padding and margin to the content

**index.html**

```html
<p class="my-3">
    Lorem, ipsum dolor sit amet consectetur adipisicing elit. Est
    eligendi tempore atque laborum. Quisquam nemo at non. Corrupti,
    vitae dolore.
</p>

```

**_utilities.scss**

```scss

// initialize a list
$spaceamount : (1, 2, 3, 4, 5);

// declare each loop to loop thru above list
@each $var in $spaceamount {
    // masrgin
    .m-#{$var}{
        margin: #{$var}rem ;
    }   
    .my-#{$var}{
        margin: #{$var}rem 0;
    }
    // padding
    .p-#{$var}{
        padding: #{$var}rem;
    }
    .py-#{$var}{
        padding: #{$var}rem 0;
    }
}

```
- *#{$var}* refers to each numbers in list spaceamount.

- for instance *.p-#{$var}* indicated *.p-1, .p-2, .p-3* etc..

- same as in case of margins to. *.m-#{$var}* refers to *.m-2, .m-1* etc..

- based on case of class in p tag, appropriate style is chosen.

- here class is *.my-3*, so corresponding margin is allocated using each loop.

---

