```http
POST /api/camiones
```

#### Parámetros y Headers de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `matricula` (string): La matrícula del camión.
- `modelo` (string): El modelo del camión.
- `anio` (number): El año de fabricación del camión.
- `estado` (string): El estado actual del camión.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

#### Ejemplo de Solicitud

```json
{
  "matricula": "ABC123",
  "modelo": "Modelo XYZ",
  "anio": 2020,
  "estado": "Disponible"
}
```

### Respuestas

#### Éxito

**Código**: 201 Created

```json
{
  "id": 1,
  "matricula": "ABC123",
  "modelo": "Modelo XYZ",
  "anio": 2020,
  "estado": "Disponible",
  "createdAt": "2024-06-01T00:00:00.000Z",
  "updatedAt": "2024-06-01T00:00:00.000Z"
}
```

#### Errores

#### Error 400 - Bad Request

**Causa**: No tiene matricula o modelo

```json
{ "error": "No tiene matricula o modelo" }
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

**Causa:** Error al crear el camion.

```json
{
  "error": "Error al crear camion",
  "detalle": ["Detalle del error de Sequelize"]
}
```
