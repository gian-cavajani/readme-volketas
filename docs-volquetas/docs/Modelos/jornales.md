## Modelo: `Jornales`

### Descripción

El modelo `Jornales` registra los detalles de los turnos de trabajo de los empleados, incluyendo las horas de entrada y salida, y el cálculo de horas extra. También incluye información sobre el tipo de jornal y quién lo creó.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `Jornales`.

-   **`empleadoId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del empleado al que corresponde el jornal. Referencia al modelo `Empleados`.

-   **`tipo`**:

    -   Tipo: `ENUM`
    -   Valores posibles: `'trabajo'`, `'licencia'`, `'enfermedad'`, `'falta'`
    -   No permite valores nulos.
    -   Descripción: Tipo de jornal registrado.

-   **`fecha`**:

    -   Tipo: `DATEONLY`
    -   No permite valores nulos.
    -   Descripción: Fecha del jornal.

-   **`entrada`**:

    -   Tipo: `TIME`
    -   Permite valores nulos.
    -   Descripción: Hora de entrada del empleado.

-   **`salida`**:

    -   Tipo: `TIME`
    -   Permite valores nulos.
    -   Descripción: Hora de salida del empleado.

-   **`horasExtra`**:

    -   Tipo: `FLOAT`
    -   Valor por defecto: `0`
    -   Descripción: Horas extra calculadas, basadas en el límite de horas diarias.

-   **`creadoPor`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador del usuario que creó el registro del jornal. Referencia al modelo `Usuarios`.

### Relaciones

-   **Relación con `Empleados`**: N a 1 (Muchos a Uno)
-   **Relación con `Usuarios`**: N a 1 (Muchos a Uno)
