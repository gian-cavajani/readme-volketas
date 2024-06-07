## Confirmar Usuario

```http
POST /api/usuarios/confirmar
```

#### Parámetros y Headers de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `email` (string): El email del usuario.

Se debera incluir Authorization header con jwt creado con un usuario de tipo **Admin** en el metodo `POST /usuarios/login`

#### Ejemplo de Solicitud

```json
{
  "email": "usuario@example.com"
}
```

### Respuestas

### Éxito

- **Código:** 202 Accepted
- **Contenido:**
  ```json
  "Usuario con mail: usuario@example.com activado exitosamente"
  ```

### Errores

#### Error 400 - Bad Request

- **Causa:** Falta el email.
  - **Contenido:**
    ```json
    { "error": "Email es obligatorio" }
    ```
- **Causa:** Usuario ya activado.

  - **Contenido:**
    ```json
    { "error": "Usuario ya esta activado" }
    ```

- **Causa:** Usuario con ese email no existe.
  - **Contenido:**
    ```json
    { "error": "Usuario con ese mail no existe" }
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
      "error": "Error al activar usuario",
      "detalle": "Mensaje de error"
    }
    ```
