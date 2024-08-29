## Modelo: `Volquetas`

### Descripción

El modelo `Volquetas` representa las volquetas utilizadas en la empresa para el manejo de residuos. Contiene información sobre el estado, tipo y ubicación de las volquetas.

### Campos

-   **`numeroVolqueta`**:

    -   Tipo: `INTEGER`
    -   Clave primaria: Sí
    -   Descripción: Número único que identifica a la volqueta.

-   **`estado`**:

    -   Tipo: `ENUM('ok', 'quemada', 'para pintar', 'perdida', 'inutilizable')`
    -   Permite valores nulos: Sí
    -   Descripción: Estado actual de la volqueta. Puede ser 'ok', 'quemada', 'para pintar', 'perdida' o 'inutilizable'.

-   **`tipo`**:

    -   Tipo: `ENUM('grande', 'chica')`
    -   No permite valores nulos.
    -   Descripción: Tipo de la volqueta, puede ser 'grande' o 'chica'.

-   **`ocupada`**:

    -   Tipo: `BOOLEAN`
    -   Valor por defecto: `false`
    -   Descripción: Indica si la volqueta está ocupada (sí o no).

-   **`ubicacionTemporal`**:

    -   Tipo: `STRING`
    -   Descripción: Ubicación temporal de la volqueta.

### Relaciones

-   **Relación con `Movimientos`**: 1 a N (Uno a Muchos)
