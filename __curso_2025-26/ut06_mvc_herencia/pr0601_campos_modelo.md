# UT06: Desarrollo de componentes: MVC y herencia

## PR0601: Campos del modelo

### ¿Qué vamos a aprender?

Vamos a ir viendo los campos más básicos del modelo

### ¿Qué recursos me pueden ser útiles?

A continuación se indican algunos recursos que complementan los apuntes del módulo y que te pueden ser útiles para realizar esta práctica:

- [Campos básicos del modelo](https://www.odoo.com/documentation/16.0/es/developer/reference/backend/orm.html#basic-fields)
- [Tipos de campos y widgets en Odoo 16](https://www.cybrosys.com/blog/field-types-and-widgets-in-odoo-16)


### ¿Qué hay que hacer?

Desarrolla un módulo en Odoo llamado gestion_productos que permita gestionar una lista de productos con la siguiente información:

- Información básica del producto:
  - **Nombre del producto**
  - **Descripción del producto**
  - **Código de producto**, este campo debe ser obligatorio
  - **Imagen del producto**
- Categoría y tipo de producto:
  - **Categoría**: el usuario podrá escoger entre *Jardín*, *Hogar* y *Electrodomésticos*
  - **Tipo de producto**: indica si es un producto destacable o no.
- Información económica:
  - **Precio de venta**
  - **Stock disponible**: la cantidad de unidades disponible
- Fechas y disponibilidad:
  - **Fecha de creación**, será la fecha actual
  - **Fecha de última actualización**
- Información adicional:
  - **Activo**, indica si el producto está disponible o no, su valor por defecto será `True`
  - **Peso del producto**, un valor numérico con dos decimales de precisión

### ¿Qué hay que entregar?

Debes entregar:

- Al igual que todas las prácticas, tendrás que documentar los pasos más relevantes en formato Markdown e incluirlo en tu repositorio.
- En la documentación tienes que incluir el código de todos los ficheros del proyecto que edites.
- También debe incluir una captura de pantalla donde se vea la vista de formualario mostrando todos los campos rellenos.


[Volver al índice](../index.html)