## Modelo: `Pedidos`

### Descripción

El modelo `Pedidos` representa los pedidos realizados en el sistema, con información sobre su estado, la obra asociada, el usuario que lo creó y otros detalles relevantes.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del pedido.

-   **`creadoPor`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del usuario que creó el pedido.
    -   Referencia: Relacionado con el modelo `Usuarios`.

-   **`obraId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador de la obra asociada al pedido.
    -   Referencia: Relacionado con el modelo `Obras`.

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Descripción: Descripción adicional del pedido.
    -   Permite valores nulos.

-   **`estado`**:

    -   Tipo: `ENUM`
    -   Valores posibles: `'iniciado'`, `'entregado'`, `'levantado'`, `'cancelado'`.
    -   Valor por defecto: `'iniciado'`.
    -   Descripción: Estado actual del pedido.

-   **`creadoComo`**:

    -   Tipo: `ENUM`
    -   Valores posibles: `'nuevo'`, `'recambio'`, `'multiple'`, `'entrega mas levante'`.
    -   No permite valores nulos.
    -   Descripción: Tipo de pedido creado.

-   **`permisoId`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Identificador del permiso asociado al pedido.
    -   Referencia: Relacionado con el modelo `Permisos`.

-   **`nroPesada`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Número de pesada asociado al pedido.

-   **`pagoPedidoId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del pago asociado al pedido.
    -   Referencia: Relacionado con el modelo `PagoPedidos`.

-   **`referenciaId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del pedido de referencia (en caso de ser un pedido relacionado con otro).
    -   Referencia: Relacionado con el modelo `Pedidos`.

### Relaciones

-   **Relación con `Usuarios`**: 1 a N (Uno a Muchos)
-   **Relación con `Obras`**: 1 a N (Uno a Muchos)
-   **Relación con `Permisos`**: N a 1 (Muchos a Uno)
-   **Relación con `PagoPedidos`**: 1 a 1 (Uno a Uno)
-   **Relación con `Pedidos`**: 1 a N (Uno a Muchos, auto-referencia)
-   **Relación con `Movimientos`**: 1 a 2 (Uno a Dos)
-   **Relación con `Sugerencias`**: 1 a 2 (Uno a Dos)
