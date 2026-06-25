# PRÁCTICAS REPASO 1ª EVALUACIÓN

## EV1PR7: Ejercicios cortos de listas y diccionarios


### 1.- Análisis de calificaciones


Partiendo de una lista con la siguiente estructura:

```python
calificaciones = [
    {"nombre": "Ana", "notas": [7.5, 8.0, 6.5]},
    {"nombre": "Luis", "notas": [4.0, 5.5, 6.0]},
    {"nombre": "Marta", "notas": [9.0, 8.5, 9.5]},
]
```

Realiza las siguientes tareas:

1. Calcula la nota media de cada alumno.
2. Crea una nueva lista con los alumnos que tienen una media igual o superior a 7.
3. Muestra un resumen general indicando:
   - Número total de alumnos
   - Media global de todas las notas
   - Nombre del alumno con mejor media


### 2.- Inventario de productos

**Objetivo:** Gestionar un inventario representado con un diccionario y realizar operaciones de consulta y modificación.

### Enunciado:

Para este ejercicio trabajaremos con un diccionario que representa un inventario con la siguiente estructura:

```python
inventario = {
    "ratón": {"precio": 12.5, "stock": 25},
    "teclado": {"precio": 20.0, "stock": 12},
    "monitor": {"precio": 150.0, "stock": 7}
}
```

Implementa funciones para realizar las siguientes operaciones:

1. Escribe una función que reciba un producto y devuelva su precio y stock.
2. Escribe una función que permita actualizar el stock de un producto tras una venta.
3. Muestra una lista ordenada por precio de menor a mayor.
4. Calcula el valor total del inventario (precio × stock de cada producto).


### 3.- Ranking de palabras

En esta práctica trabajaremos con un texto que puedes tener almacenado en una variable

```python
texto = "python es fácil de aprender y python es muy útil en ciencia de datos y desarrollo web"
```

El objetivo será crear funciones para realizar las siguientes operaciones sobre el texto.

1. Crea un diccionario donde las claves sean las palabras y los valores su número de apariciones.
2. Muestra las palabras más repetidas (top 3).
3. Convierte el diccionario en una lista de tuplas ordenadas por frecuencia descendente.
4. Elimina palabras que solo aparecen una vez.


### 4.- Agrupación por categorías

Suponiendo la siguiente estructura de datos:

```python
productos = [
    {"nombre": "manzana", "categoria": "fruta"},
    {"nombre": "zanahoria", "categoria": "verdura"},
    {"nombre": "plátano", "categoria": "fruta"},
    {"nombre": "lechuga", "categoria": "verdura"},
    {"nombre": "pera", "categoria": "fruta"},
]
```

Realiza las siguientes operaciones:

1. Crea un diccionario donde las claves sean las categorías y los valores sean listas de productos de esa categoría.
2. Imprime las frutas y las verduras por separado.
3. Añade una nueva categoría "otros" e incluye un nuevo producto.
4. Escribe una función que reciba el nombre de una categoría y devuelva los productos de esa categoría.

