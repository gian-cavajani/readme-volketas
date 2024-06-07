## Registrar Usuario

```http
POST /api/usuarios
```

#### Parámetros y Headers de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `rol` (string): El rol del usuario (debe ser 'admin' o 'normal').
- `email` (string): El email del usuario.
- `password` (string): La contraseña del usuario.
- `confirmPassword` (string): Confirmación de la contraseña (debe coincidir con `password`).
- `empleadoId` (integer): ID del empleado asociado al usuario.

No se deberan incluir Headers.

#### Ejemplo de Solicitud

```json
{
  "rol": "admin",
  "email": "usuario@example.com",
  "password": "password123",
  "confirmPassword": "password123",
  "empleadoId": 1
}
```

### Respuestas

### Éxito

- **Código:** 201 Created
- **Contenido:**
  ```json
  {
    "id": 1,
    "email": "usuario@example.com",
    "empleadoId": 1,
    "rol": "admin",
    "activo": false
  }
  ```

### Errores

#### Error 400 - Bad Request

- **Causa:** Algún campo obligatorio falta o es inválido.
  - **Contenido:**
    ```json
    { "error": "Todos los campos son obligatorios" }
    ```
- **Causa:** El email no es válido.
  - **Contenido:**
    ```json
    { "error": "Email inválido" }
    ```
- **Causa:** Las contraseñas no coinciden.
  - **Contenido:**
    ```json
    { "error": "Las contraseñas no coinciden" }
    ```
- **Causa:** El rol no es válido.
  - **Contenido:**
    ```json
    { "error": "Rol inválido" }
    ```
- **Causa:** El empleado no existe.
  - **Contenido:**
    ```json
    { "error": "Empleado no existe" }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error del servidor o errores específicos de Sequelize.
  - **Contenido:**
    ```json
    {
      "error": "Error al crear usuario",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
- **Causa:** Error general del servidor.
  - **Contenido:**
    ```json
    {
      "error": "Error al crear usuario",
      "detalle": "Mensaje de error"
    }
    ```
