## Endpoint `/api/jornales`

Esta API permite la gestión de jornales en un sistema. Incluye la creación de nuevos jornales, obtención de jornales por periodos y de la lista de jornales.

### Jornales

| Método                                             | Descripción                                            | Tipo de Token |
| -------------------------------------------------- | ------------------------------------------------------ | ------------- |
| `POST` /api/jornales                               | Nuevo jornal                                           | Normal        |
| `GET` /api/jornales/:jornalId                      | Obtener jornal                                         | Normal        |
| `GET` /api/jornales/todos/:inicio/:fin             | Obtener jornales de todos los empleados entre 2 fechas | Normal        |
| `GET` /api/jornales/:empleadoId/:inicio/:fin       | Obtener jornales de un empleado entre 2 fechas         | Normal        |
| `GET` /api/jornales/horas/:empleadoId/:inicio/:fin | Obtener horas trabajadas de un empleado entre 2 fechas | Normal        |
| `PUT` /api/jornales/:jornalId/                     | Modificar jornal                                       | Admin         |
| `DELETE` /api/jornales/:jornalIdid                 | Borrar jornal                                          | Admin         |
