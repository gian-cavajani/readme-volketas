---
hide:
    - toc
---

## Servicios-Camion:

| Método HTTP | Endpoint                 | Descripción                  | Parámetros (Body/Query/Path)                                         | Respuesta Exitosa                               | Respuesta de Error                                                                                                                     | Token de Login   |
| ----------- | ------------------------ | ---------------------------- | -------------------------------------------------------------------- | ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| POST        | /api/servicios           | Crear un nuevo servicio      | Body: `precio`, `camionId`, `tipo`, `fecha`, `descripcion`, `moneda` | 201 Created con los detalles del nuevo servicio | 400 Bad Request por tipo o moneda inválidos, o si el camión no existe <br>500 Internal Server Error con detalles del error de creación | Requerido        |
| GET         | /api/servicios           | Obtener todos los servicios  | \-                                                                   | 200 OK con la lista de servicios                | 500 Internal Server Error con detalles del error de consulta                                                                           | Requerido        |
| GET         | /api/servicios/:camionid | Obtener servicios por camión | Path: `camionId`                                                     | 200 OK con la lista de servicios                | 500 Internal Server Error con detalles del error de consulta                                                                           | Requerido        |
| GET         | /api/servicios/mensuales | Obtener servicios mensuales  | Query: `month`, `year`, `camionId`                                   | 200 OK con la lista de servicios                | 400 Bad Request por mes o año inválidos <br>500 Internal Server Error con detalles del error de consulta                               | Requerido        |
| DELETE      | /api/servicios/:id       | Eliminar un servicio         | Path: `servicioId`                                                   | 200 OK con mensaje de éxito                     | 400 Not Found si el servicio no existe <br>500 Internal Server Error con detalles del error de eliminación                             | Requerido(Admin) |
