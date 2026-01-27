# Proyecto Final: Sistema de Gestión de Inventario IT


## 1. Objetivo

En este proyecto actuaréis como desarrolladores backend. Un cliente real no os dará un diagrama de base de datos, sino una lista de problemas. Vuestra misión es interpretar esas necesidades y convertirlas en una estructura de módulos de Odoo funcional.

El ciente *TechSchool Solutions* e un centro educativo que presta material tecnológico (portátiles, tablets, cámaras) a alumnos y profesores. Actualmente usan una libreta de papel y es un desastre.


## 2. Requerimientos del cliente

Debéis desarrollar una solución que cubra estas tres necesidades fundamentales:

### A. El catálogo de equipos (Inventario)

Necesitan una "base de datos" donde registrar cada aparato físico que posee el centro.

- **Datos necesarios:** nombre del equipo, Número de Serie (único), Modelo y Estado (si funciona o está roto).
- **Organización:** los equipos deben estar clasificados por "Categoría" (ej: Ordenadores, Periféricos, Cables).

### B. El control de préstamos (La Lógica)

Necesitan registrar quién se lleva algo y cuándo.

* Se debe poder seleccionar un **Equipo** y un **Usuario** (usad el modelo `res.partner` que ya trae Odoo).
* Debe tener Fecha de Préstamo y Fecha de Devolución.
* **Validación Automática (Importante):** El sistema **no debe permitir** crear un préstamo nuevo para un equipo si ese equipo ya está prestado a otra persona y no ha sido devuelto. *Esto debéis programarlo con una restricción en Python.*

### C. Consulta Externa (API Web)

El equipo de desarrollo web del cliente quiere mostrar en su página pública qué equipos están libres.

* Necesitan que creéis una dirección web (URL) simple.
* Al entrar en esa dirección, el navegador debe mostrar un texto o JSON con la lista de equipos disponibles.

---

## 3. Especificaciones Técnicas

### Estructura de Módulos

El código debe estar organizado en módulos. Podéis hacer uno solo (ej: `tech_management`) o separarlo en dos, pero debe tener su estructura correcta:

* Carpeta `models` (código Python).
* Carpeta `views` (archivos XML).
* Archivo `__manifest__.py` con las dependencias correctas (`base`).

### Interfaz (Vistas)

No se pide diseño avanzado, solo funcionalidad:

* **Vista Lista (Tree):** Para ver el listado de equipos y préstamos.
* **Vista Formulario (Form):** La vista básica que genera Odoo para poder crear y editar los registros.

### Despliegue (Docker)

El proyecto debe entregarse listo para "levantar y usar".

* Debéis incluir un archivo `docker-compose.yml`.
* Este archivo debe arrancar dos servicios:
1. **Base de Datos** (PostgreSQL).
2. **Odoo** (conectado a esa base de datos y con acceso a vuestra carpeta de módulos).



---

## 4. Entregables

Subir un archivo comprimido (.zip) o enlace al repositorio git con:

1. **Código Fuente:** La carpeta de vuestro módulo.
2. **Docker Compose:** El archivo `.yml` para levantar el entorno.
3. **Instrucciones (Léeme):** Un archivo de texto breve explicando:
* Nombre del módulo a instalar.
* Usuario y contraseña de acceso al Odoo.
* La URL exacta para probar la parte de la API Web.



---

## 5. Criterios de Evaluación

| Criterio | Peso | Qué se valora |
| --- | --- | --- |
| **Estructura de Datos** | **30%** | ¿Están bien creados los Modelos? ¿Usáis correctamente `Many2one` para la Categoría y el Usuario? |
| **Lógica Python (Constraints)** | **30%** | ¿El sistema impide realmente prestar un equipo que ya está ocupado? (Esta es la parte más importante de programación). |
| **API / Controller** | **20%** | ¿Funciona la ruta web `@http.route`? ¿Muestra datos reales de la base de datos? |
| **Funcionamiento General** | **20%** | El `docker-compose` levanta sin errores. Se pueden crear, editar y guardar registros desde las vistas lista/formulario. |

---

### Pista para la API

Recordad que para hacer una página web o API en Odoo, necesitáis crear un archivo en una carpeta `controllers` y usar el decorador `@http.route`. No hace falta autenticación compleja, con `auth='public'` es suficiente para este nivel.