# Modelo: `Sugerencias`

### Descripción

El modelo `Sugerencias` representa las sugerencias asociadas a pedidos, incluyendo el horario sugerido, el chofer recomendado y el tipo de sugerencia (entrega o levante).

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental: Sí
    -   Clave primaria: Sí
    -   Descripción: Identificador único de la sugerencia.

-   **`horarioSugerido`**:

    -   Tipo: `DATE`
    -   Permite valores nulos.
    -   Descripción: Horario sugerido para la acción recomendada.

-   **`choferSugeridoId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del chofer recomendado para el pedido.
    -   Referencia: Relacionado con el modelo `Empleados`.

-   **`tipoSugerido`**:

    -   Tipo: `ENUM('entrega', 'levante')`
    -   No permite valores nulos.
    -   Descripción: Tipo de acción sugerida (entrega o levante).

-   **`pedidoId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del pedido asociado a la sugerencia.
    -   Referencia: Relacionado con el modelo `Pedidos`.

### Relaciones

-   **Relación con `Empleados`**: N a 1 (Muchos a Uno)
-   **Relación con `Pedidos`**: N a 1 (Muchos a Uno)
