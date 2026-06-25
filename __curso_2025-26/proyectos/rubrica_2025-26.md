### Rúbrica de Evaluación: Proyecto Odoo - TechSchool Solutions

---

#### 1. Backend y modelado de datos (35% - Hasta 3.5 puntos)

*Evalúa la correcta definición arquitectónica en Odoo, relaciones de base de datos y vistas.*

| Criterio | Excelente (3.5 pts) | Bien (2.6 pts) | Suficiente (1.75 pts) | Insuficiente (0 - 0.8 pts) |
| --- | --- | --- | --- | --- |
| **Modelos y Nomenclatura** | El módulo se llama correctamente `tech_iniciales`. Se han creado los 4 modelos requeridos con todos sus campos exactos y el campo `Número de Serie` tiene restricción *Unique*. | El módulo tiene el nombre correcto y los modelos existen, pero falta algún campo secundario o la restricción de unicidad falla. | El nombre del módulo es incorrecto o falta algún modelo principal. Tipos de datos básicos mal definidos. | No se ha creado la estructura de modelos o da errores de base de datos al instalar. |
| **Relaciones (ORM)** | Uso perfecto de `Many2one` y/o `One2many` entre Categorías-Activos, Mantenimientos-Activos/Usuarios y Préstamos-Activos/Partners. | Relaciones creadas correctamente pero alguna no es bidireccional cuando debería, o el borrado en cascada está mal configurado. | Faltan relaciones clave (ej. Préstamo no enlaza con el Activo real, sino que usa un campo de texto). | No hay relaciones entre modelos. Base de datos no relacional. |
| **Vistas e Interfaz** *(No explícito en el texto, pero necesario en Odoo)* | Menús, vistas *Tree* y *Form* bien estructuradas, intuitivas y que permiten gestionar todos los modelos. | Vistas funcionales pero desordenadas o sin adaptar (muestran todos los campos por defecto). | Las vistas existen pero algunas no cargan o son inaccesibles desde el menú. | No se han creado vistas; no se puede interactuar desde el backend. |

---

#### 2. Lógica de negocio y automatización (25% - Hasta 2.5 puntos)

*Evalúa el código Python (ORM, `@api.depends`, `@api.constrains`, `@api.onchange`) para asegurar la solidez del sistema.*

| Criterio | Excelente (2.5 pts) | Bien (1.8 pts) | Suficiente (1.25 pts) | Insuficiente (0 - 0.6 pts) |
| --- | --- | --- | --- | --- |
| **Cálculo de Fechas** | La "Fecha Devolución Prevista" se autocalcula sin fallos al seleccionar el equipo, sumando los días definidos en la Categoría. | El cálculo funciona, pero requiere guardar el registro antes de actualizarse, o falla en casos límite (bisiestos, etc.). | El cálculo a veces falla o requiere intervención manual del usuario para actualizarse. | No hay cálculo automático; la fecha se debe introducir manualmente. |
| **Gestión de Estados** | El flujo de estados (Disponible -> Prestado -> Disponible) y el paso a "En Mantenimiento" es 100% automático e impecable. | La mayoría de los estados cambian correctamente, pero hay algún fallo menor (ej. al terminar mantenimiento no vuelve a disponible). | Solo funciona la mitad de la automatización de estados; el resto es manual. | Los estados no se actualizan automáticamente en ningún caso. |
| **Restricciones y Validaciones** | Impide perfectamente prestar equipos no disponibles (Raise ValidationError) y bloquea a los morosos con préstamos caducados. | Las validaciones funcionan pero los mensajes de error son confusos o no bloquean al usuario moroso en el 100% de los casos. | Falla una de las dos validaciones principales (se pueden prestar equipos averiados o se presta a morosos). | No hay control de errores ni validaciones implementadas en Python. |

---

#### 3. Frontend y API (25% - Hasta 2.5 puntos)

*Evalúa la capacidad de exponer los datos hacia el exterior mediante controladores y rutas web.*

| Criterio | Excelente (2.5 pts) | Bien (1.8 pts) | Suficiente (1.25 pts) | Insuficiente (0 - 0.6 pts) |
| --- | --- | --- | --- | --- |
| **Frontend Web (QWeb)** | Ruta `/iniciales/catalog/assets` accesible, renderiza dinámicamente todos los activos usando una plantilla QWeb limpia. | La ruta funciona y muestra datos, pero el código de la plantilla está muy desordenado o no usa QWeb correctamente. | La página carga pero muestra datos estáticos, o la ruta no cumple con el formato solicitado. | No hay página web o da error 500 al intentar acceder. |
| **API RESTful** | Ruta `/iniciales/api/assets` exacta, devuelve el JSON *exactamente* con la estructura solicitada. | Devuelve los datos en JSON pero la estructura de las claves (keys) difiere ligeramente del modelo pedido. | La API responde pero no es JSON válido, o el formato es completamente distinto al solicitado. | El endpoint de la API no existe o no responde. |
| **Filtrado API** | El parámetro `?state=available` funciona perfectamente y filtra la consulta desde la base de datos de manera óptima. | El filtro funciona, pero lo hace procesando todos los datos en Python en lugar de filtrar en el `search` del ORM. | El filtro ignora el parámetro de la URL y devuelve siempre todo, o rompe la API. | No se ha intentado implementar el filtrado. |

---

#### 4. Entregables y calidad (15% - Hasta 1.5 puntos)

*Evalúa el cumplimiento de las normas de entrega, la reflexión técnica y el código limpio.*

| Criterio | Excelente (1.5 pts) | Bien (1.1 pts) | Suficiente (0.75 pts) | Insuficiente (0 - 0.3 pts) |
| --- | --- | --- | --- | --- |
| **Memoria Técnica** | Documento de 2-3 páginas muy claro. Explica excelentemente el modelo E/R, las decisiones tomadas y los bloqueos resueltos. | La memoria está entregada pero le falta profundidad técnica o no menciona los problemas encontrados. | Memoria muy escueta (1 página), incompleta, o que parece un mero manual de usuario. | No se entrega memoria o no tiene relación con el proyecto. |
| **Vídeo Demostrativo** | Menos de 10 minutos, audio claro, demuestra fluidamente el backend, web, API (Postman/Navegador) y restricciones. | El vídeo demuestra lo básico pero excede los 10 minutos, o el audio es muy deficiente. | Vídeo incompleto (solo muestra backend y omite la API, por ejemplo). | No hay vídeo o no se demuestra el funcionamiento del módulo. |
| **Calidad del Código** | Código Python y XML indentado, limpio, siguiendo la guía de estilos de Odoo/PEP8 y sin dependencias o archivos "basura". | Código funcional pero algo desordenado, comentarios innecesarios o variables mal nombradas. | Código difícil de leer, mal tabulado que dificulta la corrección del proyecto. | Entrega incompleta, sin el archivo ZIP o con archivos que no pertenecen a Odoo. |

---