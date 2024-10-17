# UT04: El lenguaje de programación Python

## PR0402: Cadenas en Python

### 1. Encontrar la subcadena más larga de caracteres únicos
Escribe un programa que encuentre la subcadena más larga en una cadena que no tenga caracteres repetidos, utilizando métodos de cadenas y estructuras auxiliares (como diccionarios o sets).

- **Ejemplo**: 
  - Para la cadena `"abcabcbb"`, el resultado debería ser `"abc"` con una longitud de 3.

---

### 2. Reformatear una cadena como un número de teléfono
Dada una cadena que contiene solo números y posiblemente algunos guiones o espacios, escribe un programa que reformatee la cadena para que tenga el formato de un número de teléfono estándar (XXX-XXX-XXXX). Usa métodos como `replace()`, `split()` o `join()`.

- **Ejemplo**: 
  - Para la cadena `"123 456 7890"`, el resultado debe ser `"123-456-7890"`.

---

### 3. Buscar la primera palabra con letras repetidas
Escribe un programa que encuentre la primera palabra en una cadena que contenga letras repetidas, utilizando métodos como `split()`, `set()`, `find()`, y `count()`.

- **Ejemplo**: 
  - Para la cadena `"hola mundo casa calle"`, el resultado debería ser `"calle"` porque tiene dos letras "l" repetidas.

---

### 4. Reorganizar una cadena por frecuencia de caracteres
Dada una cadena, escribe un programa que reorganice los caracteres de la cadena en función de la frecuencia con la que aparecen, de mayor a menor. Usa el método `count()` para contar las ocurrencias de cada carácter.

- **Ejemplo**: 
  - Para la cadena `"tree"`, el resultado debería ser `"eetr"` o `"eert"` (ya que la letra "e" aparece dos veces y las otras solo una).

---

### 5. Comprimir una cadena
Escribe un programa que comprima una cadena de caracteres contando las repeticiones consecutivas de cada carácter. Por ejemplo, `"aaabbcccc"` debería convertirse en `"a3b2c4"`. Si la cadena comprimida no es más corta que la original, devuelve la original.

- **Ejemplo**: 
  - Para la cadena `"aaabbcccc"`, el resultado debería ser `"a3b2c4"`, pero para `"abc"`, debería devolver `"abc"` (ya que la versión comprimida no sería más corta).


### 6. Rotar una cadena
Escribe un programa que tome una cadena y un número entero `n`, y devuelva la cadena rotada a la izquierda por `n` posiciones. Por ejemplo, rotar `"abcdef"` por 2 posiciones daría como resultado `"cdefab"`.

- **Ejemplo**:
  - Para la cadena `"python"` y `n=3`, el resultado debe ser `"honpyt"`.

---

### 7. Encontrar la subcadena más común
Escribe un programa que encuentre la subcadena de longitud `k` que más veces aparece en una cadena dada. Usa los métodos de cadena como `count()` para resolver el problema.

- **Ejemplo**:
  - Para la cadena `"ababab"` y `k=2`, el resultado debería ser `"ab"`, ya que aparece 3 veces.

---

### 8. Revertir las palabras de una cadena
Escribe un programa que invierta el orden de las palabras en una cadena, pero no los caracteres de las palabras. Usa `split()` y `join()` para trabajar con la cadena.

- **Ejemplo**:
  - Para la cadena `"Hola mundo desde Python"`, el resultado debe ser `"Python desde mundo Hola"`.

---

### 9. Intercambiar mayúsculas y minúsculas alternadamente
Dada una cadena, escribe un programa que convierta las letras a mayúsculas y minúsculas de forma alterna. Usa métodos como `isupper()`, `islower()`, `upper()`, y `lower()` para conseguirlo.

- **Ejemplo**:
  - Para la cadena `"python"`, el resultado debería ser `"PyThOn"`.

---

### 10. Encontrar el índice de la primera aparición de una subcadena
Escribe un programa que encuentre el índice de la primera aparición de una subcadena dentro de otra cadena sin utilizar el método `find()`. Debes implementar tu propia versión para buscar subcadenas.

- **Ejemplo**:
  - Para la cadena `"abracadabra"` y la subcadena `"cad"`, el resultado debería ser `4`.





Ejercicios Básicos:

    Contar vocales y consonantes: Escribe una función que reciba una cadena y cuente cuántas vocales y consonantes contiene.
    Invertir una cadena: Crea un programa que invierta una cadena sin usar funciones predefinidas de Python.
    Verificar palíndromo: Escribe un programa que verifique si una cadena es un palíndromo (se lee igual de izquierda a derecha y de derecha a izquierda).
    Contar palabras: Crea una función que cuente cuántas palabras hay en una cadena, suponiendo que las palabras están separadas por espacios.
    Eliminar caracteres repetidos: Escribe una función que elimine los caracteres duplicados en una cadena, manteniendo solo la primera aparición de cada uno.
    Mayúsculas y minúsculas: Escribe un programa que convierta las letras minúsculas de una cadena en mayúsculas y viceversa.

Ejercicios Intermedios:

    Buscar subcadena: Implementa una función que busque si una subcadena existe dentro de otra cadena.
    Reemplazar caracteres: Escribe un programa que reemplace todas las apariciones de un carácter en una cadena con otro carácter.
    Frecuencia de caracteres: Crea una función que cuente la frecuencia de aparición de cada carácter en una cadena.
    Eliminar espacios: Escribe un programa que elimine todos los espacios de una cadena.
    Formatear cadena: Dada una cadena de entrada, formatea la cadena de manera que la primera letra de cada palabra esté en mayúscula.
    Codificar una cadena (Cifrado César): Crea un programa que codifique una cadena utilizando un cifrado César simple, desplazando los caracteres un número determinado de posiciones en el alfabeto.
    Concatenar cadenas: Escribe un programa que tome una lista de cadenas y las combine en una sola cadena, separándolas por comas.
    Contar caracteres específicos: Crea un programa que cuente cuántas veces aparece un carácter específico en una cadena.
    Comprobar sufijo: Escribe una función que verifique si una cadena termina con un sufijo determinado.
    Eliminar caracteres no alfanuméricos: Implementa una función que elimine todos los caracteres que no sean letras o números de una cadena.

Ejercicios Avanzados:

    Expresión regular básica: Utiliza expresiones regulares para encontrar todas las direcciones de correo electrónico en un texto.
    Cifrado de palabras: Escribe un programa que codifique cada palabra de una cadena utilizando la primera letra de la palabra como clave y reordene el resto de las letras en orden alfabético.
    Anagramas: Crea una función que determine si dos cadenas son anagramas (si las letras de una cadena se pueden reordenar para formar la otra).
    Expandir abreviaciones: Escribe una función que expanda abreviaciones comunes en una cadena, por ejemplo, convertir "no." en "número" o "Sr." en "Señor".