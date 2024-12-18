# UT06: Desarrollo de componentes: MVC y herencia

## PR0603: Campos calculados y restricciones

### ¿Qué vamos a aprender?

En este ejercicio practicarás con campos calculados y con restricciones en el modelo, tanto SQL como Python.

### ¿Qué recursos me pueden ser útiles?

A continuación se indican algunos recursos que complementan los apuntes del módulo y que te pueden ser útiles para realizar esta práctica:

- [Campos relacionales del modelo](https://www.odoo.com/documentation/16.0/es/developer/reference/backend/orm.html#relational-fields)


### ¿Qué hay que hacer?

Vamos a crear un módulo sobre gestión de productos. Las características que tendrá son:

- **Nombre del módulo**: `stock_management`
- **Modelos**: tendrá un único modelo que se llamará `stock.product`
- **Campos del modelo**: el modelo tendrá los siguientes campos:
  - `name`: nombre del producto
  - `category`: categoría del producto, será un `Selection`
  - `price`: precio unitario del producto
  - `quantity`: cantidad en stock
  - `total_value`: campo calculado con el valor total del stock (precio por la cantidad total)
  - `minimum_quantity`: valor entero 
  - `stock_status`: campo calculado de tipo `Selection`. Podrá ser *normal* si la cantidad es superior a la cantidad mímina y *Low Stock* si es inferior.
  - `full_name`: el nombre completo será un campo calculado que generará a partir del nombre y de la categoría. Por ejemplo: `Ryzen 7 5800X (Microprocesadores)`
- **Restricciones**: tienes que aplicar las siguientes restricciones:
  - **SQL**: 
    - El nombre del producto debe ser único
    - La cantidad en stock debe ser mayor a igual a 0
  - **Python**:
    - El precio debe ser mayor que 0
    - La cantidad debe ser mayor o igual a 0
    - El valor total del stock no puede ser superior a 100000 unidades monetarias
    - No se permiten productos sin categoría


### ¿Te ha parecido muy fácil y quieres más?

Si has acabado pronto la práctica puedes probar a añadir las siguientes restricciones SQL:

- Evitar duplicados en la combinación de nombre y categoría. La sentencia SQL que necesitas es `unique(name, category)`
- El nombre del producto debe tener al menos 3 caracteres. La sentencia SQL es `CHECK(LENGTH(name) >= 3)`



### ¿Qué hay que entregar?

Debes entregar:

- Al igual que todas las prácticas, tendrás que documentar los pasos más relevantes en formato Markdown e incluirlo en tu repositorio.
- En la documentación tienes que incluir el código de todos los ficheros del proyecto que edites.
- También debe incluir una captura de pantalla donde se vea como el módulo funciona correctamente.


[Volver al índice](../index.html)