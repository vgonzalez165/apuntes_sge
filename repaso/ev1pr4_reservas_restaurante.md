# PRÁCTICAS REPASO 1ª EVALUACIÓN

## EV1PR4: Calculadora de presupuesto personal

### Introducción

Siguiendo la línea de las prácticas anteriores, vamos a crear ahora un programa que nos ayude a gestionar las reservas de un restaurante. La estructura de este programa es muy parecida a la de otras prácticas que hemos realizado, pero es altamente recomendable que no mires dichas prácticas sino que intentes hacer tú solo la aplicación


### Requisitos funcionales

Desarrolla un programa en Python que permita gestionar las reservas de un restaurante. El programa debe cumplir con los siguientes requisitos:

1. **Menú principal**: el programa debe mostrar un menú con las siguientes opciones:
    - Ver todas las reservas.
    - Hacer una nueva reserva.
    - Cancelar una reserva.
    - Salir.

2. **Ver todas las reservas**: al seleccionar esta opción, el programa debe mostrar una lista de todas las reservas realizadas, incluyendo el nombre del cliente, la fecha, la hora y el número de personas.

3. **Hacer una nueva reserva**: El programa debe solicitar al usuario los siguientes datos:

    - Nombre del cliente.
    - Fecha de la reserva (en formato dd/mm/aaaa).
    - Hora de la reserva (en formato hh:mm).
    - Número de personas.
    - Número de teléfono del cliente
    
    El programa debe validar que la fecha y la hora sean futuras y que el número de personas sea mayor que 0. Una vez validados los datos, la reserva debe ser almacenada.

4. **Editar una reserva**: el usuario debe poder modificar el nombre del cliente, la fecha, la hora o el número de personas. El programa debe validar que los nuevos datos no superen la capacidad máxima del restaurante.

5. **Búsqueda de reservas**: se podrán buscar reservas por nombre de cliente o por feche, mostrando todas las reservas que coincidan con la búsqueda.

6. **Cancelar una reserva**: El programa debe solicitar el nombre del cliente y la fecha de la reserva que se desea cancelar. Si la reserva existe, debe ser eliminada del sistema. Si no existe, el programa debe mostrar un mensaje indicando que no se encontró la reserva.

7. **Salir**: El programa debe terminar su ejecución.


### Consejos a tener en cuenta

- Utiliza una lista para almacenar los diccionarios de reservas
- Implementa funciones para cada una de las opciones del menú.
- El programa debe seguir ejecutándose hasta que el usuario seleccione la opción de salir
- Verifica que los datos introducidos por el usuario sean correctos, por ejemplo, que la fecha tenga el formato correcto.
