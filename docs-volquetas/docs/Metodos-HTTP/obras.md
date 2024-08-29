## Modelo: `Obras`

### Descripción

El modelo `Obras` representa una obra con detalles como la ubicación, descripción y estado activo. Puede estar asociada tanto a una empresa como a un particular.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `Obras`.

-   **`calle`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Descripción: Nombre de la calle donde se encuentra la obra.

-   **`esquina`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Esquina o cruce relevante para la ubicación de la obra.

-   **`barrio`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Barrio donde se encuentra la obra.

-   **`coordenadas`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Coordenadas geográficas de la ubicación de la obra.

-   **`numeroPuerta`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Número de puerta asociado a la obra.

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Descripción detallada de la obra.

-   **`activa`**:

    -   Tipo: `BOOLEAN`
    -   Valor por defecto: `true`
    -   Descripción: Indica si la obra está activa.

-   **`particularId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del particular asociado a la obra. Referencia al campo `id` del modelo `Particulares`.

-   **`empresaId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador de la empresa asociada a la obra. Referencia al campo `id` del modelo `Empresas`.

### Relaciones

-   **Relación con `Particulares`**: N a 1 (Muchos a Uno)
-   **Relación con `Empresas`**: N a 1 (Muchos a Uno)
