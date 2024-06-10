## Endpoint `/api/empleados`

El endpoint de empleados proporciona funcionalidades para gestionar la información de los empleados de la empresa. Permite agregar nuevos empleados, editar la información de empleados existentes, eliminar empleados y obtener detalles de un empleado específico.

### Empleados

| Método                             | Descripción                   | Tipo de Token |
| ---------------------------------- | ----------------------------- | ------------- |
| `GET` /api/empleados               | Obtener Empleados             | Normal        |
| `GET` /api/empleados/:id           | Obtener Empleado              | Normal        |
| `POST` /api/empleados              | Nuevo Empleado                | Normal        |
| `PATCH` /api/empleados/:id/estado/ | Modificar Estado del Empleado | Admin         |
| `DELETE` /api/empleados/:id        | Borrar Empleado               | Admin         |
