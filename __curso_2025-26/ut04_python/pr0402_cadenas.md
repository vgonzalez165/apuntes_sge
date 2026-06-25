# UT04: El lenguaje de programación Python

## PR0402: Ejercicios de cadenas

**NOTA**: para poder evaluar esta práctica como APTA debes haber realizado, por lo menos, 12 ejercicios de los propuestos.

### 1. Contar vocales y consonantes

Escribe una función que reciba una cadena y cuente cuántas vocales y consonantes contiene.

### 2. Invertir una cadena

Crea un programa que invierta una cadena.

### 3. Verificar palíndromo

Escribe un programa que verifique si una cadena es un palíndromo (se lee igual de izquierda a derecha y de derecha a izquierda).

### 4. Contar palabras

Crea una función que cuente cuántas palabras hay en una cadena, suponiendo que las palabras están separadas por espacios.

### 5. Eliminar caracteres repetidos

Escribe una función que elimine los caracteres duplicados en una cadena, manteniendo solo la primera aparición de cada uno.

### 6. Mayúsculas y minúsculas

Escribe un programa que convierta las letras minúsculas de una cadena en mayúsculas y viceversa.

### 7. Rotar caracteres de una cadena

Escribe una función que rote una cadena hacia la izquierda un número dado de veces.

**Ejemplo**: `"abcdef"` rotado 2 veces convierte la cadena en `"cdefab"`.

### 8. Anagrama

Crea un programa que verifique si dos cadenas son **anagramas**. Se considera que dos palabras son anagramas si tienen las mismas letras en diferente orden, por ejemplo, *lácteo* y *coleta*.

### 9. Frecuencia de caracteres (Este no)

Crea una función que reciba una cadena y devuelva un diccionario con la frecuencia de cada carácter.

### 10. Quitar caracteres alfanuméricos

Escribe un programa que elimine todos los caracteres no alfanuméricos (como signos de puntuación) de una cadena.

### 11. Transformar a camelCase

Escribe un programa que transforme una cadena de palabras separadas por espacios o guiones en formato camelCase (la primera letra de cada palabra, excepto la primera, debe ser mayúscula y no debe haber espacios ni guiones).

### 12. Codificación RLE (Run-Length Enconding)

Escribe una función que implemente la codificación por longitud de ejecución (RLE), que consiste en comprimir una cadena representando las secuencias consecutivas de caracteres iguales con el carácter seguido de la cantidad de repeticiones.

Por ejemplo, la cadena `aaron` la reemplazaría por `a2r1o1n1`. Por simplicidad, puedes asumir que un carácter no se va a repetir más de 9 veces consecutivas.

### 13. Decodificar RLE

Crea una función que decodifique una cadena que ha sido comprimida usando el método RLE.

### 14. Formateo de cadenas con plantillas (este no)

Escribe un programa que tome una plantilla de cadena y un diccionario, y reemplace los marcadores en la plantilla por los valores correspondientes en el diccionario.

**Ejemplo**: la cadena `"Hola, {nombre}"` con el diccionario `{"nombre": "Victor"}` debería devolver `"Hola, Victor"`

### 15. Comparar cadenas por valor ASCII

Escribe una función que compare dos cadenas sumando el valor ASCII de cada carácter y devuelva cuál tiene un mayor valor total. Para este ejercicio ten en cuenta que la función integrada `ord()` devuelve el valor ASCII de un carácter

### 16. Contar la longitud de palabra más larga

Escribe un programa que reciba una cadena y devuelva la longitud de la palabra más larga

### 17. Formatear número con separador de miles

Escribe una función que tome un número de forma de cadena y le agregue separadores de miles.

**Ejemplo**: `"123456756"` debería convertirse en `"123.456.789"`.

