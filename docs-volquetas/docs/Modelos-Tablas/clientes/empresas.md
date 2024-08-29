# Modelo: `Empresas`

### Descripción

El modelo `Empresas` representa a las empresas dentro del sistema. Este modelo incluye información sobre el RUT, nombre, razón social y descripción de cada empresa.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único de la empresa en la tabla `Empresas`.

-   **`rut`**:

    -   Tipo: `STRING(12)`
    -   Único: Sí.
    -   Descripción: RUT (Rol Único Tributario) de la empresa. Este campo puede ser nulo y debe ser único si se proporciona.

-   **`nombre`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Descripción: Nombre de la empresa.

-   **`razonSocial`**:

    -   Tipo: `STRING`
    -   Descripción: Razón social de la empresa. Es un campo opcional.

-   **`descripcion`**:

    -   Tipo: `STRING`
    -   Descripción: Descripción adicional sobre la empresa. Es un campo opcional.

### Relaciones

1.  **Relación con `ContactoEmpresas`**
    -   **Tipo**: 1 a N (Uno a Muchos)
2.  **Relación con `Obras`**
    -   **Tipo**: 1 a N (Uno a Muchos)
3.  **Relación con `Permisos`**
    -   **Tipo**: 1 a N (Uno a Muchos)
4.  **Relación con `Cajas`**
    -   **Tipo**: 1 a N (Uno a Muchos)
