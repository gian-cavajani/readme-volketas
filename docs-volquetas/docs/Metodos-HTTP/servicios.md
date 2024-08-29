## Modelo: `Servicios`

### Descripción

El modelo `Servicios` representa los diferentes tipos de servicios realizados a los camiones, incluyendo información sobre el tipo de servicio, la fecha, el precio, y la moneda.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental: Sí
    -   Clave primaria: Sí
    -   Descripción: Identificador único del servicio.

-   **`camionId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del camión al que se le realizó el servicio.
    -   Referencia: Relacionado con el modelo `Camiones`.

-   **`fecha`**:

    -   Tipo: `DATE`
    -   No permite valores nulos.
    -   Descripción: Fecha en que se realizó el servicio.

-   **`tipo`**:

    -   Tipo: `ENUM('arreglo', 'service', 'chequeo', 'pintura')`
    -   No permite valores nulos.
    -   Descripción: Tipo de servicio realizado.

-   **`precio`**:

    -   Tipo: `FLOAT`
    -   Permite valores nulos.
    -   Descripción: Costo del servicio.

-   **`moneda`**:

    -   Tipo: `ENUM('peso', 'dolar')`
    -   Permite valores nulos.
    -   Descripción: Moneda en la que se pagó el servicio.

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Descripción detallada del servicio.

### Relaciones

-   **Relación con `Camiones`**: N a 1 (Muchos a Uno)
