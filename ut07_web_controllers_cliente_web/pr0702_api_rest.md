# UT07: Web Controllers y cliente Web

## PR0702: API REST

### ¿Qué vamos a aprender?

Repasaremos los fundamentos de las API REST implementando un par de llamadas


### ¿Qué hay que hacer?

Modifica el módulo de **suscripciones** de la práctica anterior para añadirle una API REST con dos endpoints. Estos serán:

- `GET /api/suscription`: devolverá una relación de todas las suscripciones que hay en la base de datos. Esta llamada podrá recibir una query string con el nombre *status* que filtrará las suscripciones devueltas según el estado. Si el valor de la query string no es uno de los permitidos deberá devolver un estado 400 (Bad request) con un mensaje de error.
- `GET /api/suscription/:name`: devolverá toda la información de una suscripción cuyo nombre se pase en el parámetro `:name`

### ¿Has acabado y quieres más?

Modifica la llamada `GET /api/suscription` para que admita en la query string el nombre `page` para que me devuelva los resultados paginados. Por ejemplo: `/api/suscription?page=3` devolvería la tercera página (registros del 21 al 30 si suponemos 10 elementos por página)

### ¿Qué hay que entregar?

Debes entregar:

- Al igual que todas las prácticas, tendrás que documentar los pasos más relevantes en formato Markdown e incluirlo en tu repositorio.
- En la documentación tienes que incluir el código de todos los ficheros del proyecto que edites.
- También debe incluir una captura de pantalla donde se vea la vista de formualario mostrando todos los campos rellenos.


[Volver al índice](../index.html)