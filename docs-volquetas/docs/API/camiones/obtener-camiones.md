## Obtener Camiones

```http
GET /api/camiones
```

#### Parámetros y Headers de la Solicitud

Sin Parámetros.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

#### Éxito

- **Código**: 200 OK

  - **Contenido**:

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
    ...
    ]
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

#### Error 500 - Internal Server Error

- **Causa:** Error al crear el empleado.
  - Contenido:
    ```json
    {
      "error": "Error al crear camion",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
