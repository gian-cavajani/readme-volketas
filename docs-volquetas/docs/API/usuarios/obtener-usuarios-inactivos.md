```http
GET /api/usuarios
```

#### Parámetros y Headers de la Solicitud

Sin Parámetros.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

### Éxito

**Código:** 200 OK

```json
[
  {
    "id": 2,
    "rol": "normal",
    "email": "usuario@example.com",
    "empleadoId": 1,
    "activo": false
  },
  {...}
]
```

### Errores

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

**Causa:** Error general del servidor.

```json
{
  "error": "Error al obtener los usuario",
  "detalle": "Mensaje de error"
}
```
