```http
DELETE /api/camiones/:camionId
```

#### Parámetros y Headers de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body :

- `camionId` (integer, required): El ID del camión a borrar.

Se debera incluir Authorization header con jwt creado con el usuario(Admin) en el metodo `POST /usuarios/login`

#### Ejemplo de Solicitud

```http
DELETE /api/camiones/1
```

## Respuestas

### Éxito

**Código**: 200 OK

```json
{
  "message": "Camión borrado exitosamente"
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

#### Error 404 - Not Found

**Causa:** Camión no encontrado.

```json
{ "error": "Camión no encontrado." }
```

#### Error 500 - Internal Server Error

**Causa:** Error al actualizar el camion.

```json
{
  "error": "Error al actualizar el camion",
  "detalle": ["Detalle del error de Sequelize"]
}
```
