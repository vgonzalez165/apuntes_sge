
# Guía de Desarrollo Backend en Odoo: Modelos y Base de Datos


Para estos apuntes, asumiremos los siguientes nombres (puedes cambiarlos según tu configuración real):

  * Nombre del contenedor Odoo: `odoo_web`
  * Nombre del contenedor Postgres: `db`
  * Nombre de la base de datos: `mi_base_datos`
  * Nombre de tu módulo: `mi_modulo_estudiante`


## Parte 1: Estructura del Módulo

Antes de crear el modelo, tu módulo debe tener una estructura de carpetas mínima.

1.  Carpeta raíz con el nombre del módulo (`mi_modulo_estudiante`).
2.  Archivo `__init__.py`: Indica a Python que esto es un paquete.
3.  Archivo `__manifest__.py`: Describe el módulo a Odoo.
4.  Carpeta `models`: Aquí guardaremos nuestros archivos de código.
5.  Archivo `models/__init__.py`: Importa los archivos `.py` que estén dentro de la carpeta `models`.
6.  Archivo `models/mi_modelo.py`: El archivo donde escribiremos el código del modelo.



## Parte 2: Creación de un Modelo en Odoo

Un "Modelo" en Odoo es una clase de Python que se traduce automáticamente en una tabla de la base de datos.

Abre tu archivo `models/mi_modelo.py` y sigue esta estructura.

### 1\. Importaciones y Definición de Clase

Todo modelo debe heredar de `models.Model`.

```python
# -*- coding: utf-8 -*-
from odoo import models, fields

class EstudianteCurso(models.Model):
    # Atributos obligatorios
    _name = 'estudiante.curso' # Nombre técnico del modelo (será el nombre de la tabla)
    _description = 'Información de los estudiantes' # Nombre legible para humanos
```

> **Nota sobre `_name`:** Odoo utiliza puntos para separar palabras en el nombre del modelo (ej. `estudiante.curso`). Sin embargo, en la base de datos PostgreSQL, estos puntos se convertirán en guiones bajos (`estudiante_curso`).

### 2\. Tipos de Datos Básicos

En Odoo, todos los campos son clases que se importan desde `odoo.fields`.

## 1\. Parámetros Globales (Comunes a todos los campos)

Estos parámetros se pueden utilizar en prácticamente cualquier tipo de dato (`Char`, `Integer`, `Many2one`, etc.).

  * **`string`** (str): Es la etiqueta del campo. Es el texto que leerá tu lector de pantalla en la interfaz.
      * *Ejemplo:* `string='Fecha de nacimiento'`
  * **`required`** (bool): Si es `True`, el usuario no podrá guardar el registro si el campo está vacío. A nivel de base de datos, establece la columna como `NOT NULL`.
      * *Default:* `False`
  * **`help`** (str): Texto de ayuda. En la interfaz web, aparece cuando el ratón pasa por encima. Para ti, es información contextual valiosa que describe para qué sirve el campo.
  * **`readonly`** (bool): Si es `True`, el campo se muestra pero no se puede editar.
  * **`index`** (bool): Si es `True`, crea un índice en la base de datos Postgres. Úsalo si vas a realizar muchas búsquedas filtrando por este campo.
  * **`default`**: Valor por defecto al crear un nuevo registro. Puede ser un valor estático (como un número) o una función.
  * **`store`** (bool): Por defecto es `True`. Si lo pones en `False`, el campo no se guarda en la base de datos (se usa para cálculos al vuelo).

## 2\. Tipos de Datos Simples

### A. Texto

Odoo distingue entre textos cortos (nombres, códigos) y largos (descripciones).

#### `fields.Char`

Guarda cadenas de texto de longitud limitada. En Postgres es un `VARCHAR`.

  * **`size`** (int): (Opcional) Número máximo de caracteres permitidos.
  * **`trim`** (bool): Por defecto `True`. Elimina espacios en blanco al inicio y al final automáticamente.

<!-- end list -->

```python
codigo_postal = fields.Char(string='Código Postal', size=5, required=True)
```

#### `fields.Text`

Guarda textos largos sin límite predefinido. En Postgres es un `TEXT`. Se usa para notas, observaciones o biografías. No tiene parámetros especiales aparte de los globales.

#### `fields.Html`

Similar a `Text`, pero permite guardar etiquetas HTML. El navegador de Odoo renderizará el formato (negritas, listas, etc.).

  * **`sanitize`** (bool): Por defecto `True`. Limpia código malicioso (scripts) por seguridad.

-----

### B. Números

#### `fields.Integer`

