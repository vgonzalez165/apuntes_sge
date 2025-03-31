# UT04: El lenguaje de programación Python

## PR04R5: Gestión de viajes en coche

Debes desarrollar un programa en Python que permita gestionar viajes, almacenar información relevante y realizar cálculos automáticos como costes, distancias o duraciones en función de los datos introducidos

### **Requisitos**

La aplicación tendrá un menú con las siguientes opciones:

```
1. Añadir vehículo
2. Mostrar vehículos
3. Eliminar vehículo
4. Añadir nuevo viaje  
5. Mostrar todos los viajes  
6. Buscar viajes por destino  
7. Estadísticas de coste  
8. Estadísticas por vehículo  
9. Mostrar viajes más cortos/largos  
Q. Salir  
```

Las opciones más relevantes son:

- **1. Añadir vehículo**: se pedirán los siguientes datos:
  - Marca y modelo
  - Número de pasajeros
  - Combustible: puede ser gasolina, gasóleo o GLP
  - Consumo: en litros a los 100 km

- **4. Añadir nuevo viaje**: solicitará al usuario los siguientes datos:
  - Nombre del viaje (p.e. Vacaciones en Soria)
  - Destino
  - Fecha
  - Vehículo: a escoger entre los que se hayan dado de alta
  - Pasajeros: si el número de pasajeros es superior a la capacidad del vehículo mostrará un error.
  - Distancia: en kilómetros

- **5. Mostrar todos los viajes**: mostrará todos los viajes registrados añadiendo la siguiente información a cada viaje:
  - Coste del viaje
  - Coste del viaje por pasajero

- **6. Buscar viajes por destino**: solicitará un destino y mostrará todos los viajes a ese destino.

- **7. Estadísticas de coste**: se mostrará la siguiente información relativa a todos los viajes realizados:
  - Coste total de todos los viajes
  - Coste medio por pasajero entre todos los viajes

- **8. Estadísticas por vehículo**: se mostrará una tabla en la que cada fila corresponderá a un vehículo y en las columnas tendrá la siguiente información:
  - Kilómetros totales
  - Combustible
  - Precio por litro del combustible
  - Coste total de todos los viajes
  - Media de pasajeros por viaje
  - Coste medio por pasajero cada 100 km

- **9. Mostrar viajes más cortos y largos**: mostrará los 3 viajes más cortos y los 3 viajes más largos.

