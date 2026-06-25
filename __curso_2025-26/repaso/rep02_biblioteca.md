# REP02: Gestión de una biblioteca escolar

El objetivo de esta práctica es diseñar y desarrollar un **módulo personalizado de Odoo** para la gestión interna de una **biblioteca escolar**, incluyendo el registro de libros, autores, préstamos, estudiantes y ejemplares.

## Requisitos funcionales

Tu módulo deberá tener los siguientes modelos:

### `biblioteca.autor`

* Campos:

  * `name` (nombre del autor)
  * `nacionalidad`
* Relaciones:

  * `One2many` con `libro`

### `biblioteca.libro`

* Campos:

  * `titulo`
  * `isbn`
  * `genero`
  * `anio_publicacion`
* Relaciones:

  * `Many2one` con `autor`
  * `One2many` con `ejemplar`

### `biblioteca.ejemplar`

* Campos:

  * `codigo_interno`
  * `estado` (disponible, prestado, deteriorado)
  * `ubicacion`
* Relaciones:

  * `Many2one` con `libro`
  * `One2many` con `prestamo`

### `biblioteca.estudiante`

* Campos:

  * `name` (nombre del alumno)
  * `curso`
  * `email`
  * `telefono`
* Relaciones:

  * `One2many` con `prestamo`

### `biblioteca.prestamo`

* Campos:

  * `fecha_inicio`
  * `fecha_devolucion`
  * `devuelto` (booleano)
  * `dias_retraso` (calculado)
* Relaciones:

  * `Many2one` con `ejemplar`
  * `Many2one` con `estudiante`

---

## Interfaz de usuario (vistas)

El módulo debe incluir una **interfaz gráfica completa** para cada uno de los modelos definidos, con una vista tipo árbol y otra tipo formulario por modelo.

Además:

### Modelo `ejemplar`

* El campo `estado` debe colorearse así:

  * Disponible → verde
  * Prestado → azul
  * Deteriorado → rojo
* Validación: no se puede registrar un ejemplar sin `ubicación`.

### Modelo `prestamo`

* Botón con opciones: *"Marcar como devuelto"*, *"Renovar préstamo"*, *"Cancelar"*
* El campo `dias_retraso` se coloreará:

  * 0 días → verde
  * 1-5 días → naranja
  * Más de 5 días → rojo
* Si el campo `devuelto` es verdadero, el formulario queda en modo solo lectura, excepto para reabrir o renovar.


## API REST

Se debe exponer una API REST básica con rutas para consultar datos de la biblioteca desde otras aplicaciones.

### 1. `GET /api/estudiantes`

* Devuelve los estudiantes registrados y su número de préstamos activos.

### 2. `GET /api/libros`

* Devuelve todos los libros con autor y cantidad de ejemplares disponibles.

### 3. `GET /api/prestamos`

* Devuelve los préstamos activos, con fechas, alumno y estado del ejemplar.

### 4. `GET /api/prestamo/<id>`

* Devuelve el detalle completo de un préstamo, incluyendo libro y estado de devolución.
