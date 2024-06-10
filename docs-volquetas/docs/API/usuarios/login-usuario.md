```http
POST /api/usuarios/login
```

#### Parámetros y Headers de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `email` (string): El email del usuario.
- `password` (string): La contraseña del usuario.

No se deberan incluir Headers.

#### Ejemplo de Solicitud

```json
{
  "email": "usuario@example.com",
  "password": "password123"
}
```

### Respuestas

### Éxito

**Código:** 200 OK

```json
{
  "token": "jwt_token"
}
```

### Errores

#### Error 400 - Bad Request

**Causa:** Falta el email o la contraseña.

```json
{ "error": "Email y contraseña son obligatorios" }
```

#### Error 401 - Unauthorized

**Causa:** Credenciales inválidas.

```json
{ "error": "Credenciales inválidas" }
```

#### Error 403 - Forbidden

**Causa:** Usuario no activado.

```json
{ "error": "Usuario no activado" }
```

#### Error 404 - Not Found

**Causa:** Usuario no encontrado.

```json
{ "error": "No hay usuario con ese email" }
```

#### Error 500 - Internal Server Error

**Causa:** Error del servidor o errores específicos de Sequelize.

```json
{
  "error": "Error al crear usuario",
  "detalle": ["Detalle del error de Sequelize"]
}
```

**Causa:** Error general del servidor.

```json
{
  "error": "Error al iniciar sesion",
  "detalle": "Mensaje de error"
}
```
