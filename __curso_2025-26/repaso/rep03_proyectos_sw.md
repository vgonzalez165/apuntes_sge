# REP03: Gestión de Proyectos de Desarrollo de Software

El objetivo de esta práctica es diseñar y desarrollar un **módulo personalizado de Odoo** para la gestión ágil de proyectos de IT (Tecnologías de la Información), permitiendo el seguimiento de proyectos, tareas (historias de usuario), desarrolladores, y la medición del esfuerzo (horas).

## Requisitos funcionales

Tu módulo deberá tener los siguientes modelos:

### `proyecto.desarrollador`

* Campos:
    * `name` (nombre completo del desarrollador)
    * `rol` (ej: Backend, Frontend, QA, DevOps)
    * `tasa_horaria_coste` (coste por hora para la empresa)
* Relaciones:
    * `One2many` con `registro_tiempo` (Todos los registros de horas de este desarrollador).

### `proyecto.proyecto`

* Campos:
    * `nombre_proyecto`
    * `cliente`
    * `fecha_inicio`
    * `fecha_limite` (deadline)
* Relaciones:
    * `One2many` con `tarea` (Todas las tareas asociadas al proyecto).

### `proyecto.tarea` (Historia de Usuario)

* Campos:
    * `titulo`
    * `prioridad` (Baja, Media, Alta, Crítica)
    * `estado` (Pendiente, En Desarrollo, En Revisión, Completada)
    * `esfuerzo_estimado_horas`
    * **`coste_total_calculado`** (Calculado a partir de los `registro_tiempo` asociados).
* Relaciones:
    * `Many2one` con `proyecto`
    * `Many2many` con `desarrollador` (Desarrolladores asignados)
    * `One2many` con `registro_tiempo` (Horas registradas para la tarea).

### `proyecto.registro_tiempo` (Time Tracking)

* Campos:
    * `fecha_trabajo`
    * `horas_registradas`
    * `descripcion_trabajo`
    * **`coste_registro`** (Calculado: `horas_registradas` * `desarrollador.tasa_horaria_coste`)
* Relaciones:
    * `Many2one` con `desarrollador`
    * `Many2one` con `tarea`


## Interfaz de usuario (vistas)

El módulo debe incluir una **interfaz gráfica completa** para cada uno de los modelos definidos, con una vista tipo árbol y otra tipo formulario por modelo.

Además:

### Modelo `proyecto.tarea`

* El campo `prioridad` debe colorearse así:
    * Crítica → rojo
    * Alta → naranja
    * Media → azul
    * Baja → verde
* Validación: no se puede cambiar el `estado` a "Completada" si las `horas_registradas` totales son cero.

### Modelo `proyecto.registro_tiempo`

* Botón con opciones: *"Aprobar Horas"*, *"Rechazar Registro"*
* Debe tener un campo calculado **`desviacion_esfuerzo_horas`** que compare las horas totales registradas en la tarea con el `esfuerzo_estimado_horas` original.
* El campo `desviacion_esfuerzo_horas` se coloreará:
    * 0% (horas registradas = estimadas) → verde
    * 1%-20% → naranja
    * Más del 20% → rojo

## API REST

Se debe exponer una API REST básica con rutas para consultar datos del proyecto desde otras aplicaciones (ej: sistemas de facturación o dashboards de gestión).

### 1. `GET /api/desarrolladores/carga`

* Devuelve los desarrolladores y la **cantidad de horas que tienen registradas** en el último mes.

### 2. `GET /api/proyectos/pendientes`

* Devuelve todos los proyectos cuya fecha límite (`fecha_limite`) sea anterior a la fecha actual y que aún tengan tareas **no completadas**.

### 3. `GET /api/tareas/costo`

* Devuelve todas las tareas con su título y su **`coste_total_calculado`** y la **`desviacion_esfuerzo_horas`** respecto a la estimación.

### 4. `GET /api/tarea/detalle/<id_tarea>`

* Devuelve el detalle completo de una tarea, incluyendo el `proyecto` al que pertenece y el listado de todos los `registro_tiempo` asociados, ordenados por fecha.