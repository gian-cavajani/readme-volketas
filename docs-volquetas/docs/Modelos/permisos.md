## Modelo: `Permisos`

### Descripción

El modelo `Permisos` representa los permisos asociados a las empresas o particulares, con información sobre su fecha de creación y vencimiento.

### Campos

-   **`id`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Único: Sí
    -   Descripción: Número único del permiso.

-   **`fechaCreacion`**:

    -   Tipo: `DATEONLY`
    -   No permite valores nulos.
    -   Descripción: Fecha en que se creó el permiso.

-   **`fechaVencimiento`**:

    -   Tipo: `DATEONLY`
    -   Permite valores nulos.
    -   Descripción: Fecha en que vence el permiso.

-   **`empresaId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador de la empresa asociada al permiso.
    -   Referencia: Relacionado con el modelo `Empresas`.

-   **`particularId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del particular asociado al permiso.
    -   Referencia: Relacionado con el modelo `Particulares`.

### Relaciones

-   **Relación con `Empresas`**: N a 1 (Muchos a Uno)
-   **Relación con `Particulares`**: N a 1 (Muchos a Uno)
