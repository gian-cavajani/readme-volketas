# Introduccion

### Usuarios

Ir a [Pagina de Usuarios](/API/usuarios/introduccion/) para mas detalles.

| Método                         | Descripción                | Tipo de Token |
| ------------------------------ | -------------------------- | ------------- |
| `GET` /api/usuarios            | Obtener Usuarios           | Admin         |
| `GET` /api/usuarios/:id        | Obtener Usuario            | Admin         |
| `GET` /api/usuarios/inactivos  | Obtener Usuarios inactivos | Admin         |
| `POST` /api/usuarios           | Nuevo Usuario              | Sin Token     |
| `POST` /api/usuarios/login     | Login Usuario              | Sin Token     |
| `POST` /api/usuarios/confirmar | Confirmar Usuario          | Admin         |
| `PUT` /api/usuarios/:id        | Modificar Usuario          | Admin         |
| `DELETE` /api/usuarios/:id     | Borrar Usuario             | Admin         |

### Empleados

Ir a [Pagina de Empleados](/API/empleados/introduccion/) para mas detalles.

| Método                             | Descripción                   | Tipo de Token |
| ---------------------------------- | ----------------------------- | ------------- |
| `GET` /api/empleados               | Obtener Empleados             | Normal        |
| `GET` /api/empleados/:id           | Obtener Empleado              | Normal        |
| `POST` /api/empleados              | Nuevo Empleado                | Normal        |
| `PATCH` /api/empleados/:id/estado/ | Modificar Estado del Empleado | Admin         |
| `DELETE` /api/empleados/:id        | Borrar Empleado               | Admin         |

### Camiones

Ir a [Pagina de Camiones](/API/camiones/introduccion/) para mas detalles.

| Método                     | Descripción      | Tipo de Token |
| -------------------------- | ---------------- | ------------- |
| `GET` /api/camiones        | Obtener Camiones | Normal        |
| `GET` /api/camiones/:id    | Obtener Camion   | Normal        |
| `POST` /api/camiones       | Nuevo Camion     | Normal        |
| `PUT` /api/camiones/:id    | Modificar Camion | Normal        |
| `DELETE` /api/camiones/:id | Borrar Camion    | Admin         |

### Jornales

Ir a [Pagina de Jornales](/API/jornales/introduccion/) para mas detalles.

| Método                                             | Descripción                                            | Tipo de Token |
| -------------------------------------------------- | ------------------------------------------------------ | ------------- |
| `POST` /api/jornales                               | Nuevo jornal                                           | Normal        |
| `GET` /api/jornales/:jornalId                      | Obtener jornal                                         | Normal        |
| `GET` /api/jornales/todos/:inicio/:fin             | Obtener jornales de todos los empleados entre 2 fechas | Normal        |
| `GET` /api/jornales/:empleadoId/:inicio/:fin       | Obtener jornales de un empleado entre 2 fechas         | Normal        |
| `GET` /api/jornales/horas/:empleadoId/:inicio/:fin | Obtener horas trabajadas de un empleado entre 2 fechas | Normal        |
| `PUT` /api/jornales/:jornalId/                     | Modificar jornal                                       | Admin         |
| `DELETE` /api/jornales/:jornalIdid                 | Borrar jornal                                          | Admin         |

### Servicios del Camion

Ir a [Pagina de Servicios](/API/servicios-camion/introduccion/) para mas detalles.

| Método                         | Descripción                              | Tipo de Token |
| ------------------------------ | ---------------------------------------- | ------------- |
| `POST` /api/servicios          | Nuevo servicio                           | Normal        |
| `GET` /api/servicios/:camionId | Obtener todos los servicios de un camion | Normal        |
| `GET` /api/servicios/          | Obtener todos los servicios              | Normal        |

### Historico del uso del Camion

Ir a [Pagina de Historico de usos del camion](/API/historico-uso-camion/introduccion/) para mas detalles.

| Método                                    | Descripción                                                       | Tipo de Token |
| ----------------------------------------- | ----------------------------------------------------------------- | ------------- |
| `POST` /api/historico-camion              | Registro de una nueva asignacion de camion                        | Normal        |
| `GET` /api/historico-camion/              | Obtener Asignaciones Actuales de los camiones                     | Normal        |
| `GET` /api/historico-camion?empleadoId=id | Obtener el historico de asignaciones de los camiones por empleado | Normal        |
| `GET` /api/historico-camion?camionId=id   | Obtener el historico de asignaciones de los camiones por camion   | Normal        |
