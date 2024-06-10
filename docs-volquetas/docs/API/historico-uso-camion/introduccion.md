## Endpoint `/api/historico-camion`

Esta API permite la gestión de los usos del camion en un sistema. Incluye la creación de nuevos registros para el uso, obtención de registros por periodos y de la lista de empleados/camiones.

### Metodos HTTP

| Método                                    | Descripción                                                       | Tipo de Token |
| ----------------------------------------- | ----------------------------------------------------------------- | ------------- |
| `POST` /api/historico-camion              | Registro de una nueva asignacion de camion                        | Normal        |
| `GET` /api/historico-camion/              | Obtener Asignaciones Actuales de los camiones                     | Normal        |
| `GET` /api/historico-camion?empleadoId=id | Obtener el historico de asignaciones de los camiones por empleado | Normal        |
| `GET` /api/historico-camion?camionId=id   | Obtener el historico de asignaciones de los camiones por camion   | Normal        |
