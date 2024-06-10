```http
GET /api/empleados/:id
```

#### Parámetros y Headers de la Solicitud

- empleadoId (integer): El ID del empleado. Debe ser proporcionado en la URL como parametro en la url.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

**Código**: 200 OK

```json
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
```

#### Errores

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

#### Error 404 - Not Found

**Causa:** Empleado no encontrado.

```json
{ "error": "Empleado no encontrado" }
```

#### Error 500 - Internal Server Error

**Causa:** Error al obtener el empleado.

```json
{
  "error": "Error al obtener el empleado",
  "detalle": ["Detalle del error de Sequelize"]
}
```
