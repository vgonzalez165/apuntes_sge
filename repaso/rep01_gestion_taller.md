# PR0606: Gestión de un taller mecánico 

El objetivo de esta práctica es diseñar y desarrollar un **módulo personalizado de Odoo** para la gestión interna de un pequeño **taller mecánico**, incluyendo el registro de clientes, vehículos, reparaciones, piezas utilizadas y técnicos.

## Requisitos funcionales

Tu módulo deberá tener los siguientes modelos:

- `taller.cliente`
  - Campos:
    - `name` (nombre)
    - `telefono`
    - `email`
    - `direccion`
  - Relaciones:
    - `One2many` con `vehiculo`

- `taller.vehiculo`
  - Campos:
    - `matricula`
    - `marca`
    - `modelo`
    - `anio`
  - Relaciones:
    - `Many2one` con `cliente`
    - `One2many` con `reparacion`

- `taller.reparacion`
  - Campos:
    - `fecha_inicio`
    - `fecha_fin`
    - `descripcion`
    - `estado` (borrador, en curso, finalizada)
    - `coste_total` (calculado)
  - Relaciones:
    - `Many2one` con `vehiculo`
    - `Many2many` con `pieza`
    - `Many2one` con técnico (`res.users`)

- `taller.pieza`
  - Campos:
    - `nombre`
    - `codigo`
    - `precio_unitario`
  - Relaciones:
    - `Many2many` con `reparacion`



## Interfaz de usuario (vistas)

El módulo debe incluir una **interfaz gráfica completa** para cada uno de los modelos definidos, definiendo una vista de tipo árbol y otra de tipo formulario para cada uno de los modelos.

La vista debe incluir por lo menos las siguientes características:

- Todas las vistas deben incluir todos los datos del modelo correspondiente.
- Modelo `pieza`
  - Se debe colorear cada registro según el precio:
    - Precio < 10 € → color verde.
    - Precio > 100 € → color rojo.
    - Precio intermedio → sin color.
  - En el mismo modelo se debe validar que el precio sea superior a 0
- Modelo `reparación`
  - Se debe colorear la columna `estado`:
    - Borrador → gris
    - En curso → azul
    - Finalizada → verde
  - Se debe incluir un botón para cambiar de estado disponiendo de las opciones *"Abrir reparación"*, *"Cerrar reparación"* y *"Reabrir"*
  - El campo `coste_total` se coloreará según los siguientes criterios:
    - Mayor de 500 € → rojo
    - Entre 100 y 500 € → naranja
    - Menor de 100 € → verde
  - Si el estado es *"finalizada"*, todos los campos quedan deshabilitados (`readonly`), excepto el botón de reabrir
  

## API REST

Debes exponer una API REST básica con rutas que permitan consultar información del taller desde aplicaciones externas.

La API debe tener los siguientes endpoints:

1. `GET /api/vehiculos`
   - Devuelve todos los vehículos registrados, con información del cliente asociado.

2. `GET /api/reparaciones`
   - Devuelve todas las reparaciones con fecha, estado, vehículo y técnico.

3. `GET /api/reparacion/<id>`
   - Devuelve el detalle completo de una reparación, incluyendo piezas.
