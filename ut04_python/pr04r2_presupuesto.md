# UT04: El lenguaje de programación Python

## PR04R2: Calculadora de presupuesto personal

### Introducción

En este ejercicio vamos a desarrollar una aplicación que permita a los usuarios gestionar su presupuesto personal. La aplicación ayudará a los usuarios a registrar sus ingresos y gastos, calcular el saldo actual y proporcionar un resumen de las transacciones. Los datos se almacenarán en un archivo para proporcionarles persistencia.


### Requisitos funcionales

La aplicación deberá tener un menú con las siguientes opciones: 

1. **Agregar ingreso**: se solicitarán los siguientes datos al usuario:
    - Cantidad a ingresar
    - Categoría: podrá escoger entre categorías ya introducidas anteriormente o indicar una nueva. Es decir, cuando el usuario introduzca el primer ingreso no habrá ninguna categoría, por lo que tendrá que introducirla, en el siguiente ingreso podrá seleccionar la primera que introdujo, o crear una nueva, y así sucesivamente.
    - Descripción (opcional)
    - Fecha, en caso de dejar este campo en blanco se pondrá la fecha actual
2. **Agregar un gasto**: los datos serán análogos a los de ingresos, es decir, cantidad, categoría, descripción y fecha.
3. **Mostrar resumen de un mes**: se le solicitará al usuario un mes y un año y mostrará el resumen de ingresos y gastos de dicho mes por días. A continuación se muestra un ejemplo de cómo podrías mostrarlo.

    ```
    MES: FEBRERO    AÑO: 2025

    Día   Descripción           Ingreso     Gasto
    ---- --------------------- ----------- ----------
    1    Comida                            -45€
    2    Nómina                +1000€
    2    Ropa                              -100€
    ...
    ---- --------------------- ----------- ----------
        TOTAL                 +1000€      -145€
    ```
4. **Generar resumen mensual**: mostrará un resumen del total de gastos e ingresos por mes.

    ```
    MES     AÑO     INGRESOS        GASTOS
    ------- ------- --------------- ---------------
    Enero   2025    1500€           -890€
    Febrero 2025    1250€           -1200€
    ...
    ```
5. **Ingresos por categoría**: solicitará al usuario una categoría y mostrará un listados de todos los ingresos que hay en dicha categoría, así como el total de los mismos.
6. **Gastos por categoría**: igual que el punto anterior, pero para los gastos.
7. **Guardar en archivo**: guardará todos los datos del usuario en un archivo en formato CSV.
8. **Cargar archivo**: cargará los datos desde un archivo CSV.
9. **Salir**


### Consejos a tener en cuenta

- **Valida los datos** introducidos por el usuario para evitar errores
- Antes de empezar a codificar nada, ten muy claro qué **estructuras de datos** vas a utilizar y estudia si se adaptan bien a lo que pide el enunciado.
- Utiliza **funciones** para organizar el código. Recuerda que las funciones tienes que ser pequeñas y específicas, lo ideal es que cada función haga una única cosa y que la haga bien.
- **Divide el programa en tareas pequeñas** y vete avanzando poco a poco. Cada vez que implementes una funcionalidad, asegúrate de probarla bien antes de pasar a la siguiente.
- **Mantén el código limpio y legible**, utiliza comentarios y asigna nombres de variables representativos de lo que van a contener.
- Para mostrar información de **forma tabulada** por pantalla, puedes utilizar las características de las *f-strings* de Python que, entre otras funciones, permiten indicar el ancho mínimo que ocupará una cadena al imprimirla. Puedes acudir a la [documentación oficial](https://docs.python.org/es/3.13/tutorial/inputoutput.html#formatted-string-literals) para verlo en más detalle.

    ```python
    >>> desc = 'Comida'
    >>> cant = 45
    # La cadena desc ocupará por lo menos 10 caracteres y cant otros 10, ajustando el contenido a la deracha
    >>> print( f'{desc:10} - {cant:10d}' )
    Comida     -         45
    ```