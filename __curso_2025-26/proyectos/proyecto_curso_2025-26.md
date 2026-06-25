# PROYECTO FINAL: Sistemas de Gestión Empresarial

## 1. Contexto del Negocio

El cliente, **TechSchool Solutions**, es un centro de formación tecnológica de alto rendimiento. Gestionan un inventario costoso de hardware (laptops de gama alta, kits de robótica, cámaras, servidores) que prestan rotativamente a estudiantes y profesores.

Actualmente, carecen de control sobre el ciclo de vida de los activos. Desconocen qué equipos están dañados, cuánto gastan en reparaciones o quién tiene un equipo que debió devolverse hace una semana.

Tu objetivo será desarrollar un módulo personalizado en Odoo que digitalice todo el flujo de inventario, mantenimiento y préstamos, integrando además una interfaz web pública y una API para terceros.


## 2. Arquitectura de datos

**NOTA**: en este texto referencio el módulo como `tech`, pero en tu caso el módulo se deberá llamar `tech_iniciales` donde inciales son las de tu nombre.

El sistema debe basarse en **al menos 3 modelos relacionales** propios (además de los nativos de Odoo como `res.partner`).

### A. Modelo: Categorías de inventario (`tech.category`)

Define las reglas de préstamo para categorías de equipos.

- **Campos:** Nombre (ej: "Portátiles", "Drones"), Descripción.
- **Regla de Negocio:** Campo `max_days_loan` (Entero). Define cuántos días máximos se puede prestar un equipo de esta categoría por defecto.

### B. Modelo: Activos / Equipos (`tech.asset`)

Representa el objeto físico.

- **Campos:** Nombre, Número de Serie (Unique), Fecha de Compra, Coste, Imagen.
- **Estado:** Campo `Selection` (Disponible, Prestado, En Mantenimiento, Baja).
- **Relaciones:**
  - Con **Categorías**, ya que cada equipo pertenece a una categoría.
  - Con **Mantenimientos**, donde se verá el historial de mantenimientos de cada equipo.


### C. Modelo: Gestión de mantenimiento (`tech.maintenance`)

Registro de incidencias y reparaciones.

- **Campos:** Descripción de la avería, Fecha de inicio, Fecha de fin, Coste de reparación.
- **Relaciones:**
  - Con **Activos**, para indicar a qué equipo corresponde la avería.
  - Con `res.users` para hacer referencia al técnico responsable de la avería.


Al crear un mantenimiento activo, el estado del **Activo** asociado debe cambiar automáticamente a *En Mantenimiento*.


### D. Modelo: Control de préstamos (`tech.loan`)

El registro transaccional de quién tiene qué.

- **Campos:** Fecha Préstamo, Fecha Devolución Prevista, Estado (Borrador, Confirmado, Devuelto).
- **Relaciones:** vincula un **Activo** con un **Usuario** (`res.partner`).
- **Lógica de Fechas:** al seleccionar el equipo, la "Fecha Devolución Prevista" debe calcularse sola sumando los días configurados en su **Categoría**.



## 3. Lógica de Negocio y restricciones

El sistema debe ser robusto y prevenir errores humanos mediante validaciones en el código Python:

1. **Integridad del préstamo:** no se puede crear un préstamo para un equipo si su estado actual es "Prestado", "En Mantenimiento" o "Baja".
2. **Bloqueo de morosos:** el sistema debe impedir prestar equipos a un usuario (`res.partner`) que tenga préstamos activos cuya "Fecha Devolución Prevista" sea anterior a la fecha actual (préstamos caducados).
3. **Gestión de estados:** al confirmar un préstamo, el estado del equipo pasa a "Prestado". Al registrar la devolución, vuelve a "Disponible".



## 4. Desarrollo Frontend 

El cliente necesita un catálogo público para que los alumnos consulten el material desde sus casas sin entrar al backend.

En la URL `/iniciales/catalog/assets` (donde iniciales son las de tu nombre) mostrará una página web generada de forma dinámica que mostrará un listado de todos los activos que hay en el sistema.




## 5. API RESTful

El equipo de IT tiene una App móvil para los bedeles del centro y necesita consultar la base de datos en tiempo real.

- **Endpoint:** `/iniciales/api/assets`
- **Método:** `GET`
- **Autenticación:** sin autenticación
- **Funcionalidad:**
  - Debe devolver un **JSON** con la lista de equipos.
  - Debe aceptar un parámetro en la URL `?state=available` que filtre la respuesta para mostrar solo los equipos disponibles.


* **Estructura JSON Respuesta:**

```json
{
    "total_items": 15,
    "items": [
        {
            "id": 10,
            "name": "Cámara Canon EOS",
            "serial_number": "CN-998877",
            "category": "Audiovisual",
            "status": "available"
        },
        ...
    ]
}

```


## 6. Entrega del proyecto

El proyecto se entregará en la tarea creada a tal efecto en Teams y consistirá en:

- Código fuente del módulo comprimido en formato ZIP
- Vídeo donde se mostrará la funcionalidad del módulo con una duración no superior a 10 minutos
- Una breve memoria (con 2 o 3 páginas es suficiente) que contenga la estructura del modelo, decisiones tomadas y problemas encontrados.


## 7. Calificación

Para la calificación del proyecto se tendrán en cuenta los siguientes apartados.

1. **Backend y modelado de datos (35%)**: estructura de la base de datos y relaciones.
2. **Lógica de negocio y automatización (25%)**: Python, restricciones y cálculos.
3. **Frontend y API (25%)**: página web QWeb y Endpoint REST.
4. **Entregables y calidad (15%)**: código limpio, memoria y vídeo.

