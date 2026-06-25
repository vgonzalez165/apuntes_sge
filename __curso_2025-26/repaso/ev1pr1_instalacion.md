# PRÁCTICAS REPASO 1ª EVALUACIÓN

## EV1PR1: Entorno con Dockerfile 

Vamos a preparar un entorno de trabajo con Docker para trabajar con Odoo en desarrollo. El objetivo será levantar lo siguientes contenedores:
- Uno con Odoo 16 
- Otro con Postgres16
- Un último contenedor con pgAdmin que servirá para gestionar la base de datos

Para conseguirlo tienes que configurar un fichero Docker Compose que levante automáticamente todos los contenedores necesarios.

Algunas cuestiones que tienes que tener en cuenta:

- Tendrás un directorio llamado `odoo_repaso` (que puedes almacenar donde quieras) que contendrá todos los ficheros.
- Odoo estará disponible a través del puerto 18000 de la máquina física
- PostgreSQL estará disponible a través del puerto 19000 de la máquina física
- Dotarás de persistencia a la base de datos montando el directorio que la contiene en el directorio `odoo_repaso/database`
- Igualmente, el directorio de addons de Odoo estará mapeado sobre el directorio `odoo_repaso/addons`