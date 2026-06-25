# **Proyecto de la 2ª Evaluación**. Extensión del modelo de suscripciones mediante métricas y estadísticas

## Descripción del proyecto

Como tenemos muy poco tiempo para desarrollar este proyecto, vamos a reutilizar las prácticas que hemos hecho con un módulo para la gestión de suscripciones. El objetivo será extender ese módulo con otro modelo de **Métricas y estadísticas**.


## Campos del modelo

El modelo tendrá los siguientes campos:

1. **Fecha**:
   - **Tipo**: `Date`
   - **Descripción**: fecha en la que se registran las métricas (puede ser diaria, semanal, mensual, etc.).
   - **Ejemplo**: `2023-10-01`.

2. **Número de suscripciones activas**:
   - **Tipo**: `Integer`
   - **Descripción**: cantidad total de suscripciones activas en la fecha indicada.
   - **Ejemplo**: `150`.

3. **Ingresos generados**:
   - **Tipo**: `Float`
   - **Descripción**: importe total de ingresos generados por las suscripciones en el período.
   - **Ejemplo**: `5000.00`.

4. **Tasa de renovación**:
   - **Tipo**: `Float`
   - **Descripción**: porcentaje de suscripciones que se renovaron en comparación con las que vencieron.
   - **Campo calculado**: `(Renovaciones / Suscripciones Activas) * 100`
   - **Ejemplo**: `85.5` (85.5%).

5. **Tasa de cancelación**:
   - **Tipo**: `Float`
   - **Descripción**: porcentaje de suscripciones canceladas en comparación con las activas.
   - **Campo calculado**: `(Cancelaciones / Suscripciones Activas) * 100`
   - **Ejemplo**: `10.2` (10.2%).

6. **Renovaciones**:
   - **Tipo**: `Integer`
   - **Descripción**: suscripciones que se han renovado.
   - **Ejemplo**: `40`

7. **Nuevas suscripciones**:
   - **Tipo**: `Integer`
   - **Descripción**: cantidad de nuevas suscripciones registradas en el período.
   - **Ejemplo**: `25`.

8. **Suscripciones canceladas**:
   - **Tipo**: `Integer`
   - **Descripción**: cantidad de suscripciones canceladas en el período.
   - **Ejemplo**: `15`.

9. **Clientes recurrentes vs nuevos**:
   - **Tipo**: `Integer` (dos campos separados)
   - **Descripción**:
     - `Clientes recurrentes`: número de clientes que renovaron su suscripción.
     - `Nuevos clientes`: número de clientes que adquirieron una suscripción por primera vez.
   - **Ejemplo**: `Recurrentes: 120`, `Nuevos: 30`.

10. **Ingresos promedio por usuario (ARPU)**:
   - **Tipo**: `Float`
   - **Descripción**: ingresos totales divididos por el número de suscripciones activas.
   - **Campo calculado**: `Ingresos Generados / Suscripciones Activas`.
   - **Ejemplo**: `33.33`.

11. **Tasa de conversión**:
    - **Tipo**: `Float`
    - **Descripción**: porcentaje de visitantes o leads que se convirtieron en suscriptores.
    - **Ejemplo**: `5.0` (5%).

12. **Churn Rate (Tasa de Pérdida de Clientes)**:
    - **Tipo**: `Float`
    - **Descripción**: porcentaje de clientes que cancelaron sus suscripciones en comparación con el total de clientes activos.
    - **Ejemplo**: `8.5` (8.5%).

13. **Lifetime Value (LTV)**:
    - **Tipo**: `Float`
    - **Descripción**: valor estimado que un cliente genera durante toda su relación con la empresa.
    - **Ejemplo**: `500.00`.

14. **Costo de adquisición de clientes (CAC)**:
    - **Tipo**: `Float`
    - **Descripción**: costo total de marketing y ventas dividido por el número de nuevos clientes adquiridos.
    - **Ejemplo**: `50.00`.

15. **Notas**:
    - **Tipo**: `Text`
    - **Descripción**: campo opcional para agregar observaciones o comentarios sobre las métricas.
    - **Ejemplo**: `"Promoción activa durante este período"`.

16. **Relación con el Modelo de Suscripciones**:
   - **Tipo**: `Uno a muchos` (desde Métricas hacia Suscripciones).
   - **Descripción**: permite vincular las métricas con las suscripciones activas o canceladas en un período específico.

## Vistas

Agrega una entrada de menú para visualizar este modelo y crea una vista de formulario en la que la información se presente claramente y de forma organizada


## Criterios de evaluación

| Concepto                 | Puntos   |
|--------------------------|----------|
| Estructura del modelo    | 3 puntos |
| Funcionalidad y cálculos | 3 puntos |
| Vista                    | 3 puntos |
| Claridad y documentación | 1 puntos |



