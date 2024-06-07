## Obtener Camion

```http
GET /api/camiones/:camionId
```

#### Parámetros y Headers de la Solicitud

- `camionId` (number): El ID del camión a obtener. Debe ser proporcionado en la URL.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

- **Código**: 200 OK

  - **Contenido**:

    ```json
    {
      "id": 1,
      "matricula": "ABC123",
      "modelo": "Modelo XYZ",
      "anio": 2020,
      "estado": "Disponible"
    }
    ```

#### Errores

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

#### Error 404 - Not Found

- **Causa**: Camion no encontrado.
  - **Contenido:**
    ```json
    {
      "error": "Camion no encontrado"
    }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error al crear el empleado.
  - Contenido:
    ```json
    {
      "error": "Error al obtener el camion",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
