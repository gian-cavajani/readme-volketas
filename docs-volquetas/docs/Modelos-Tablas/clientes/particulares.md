# Modelo: `Particulares`

### Descripción

El modelo `Particulares` representa a un cliente individual, con detalles como nombre, cédula, correo electrónico y una descripción adicional.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `Particulares`.

-   **`nombre`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Descripción: Nombre del cliente.

-   **`cedula`**:

    -   Tipo: `STRING(8)`
    -   Único.
    -   Descripción: Cédula del cliente. Debe ser única en la base de datos.

-   **`email`**:

    -   Tipo: `STRING`
    -   Descripción: Correo electrónico del cliente.
    -   Validación: Debe ser una dirección de correo electrónico válida.

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Descripción: Descripción adicional sobre el cliente.

### Relaciones

-   **Relación con `Obras`**: 1 a N (Uno a Muchos)
