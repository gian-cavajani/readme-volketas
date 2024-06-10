```http
GET /api/camiones
```

#### Parámetros y Headers de la Solicitud

Sin Parámetros.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

**Código**: 200 OK

```json
[{
  "id": 1,
  "matricula": "ABC123",
  "modelo": "Modelo XYZ",
  "anio": 2020,
  "estado": "Disponible",
  "createdAt": "2024-06-01T00:00:00.000Z",
  "updatedAt": "2024-06-01T00:00:00.000Z"
},
{...}
]
```

#### Errores

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
  "error": "Error al crear camion",
  "detalle": ["Detalle del error de Sequelize"]
}
```
