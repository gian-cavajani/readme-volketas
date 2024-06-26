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

**Código:** 202 Accepted

```json
"Usuario con mail: usuario@example.com activado exitosamente"
```

### Errores

#### Error 400 - Bad Request

**Causa:** Falta el email.

```json
{ "error": "Email es obligatorio" }
```

**Causa:** Usuario ya activado.

```json
{ "error": "Usuario ya esta activado" }
```

#### Error 401 - Unauthorized

**Causa:** Token de autorización no proporcionado.

```json
{ "error": "Token de autorización no proporcionado" }
```

**Causa:** Token de autorización vencido.

```json
{ "error": "El token expiró, inicie sesión nuevamente" }
```

**Causa:** Token inválido

```json
{ "error": "Token inválido, inicie sesión nuevamente" }
```

**Causa:** Token de autorización requerido no es de un usuario Admin.

```json
{ "error": "Debe iniciar sesión como administrador." }
```

#### Error 404 - Not Found

**Causa:** Usuario con ese email no existe.

```json
{ "error": "Usuario con ese mail no existe" }
```

#### Error 500 - Internal Server Error

**Causa:** Error general del servidor.

```json
{
  "error": "Error al activar usuario",
  "detalle": "Mensaje de error"
}
```
