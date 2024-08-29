# Modelo: `Facturas`

### Descripción

El modelo `Facturas` representa una factura en el sistema. Incluye información sobre el tipo de factura, numeración, estado, fecha de pago, monto y descripción.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único de la factura en la tabla `Facturas`.

-   **`tipo`**:

    -   Tipo: `ENUM('credito', 'contado', 'recibo')`
    -   No permite valores nulos.
    -   Descripción: Tipo de la factura (crédito, contado, recibo).

-   **`numeracion`**:

    -   Tipo: `STRING`
    -   Único: Sí.
    -   Descripción: Número de la factura. Debe ser único en el sistema.

-   **`estado`**:

    -   Tipo: `ENUM('pendiente', 'pagada', 'anulada')`
    -   No permite valores nulos.
    -   Descripción: Estado de la factura (pendiente, pagada, anulada).

-   **`fechaPago`**:

    -   Tipo: `DATEONLY`
    -   Descripción: Fecha en la que se realizó el pago de la factura. Es opcional.

-   **`monto`**:

    -   Tipo: `FLOAT`
    -   Descripción: Monto total de la factura.

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Descripción: Descripción adicional sobre la factura.

-   **`particularId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del cliente particular asociado a la factura. Referencia al modelo `Particulares`.

-   **`empresaId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador de la empresa asociada a la factura. Referencia al modelo `Empresas`.

### Relaciones

-   **Relación con `Particulares`**: 1 a N (Uno a Muchos)
-   **Relación con `Empresas`**: 1 a N (Uno a Muchos)
