# Modelo: `ObraDetalles`

### Descripción

El modelo `ObraDetalles` almacena información detallada sobre el manejo de residuos en una obra específica. Incluye datos sobre el tipo de residuos, su destino final, y la frecuencia de recolección.

### Campos

-   **`id`**:

    -   Tipo: `INTEGER`
    -   Auto-incremental y clave primaria.
    -   Descripción: Identificador único del registro en la tabla `ObraDetalles`.

-   **`detalleResiduos`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Descripción de los residuos gestionados en la obra.

-   **`residuosMezclados`**:

    -   Tipo: `BOOLEAN`
    -   Permite valores nulos.
    -   Descripción: Indica si los residuos están mezclados.

-   **`residuosReciclados`**:

    -   Tipo: `BOOLEAN`
    -   Permite valores nulos.
    -   Descripción: Indica si los residuos están reciclados.

-   **`frecuenciaSemanal`**:

    -   Tipo: `RANGE(DataTypes.INTEGER)`
    -   Permite valores nulos.
    -   Descripción: Rango de frecuencia semanal para la recolección de residuos.

-   **`destinoFinal`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Destino final de los residuos.

-   **`dias`**:

    -   Tipo: `STRING`
    -   Permite valores nulos.
    -   Descripción: Días de la semana en los que se realiza la recolección.

-   **`obraId`**:

    -   Tipo: `INTEGER`
    -   No permite valores nulos.
    -   Descripción: Identificador de la obra asociada. Referencia al campo `id` del modelo `Obras`.

### Relaciones

-   **Relación con `Obras`**: 1 a 1 (Uno a Uno)
