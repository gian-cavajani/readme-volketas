```http
GET /api/empleados
```

### Descripción

Obtiene una lista de todos los empleados, incluyendo sus teléfonos asociados.

#### Parámetros y Headers de la Solicitud

Sin Parámetros.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

**Código**: 200 OK

```json
[
  {
    "id": 1,
    "nombre": "Juan Perez",
    "rol": "chofer",
    "cedula": 12345678,
    "habilitado": true,
    "createdAt": "2024-06-07T22:31:06.148Z",
    "updatedAt": "2024-06-07T22:31:06.148Z",
    "TelefonoPropietarios": [
      {
        "telefonoId": 1,
        "Telefonos": {
          "telefono": "24127332",
          "tipo": "telefono"
        }
      }
    ]
  }
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

**Causa:** Error al obtener los empleados.

```json
{
  "error": "Error al obtener los empleados",
  "detalle": ["Detalle del error de Sequelize"]
}
```
