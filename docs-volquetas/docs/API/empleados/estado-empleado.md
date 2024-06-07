# Estado Empleado

```http
PATCH /api/empleados/:empleadoId/estado
```

#### Parámetros y Headers de la Solicitud

- `empleadoId` (number): El ID del empleado cuyo estado será cambiado. Debe ser proporcionado en la URL.

Se debera incluir Authorization header con jwt creado con el usuario tipo **Admin** en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

- **Código**: 202 Accepted

  - **Contenido**:

    ```json
    {
      "detalle": "Empleado {nombre} con CI: {cedula} fue {habilitado/deshabilitado} exitosamente"
    }
    ```

#### Errores

#### Error 400 - Bad Request

- **Causa**: Id en parámetros no es un entero.

  - Contenido:
    ```json
    { "error": "El ID del empleado debe ser un entero" }
    ```

- **Causa:** El empleado no encontrado.
  - **Contenido:**
    ```json
    {
      "error": "Empleado no existe"
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

#### Error 500 - Internal Server Error

- **Causa:** Error al obtener los empleados.
  - Contenido:
    ```json
    {
      "error": "Error al habilitar/deshabilitar al empleado",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
