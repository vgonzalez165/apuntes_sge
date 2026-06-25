# REP04: Gestión de un hospital veterinario

El objetivo de esta práctica es diseñar y desarrollar un **módulo personalizado de Odoo** para la gestión de un hospital veterinario, incluyendo el registro de mascotas, propietarios, tratamientos médicos, y la facturación de servicios.

## Requisitos funcionales

Tu módulo deberá tener los siguientes modelos:

### `veterinaria.veterinario`

* Campos:
    * `name` (nombre completo del veterinario)
    * `num_colegiado` (Número de colegiado único)
    * `especialidad` (ej: Cirugía, Odontología, Medicina General)
* Relaciones:
    * `One2many` con `tratamiento` (Los tratamientos realizados por este veterinario).

### `veterinaria.propietario`

* Campos:
    * `name` (nombre del propietario)
    * `dni`
    * `email`
    * `telefono`
* Relaciones:
    * `One2many` con `mascota` (Mascotas de su propiedad).

### `veterinaria.mascota`

* Campos:
    * `name` (nombre de la mascota)
    * `especie` (Perro, Gato, Ave, etc.)
    * `raza`
    * `fecha_nacimiento`
    * **`edad_anios`** (Calculado a partir de `fecha_nacimiento`).
* Relaciones:
    * `Many2one` con `propietario`
    * `One2many` con `tratamiento` (Historial médico completo).

### `veterinaria.servicio_medico`

* Campos:
    * `nombre_servicio` (ej: Vacunación, Rayos X, Análisis de sangre)
    * `precio_base`
    * `es_urgencia` (Booleano)
* Relaciones:
    * `Many2many` con `tratamiento` (Servicios incluidos en un tratamiento).

### `veterinaria.tratamiento` (Orden de Servicio Médico)

* Campos:
    * `fecha_consulta`
    * `diagnostico`
    * `estado_facturacion` (Pendiente, Facturado, Pagado)
    * `es_urgencia` (Calculado si algún servicio asociado tiene `es_urgencia` True)
    * **`monto_total_calculado`** (Calculado sumando los precios de los `servicio_medico` asociados).
* Relaciones:
    * `Many2one` con `mascota`
    * `Many2one` con `veterinario` (Veterinario principal a cargo).
    * `Many2many` con `servicio_medico`.


## Interfaz de usuario (vistas)

El módulo debe incluir una **interfaz gráfica completa** para cada uno de los modelos definidos, con una vista tipo árbol y otra tipo formulario por modelo.

Además:

### Modelo `veterinaria.tratamiento`

* El campo `estado_facturacion` debe colorearse así:
    * Pendiente → rojo
    * Facturado → naranja
    * Pagado → verde
* Validación: no se puede cambiar el `estado_facturacion` a "Facturado" si el `monto_total_calculado` es cero.

### Modelo `veterinaria.mascota`

* El campo `edad_anios` debe ser visible en el formulario.
* Botón de acción: *"Crear Nuevo Tratamiento"* (que abre un formulario pre-rellenado con la mascota y el propietario).
* El historial médico (`tratamiento` `One2many`) debe mostrarse de forma destacada en el formulario de la mascota, ordenado por fecha de consulta descendente.

## API REST

Se debe exponer una API REST básica con rutas para consultar datos del hospital veterinario.

### 1. `GET /api/mascotas/vacunas`

* Devuelve un listado de mascotas que tienen más de 5 años y que **no han tenido** un tratamiento de "Vacunación" en el último año.

### 2. `GET /api/veterinarios/urgencias`

* Devuelve los veterinarios y el **número de tratamientos de urgencia** que han realizado en el último mes.

### 3. `GET /api/tratamientos/pendientes`

* Devuelve todos los tratamientos cuyo `estado_facturacion` sea "Pendiente", incluyendo el nombre de la mascota y el `monto_total_calculado`.

### 4. `GET /api/propietario/historial/<dni>`

* Devuelve el historial completo de tratamientos de **todas** las mascotas asociadas a un DNI de propietario específico.