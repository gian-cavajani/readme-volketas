## Modificar Camion

```http
PUT /api/camiones/:camionId
```

#### Parámetros y Headers de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body (todos opcionales):

- `matricula` (string): La matrícula del camión.
- `modelo` (string): El modelo del camión.
- `anio` (number): El año del camión.
- `estado` (string): El estado del camión.

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

#### Ejemplo de Solicitud

```json
{
  "matricula": "ABC123",
  "modelo": "Scania",
  "anio": 2021,
  "estado": "Inactivo"
}
```

### Respuestas

#### Éxito

- **Código**: 200 OK

  - **Contenido**:
    ```json
    {
      "matricula": "ABC123",
      "modelo": "Scania",
      "anio": 2021,
      "estado": "Inactivo"
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

- **Causa:** Camión no encontrado.
  - **Contenido:**
    ```json
    { "error": "Camión no encontrado." }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error al actualizar el camion.
  - Contenido:
    ```json
    {
      "error": "Error al actualizar el camion",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