Guarda números enteros (sin decimales).

  * No tiene parámetros específicos extra, más allá de los globales.

<!-- end list -->

```python
edad = fields.Integer(string='Edad', default=18)
```

#### `fields.Float`

Guarda números con decimales.

  * **`digits`** (tuple): Es una tupla `(total_precision, decimales)`. Define cuántos dígitos se guardan en total y cuántos son decimales.
      * *Ejemplo:* `digits=(10, 2)` significa hasta 10 números en total, de los cuales 2 son decimales.

<!-- end list -->

```python
peso = fields.Float(string='Peso en kg', digits=(5, 2))
```

#### `fields.Monetary`

Es un tipo especial de `Float` diseñado para dinero.

  * **`currency_field`** (str): Indica el nombre del campo que contiene la moneda (por defecto busca un campo llamado `currency_id`). Es obligatorio tener un campo Many2one a `res.currency` en el mismo modelo para usar esto.

-----

### C. Lógicos y Fechas

#### `fields.Boolean`

Guarda `True` o `False`. En la interfaz se ve como una casilla de verificación (checkbox).

```python
es_alumno = fields.Boolean(string='¿Es alumno?', default=True)
```

#### `fields.Date`

Guarda una fecha (Año-Mes-Día).

  * Para poner la fecha de hoy por defecto, usa `default=fields.Date.context_today`.

#### `fields.Datetime`

Guarda fecha y hora.

  * Para poner el momento actual ("ahora") por defecto, usa `default=fields.Datetime.now`.

-----

### D. Selección y Archivos

#### `fields.Selection`

Crea una lista cerrada de opciones (un menú desplegable).
Es obligatorio definir el primer parámetro, que es una **lista de tuplas**.
Cada tupla tiene dos elementos: `('valor_interno', 'Etiqueta a mostrar')`.

  * El *valor\_interno* es lo que se guarda en Postgres.
  * La *Etiqueta* es lo que lee el usuario.

<!-- end list -->

```python
estado = fields.Selection([
    ('borrador', 'Borrador'),
    ('confirmado', 'Confirmado'),
    ('cancelado', 'Cancelado')
], string='Estado del documento', default='borrador')
```

#### `fields.Binary`

Se usa para subir archivos o imágenes. Guarda el archivo codificado en Base64.

  * **`attachment`** (bool): Por defecto `True`. Indica si el archivo se guarda como adjunto en Odoo (mejor rendimiento) o dentro de la columna de la tabla.

-----

## 3\. Tipos de Datos Relacionales (Detallado)

Estos campos son punteros a otras tablas.

### A. `fields.Many2one` (Muchos a Uno)

Crea una clave foránea en Postgres.

  * **`comodel_name`** (str): (Obligatorio, primer argumento posicional). El nombre del modelo destino (ej. `'res.partner'`).
  * **`ondelete`** (str): Define qué pasa si se borra el registro al que apuntamos.
      * `'set null'`: (Default) Si borras la escuela, el campo escuela del alumno se queda vacío.
      * `'cascade'`: Si borras la escuela, se borran también todos los alumnos.
      * `'restrict'`: No te deja borrar la escuela si tiene alumnos.

<!-- end list -->

```python
# Ejemplo: Un libro tiene un autor
autor_id = fields.Many2one(
    comodel_name='res.partner',
    string='Autor',
    ondelete='restrict'
)
```

### B. `fields.One2many` (Uno a Muchos)

Es una lista virtual. No crea una columna en la tabla actual en Postgres, sino que hace una consulta inversa a la otra tabla.

  * **`comodel_name`** (str): El modelo destino.
  * **`inverse_name`** (str): El nombre del campo `Many2one` en el otro modelo que apunta hacia aquí.
  * **`domain`** (list): (Opcional) Un filtro para mostrar solo ciertos registros.

<!-- end list -->

```python
# Ejemplo: Un autor tiene muchos libros
# En el modelo de libros debe existir un campo 'autor_id'
libro_ids = fields.One2many(
    comodel_name='biblioteca.libro',
    inverse_name='autor_id',
    string='Libros escritos'
)
```

### C. `fields.Many2many` (Muchos a Muchos)

Crea una tabla intermedia automáticamente en Postgres.

  * **`comodel_name`** (str): El modelo destino.
  * **`relation`** (str): (Opcional) Nombre de la tabla intermedia en Postgres. Si no lo pones, Odoo genera uno automáticamente.
  * **`column1`** y **`column2`** (str): (Opcional) Nombres de las columnas en la tabla intermedia. Útil si relacionas un modelo consigo mismo.

