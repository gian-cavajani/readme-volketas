## Endpoint `/api/servicios`

Esta API permite la gestión de los servicios de los camiones en un sistema. Incluye la creación de nuevos servicios, obtención de servicios.

### Servicios

| Método                         | Descripción                              | Tipo de Token |
| ------------------------------ | ---------------------------------------- | ------------- |
| `POST` /api/servicios          | Nuevo servicio                           | Normal        |
| `GET` /api/servicios/:camionId | Obtener todos los servicios de un camion | Normal        |
| `GET` /api/servicios/          | Obtener todos los servicios              | Normal        |
