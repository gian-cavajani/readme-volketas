## Modelo: `HistoricoUsoCamion`

### Descripción

El modelo `HistoricoUsoCamion` registra el historial de uso de camiones por parte de empleados. Incluye información sobre el empleado, el camión, y las fechas de inicio y fin del uso del camión.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `HistoricoUsoCamion`.

-   **`empleadoId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del empleado que utilizó el camión. Referencia al modelo `Empleados`.

-   **`camionId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del camión que fue utilizado. Referencia al modelo `Camiones`.

-   **`fechaInicio`**:

    -   Tipo: `DATE`
    -   No permite valores nulos.
    -   Descripción: Fecha de inicio del uso del camión.

-   **`fechaFin`**:

    -   Tipo: `DATE`
    -   Permite valores nulos.
    -   Descripción: Fecha de finalización del uso del camión. Es opcional si el camión aún está en uso.

### Relaciones

-   **Relación con `Empleados`**: N a 1 (Muchos a Uno)
-   **Relación con `Camiones`**: N a 1 (Muchos a Uno)
