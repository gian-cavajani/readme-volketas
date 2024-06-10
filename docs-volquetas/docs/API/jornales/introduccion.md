## Endpoint `/api/jornales`

La API proporciona endpoints para gestionar jornales de empleados. Permite crear, editar, eliminar y obtener jornales individuales o por periodo. También proporciona endpoints para obtener las horas trabajadas por empleado en un periodo específico. La autenticación se realiza mediante tokens JWT.

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
