```http
DELETE /api/usuarios/id
```

#### Parámetros y Headers de la Solicitud

URL:

`usuarioId` (integer, required): El ID del usuario a Eliminar.

Ningun campo es requerido en el body:

Se debera incluir Authorization header con jwt creado con un usuario de tipo **Admin** en el metodo `POST /usuarios/login`

### Respuestas

### Éxito

**Código:** 200 OK

```json
{
  "detalle": "Usuario borrado exitosamente"
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
