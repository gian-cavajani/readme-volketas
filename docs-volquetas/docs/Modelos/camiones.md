## Modelo: `Camiones`

### Descripción

El modelo `Camiones` representa los vehículos utilizados en la empresa. Incluye información sobre la matrícula, modelo, año y estado del camión.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `Camiones`.

-   **`matricula`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   **Único**: Debe ser único en la tabla.
    -   Validaciones:
        -   No puede estar vacío.
    -   Descripción: Matrícula del camión.

-   **`modelo`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Validaciones:
        -   No puede estar vacío.
    -   Descripción: Modelo del camión.

-   **`anio`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Año de fabricación del camión.

-   **`estado`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Estado actual del camión (por ejemplo, activo, en mantenimiento, etc.).

### Relaciones

1.  **Relación con `HistoricoUsoCamion`**
    -   **Tipo**: 1 a N (Uno a Muchos)
2.  **Relación con `Servicios`**
    -   **Tipo**: 1 a N (Uno a Muchos)
3.  **Relación con `Movimientos`**
    -   **Tipo**: 1 a N (Uno a Muchos)
