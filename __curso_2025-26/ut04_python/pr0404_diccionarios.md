# UT04: El lenguaje de programación Python

## PR0404: Ejercicios con diccionarios

**NOTA**: para poder evaluar esta práctica como APTA debes haber realizado, por lo menos, 6 ejercicios de los propuestos.


### 1.- Buscar valor en un diccionario

Crea un diccionario de frutas y precios. Permite al usuario ingresar el nombre de una fruta y muestra su precio si existe en el diccionario, o un mensaje de que no está disponible en caso contrario.

### 2.- Contar elementos en un diccionario

Suponiendo un diccionario con al siguiente estructura, crea un programa que calcule cuántas categorías hay, cuántos productos tiene cada categoría y cuántos productos hay en total.

```bash
productos = {
    "Electrónica": ["Smartphone", "Laptop", "Tablet", "Auriculares", "Smartwatch"],
    "Hogar": ["Aspiradora", "Microondas", "Lámpara", "Sofá", "Cafetera"],
    "Ropa": ["Camisa", "Pantalones", "Chaqueta", "Zapatos", "Bufanda"],
    "Deportes": ["Pelota de fútbol", "Raqueta de tenis", "Bicicleta", "Pesas", "Cuerda de saltar"],
    "Juguetes": ["Muñeca", "Bloques de construcción", "Peluche", "Rompecabezas", "Coche de juguete"],
}
```

### 3.- Contador de frecuencias de palabras

Escribe un programa que tome una frase y use un diccionario para contar la frecuencia de cada palabra.

### 4.- Diccionario de listas

Supón un diccionario donde cada clave es una asignatura y el valor correspondiente una lista de estudiantes matriculados, tal como se muestra en el diccionario de ejemplo. Crea un programa que tenga un menú con tres opciones:
- Listar estudiantes matriculados en una asignatura
- Matricular un estudiante en una asignatura
- Dar de baja un estudiante de una asignatura.


```python
asignaturas = {
    "Matemáticas": ["Ana", "Carlos", "Luis", "María", "Jorge"],
    "Física": ["Elena", "Luis", "Juan", "Sofía"],
    "Programación": ["Ana", "Carlos", "Sofía", "Jorge", "Pedro"],
    "Historia": ["María", "Juan", "Elena", "Ana"],
    "Inglés": ["Carlos", "Sofía", "Jorge", "María"],
}
```


### 5.- Diccionario invertido

Escribe una función que tome un diccionario y devuelva otro con las claves y valores intercambiados (lo que antes eran valores ahora son claves, y viceversa). 

### 6.- Combinar dos diccionarios

Escribe un programa que tome dos diccionarios de productos y precios, y combine los productos comunes sumando sus precios, sin duplicar los elementos únicos.

### 7.- Filtrar claves y valores

Dado un diccionario de empleados y salarios, filtra e imprime solo los empleados con un salario mayor a un umbral definido.


### 8.- Anidación de diccionarios

Partiendo de un diccionario donde las claves son nombres de departamentos y los valores, diccionarios de empleados y sus puestos, tal como se ve en el código de ejemplo, crea un programa que permita realizar las siguientes funciones:
   - Mostrar el listado de todos los empleados de un departamento
   - Añadir un empleado a un departamento
   - Eliminar un empleado de un departamento

```python
departamentos = {
    "Recursos Humanos": {
        "Ana": "Gerente de Recursos Humanos",
        "Luis": "Especialista en Reclutamiento",
        "Elena": "Asistente de Recursos Humanos"
    },
    "Tecnología": {
        "Carlos": "Desarrollador Backend",
        "María": "Desarrolladora Frontend",
        "Pedro": "Administrador de Sistemas"
    },
    "Marketing": {
        "Sofía": "Directora de Marketing",
        "Jorge": "Especialista en SEO",
        "Laura": "Community Manager"
    },
    "Finanzas": {
        "Juan": "Analista Financiero",
        "Lucía": "Contadora",
        "Raúl": "Asesor Financiero"
    }
}
```


### 9.- Transformación de datos

Dado un diccionario con claves como nombres de estudiantes y valores como una lista de calificaciones, haz un programa que:
- Cree un nuevo diccionario que contenga el promedio de calificaciones para cada estudiante
- Crea otro diccionario que contengan la nota promedio en cada asignatura


```python
estudiantes = {
    "Ana": {"Matemáticas": 8.5, "Física": 9.0, "Programación": 7.8},
    "Carlos": {"Matemáticas": 9.2, "Física": 8.8, "Programación": 9.4},
    "Luis": {"Matemáticas": 7.6, "Física": 8.0, "Programación": 8.5},
    "María": {"Matemáticas": 9.5, "Física": 10.0, "Programación": 9.8},
    "Jorge": {"Matemáticas": 8.8, "Física": 8.4, "Programación": 7.9},
    "Sofía": {"Matemáticas": 9.1, "Física": 8.9, "Programación": 9.3}
}
```



