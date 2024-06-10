```http
PUT /api/usuarios/id
```

#### Parámetros y Headers de la Solicitud

URL:

`usuarioId` (integer, required): El ID del usuario a modificar.

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `rol` (string, optional): El rol del usuario.
- `email` (string, optional): El correo electrónico del usuario.
- `password` (string, optional): La contraseña del usuario.
- `activo` (boolean, optional): El estado activo del usuario.

Se debera incluir Authorization header con jwt creado con un usuario de tipo **Admin** en el metodo `POST /usuarios/login`

#### Ejemplo de Solicitud

```json
{
  "rol": "admin",
  "email": "usuario@example.com",
  "password": "password123",
  "confirmPassword": "password123"
}
```

### Respuestas

### Éxito

**Código:** 200 OK

```json
{
  "rol": "admin",
  "email": "usuario@example.com"
}
```

### Errores

#### Error 400 - Bad Request

**Causa:** Id pasado en parametros no es un entero

```json
{ "error": "El parámetro ${paramName} debe ser un entero" }
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

#### Error 500 - Internal Server Error

**Causa:** Error del servidor o errores específicos de Sequelize.

```json
{
  "error": "Error al modificar el usuario",
  "detalle": ["Detalle del error de Sequelize"]
}
```
