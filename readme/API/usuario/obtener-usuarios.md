## Obtener Usuarios

```http
GET /api/usuarios
```

#### Parámetros y Headers de la Solicitud

Sin Parámetros.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

### Éxito

- **Código:** 200 OK
- **Contenido:**
  ```json
  [
    {
      "id": 1,
      "rol": "admin",
      "email": "usuario@example.com",
      "empleadoId": 1,
      "activo": true
    },
    {...}
  ]
  ```

### Errores

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
- **Causa:** Usuario en el Token de autorización no es de tipo Admin.
  - **Contenido:**
    ```json
    { "error": "Debe iniciar sesion como administrador para ver este segmento" }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error general del servidor.
  - **Contenido:**
    ```json
    {
      "error": "Error al obtener los usuario",
      "detalle": "Mensaje de error"
    }
    ```
