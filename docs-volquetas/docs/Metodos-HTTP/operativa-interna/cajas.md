---
hide:
    - toc
---
## Cajas:

| Método HTTP | Endpoint      | Descripción               | Parámetros (Body/Query/Path)                                                               | Respuesta Exitosa                                                    | Respuesta de Error                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Token de Login |
| ----------- | ------------- | ------------------------- | ------------------------------------------------------------------------------------------ | -------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| POST        | /api/cajas    | Crear una nueva caja      | Body: { fecha, motivo, empleadoId, pedidoId, monto, descripcion, moneda }                  | 201 Created: { nuevaCaja }                                           | 400 Bad Request: { error: 'La fecha es obligatoria y debe ser válida' } <br>400 Bad Request: { error: 'Monto es obligatorio' } <br>400 Bad Request: { error: 'Motivo inválido, debe ser: ('vale', 'gasto','ingreso', 'ingreso pedido', 'ingreso cochera', 'extraccion')' } <br>400 Bad Request: { error: 'Moneda inválida, debe ser: ('dolar' o 'peso')' } <br>400 Bad Request: { error: 'Monto inválido, este tipo de motivo debe tener monto positivo' } <br>400 Bad Request: { error: 'Monto inválido, este tipo de motivo debe tener monto negativo' } <br>400 Bad Request: { error: 'Debe agregar un empleado para el vale' } <br>400 Bad Request: { error: 'Debe agregar un pedido para el ingreso de tipo pedido' } <br>404 Not Found: { error: 'Empleado no existe' } <br>404 Not Found: { error: 'Pedido no existe' } <br>400 Bad Request: { error: 'Pedido ya tiene una entrada de dinero', cajasConPedido } | Requerido      |
| GET         | /api/cajas    | Obtener todas las cajas   | Query: fechaInicio, fechaFin                                                               | 200 OK: { datos: { contadorMotivos, montoPeso, montoDolar }, cajas } | 400 Bad Request: { error: 'Debe ingresar fecha de inicio y fecha de fin' } <br>500 Internal Server Error: { error: 'Error al obtener los datos de la caja', detalle: errorsSequelize }                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Requerido      |
| GET         | /api/cajas/id | Obtener una caja por ID   | Path: cajaId                                                                               | 200 OK: { caja }                                                     | 404 Not Found: { error: 'Caja no encontrada' } <br>500 Internal Server Error: { error: 'Error al obtener la caja', detalle: errorsSequelize }                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Requerido      |
| DELETE      | /api/cajas/id | Eliminar una caja por ID  | Path: cajaId                                                                               | 200 OK: { detalle: 'Caja eliminada exitosamente' }                   | 404 Not Found: { error: 'Caja no encontrada' } <br>500 Internal Server Error: { error: 'Error al eliminar la caja', detalle: errorsSequelize }                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Requerido      |
| PUT         | /api/cajas/id | Modificar una caja por ID | Path: cajaId <br>Body: { fecha, motivo, empleadoId, pedidoId, monto, descripcion, moneda } | 200 OK: { caja }                                                     | 400 Bad Request: { error: 'La fecha debe ser válida' } <br>400 Bad Request: { error: "Motivo inválido, debe ser: ('vale', 'gasto', 'ingreso', 'ingreso pedido', 'ingreso cochera', 'extraccion')" } <br>400 Bad Request: { error: "Moneda inválida, debe ser: ('dolar' o 'peso')" } <br>404 Not Found: { error: 'Empleado no existe' } <br>404 Not Found: { error: 'Pedido no existe' } <br>500 Internal Server Error: { error: 'Error al modificar la caja', detalle: errorsSequelize }                                                                                                                                                                                                                                                                                                                                                                                                                               | Requerido      |