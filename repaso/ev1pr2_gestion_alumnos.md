# PRÁCTICAS REPASO 1ª EVALUACIÓN

## EV1PR2: Gestión de alumnos

Vamos a crear un programa que permitirá gestionar las notas de los alumnos de un curso y calcular diversas estadísticas.

El programa almacenará la siguiente información:

- **Alumnos**: la información de los alumnos se guardará en un diccionario y constará de:
    - *Nombre y apellidos*
    - *Código*, que será un número entero asignado secuencialmente, siempre tendrá 4 caracteres (p.e. `0001` ó `0081`) y no se podrá repetir (aunque se haya eliminado el usuario que lo tenga).
    - *Módulos*: será una lista de diccionarios donde cada clave corresponderá a cada módulo en el que esté matriculado y el valor la nota en el mismo.

- **Módulos**: puedes elegir la estructura de datos que desees. Contendrá los módulos que hay disponibles.

Nuestra aplicación tendrá un menú con las siguientes funcionalidades:

1.	**Registrar módulo**: solicita el nombre del módulo y lo registra en el sistema. No se pueden registrar módulos que ya están registrados.
2.	**Ver módulos**: muestra los módulos que se han registrado.
3.	**Eliminar módulo**: elimina un módulo, si el nombre del módulo indicado no existe lo indicará mediante un aviso.
4.	**Matricular alumno**: pide datos del alumno y lo da de alta
5.	**Eliminar alumno**
6.	**Introducir nota**: pide el código del alumno, el nombre del módulo y la nota. Si se da alguno de estos casos mostrará un aviso indicando qué ha pasado y volverá al menú principal:
    - Si el código del alumno no existe
    - Si no hay ningún módulo con ese nombre
    - Si la nota no es un valor comprendido entre 0 y 10
7. **Mostrar alumnos**: mostrará una relación de todos los alumnnos con los módulos en los que están matriculados y sus notas
8. **Información de alumno**: se pide el código del alumno y mostrará por pantalla su nombre, los módulos en que está matriculado y sus notas.
9.	**Estadísticas**: pedirá el nombre de un módulo y mostrará:
    - La nota media en ese módulo
    - La mejor y peor nota, indicando para cada una el nombre del alumno que la ha obtenido
    - Número de aprobados (nota >= 5) y número de suspensos
    - Mediana: la mediana se calcula según la siguiente fórmula:
        - Se ordenan de menor a mayor los números cuya mediana queremos calcular
        - Si la cantidad de números es impar, la mediana será el número que está en el centro.
        - Si la cantidad de números es par, la mediana es el promedio de los dos valores centrales


