## Modelo: `Config`

### Descripción

El modelo `Config` representa la configuración relacionada con precios y horas de trabajo. Incluye información sobre el precio sin IVA, el precio con IVA, el año de la configuración y si la configuración está activa.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `Config`.

-   **`anio`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Año asociado a la configuración.

-   **`precioSinIva`**:

    -   Tipo: `FLOAT`
    -   Permite valores nulos.
    -   Descripción: Precio base sin IVA.

-   **`precioConIva`**:

    -   Tipo: `FLOAT`
    -   Permite valores nulos.
    -   Descripción: Precio con IVA. Este campo se calcula automáticamente basado en `precioSinIva`.

-   **`horasDeTrabajo`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Número de horas de trabajo asociadas a la configuración.

-   **`configActiva`**:

    -   Tipo: `BOOLEAN`
    -   Permite valores nulos.
    -   Descripción: Indica si la configuración está activa (`true`) o no (`false`).

### Hooks

-   **`beforeCreate`**: Calcula el `precioConIva` antes de que se cree un nuevo registro. Si `precioSinIva` tiene un valor, `precioConIva` se establece en `precioSinIva * 1.22`.

-   **`beforeUpdate`**: Calcula el `precioConIva` antes de que se actualice un registro existente. Si `precioSinIva` tiene un valor, `precioConIva` se establece en `precioSinIva * 1.22`.

### Relaciones

El modelo `Config` no tiene relaciones.
