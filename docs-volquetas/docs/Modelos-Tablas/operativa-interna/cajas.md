# Modelo: `Cajas`

### Descripción

El modelo `Cajas` representa registros financieros en la caja, como gastos, ingresos, y otros movimientos contables. Cada registro incluye información sobre la fecha, motivo, descripción, moneda, monto, y referencias a empleados y pedidos relacionados.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `Cajas`.

-   **`fecha`**:

    -   Tipo: `DATEONLY`
    -   No permite valores nulos.
    -   Descripción: Fecha del movimiento registrado en la caja.

-   **`motivo`**:

    -   Tipo: `ENUM('vale', 'gasto', 'ingreso', 'ingreso pedido', 'ingreso cochera', 'extraccion')`
    -   No permite valores nulos.
    -   Descripción: Motivo del movimiento en la caja (vale, gasto, ingreso, etc.).

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Descripción opcional del movimiento.

-   **`moneda`**:

    -   Tipo: `ENUM('peso', 'dolar')`
    -   No permite valores nulos.
    -   Descripción: Tipo de moneda en el registro (peso o dólar).

-   **`monto`**:

    -   Tipo: `FLOAT`
    -   No permite valores nulos.
    -   Descripción: Monto del movimiento registrado en la caja.

-   **`empleadoId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Clave foránea que referencia al `Empleado` que realizó el movimiento, si aplica.

-   **`pedidoId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Clave foránea que referencia al `Pedido` asociado al movimiento, si aplica.

### Relaciones

1.  **Relación con `Empleados`**
    -   **Tipo**: N a 1 (Muchos a Uno)
2.  **Relación con `Pedidos`**
    -   **Tipo**: N a 1 (Muchos a Uno)
