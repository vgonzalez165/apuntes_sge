# UT04: El lenguaje de programación Python

## PR04R4: Gestión de biblioteca

Desarrollar un programa en Python que gestione el inventario de una biblioteca, con funcionalidades como búsquedas, préstamos y estadísticas.

### **Requisitos**

Los datos se almacenarán en un diccionario llamado `biblioteca`, donde las **claves** son los ISBN de los libros (strings) y los **valores** son otro diccionario con:
```python
{
     "titulo": str,
     "autor": str,
     "año_publicacion": int,
     "copias_disponibles": int,
     "prestados": int  # Inicialmente 0
}
```  

Debes implementar las siguientes funciones:

- **`agregar_libro()`**: añade un nuevo libro a la biblioteca. Debes verificar que el ISBN no esté ya registrado.
- **`prestar_libro(isbn)`**: reduce `copias_disponibles` y aumenta `prestados`. Si no hay copias, muestra un mensaje.
- **`devolver_libro(isbn)`**: incrementa `copias_disponibles` y reduce `prestados`.
- **`buscar_por_titulo(titulo)`**: retorna una lista de libros cuyo título coincida (búsqueda parcial, case-insensitive).
- **`libros_mas_prestados()`**: retorna los 3 libros con más préstamos (orden descendente).  
- **`estadisticas()`**: muestra:
  - Total de libros únicos (por ISBN).
  - Total de ejemplares disponibles en toda la biblioteca.
  - Porcentaje de libros prestados respecto al total de copias.
