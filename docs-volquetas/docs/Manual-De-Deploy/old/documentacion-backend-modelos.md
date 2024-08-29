- [Modelo: \`Cajas\`](#Modelo: `Cajas` "wikilink")
- [Modelo: \`Camiones\`](#Modelo: `Camiones` "wikilink")
- [Modelo: \`Config\`](#Modelo: `Config` "wikilink")
- [Modelo: \`ContactoEmpresas\`](#Modelo: `ContactoEmpresas` "wikilink")
- [Modelo: \`Empleados\`](#Modelo: `Empleados` "wikilink")
- [Modelo: \`Empresas\`](#Modelo: `Empresas` "wikilink")
- [Modelo: \`Facturas\`](#Modelo: `Facturas` "wikilink")
- [Modelo: \`HistoricoUsoCamion\`](#Modelo: `HistoricoUsoCamion` "wikilink")
- [Modelo: \`Jornales\`](#Modelo: `Jornales` "wikilink")
- [Modelo: \`Movimientos\`](#Modelo: `Movimientos` "wikilink")
- [Modelo: \`Obras\`](#Modelo: `Obras` "wikilink")
- [Modelo: \`ObraDetalles\`](#Modelo: `ObraDetalles` "wikilink")
- [Modelo: \`PagoPedidos\`](#Modelo: `PagoPedidos` "wikilink")
- [Modelo: \`PagoPedidos\`](#Modelo: `PagoPedidos` "wikilink")
- [Modelo: \`Particulares\`](#Modelo: `Particulares` "wikilink")
- [Modelo: \`Pedidos\`](#Modelo: `Pedidos` "wikilink")
- [Modelo: \`Permisos\`](#Modelo: `Permisos` "wikilink")
- [Modelo: \`Servicios\`](#Modelo: `Servicios` "wikilink")
- [Modelo: \`Sugerencias\`](#Modelo: `Sugerencias` "wikilink")
- [Modelo: \`Telefonos\`](#Modelo: `Telefonos` "wikilink")
- [Modelo: \`Usuarios\`](#Modelo: `Usuarios` "wikilink")
- [Modelo: \`Volquetas\`](#Modelo: `Volquetas` "wikilink")

## Modelo: `Cajas`

### Descripción

El modelo `Cajas` representa registros financieros en la caja, como gastos, ingresos, y otros movimientos contables. Cada registro incluye información sobre la fecha, motivo, descripción, moneda, monto, y referencias a empleados y pedidos relacionados.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `Cajas`.

- **`fecha`**:

  - Tipo: `DATEONLY`
  - No permite valores nulos.
  - Descripción: Fecha del movimiento registrado en la caja.

- **`motivo`**:

  - Tipo: `ENUM('vale', 'gasto', 'ingreso', 'ingreso pedido', 'ingreso cochera', 'extraccion')`
  - No permite valores nulos.
  - Descripción: Motivo del movimiento en la caja (vale, gasto, ingreso, etc.).

- **`descripcion`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Descripción opcional del movimiento.

- **`moneda`**:

  - Tipo: `ENUM('peso', 'dolar')`
  - No permite valores nulos.
  - Descripción: Tipo de moneda en el registro (peso o dólar).

- **`monto`**:

  - Tipo: `FLOAT`
  - No permite valores nulos.
  - Descripción: Monto del movimiento registrado en la caja.

- **`empleadoId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Clave foránea que referencia al `Empleado` que realizó el movimiento, si aplica.

- **`pedidoId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Clave foránea que referencia al `Pedido` asociado al movimiento, si aplica.

### Relaciones

1.  **Relación con `Empleados`**
    - **Tipo**: N a 1 (Muchos a Uno)
2.  **Relación con `Pedidos`**
    - **Tipo**: N a 1 (Muchos a Uno)

## Modelo: `Camiones`

### Descripción

El modelo `Camiones` representa los vehículos utilizados en la empresa. Incluye información sobre la matrícula, modelo, año y estado del camión.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `Camiones`.

- **`matricula`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - **Único**: Debe ser único en la tabla.
  - Validaciones:
    - No puede estar vacío.
  - Descripción: Matrícula del camión.

- **`modelo`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Validaciones:
    - No puede estar vacío.
  - Descripción: Modelo del camión.

- **`anio`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Año de fabricación del camión.

- **`estado`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Estado actual del camión (por ejemplo, activo, en mantenimiento, etc.).

### Relaciones

1.  **Relación con `HistoricoUsoCamion`**
    - **Tipo**: 1 a N (Uno a Muchos)
2.  **Relación con `Servicios`**
    - **Tipo**: 1 a N (Uno a Muchos)
3.  **Relación con `Movimientos`**
    - **Tipo**: 1 a N (Uno a Muchos)

## Modelo: `Config`

### Descripción

El modelo `Config` representa la configuración relacionada con precios y horas de trabajo. Incluye información sobre el precio sin IVA, el precio con IVA, el año de la configuración y si la configuración está activa.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `Config`.

- **`anio`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Año asociado a la configuración.

- **`precioSinIva`**:

  - Tipo: `FLOAT`
  - Permite valores nulos.
  - Descripción: Precio base sin IVA.

- **`precioConIva`**:

  - Tipo: `FLOAT`
  - Permite valores nulos.
  - Descripción: Precio con IVA. Este campo se calcula automáticamente basado en `precioSinIva`.

- **`horasDeTrabajo`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Número de horas de trabajo asociadas a la configuración.

- **`configActiva`**:

  - Tipo: `BOOLEAN`
  - Permite valores nulos.
  - Descripción: Indica si la configuración está activa (`true`) o no (`false`).

### Hooks

- **`beforeCreate`**: Calcula el `precioConIva` antes de que se cree un nuevo registro. Si `precioSinIva` tiene un valor, `precioConIva` se establece en `precioSinIva * 1.22`.

- **`beforeUpdate`**: Calcula el `precioConIva` antes de que se actualice un registro existente. Si `precioSinIva` tiene un valor, `precioConIva` se establece en `precioSinIva * 1.22`.

### Relaciones

El modelo `Config` no tiene relaciones.

## Modelo: `ContactoEmpresas`

### Descripción

El modelo `ContactoEmpresas` representa los contactos asociados a empresas. Este modelo incluye información sobre el nombre del contacto, una descripción opcional, un email y las relaciones con las empresas y obras asociadas.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del contacto en la tabla `ContactoEmpresas`.

- **`nombre`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Descripción: Nombre del contacto.

- **`descripcion`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Descripción adicional sobre el contacto.

- **`email`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Correo electrónico del contacto. Debe ser un email válido (`validate: { isEmail: true }`).

- **`empresaId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Referencia a la empresa a la que pertenece el contacto. Este campo es una clave foránea que referencia al modelo `Empresas`.

- **`obraId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Referencia a una obra asociada al contacto. Este campo es una clave foránea que referencia al modelo `Obras`.

### Relaciones

1.  **Relación con `Empresas`**
    - **Tipo**: 1 a N (Uno a Muchos)
2.  **Relación con `Obras`**
    - **Tipo**: 1 a N (Uno a Muchos)

## Modelo: `Empleados`

### Descripción

El modelo `Empleados` representa a los empleados de la empresa. Este modelo incluye información sobre el nombre, rol, cédula, estado de habilitación, fechas de entrada y salida de la empresa, y dirección de cada empleado.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del empleado en la tabla `Empleados`.

- **`nombre`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Descripción: Nombre del empleado.

- **`rol`**:

  - Tipo: `ENUM`
  - Valores permitidos: `'admin'`, `'normal'`, `'chofer'`.
  - No permite valores nulos.
  - Descripción: Rol del empleado dentro de la empresa.

- **`cedula`**:

  - Tipo: `STRING(8)`
  - No permite valores nulos.
  - Único: Sí.
  - Descripción: Cédula del empleado. Debe ser única en la tabla `Empleados`.

- **`habilitado`**:

  - Tipo: `BOOLEAN`
  - Valor por defecto: `true`.
  - Descripción: Estado de habilitación del empleado. Indica si el empleado está habilitado o no.

- **`fechaEntrada`**:

  - Tipo: `DATEONLY`
  - Descripción: Fecha en la que el empleado comenzó a trabajar.

- **`fechaSalida`**:

  - Tipo: `DATEONLY`
  - Valor por defecto: `null`.
  - Descripción: Fecha en la que el empleado dejó de trabajar. Si el empleado sigue trabajando, este campo será `null`.

- **`direccion`**:

  - Tipo: `STRING`
  - Descripción: Dirección del empleado.

### Relaciones

1.  **Relación con `Usuarios`**
    - **Tipo**: 1 a 1
2.  **Relación con `HistoricoUsoCamion`**
    - **Tipo**: 1 a N (Uno a Muchos)
3.  **Relación con `Jornales`**
    - **Tipo**: 1 a N (Uno a Muchos)
4.  **Relación con `Telefonos`**
    - **Tipo**: 1 a N (Uno a Muchos)
5.  **Relación con `Cajas`**
    - **Tipo**: 1 a N (Uno a Muchos)
6.  **Relación con `Sugerencias`**
    - **Tipo**: 1 a N (Uno a Muchos)

## Modelo: `Empresas`

### Descripción

El modelo `Empresas` representa a las empresas dentro del sistema. Este modelo incluye información sobre el RUT, nombre, razón social y descripción de cada empresa.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único de la empresa en la tabla `Empresas`.

- **`rut`**:

  - Tipo: `STRING(12)`
  - Único: Sí.
  - Descripción: RUT (Rol Único Tributario) de la empresa. Este campo puede ser nulo y debe ser único si se proporciona.

- **`nombre`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Descripción: Nombre de la empresa.

- **`razonSocial`**:

  - Tipo: `STRING`
  - Descripción: Razón social de la empresa. Es un campo opcional.

- **`descripcion`**:

  - Tipo: `STRING`
  - Descripción: Descripción adicional sobre la empresa. Es un campo opcional.

### Relaciones

1.  **Relación con `ContactoEmpresas`**
    - **Tipo**: 1 a N (Uno a Muchos)
2.  **Relación con `Obras`**
    - **Tipo**: 1 a N (Uno a Muchos)
3.  **Relación con `Permisos`**
    - **Tipo**: 1 a N (Uno a Muchos)
4.  **Relación con `Cajas`**
    - **Tipo**: 1 a N (Uno a Muchos)

## Modelo: `Facturas`

### Descripción

El modelo `Facturas` representa una factura en el sistema. Incluye información sobre el tipo de factura, numeración, estado, fecha de pago, monto y descripción.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único de la factura en la tabla `Facturas`.

- **`tipo`**:

  - Tipo: `ENUM('credito', 'contado', 'recibo')`
  - No permite valores nulos.
  - Descripción: Tipo de la factura (crédito, contado, recibo).

- **`numeracion`**:

  - Tipo: `STRING`
  - Único: Sí.
  - Descripción: Número de la factura. Debe ser único en el sistema.

- **`estado`**:

  - Tipo: `ENUM('pendiente', 'pagada', 'anulada')`
  - No permite valores nulos.
  - Descripción: Estado de la factura (pendiente, pagada, anulada).

- **`fechaPago`**:

  - Tipo: `DATEONLY`
  - Descripción: Fecha en la que se realizó el pago de la factura. Es opcional.

- **`monto`**:

  - Tipo: `FLOAT`
  - Descripción: Monto total de la factura.

- **`descripcion`**:

  - Tipo: `STRING`
  - Descripción: Descripción adicional sobre la factura.

- **`particularId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del cliente particular asociado a la factura. Referencia al modelo `Particulares`.

- **`empresaId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador de la empresa asociada a la factura. Referencia al modelo `Empresas`.

### Relaciones

- **Relación con `Particulares`**: 1 a N (Uno a Muchos)
- **Relación con `Empresas`**: 1 a N (Uno a Muchos)

## Modelo: `HistoricoUsoCamion`

### Descripción

El modelo `HistoricoUsoCamion` registra el historial de uso de camiones por parte de empleados. Incluye información sobre el empleado, el camión, y las fechas de inicio y fin del uso del camión.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `HistoricoUsoCamion`.

- **`empleadoId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del empleado que utilizó el camión. Referencia al modelo `Empleados`.

- **`camionId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del camión que fue utilizado. Referencia al modelo `Camiones`.

- **`fechaInicio`**:

  - Tipo: `DATE`
  - No permite valores nulos.
  - Descripción: Fecha de inicio del uso del camión.

- **`fechaFin`**:

  - Tipo: `DATE`
  - Permite valores nulos.
  - Descripción: Fecha de finalización del uso del camión. Es opcional si el camión aún está en uso.

### Relaciones

- **Relación con `Empleados`**: N a 1 (Muchos a Uno)
- **Relación con `Camiones`**: N a 1 (Muchos a Uno)

## Modelo: `Jornales`

### Descripción

El modelo `Jornales` registra los detalles de los turnos de trabajo de los empleados, incluyendo las horas de entrada y salida, y el cálculo de horas extra. También incluye información sobre el tipo de jornal y quién lo creó.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `Jornales`.

- **`empleadoId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del empleado al que corresponde el jornal. Referencia al modelo `Empleados`.

- **`tipo`**:

  - Tipo: `ENUM`
  - Valores posibles: `'trabajo'`, `'licencia'`, `'enfermedad'`, `'falta'`
  - No permite valores nulos.
  - Descripción: Tipo de jornal registrado.

- **`fecha`**:

  - Tipo: `DATEONLY`
  - No permite valores nulos.
  - Descripción: Fecha del jornal.

- **`entrada`**:

  - Tipo: `TIME`
  - Permite valores nulos.
  - Descripción: Hora de entrada del empleado.

- **`salida`**:

  - Tipo: `TIME`
  - Permite valores nulos.
  - Descripción: Hora de salida del empleado.

- **`horasExtra`**:

  - Tipo: `FLOAT`
  - Valor por defecto: `0`
  - Descripción: Horas extra calculadas, basadas en el límite de horas diarias.

- **`creadoPor`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del usuario que creó el registro del jornal. Referencia al modelo `Usuarios`.

### Relaciones

- **Relación con `Empleados`**: N a 1 (Muchos a Uno)
- **Relación con `Usuarios`**: N a 1 (Muchos a Uno)

## Modelo: `Movimientos`

### Descripción

El modelo `Movimientos` registra los movimientos de las volquetas asociados a pedidos. Incluye información sobre el número de volqueta, el pedido asociado, el horario del movimiento, el tipo de movimiento y el chofer responsable.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `Movimientos`.

- **`numeroVolqueta`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Número de la volqueta asociada al movimiento. Referencia al campo `numeroVolqueta` del modelo `Volquetas`.

- **`pedidoId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del pedido asociado al movimiento. Referencia al campo `id` del modelo `Pedidos`.

- **`horario`**:

  - Tipo: `DATE`
  - No permite valores nulos.
  - Descripción: Fecha y hora del movimiento.

- **`tipo`**:

  - Tipo: `ENUM`
  - Valores posibles: `'entrega'`, `'levante'`
  - Descripción: Tipo de movimiento registrado.

- **`choferId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del chofer responsable del movimiento. Referencia al campo `id` del modelo `Empleados`.

### Relaciones

- **Relación con `Volquetas`**: N a 1 (Muchos a Uno)
- **Relación con `Pedidos`**: N a 1 (Muchos a Uno)
- **Relación con `Empleados`**: N a 1 (Muchos a Uno)

## Modelo: `Obras`

### Descripción

El modelo `Obras` representa una obra con detalles como la ubicación, descripción y estado activo. Puede estar asociada tanto a una empresa como a un particular.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `Obras`.

- **`calle`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Descripción: Nombre de la calle donde se encuentra la obra.

- **`esquina`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Esquina o cruce relevante para la ubicación de la obra.

- **`barrio`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Barrio donde se encuentra la obra.

- **`coordenadas`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Coordenadas geográficas de la ubicación de la obra.

- **`numeroPuerta`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Número de puerta asociado a la obra.

- **`descripcion`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Descripción detallada de la obra.

- **`activa`**:

  - Tipo: `BOOLEAN`
  - Valor por defecto: `true`
  - Descripción: Indica si la obra está activa.

- **`particularId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del particular asociado a la obra. Referencia al campo `id` del modelo `Particulares`.

- **`empresaId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador de la empresa asociada a la obra. Referencia al campo `id` del modelo `Empresas`.

### Relaciones

- **Relación con `Particulares`**: N a 1 (Muchos a Uno)
- **Relación con `Empresas`**: N a 1 (Muchos a Uno)

## Modelo: `ObraDetalles`

### Descripción

El modelo `ObraDetalles` almacena información detallada sobre el manejo de residuos en una obra específica. Incluye datos sobre el tipo de residuos, su destino final, y la frecuencia de recolección.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `ObraDetalles`.

- **`detalleResiduos`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Descripción de los residuos gestionados en la obra.

- **`residuosMezclados`**:

  - Tipo: `BOOLEAN`
  - Permite valores nulos.
  - Descripción: Indica si los residuos están mezclados.

- **`residuosReciclados`**:

  - Tipo: `BOOLEAN`
  - Permite valores nulos.
  - Descripción: Indica si los residuos están reciclados.

- **`frecuenciaSemanal`**:

  - Tipo: `RANGE(DataTypes.INTEGER)`
  - Permite valores nulos.
  - Descripción: Rango de frecuencia semanal para la recolección de residuos.

- **`destinoFinal`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Destino final de los residuos.

- **`dias`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Días de la semana en los que se realiza la recolección.

- **`obraId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador de la obra asociada. Referencia al campo `id` del modelo `Obras`.

### Relaciones

- **Relación con `Obras`**: 1 a 1 (Uno a Uno)

## Modelo: `PagoPedidos`

### Descripción

El modelo `PagoPedidos` representa el pago asociado a un pedido, con detalles como el precio, el estado de pago, el remito y el tipo de pago.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `PagoPedidos`.

- **`precio`**:

  - Tipo: `FLOAT`
  - No permite valores nulos.
  - Descripción: Monto del pago.

- **`pagado`**:

  - Tipo: `BOOLEAN`
  - Valor por defecto: `false`
  - Descripción: Indica si el pago ha sido realizado o no.

- **`remito`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Número de remito asociado al pago.

- **`tipoPago`**:

  - Tipo: `ENUM('transferencia', 'efectivo', 'cheque')`
  - Permite valores nulos.
  - Descripción: Tipo de pago utilizado.

- **`facturaId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador de la factura asociada al pago. Referencia al campo `id` del modelo `Facturas`.

### Relaciones

- **Relación con `Facturas`**: N a 1 (Muchos a Uno)

## Modelo: `PagoPedidos`

### Descripción

El modelo `PagoPedidos` representa el pago asociado a un pedido, con detalles como el precio, el estado de pago, el remito y el tipo de pago.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `PagoPedidos`.

- **`precio`**:

  - Tipo: `FLOAT`
  - No permite valores nulos.
  - Descripción: Monto del pago.

- **`pagado`**:

  - Tipo: `BOOLEAN`
  - Valor por defecto: `false`
  - Descripción: Indica si el pago ha sido realizado o no.

- **`remito`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Número de remito asociado al pago.

- **`tipoPago`**:

  - Tipo: `ENUM('transferencia', 'efectivo', 'cheque')`
  - Permite valores nulos.
  - Descripción: Tipo de pago utilizado.

- **`facturaId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador de la factura asociada al pago. Referencia al campo `id` del modelo `Facturas`.

### Relaciones

- **Relación con `Facturas`**: N a 1 (Muchos a Uno)
- **Relación con `Pedidos`**: 1 a 1 (Uno a Uno)

## Modelo: `Particulares`

### Descripción

El modelo `Particulares` representa a un cliente individual, con detalles como nombre, cédula, correo electrónico y una descripción adicional.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del registro en la tabla `Particulares`.

- **`nombre`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Descripción: Nombre del cliente.

- **`cedula`**:

  - Tipo: `STRING(8)`
  - Único.
  - Descripción: Cédula del cliente. Debe ser única en la base de datos.

- **`email`**:

  - Tipo: `STRING`
  - Descripción: Correo electrónico del cliente.
  - Validación: Debe ser una dirección de correo electrónico válida.

- **`descripcion`**:

  - Tipo: `STRING`
  - Descripción: Descripción adicional sobre el cliente.

### Relaciones

- **Relación con `Obras`**: 1 a N (Uno a Muchos)

## Modelo: `Pedidos`

### Descripción

El modelo `Pedidos` representa los pedidos realizados en el sistema, con información sobre su estado, la obra asociada, el usuario que lo creó y otros detalles relevantes.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental y clave primaria.
  - Descripción: Identificador único del pedido.

- **`creadoPor`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del usuario que creó el pedido.
  - Referencia: Relacionado con el modelo `Usuarios`.

- **`obraId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador de la obra asociada al pedido.
  - Referencia: Relacionado con el modelo `Obras`.

- **`descripcion`**:

  - Tipo: `STRING`
  - Descripción: Descripción adicional del pedido.
  - Permite valores nulos.

- **`estado`**:

  - Tipo: `ENUM`
  - Valores posibles: `'iniciado'`, `'entregado'`, `'levantado'`, `'cancelado'`.
  - Valor por defecto: `'iniciado'`.
  - Descripción: Estado actual del pedido.

- **`creadoComo`**:

  - Tipo: `ENUM`
  - Valores posibles: `'nuevo'`, `'recambio'`, `'multiple'`, `'entrega mas levante'`.
  - No permite valores nulos.
  - Descripción: Tipo de pedido creado.

- **`permisoId`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Identificador del permiso asociado al pedido.
  - Referencia: Relacionado con el modelo `Permisos`.

- **`nroPesada`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Número de pesada asociado al pedido.

- **`pagoPedidoId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del pago asociado al pedido.
  - Referencia: Relacionado con el modelo `PagoPedidos`.

- **`referenciaId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del pedido de referencia (en caso de ser un pedido relacionado con otro).
  - Referencia: Relacionado con el modelo `Pedidos`.

### Relaciones

- **Relación con `Usuarios`**: 1 a N (Uno a Muchos)
- **Relación con `Obras`**: 1 a N (Uno a Muchos)
- **Relación con `Permisos`**: N a 1 (Muchos a Uno)
- **Relación con `PagoPedidos`**: 1 a 1 (Uno a Uno)
- **Relación con `Pedidos`**: 1 a N (Uno a Muchos, auto-referencia)
- **Relación con `Movimientos`**: 1 a 2 (Uno a Dos)
- **Relación con `Sugerencias`**: 1 a 2 (Uno a Dos)

## Modelo: `Permisos`

### Descripción

El modelo `Permisos` representa los permisos asociados a las empresas o particulares, con información sobre su fecha de creación y vencimiento.

### Campos

- **`id`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Único: Sí
  - Descripción: Número único del permiso.

- **`fechaCreacion`**:

  - Tipo: `DATEONLY`
  - No permite valores nulos.
  - Descripción: Fecha en que se creó el permiso.

- **`fechaVencimiento`**:

  - Tipo: `DATEONLY`
  - Permite valores nulos.
  - Descripción: Fecha en que vence el permiso.

- **`empresaId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador de la empresa asociada al permiso.
  - Referencia: Relacionado con el modelo `Empresas`.

- **`particularId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del particular asociado al permiso.
  - Referencia: Relacionado con el modelo `Particulares`.

### Relaciones

- **Relación con `Empresas`**: N a 1 (Muchos a Uno)
- **Relación con `Particulares`**: N a 1 (Muchos a Uno)

## Modelo: `Servicios`

### Descripción

El modelo `Servicios` representa los diferentes tipos de servicios realizados a los camiones, incluyendo información sobre el tipo de servicio, la fecha, el precio, y la moneda.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental: Sí
  - Clave primaria: Sí
  - Descripción: Identificador único del servicio.

- **`camionId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del camión al que se le realizó el servicio.
  - Referencia: Relacionado con el modelo `Camiones`.

- **`fecha`**:

  - Tipo: `DATE`
  - No permite valores nulos.
  - Descripción: Fecha en que se realizó el servicio.

- **`tipo`**:

  - Tipo: `ENUM('arreglo', 'service', 'chequeo', 'pintura')`
  - No permite valores nulos.
  - Descripción: Tipo de servicio realizado.

- **`precio`**:

  - Tipo: `FLOAT`
  - Permite valores nulos.
  - Descripción: Costo del servicio.

- **`moneda`**:

  - Tipo: `ENUM('peso', 'dolar')`
  - Permite valores nulos.
  - Descripción: Moneda en la que se pagó el servicio.

- **`descripcion`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Descripción detallada del servicio.

### Relaciones

- **Relación con `Camiones`**: N a 1 (Muchos a Uno)

## Modelo: `Sugerencias`

### Descripción

El modelo `Sugerencias` representa las sugerencias asociadas a pedidos, incluyendo el horario sugerido, el chofer recomendado y el tipo de sugerencia (entrega o levante).

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental: Sí
  - Clave primaria: Sí
  - Descripción: Identificador único de la sugerencia.

- **`horarioSugerido`**:

  - Tipo: `DATE`
  - Permite valores nulos.
  - Descripción: Horario sugerido para la acción recomendada.

- **`choferSugeridoId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del chofer recomendado para el pedido.
  - Referencia: Relacionado con el modelo `Empleados`.

- **`tipoSugerido`**:

  - Tipo: `ENUM('entrega', 'levante')`
  - No permite valores nulos.
  - Descripción: Tipo de acción sugerida (entrega o levante).

- **`pedidoId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del pedido asociado a la sugerencia.
  - Referencia: Relacionado con el modelo `Pedidos`.

### Relaciones

- **Relación con `Empleados`**: N a 1 (Muchos a Uno)
- **Relación con `Pedidos`**: N a 1 (Muchos a Uno)

## Modelo: `Telefonos`

### Descripción

El modelo `Telefonos` representa la información de contacto telefónico, que puede estar asociada a empleados, particulares, o contactos de empresas.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental: Sí
  - Clave primaria: Sí
  - Descripción: Identificador único del teléfono.

- **`telefono`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Único: Sí
  - Descripción: Número de teléfono.

- **`extension`**:

  - Tipo: `STRING`
  - Permite valores nulos.
  - Descripción: Extensión telefónica (opcional).

- **`tipo`**:

  - Tipo: `ENUM('telefono', 'celular')`
  - No permite valores nulos.
  - Descripción: Tipo de teléfono (teléfono fijo o celular).

- **`empleadoId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del empleado asociado al teléfono.
  - Referencia: Relacionado con el modelo `Empleados`.

- **`particularId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del particular asociado al teléfono.
  - Referencia: Relacionado con el modelo `Particulares`.

- **`contactoEmpresaId`**:

  - Tipo: `INTEGER`
  - Permite valores nulos.
  - Descripción: Identificador del contacto de la empresa asociado al teléfono.
  - Referencia: Relacionado con el modelo `ContactoEmpresas`.

### Relaciones

- **Relación con `Empleados`**: N a 1 (Muchos a Uno)
- **Relación con `Particulares`**: N a 1 (Muchos a Uno)
- **Relación con `ContactoEmpresas`**: N a 1 (Muchos a Uno)

## Modelo: `Usuarios`

### Descripción

El modelo `Usuarios` representa los usuarios del sistema, que están asociados a empleados y tienen roles específicos.

### Campos

- **`id`**:

  - Tipo: `INTEGER`
  - Auto-incremental: Sí
  - Clave primaria: Sí
  - Descripción: Identificador único del usuario.

- **`empleadoId`**:

  - Tipo: `INTEGER`
  - No permite valores nulos.
  - Descripción: Identificador del empleado asociado al usuario.
  - Referencia: Relacionado con el modelo `Empleados`.

- **`rol`**:

  - Tipo: `ENUM('admin', 'normal')`
  - No permite valores nulos.
  - Descripción: Rol del usuario en el sistema (administrador o usuario normal).

- **`email`**:

  - Tipo: `STRING`
  - Validación: Debe ser una dirección de correo electrónico válida.
  - Único: Sí
  - Descripción: Correo electrónico del usuario.

- **`password`**:

  - Tipo: `STRING`
  - No permite valores nulos.
  - Único: Sí
  - Descripción: Contraseña del usuario.

- **`activo`**:

  - Tipo: `BOOLEAN`
  - Valor por defecto: `false`
  - Descripción: Estado del usuario (activo o inactivo).

### Relaciones

- **Relación con `Empleados`**: N a 1 (Muchos a Uno)

## Modelo: `Volquetas`

### Descripción

El modelo `Volquetas` representa las volquetas utilizadas en la empresa para el manejo de residuos. Contiene información sobre el estado, tipo y ubicación de las volquetas.

### Campos

- **`numeroVolqueta`**:

  - Tipo: `INTEGER`
  - Clave primaria: Sí
  - Descripción: Número único que identifica a la volqueta.

- **`estado`**:

  - Tipo: `ENUM('ok', 'quemada', 'para pintar', 'perdida', 'inutilizable')`
  - Permite valores nulos: Sí
  - Descripción: Estado actual de la volqueta. Puede ser 'ok', 'quemada', 'para pintar', 'perdida' o 'inutilizable'.

- **`tipo`**:

  - Tipo: `ENUM('grande', 'chica')`
  - No permite valores nulos.
  - Descripción: Tipo de la volqueta, puede ser 'grande' o 'chica'.

- **`ocupada`**:

  - Tipo: `BOOLEAN`
  - Valor por defecto: `false`
  - Descripción: Indica si la volqueta está ocupada (sí o no).

- **`ubicacionTemporal`**:

  - Tipo: `STRING`
  - Descripción: Ubicación temporal de la volqueta.

### Relaciones

- **Relación con `Movimientos`**: 1 a N (Uno a Muchos)
