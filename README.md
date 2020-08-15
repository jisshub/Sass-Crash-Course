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





