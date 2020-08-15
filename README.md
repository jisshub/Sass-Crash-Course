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

![CodePen For Reference](https://codepen.io/bradtraversy/pen/ExjmGdY?editors=1100)

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

- install it and run the compiler to watch changes,

```bash

npm i -g sass

sass --watch scss/style.scss css/style.css

```

- here changes made in sass file will also reflected in css file.

---
