## Obtener Empleados

```http
DELETE /api/empleados/:empleadoId
```

#### Parámetros y Headers de la Solicitud

- `empleadoId` (number): El ID del empleado a eliminar. Debe ser proporcionado en la URL.

Se debera incluir Authorization header con jwt creado con el usuario tipo **Admin** en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

- **Código**: 200 OK

  - **Contenido**:

    ```json
    {
      "detalle": "Empleado eliminado exitosamente"
    }
    ```

#### Errores

#### Error 400 - Bad Request

- **Causa**: Id en parámetros no es un entero.

  - Contenido:
    ```json
    { "error": "El ID del empleado debe ser un entero" }
    ```

- **Causa:** El empleado tiene un usuario vinculado.
  - **Contenido:**
    ```json
    {
      "error": "No se puede eliminar el empleado porque tiene un usuario vinculado"
    }
    ```

#### Error 401 - Unauthorized

- **Causa:** Token de autorización no proporcionado.
  - **Contenido:**
    ```json
    { "error": "Token de autorización no proporcionado" }
    ```
- **Causa:** Token de autorización invalido o vencido.
  - **Contenido:**
    ```json
    { "error": "Debe iniciar Sesion - TOKEN INVALIDO" }
    ```
- **Causa:** Usuario en el Token de autorización no es de tipo Admin.
  - **Contenido:**
    ```json
    { "error": "Debe iniciar sesion como administrador para ver este segmento" }
    ```

#### Error 404 - Not Found

- **Causa**: Empleado no encontrado.
  - **Contenido:**
    ```json
    {
      "error": "Empleado no encontrado"
    }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error al obtener los empleados.
  - Contenido:
    ```json
    {
      "error": "Error al eliminar empleado",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
