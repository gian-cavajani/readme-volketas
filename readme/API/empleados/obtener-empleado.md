## Obtener Empleado

```http
GET /api/empleados/:id
```

#### Parámetros y Headers de la Solicitud

- empleadoId (number): El ID del empleado. Debe ser proporcionado en la URL como parametro en la url.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

- **Código**: 200 OK
  - **Contenido**:
    ```json
    {
      "id": 1,
      "nombre": "Juan Perez",
      "cedula": "12345678",
      "rol": "admin",
      "habilitado": "true",
      "Telefonos": [
        {
          "telefono": "987654321"
        }
      ]
    }
    ```

#### Errores

#### Error 400 - Bad Request

- **Causa**: Id en parámetros no es un entero.
  - Contenido:
    ```json
    { "error": "El ID del empleado debe ser un entero" }
    ```

#### Error 401 - Unauthorized

- **Causa:** Token de autorización no proporcionado.
  - **Contenido:**
    ```json
    { "error": "Token de autorización no proporcionado" }
    ```
- **Causa:** Token de autorización invalido o vencido.
  - **Contenido:**
    ```json
    { "error": "Debe iniciar Sesion - TOKEN INVALIDO" }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error al obtener el empleado.
  - Contenido:
    ```json
    {
      "error": "Error al obtener el empleado",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
