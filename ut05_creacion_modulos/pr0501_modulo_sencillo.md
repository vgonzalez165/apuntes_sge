# UT05: Desarrollo de componentes. Primer módulo

## PR0501: Creación de un módulo básico

### ¿Qué vamos a aprender?

En esta práctica repasaremos los conceptos básicos de creación de módulos en Odoo mediante la implementación de un módulo sencillo de **Gestión de reserva de salas**.

### ¿Qué recursos me pueden ser útiles?

A continuación se indican algunos recursos que complementan los apuntes del módulo y que te pueden ser útiles para realizar esta práctica:

- [Campos básicos del modelo](https://www.odoo.com/documentation/16.0/es/developer/tutorials/getting_started/04_basicmodel.html)


### ¿Qué hay que hacer?

El objetivo de esta práctica es crear un módulo en Odoo que gestione reservas de salas en una empresa. Cada reserva tendrá los siguientes campos:

- **Nombre de la Sala**, de tipo texto.
- **Capacidad**, de tipo entero.
- **Fecha de Reserva**, de tipo fecha.
- **Reservada**, de tipo booleano,indicará si está disponible o no.
- **Comentarios** de tipo texto.

El módulo incluirá un sistema de menús con tres niveles. Los menús tendrán la siguiente estructura:

```
Gestión de salas
   |
   |-- Salas
         |
         |--Salas Disponibles
```

### ¿Qué hay que entregar?

Debes entregar:

- Al igual que todas las prácticas, tendrás que documentar los pasos más relevantes en formato Markdown e incluirlo en tu repositorio.
- En la documentación tienes que incluir el código de todos los ficheros del proyecto que edites.
- También debe incluir una captura de pantalla donde se vea que el módulo funciona correctamente.


[Volver al índice](../index.html)