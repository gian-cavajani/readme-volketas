```http
PATCH /api/empleados/:empleadoId/estado
```

### Descripción

Modifica el estado (habilitado/deshabilitado) de un empleado.

#### Parámetros y Headers de la Solicitud

- `empleadoId` (number): El ID del empleado cuyo estado será cambiado. Debe ser proporcionado en la URL.

Se debera incluir Authorization header con jwt creado con el usuario tipo **Admin** en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

**Código**: 202 Accepted

```json
{
  "detalle": "Empleado {nombre} con CI: {cedula} fue {habilitado/deshabilitado} exitosamente"
}
```

#### Errores

#### Error 400 - Bad Request

**Causa**: Id en parámetros no es un entero.

```json
{ "error": "El ID del empleado debe ser un entero" }
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

**Causa**: El empleado con el ID especificado no fue encontrado.

```json
{
  "error": "Empleado no existe"
}
```

#### Error 500 - Internal Server Error

**Causa:** Error al obtener los empleados.

```json
{
  "error": "Error al habilitar/deshabilitar al empleado",
  "detalle": ["Detalle del error de Sequelize"]
}
```
