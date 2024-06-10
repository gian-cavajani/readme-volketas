```http
DELETE /api/empleados/:empleadoId
```

### Descripción

Elimina un empleado específico si no tiene un usuario vinculado.

#### Parámetros y Headers de la Solicitud

- `empleadoId` (number): El ID del empleado a eliminar. Debe ser proporcionado en la URL.

Se debera incluir Authorization header con jwt creado con el usuario tipo **Admin** en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

**Código**: 200 OK

    ```json
    {
      "detalle": "Empleado eliminado exitosamente"
    }
    ```

#### Errores

#### Error 400 - Bad Request

**Causa**: Id en parámetros no es un entero.

    ```json
    { "error": "El ID del empleado debe ser un entero" }
    ```

**Causa:** El empleado tiene un usuario vinculado.

```json
{
  "error": "No se puede eliminar el empleado porque tiene un usuario vinculado"
}
```

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

**Causa**: Empleado no encontrado.

```json
{
  "error": "Empleado no encontrado"
}
```

#### Error 500 - Internal Server Error

**Causa:** Error al eliminar el empleado.

```json
{
  "error": "Error al eliminar empleado",
  "detalle": ["Detalle del error de Sequelize"]
}
```
