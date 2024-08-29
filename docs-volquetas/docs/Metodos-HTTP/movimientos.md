## Modelo: `Movimientos`

### Descripción

El modelo `Movimientos` registra los movimientos de las volquetas asociados a pedidos. Incluye información sobre el número de volqueta, el pedido asociado, el horario del movimiento, el tipo de movimiento y el chofer responsable.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `Movimientos`.

-   **`numeroVolqueta`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Número de la volqueta asociada al movimiento. Referencia al campo `numeroVolqueta` del modelo `Volquetas`.

-   **`pedidoId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del pedido asociado al movimiento. Referencia al campo `id` del modelo `Pedidos`.

-   **`horario`**:

    -   Tipo: `DATE`
    -   No permite valores nulos.
    -   Descripción: Fecha y hora del movimiento.

-   **`tipo`**:

    -   Tipo: `ENUM`
    -   Valores posibles: `'entrega'`, `'levante'`
    -   Descripción: Tipo de movimiento registrado.

-   **`choferId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del chofer responsable del movimiento. Referencia al campo `id` del modelo `Empleados`.

### Relaciones

-   **Relación con `Volquetas`**: N a 1 (Muchos a Uno)
-   **Relación con `Pedidos`**: N a 1 (Muchos a Uno)
-   **Relación con `Empleados`**: N a 1 (Muchos a Uno)
