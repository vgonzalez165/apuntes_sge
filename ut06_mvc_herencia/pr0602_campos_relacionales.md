# UT06: Desarrollo de componentes: MVC y herencia

## PR0601: Campos del modelo

### ¿Qué vamos a aprender?

Un tipo de campos especiales del modelo en Odoo son los **campos relacionales**, que nos permiten establecer relaciones entre diferentes modelos, pudiendo ser estas relaciones de tres tipos: muchos a uno (`Many2one`), uno a muchos (`One2many`) y muchos a muchos (`Many2many`).

En esta práctica tendrás que utilizar estos tres tipos de campos para realizar un módulo con varios modelos interrelacionados entre sí.

### ¿Qué recursos me pueden ser útiles?

A continuación se indican algunos recursos que complementan los apuntes del módulo y que te pueden ser útiles para realizar esta práctica:

- [Campos relacionales del modelo](https://www.odoo.com/documentation/16.0/es/developer/reference/backend/orm.html#relational-fields)


### ¿Qué hay que hacer?

Tienes que crear un módulo para la gestión de una biblioteca, similar al que ya creamos en una práctica anterior pero enfatizando en los campos relacionales.

Las características que tiene que tener este módulo son:

- El módulo se llamará `library_{iniciales}`, por ejemplo, en mi caso sería `library_vjgr`.
- Se deben respetar las normas de nomenclatura que hemos visto para nombrar todos los elementos
- Debes organizar tanto el modelo como las vistas en diferentes ficheros, tal como vimos en la última práctica de la unidad anterior.
- El módulo tendrá los siguientes modelos:
  - **Libros**: cada libro tendrá un título, un autor, un género (novela, drama, ciencia ficción, misterio, terror, histórico) y puede ser prestado a varios socios.
  - **Autores**: un autor tendrá un nombre, un país de origen (recuerda que Odoo tiene un modelo llamado `res.country` que contiene los países) y podrá tener varios libros escritos.
  - **Socios**: puedes poner algún dato general como nombre o teléfono, y además podrá pedir prestados varios libros.


### ¿Te ha parecido muy fácil y quieres más?

Si has acabado pronto la práctica puedes modificar el módulo con lo siguiente:

- Crea un nuevo modelo **género** que almacene los géneros literarios y reemplace el selector del modelo **libros**.
- Modifica el módulo para que se ajuste a lo siguiente:
  - Un libro puede tener varios autores
  - Un libro podrá tener uno o varios revisores, que estarán en el campo autores, y de forma análoga, un autor podrá ser autor de varios libros y también revisor de varios libros.


### ¿Qué hay que entregar?

Debes entregar:

- Al igual que todas las prácticas, tendrás que documentar los pasos más relevantes en formato Markdown e incluirlo en tu repositorio.
- En la documentación tienes que incluir el código de todos los ficheros del proyecto que edites.
- También debe incluir una captura de pantalla donde se vea como el módulo funciona correctamente.


[Volver al índice](../index.html)