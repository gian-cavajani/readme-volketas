# Modelo: `ContactoEmpresas`

### Descripción

El modelo `ContactoEmpresas` representa los contactos asociados a empresas. Este modelo incluye información sobre el nombre del contacto, una descripción opcional, un email y las relaciones con las empresas y obras asociadas.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del contacto en la tabla `ContactoEmpresas`.

-   **`nombre`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Descripción: Nombre del contacto.

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Descripción adicional sobre el contacto.

-   **`email`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Correo electrónico del contacto. Debe ser un email válido (`validate: { isEmail: true }`).

-   **`empresaId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Referencia a la empresa a la que pertenece el contacto. Este campo es una clave foránea que referencia al modelo `Empresas`.

-   **`obraId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Referencia a una obra asociada al contacto. Este campo es una clave foránea que referencia al modelo `Obras`.

### Relaciones

1.  **Relación con `Empresas`**
    -   **Tipo**: 1 a N (Uno a Muchos)
2.  **Relación con `Obras`**
    -   **Tipo**: 1 a N (Uno a Muchos)
