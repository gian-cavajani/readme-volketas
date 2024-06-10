```http
POST /api/empleados
```

#### Parámetros y Headers de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `nombre` (string): El nombre del empleado.
- `cedula` (string): La cédula del empleado (debe tener 8 dígitos).
- `rol` (string): El rol del empleado. Puede ser "admin", "normal" o "chofer".

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

#### Ejemplo de Solicitud

```json
{
  "nombre": "Juan Perez",
  "cedula": "12345678",
  "rol": "admin"
}
```

### Respuestas

#### Éxito

**Código**: 201 Created

```json
{
  "id": 1,
  "nombre": "Juan Perez",
  "cedula": "12345678",
  "rol": "admin",
  "habilitado": "true",
  "createdAt": "2024-06-01T00:00:00.000Z",
  "updatedAt": "2024-06-01T00:00:00.000Z"
}
```

#### Errores

#### Error 400 - Bad Request

**Causa**: La cédula no tiene 8 dígitos.

```json
{ "error": "Cedula invalida, deben ser 8 numeros" }
```

**Causa**: Rol no es ni "admin", ni "normal", ni "chofer".

```json
{ "error": "Rol invalido" }
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

#### Error 500 - Internal Server Error

**Causa:** Error al crear el empleado.

```json
{
  "error": "Error al crear empleado",
  "detalle": ["Detalle del error de Sequelize"]
}
```
