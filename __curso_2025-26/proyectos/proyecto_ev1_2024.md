# Proyecto de la 1ª Evaluación

## Sistema de gestión de tareas pendientes

### Descripción del proyecto

Crear una aplicación de consola que permita gestionar una lista de tareas. Cada tarea tendrá, por lo menos, las siguientes propiedades: 
- Nombre de la tarea
- Prioridad
- Fecha límite
- Si está completada o no.

Opcionalmente, podrás añadirle nuevas propiedades si quieres ampliar la funcionalidad de tu aplicación.


### Funcionalidades

- **Añadir tarea**: solicitará al usuario los datos de la tarea (nombre, prioridad y fecha límite) y los guardará en una lista de diccionarios.
- **Listar tareas**: mostrará todas las tareas pendientes, indicando sus detalles y resaltando si alguna está vencida.
- **Marcar tarea como completada**: cambiará el estado de una tarea a *completada* usando el índice.
- **Eliminar tarea**: permitirá al usuario borrar tareas que ya no necesita.
- **Guardar y cargar desde fichero**: Al salir, guardar las tareas en un fichero CSV, y al iniciar, cargar las tareas previamente guardadas. 
- **Tareas vencidas**: opcionalmente dispondrá de la posibilidad de notificar al usuario sobre las tareas que han vencido.


### Recursos

Algunos recursos que te pueden resultar interesantes para realizar este proyecto:

- [Ficheros CSV en Python](https://realpython.com/python-csv/)
- [Coloreando la salida de Python en la terminal](https://sentry.io/answers/print-colored-text-to-terminal-with-python/)
- [Manipulación de fechas y horas en Python](https://www.programaenpython.com/fundamentos/fechas-y-horas-en-python/)


### Calificación del proyecto

La calificación del proyecto se obtendrá a partir de la siguiente rúbrica:

| **Criterio**                | **Descripción**                                                                                         | **Puntos**    |
|-----------------------------|---------------------------------------------------------------------------------------------------------|---------------|
| **FUNCIONALIDAD**           |                                                                                                         | **40 puntos** |
| **Añadir Tarea**            | Permite añadir tareas correctamente con todos los campos requeridos.                                    | 0 - 10        |
| **Listar Tareas**           | Muestra correctamente todas las tareas, incluyendo detalles, estado de vencimiento, y completadas.      | 0 - 10        |
| **Marcar como Completada**  | Permite al usuario marcar tareas como completadas de manera precisa.                                    | 0 - 5         |
| **Eliminar Tarea**          | Elimina las tareas seleccionadas sin errores ni impactos negativos en otras funcionalidades.            | 0 - 5         |
| **Guardar/Cargar Tareas**   | Guarda y carga datos correctamente en el formato especificado (CSV).                                    | 0 - 10        |
| **PRESENTACIÓN**            |                                                                                                         | **30 puntos** |
| **Documentación del Código**| Código comentado y estructurado, explicando secciones importantes y documentando funciones.             | 0 - 10        |
| **Claridad de Código**      | Código claro y fácil de seguir; uso adecuado de nombres de variables, estructura y separación lógica.   | 0 - 10        |
| **Formato de Salida**       | Salida legible y organizada en la consola, con mensajes de usuario claros y formato de visualización.   | 0 - 10        |
| **CORRECTITUD Y PRUEBAS**   |                                                                                                         | **20 puntos** |
| **Pruebas Básicas**         | Realización de pruebas que cubren las funciones principales: añadir, listar, completar y eliminar.      | 0 - 10        |
| **Manejo de Errores**       | Captura y gestión de errores comunes (entrada de usuario, problemas de carga/guardar ficheros, etc.).   | 0 - 10        |
| **CREATIVIDAD Y MEJORA**    |                                                                                                         | **10 puntos** |
| **Opcional: Fechas Vencidas** | Funcionalidad para mostrar si alguna tarea ha vencido, usando manejo de fechas (opcional).            | 0 - 5         |
| **Extras y Mejoras**        | Añadidos interesantes que mejoran la funcionalidad o usabilidad (por ejemplo, prioridades, filtros).    | 0 - 5         |
| **Puntuación Total**        |                                                                                                         | **100 puntos**|
