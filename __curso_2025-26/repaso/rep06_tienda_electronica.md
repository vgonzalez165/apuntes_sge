## REP06: Gestión de inventario y cadena de suministro para electrónica

El objetivo de esta práctica es diseñar y desarrollar un **módulo personalizado de Odoo** para la gestión de inventario, proveedores, pedidos de compra y, crucialmente, la **visualización en tiempo real de las necesidades de reabastecimiento** a través de una página web dinámica.

## Requisitos funcionales

Tu módulo deberá tener los siguientes modelos:

### `suministro.proveedor`

* Campos:
    * `name` (nombre del proveedor)
    * `contacto_principal`
    * `tiempo_entrega_dias` (Tiempo promedio que tarda en enviar un pedido)
* Relaciones:
    * `One2many` con `producto` (Productos que suministra).

### `suministro.producto`

* Campos:
    * `nombre_producto`
    * `sku` (Código único de inventario)
    * `precio_venta`
    * **`stock_actual`** (Calculado: suma de las entradas menos las salidas en `movimiento_stock`)
    * `stock_minimo_reabastecimiento` (Nivel en el que se debe generar una orden de compra)
    * **`stock_objetivo`** (Nivel de stock ideal al que se quiere reabastecer).
* Relaciones:
    * `Many2one` con `proveedor`
    * `One2many` con `movimiento_stock` (Historial de movimientos de este producto).

### `suministro.orden_compra`

* Campos:
    * `fecha_pedido`
    * `estado_pedido` (Borrador, Enviado a Proveedor, Recibido Parcial, Recibido Completo)
    * **`coste_total_calculado`** (Calculado por las líneas de la orden).
* Relaciones:
    * `Many2one` con `proveedor`
    * `One2many` con `linea_orden_compra`.

### `suministro.linea_orden_compra`

* Campos:
    * `cantidad_pedida`
    * `precio_unitario_acordado`
    * `cantidad_recibida`
    * **`cantidad_pendiente`** (Calculado: `cantidad_pedida` - `cantidad_recibida`)
* Relaciones:
    * `Many2one` con `orden_compra`
    * `Many2one` con `producto`

### `suministro.movimiento_stock`

* Campos:
    * `fecha_movimiento`
    * `tipo_movimiento` (Entrada, Salida, Ajuste)
    * `cantidad`
    * `origen_destino` (Ej: Venta, Recepción de OC #123)
* Relaciones:
    * `Many2one` con `producto`.



## Interfaz de usuario (vistas)

El módulo debe incluir una **interfaz gráfica completa** para cada uno de los modelos definidos, con una vista tipo árbol y otra tipo formulario por modelo.

Además:

### Modelo `suministro.producto`

* Debe tener un campo calculado **`necesidad_reabastecimiento`** que sea igual a `stock_objetivo` - `stock_actual` (solo si el resultado es positivo). Si `stock_actual` es suficiente, el valor es 0.
* El campo `stock_actual` debe colorearse:
    * `stock_actual` > `stock_minimo_reabastecimiento` → verde
    * `stock_actual` bajo (entre 1 y `stock_minimo_reabastecimiento`) → naranja
    * `stock_actual` = 0 → rojo
* **Botón de Acción:** *"Generar Orden de Compra"* (Solo visible si `necesidad_reabastecimiento` > 0).

### Modelo `suministro.orden_compra`

* Debe tener un campo calculado que muestre el **% recibido** de la orden.
* **Botón de Acción:** *"Registrar Recepción y Actualizar Stock"* (Que genera un `movimiento_stock` de tipo "Entrada" con la `cantidad_recibida`).

## Portal web (planificación y reabastecimiento)

El módulo debe incluir un **controlador web** que genere una página web dinámica accesible a través de una URL de la forma `/suministro/necesidades`.

### 1. Panel de control de reabastecimiento (/suministro/necesidades)

El objetivo de este panel será proporcionar una visión consolidada y en tiempo real de qué productos necesitan ser pedidos.

* **Contenido Dinámico:**
    * **Sección 1: Productos Críticos (Stock Cero)**
        * Listado de todos los `suministro.producto`s con `stock_actual` igual a **cero**.
        * Mostrar el `nombre_producto`, `proveedor` y la `necesidad_reabastecimiento` (la cantidad a pedir).
    * **Sección 2: Productos Pendientes de Pedir**
        * Listado de todos los `suministro.producto`s donde `stock_actual` es menor que `stock_minimo_reabastecimiento`, pero mayor que cero.
        * Mostrar el `nombre_producto`, `proveedor` y la `necesidad_reabastecimiento`.
    * **Sección 3: Órdenes de Compra en Tránsito**
        * Listado de todas las `orden_compra`s en estado **"Enviado a Proveedor"**.
        * Mostrar `fecha_pedido`, `proveedor`, y el **porcentaje de productos recibidos** (campo calculado).
    * **Botón de Acción en la Web:** Debe haber un botón al lado de cada producto en las Secciones 1 y 2 que diga **"Añadir a Borrador de Orden"**. Al hacer clic, se debe crear (o añadir a una orden de compra existente en borrador) una `linea_orden_compra` con la cantidad necesaria.