<!-- end list -->

```python
# Ejemplo: Un libro tiene muchas etiquetas (tags)
etiqueta_ids = fields.Many2many(
    comodel_name='biblioteca.etiqueta',
    string='Etiquetas'
)
```

-----

## 4\. Campos Calculados (Computed Fields)

Cualquier tipo de dato anterior puede convertirse en calculado si le añades el parámetro `compute`.

  * **`compute`** (str): Nombre del método (función) que calculará el valor.
  * **`store`** (bool):
      * `False` (Default): Se calcula cada vez que se lee (no se guarda en DB, no se puede buscar por él).
      * `True`: Se calcula y se guarda en DB. Se recalcula solo cuando cambian las dependencias.

<!-- end list -->

```python
# Definición del campo
importe_total = fields.Float(string='Total', compute='_calcular_total', store=True)

# Definición de la función (se explicará en detalle en otra lección)
@api.depends('precio', 'cantidad')
def _calcular_total(self):
    for record in self:
        record.importe_total = record.precio * record.cantidad
```




## Parte 3: Instalación desde Odoo Shell

Como eres un usuario experto en teclado, utilizaremos la consola interactiva de Odoo (`shell`) para instalar el módulo sin usar el navegador.

### Paso 1: Acceder al contenedor de Odoo

Abre tu terminal y ejecuta el siguiente comando para entrar al contenedor:

```bash
docker exec -it odoo_web /bin/bash
```

### Paso 2: Iniciar Odoo Shell

Una vez dentro, iniciamos el entorno interactivo de Odoo apuntando a tu base de datos:

```bash
odoo-bin shell -d mi_base_datos
```

*Si el comando `odoo-bin` no se encuentra, prueba simplemente con `odoo shell -d mi_base_datos`.*

Esperarás unos segundos hasta que veas el prompt de Python `>>>`.

### Paso 3: Instalar el módulo mediante código Python

Dentro del shell, tienes acceso a la variable `env` (el entorno de Odoo). Escribe lo siguiente línea por línea:

1.  Busca tu módulo:

    ```python
    modulo = env['ir.module.module'].search([('name', '=', 'mi_modulo_estudiante')])
    ```

2.  Verifica que lo encontró (debe devolver algo como `ir.module.module(ID,)`):

    ```python
    print(modulo)
    ```

3.  Instálalo:

    ```python
    modulo.button_immediate_install()
    ```

    *Nota: Esto iniciará un proceso de carga. Si no hay errores, volverás al prompt.*

4.  Sal del shell:

    ```python
    exit()
    ```

-----

## Parte 4: Comprobación en PostgreSQL

Ahora verificaremos que Odoo ha creado realmente la tabla en la base de datos.

### Paso 1: Acceder al contenedor de Base de Datos

Desde tu terminal principal (fuera del contenedor de Odoo), accede al contenedor de Postgres:

```bash
docker exec -it db psql -U odoo -d mi_base_datos
```

  * `-U odoo`: Indica el usuario (comúnmente es 'odoo').
  * `-d mi_base_datos`: Indica la base de datos a conectar.

Deberías ver un prompt que termina en `mi_base_datos=#`.

### Paso 2: Listar las tablas

El comando para listar tablas en psql es `\dt`. Sin embargo, hay muchas. Vamos a filtrar buscando tu tabla. Recuerda que el punto se convierte en guion bajo.

```sql
\dt *estudiante*
```

Deberías ver una salida tabular que lista `public | estudiante_curso | table | odoo`. Esto confirma que la tabla existe.

### Paso 3: Inspeccionar la estructura

Para ver si tus campos (columnas) se crearon con los tipos correctos, usa el comando `\d` seguido del nombre de la tabla:

```sql
\d estudiante_curso
```

El lector de pantalla leerá una lista con tres columnas principales:

1.  **Column:** Nombre del campo (ej. `name`, `edad`, `escuela_id`).
2.  **Type:** Tipo de dato SQL (ej. `integer`, `character varying`, `boolean`).
3.  **Collation/Nullable/Default:** Restricciones.

Observarás que Odoo añade automáticamente campos "mágicos" que tú no escribiste, como:

  * `id` (Clave primaria).
  * `create_uid` (Quién lo creó).
  * `create_date` (Cuándo se creó).
  * `write_date` (Última modificación).

### Paso 4: Realizar una consulta de prueba

Si quieres ver los datos (estará vacía por ahora), usa SQL estándar:

```sql
SELECT * FROM estudiante_curso;
```

Para salir de la consola de Postgres, escribe:

```sql
\q
```
