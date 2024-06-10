## Endpoint `/api/empleados`

Esta API permite la gestión de empleados en un sistema. Incluye la creación de nuevos empleados, obtención de un empleado y de la lista de empleados.

### Empleados

| Método                             | Descripción                   | Tipo de Token |
| ---------------------------------- | ----------------------------- | ------------- |
| `GET` /api/empleados               | Obtener Empleados             | Normal        |
| `GET` /api/empleados/:id           | Obtener Empleado              | Normal        |
| `POST` /api/empleados              | Nuevo Empleado                | Normal        |
| `PATCH` /api/empleados/:id/estado/ | Modificar Estado del Empleado | Admin         |
| `DELETE` /api/empleados/:id        | Borrar Empleado               | Admin         |
