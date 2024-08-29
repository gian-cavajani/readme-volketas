# Modelo: `Usuarios`

### Descripción

El modelo `Usuarios` representa los usuarios del sistema, que están asociados a empleados y tienen roles específicos.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental: Sí
    -   Clave primaria: Sí
    -   Descripción: Identificador único del usuario.

-   **`empleadoId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del empleado asociado al usuario.
    -   Referencia: Relacionado con el modelo `Empleados`.

-   **`rol`**:

    -   Tipo: `ENUM('admin', 'normal')`
    -   No permite valores nulos.
    -   Descripción: Rol del usuario en el sistema (administrador o usuario normal).

-   **`email`**:

    -   Tipo: `STRING`
    -   Validación: Debe ser una dirección de correo electrónico válida.
    -   Único: Sí
    -   Descripción: Correo electrónico del usuario.

-   **`password`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Único: Sí
    -   Descripción: Contraseña del usuario.

-   **`activo`**:

    -   Tipo: `BOOLEAN`
    -   Valor por defecto: `false`
    -   Descripción: Estado del usuario (activo o inactivo).

### Relaciones

-   **Relación con `Empleados`**: N a 1 (Muchos a Uno)
