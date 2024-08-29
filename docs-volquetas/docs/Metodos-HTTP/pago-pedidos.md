## Modelo: `PagoPedidos`

### Descripción

El modelo `PagoPedidos` representa el pago asociado a un pedido, con detalles como el precio, el estado de pago, el remito y el tipo de pago.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `PagoPedidos`.

-   **`precio`**:

    -   Tipo: `FLOAT`
    -   No permite valores nulos.
    -   Descripción: Monto del pago.

-   **`pagado`**:

    -   Tipo: `BOOLEAN`
    -   Valor por defecto: `false`
    -   Descripción: Indica si el pago ha sido realizado o no.

-   **`remito`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Número de remito asociado al pago.

-   **`tipoPago`**:

    -   Tipo: `ENUM('transferencia', 'efectivo', 'cheque')`
    -   Permite valores nulos.
    -   Descripción: Tipo de pago utilizado.

-   **`facturaId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador de la factura asociada al pago. Referencia al campo `id` del modelo `Facturas`.

### Relaciones

-   **Relación con `Facturas`**: N a 1 (Muchos a Uno)
