## Modelo: `Empleados`

### Descripción

El modelo `Empleados` representa a los empleados de la empresa. Este modelo incluye información sobre el nombre, rol, cédula, estado de habilitación, fechas de entrada y salida de la empresa, y dirección de cada empleado.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del empleado en la tabla `Empleados`.

-   **`nombre`**:

    -   Tipo: `STRING`
    -   No permite valores nulos.
    -   Descripción: Nombre del empleado.

-   **`rol`**:

    -   Tipo: `ENUM`
    -   Valores permitidos: `'admin'`, `'normal'`, `'chofer'`.
    -   No permite valores nulos.
    -   Descripción: Rol del empleado dentro de la empresa.

-   **`cedula`**:

    -   Tipo: `STRING(8)`
    -   No permite valores nulos.
    -   Único: Sí.
    -   Descripción: Cédula del empleado. Debe ser única en la tabla `Empleados`.

-   **`habilitado`**:

    -   Tipo: `BOOLEAN`
    -   Valor por defecto: `true`.
    -   Descripción: Estado de habilitación del empleado. Indica si el empleado está habilitado o no.

-   **`fechaEntrada`**:

    -   Tipo: `DATEONLY`
    -   Descripción: Fecha en la que el empleado comenzó a trabajar.

-   **`fechaSalida`**:

    -   Tipo: `DATEONLY`
    -   Valor por defecto: `null`.
    -   Descripción: Fecha en la que el empleado dejó de trabajar. Si el empleado sigue trabajando, este campo será `null`.

-   **`direccion`**:

    -   Tipo: `STRING`
    -   Descripción: Dirección del empleado.

### Relaciones

1.  **Relación con `Usuarios`**
    -   **Tipo**: 1 a 1
2.  **Relación con `HistoricoUsoCamion`**
    -   **Tipo**: 1 a N (Uno a Muchos)
3.  **Relación con `Jornales`**
    -   **Tipo**: 1 a N (Uno a Muchos)
4.  **Relación con `Telefonos`**
    -   **Tipo**: 1 a N (Uno a Muchos)
5.  **Relación con `Cajas`**
    -   **Tipo**: 1 a N (Uno a Muchos)
6.  **Relación con `Sugerencias`**
    -   **Tipo**: 1 a N (Uno a Muchos)
