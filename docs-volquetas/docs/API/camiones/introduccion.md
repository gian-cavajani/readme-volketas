# Introduccion

## Endpoint `/api/camiones`

El endpoint de camiones ofrece funcionalidades para gestionar la información de los camiones de la empresa. Permite agregar nuevos camiones, editar la información de camiones existentes, eliminar camiones y obtener detalles de un camión específico.

### Métodos HTTP

| Método                     | Descripción      | Tipo de Token |
| -------------------------- | ---------------- | ------------- |
| `GET` /api/camiones        | Obtener Camiones | Normal        |
| `GET` /api/camiones/:id    | Obtener Camion   | Normal        |
| `POST` /api/camiones       | Nuevo Camion     | Normal        |
| `PUT` /api/camiones/:id    | Modificar Camion | Normal        |
| `DELETE` /api/camiones/:id | Borrar Camion    | Admin         |
