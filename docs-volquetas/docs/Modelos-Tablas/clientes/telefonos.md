# Modelo: `Telefonos`

### Descripción

El modelo `Telefonos` representa la información de contacto telefónico, que puede estar asociada a empleados, particulares, o contactos de empresas.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental: Sí
    -   Clave primaria: Sí
    -   Descripción: Identificador único del teléfono.

-   **`telefono`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Único: Sí
    -   Descripción: Número de teléfono.

-   **`extension`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Extensión telefónica (opcional).

-   **`tipo`**:

    -   Tipo: `ENUM('telefono', 'celular')`
    -   No permite valores nulos.
    -   Descripción: Tipo de teléfono (teléfono fijo o celular).

-   **`empleadoId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del empleado asociado al teléfono.
    -   Referencia: Relacionado con el modelo `Empleados`.

-   **`particularId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del particular asociado al teléfono.
    -   Referencia: Relacionado con el modelo `Particulares`.

-   **`contactoEmpresaId`**:

    -   Tipo: `INTEGER`
    -   Permite valores nulos.
    -   Descripción: Identificador del contacto de la empresa asociado al teléfono.
    -   Referencia: Relacionado con el modelo `ContactoEmpresas`.

### Relaciones

-   **Relación con `Empleados`**: N a 1 (Muchos a Uno)
-   **Relación con `Particulares`**: N a 1 (Muchos a Uno)
-   **Relación con `ContactoEmpresas`**: N a 1 (Muchos a Uno)
