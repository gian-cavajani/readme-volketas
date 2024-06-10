# Introduccion

## Endpoint `/api/camiones`

Esta API permite la gestión de camiones en un sistema. Incluye la creación, obtención, modificacion y borrado de camiones.

### Métodos HTTP

| Método                     | Descripción      | Tipo de Token |
| -------------------------- | ---------------- | ------------- |
| `GET` /api/camiones        | Obtener Camiones | Normal        |
| `GET` /api/camiones/:id    | Obtener Camion   | Normal        |
| `POST` /api/camiones       | Nuevo Camion     | Normal        |
| `PUT` /api/camiones/:id    | Modificar Camion | Normal        |
| `DELETE` /api/camiones/:id | Borrar Camion    | Admin         |
