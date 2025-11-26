## REP05: Gestión de un club deportivo

El objetivo de esta práctica es diseñar y desarrollar un **módulo personalizado de Odoo** para la gestión de un **club deportivo**, incluyendo el registro de miembros, cuotas, entrenadores, y el manejo de las actividades (clases o eventos).

## Requisitos funcionales

Tu módulo deberá tener los siguientes modelos:

### `club.entrenador`

  * Campos:
      * `name` (nombre completo del entrenador)
      * `titulo_deportivo` (ej: Entrenador Nacional de Baloncesto, Instructor de Yoga)
      * `salario_base`
  * Relaciones:
      * `One2many` con `actividad` (Las actividades o clases que imparte).

### `club.miembro`

  * Campos:
      * `name` (nombre completo del miembro)
      * `dni`
      * `email`
      * `fecha_alta`
      * **`estado_cuota`** (Calculado: Si la última cuota está pagada o pendiente).
  * Relaciones:
      * `One2many` con `cuota` (Historial de pagos).
      * `Many2many` con `actividad` (Actividades en las que está inscrito).

### `club.actividad` (Clase o Evento)

  * Campos:
      * `nombre_actividad` (ej: Natación Nivel Avanzado, Fitness)
      * `dia_semana` (Selección: Lunes, Martes, etc.)
      * `hora_inicio`
      * `duracion_minutos`
      * `aforo_maximo`
  * Relaciones:
      * `Many2one` con `entrenador` (Entrenador a cargo).
      * `Many2many` con `miembro` (Miembros inscritos).

### `club.cuota` (Pago Mensual)

  * Campos:
      * `fecha_emision`
      * `fecha_vencimiento`
      * `monto`
      * `pagada` (Booleano)
      * `metodo_pago` (Transferencia, Efectivo, Tarjeta)
  * Relaciones:
      * `Many2one` con `miembro`.


## Interfaz de usuario (vistas)

El módulo debe incluir una **interfaz gráfica completa** para cada uno de los modelos definidos, con una vista tipo árbol y otra tipo formulario por modelo.

Además:

### Modelo `club.actividad`

  * Validación: El campo `aforo_maximo` debe ser mayor que el número actual de miembros inscritos (al guardar).
  * Debe tener un campo calculado **`plazas_disponibles`**.
  * El campo `plazas_disponibles` debe colorearse:
      * Plazas \> 5 → verde
      * Plazas 1-5 → naranja
      * Plazas = 0 → rojo

### Modelo `club.miembro`

  * El campo `estado_cuota` se coloreará:
      * Pagada → verde
      * Pendiente → rojo

## Portal Web

El módulo debe incluir un **controlador web** que genere una página web dinámica para los clientes (no requiere autenticación, es pública) y que se pueda acceder a través de una URL de la forma `/club/horario`.

### 1\. Horario de Actividades (/club/horario)

  * **Objetivo:** Mostrar la disponibilidad de las clases a los posibles miembros.
  * **Contenido Dinámico:**
      * Tabla con la lista de todas las `actividad`s.
      * Debe estar ordenada por `dia_semana` y `hora_inicio`.
      * Debe mostrar el `nombre_actividad`, el `entrenador` y el número actual de **`plazas_disponibles`** (calculado en la vista).

### 2\. Detalle de Actividad (/club/actividad/\<id\>)

  * **Objetivo:** Mostrar información detallada de una clase.
  * **Contenido Dinámico:**
      * Nombre de la actividad, día, hora y duración.
      * Nombre y especialidad del `entrenador`.
      * Un listado de todos los `miembro`s **inscritos** en esa actividad.
      * Un botón de acción simulado (por ejemplo, "Inscribirse") que solo se muestre si las `plazas_disponibles` son mayores a cero.