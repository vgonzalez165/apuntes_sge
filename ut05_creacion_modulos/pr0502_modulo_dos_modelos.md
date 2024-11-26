# UT05: Desarrollo de componentes. Primer módulo

## PR0501: Creación de un módulo básico

### ¿Qué vamos a aprender?

Para que queden bien claros todos los conceptos fundamentales del desarrollo de módulos antes de entrar en profundidad en ellos.

### ¿Qué recursos me pueden ser útiles?

A continuación se indican algunos recursos que complementan los apuntes del módulo y que te pueden ser útiles para realizar esta práctica:

- [Campos básicos del modelo](https://www.odoo.com/documentation/16.0/es/developer/reference/backend/orm.html#basic-fields)
- [Tipos de campos y widgets en Odoo 16](https://www.cybrosys.com/blog/field-types-and-widgets-in-odoo-16)


### ¿Qué hay que hacer?

En esta ocasión vamos a crear un módulo de **gestión de biblioteca** que contendrá dos modelos, uno para almacenar los autores y otro para los libros. Esto implica que nuestro módulo tendrá dos modelos, y, de forma análoga tendrá una vista para cada modelo. 

Los campos que tendrá cada modelo son:

- **Autor**
   - Nombre
   - Fecha de nacimiento
   - Biografía
   - Libros, este campo debería ser una relación de uno a muchos en nuestra base de datos, como aún no hemos visto como hacerlo nos limitaremos a dejarlo de tipo texto.
- **Libro**
  - Nombre
  - Autor, nuevamente, este campo debería estar relacionado con el tro modelo. Por ahora lo dejaremos de tipo char
  - Fecha de publicación
  - ISBN
  - Sinopsis

Te indico algunas pautas a seguir cuando tenemos un módulo con varios modelos:

- Lo ideal es crear un fichero dentro de `models` para cada **modelo**. El nombre del fichero en este caso debería ser descriptivo, por ejemplo, `library_book` para el modelo de los libros.
- Para que Odoo reconozca estos ficheros debemos indicarlos en el fichero `models/__init__.py` mediante un `import` para cada fichero. Por ejemplo, el correspondiente al ejemplo anterior sería `import * from library_book`
- También tendremos que crear una **vista** para cada uno de los modelos, podemos crear todas en el mismo fichero o bien crear diferentes ficheros para las vistas y así tenerlo más ordenado. Un ejemplo de cómo podríamos dividirlo en ficheros sería:
  - `library_menu_views.xml`, que contendría todos los elementos `<menuitem>`
  - `library_book_views.xml`, con las vistas y acciones que corresponden a los libros
  - `library_author_views.xml`, que contendrá las vistas y acciones de los autores
- Seguro que ahora te estás preguntando si estos ficheros los reconoce automáticamente Odoo, y la respuesta en no. Tenemos que decirle nosotros qué ficheros de vista se cargan con el módulo, y eso lo hacemos en el archivo `__manifest__`, añadiendo a la lista del campo `data` todos los ficheros de las vistas.
- Por último, nos quedarían las **reglas de acceso** que se indican en el fichero `ir.model.access.csv`, donde habría que añadir una línea para cada modelo con la siguiente estructura:

```csv
access_library_book,access_library_author,model_library_author,base.group_user,1,1,1,1
```

- El campo más importante es el tercero, que es el que hace referencia al modelo. Fíjate que la forma de indicarlo es mediante la cadena `model_` seguido del nombre del modelo correspondiente.



### ¿Qué hay que entregar?

Debes entregar:

- Al igual que todas las prácticas, tendrás que documentar los pasos más relevantes en formato Markdown e incluirlo en tu repositorio.
- En la documentación tienes que incluir el código de todos los ficheros del proyecto que edites.
- También debe incluir una captura de pantalla donde se vea que el módulo funciona correctamente.


[Volver al índice](../index.html)