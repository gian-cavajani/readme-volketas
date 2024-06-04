# Proyecto

Proyecto de gestor de volquetas en node.js con postgressql.

#### Relacionado:

Proyecto frontend en Reactjs: [Frontend](https://github.com/davidLB890/volquetasFront)

## Tabla de Contenidos

- [Librerias NPM utilizadas](#Librerias-NPM-utilizadas)
- [Variables de entorno](#variables-de-entorno)
- [Documentacion de la API](#documentacion-de-la-api)
  - [/api/usuarios](#endpoint-apiusuarios)
    - [Registrar Usuario `POST /usuarios`](#registrar-usuario)
    - [Login Usuario `POST usuarios/login`](#login-usuario)
    - [Obtener Usuarios `GET /usuarios`](#obtener-usuarios)
    - [Confirmar Usuario `POST /usuarios/confirmar`](#confirmar-usuario)
  - [/api/empleados](#endpoint-apiempleados)
    - [Registrar Empleado `POST /empleados`](#registrar-empleado)
    - [Obtener Empleados `GET /empleados`](#obtener-empleados)
    - [Obtener Empleado `GET /empleados/:n`](#obtener-empleado)
  - ...
- [Modelos](#modelos)
  - [Usuarios](#usuarios)
  - [Empleados](#empleados)
  - [Camiones](#camiones)
  - [Telefonos](#telefonos)
  - [Servicios](#servicios)
  - [HistoricoUsoCamion](#historicousocamion)
- Autores

## Librerias NPM utilizadas

- bcryptjs: `version: 2.4.3`
- cors: `version: 2.8.5`
- dotenv: `version: 16.4.5`
- express: `version: 4.19.2`
- jsonwebtoken: `version: 9.0.2`
- pg: `version: 8.11.5`
- sequelize: `version: 6.37.3`
- validator: `version: 13.12.0`

#### Librerias de Desarrollo:

- nodemon: `version 3.1.1`

## Variables de Entorno

Para ejecutar este proyecto hace falta agregar las siguientes variables al archivo .env:

`PORT` Puerto donde esta corriendo el servidor
`SECRETO` Secreto para generar el hash de las contrasenas

# Documentacion de la api

# Endpoint `/api/usuarios`

Esta API permite la gestión de usuarios en un sistema. Incluye la creación de nuevos usuarios, autenticación, activación de usuarios y la obtención de la lista de usuarios.

## Registrar Usuario

```http
POST /api/usuarios
```

#### Parámetros de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `rol` (string): El rol del usuario (debe ser 'admin' o 'normal').
- `email` (string): El email del usuario.
- `password` (string): La contraseña del usuario.
- `confirmPassword` (string): Confirmación de la contraseña (debe coincidir con `password`).
- `empleadoId` (integer): ID del empleado asociado al usuario.

#### Headers de la Solicitud

No se deberan incluir Headers.

#### Ejemplo de Solicitud

```json
{
  "rol": "admin",
  "email": "usuario@example.com",
  "password": "password123",
  "confirmPassword": "password123",
  "empleadoId": 1
}
```

### Respuestas

### Éxito

- **Código:** 201 Created
- **Contenido:**
  ```json
  {
    "id": 1,
    "email": "usuario@example.com",
    "empleadoId": 1,
    "rol": "admin",
    "activo": false
  }
  ```

### Errores

#### Error 400 - Bad Request

- **Causa:** Algún campo obligatorio falta o es inválido.
  - **Contenido:**
    ```json
    { "error": "Todos los campos son obligatorios" }
    ```
- **Causa:** El email no es válido.
  - **Contenido:**
    ```json
    { "error": "Email inválido" }
    ```
- **Causa:** Las contraseñas no coinciden.
  - **Contenido:**
    ```json
    { "error": "Las contraseñas no coinciden" }
    ```
- **Causa:** El rol no es válido.
  - **Contenido:**
    ```json
    { "error": "Rol inválido" }
    ```
- **Causa:** El empleado no existe.
  - **Contenido:**
    ```json
    { "error": "Empleado no existe" }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error del servidor o errores específicos de Sequelize.
  - **Contenido:**
    ```json
    {
      "error": "Error al crear usuario",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
- **Causa:** Error general del servidor.
  - **Contenido:**
    ```json
    {
      "error": "Error al crear usuario",
      "detalle": "Mensaje de error"
    }
    ```

## Login Usuario

```http
POST /api/usuarios/login
```

#### Parámetros de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `email` (string): El email del usuario.
- `password` (string): La contraseña del usuario.

#### Headers de la Solicitud

No se deberan incluir Headers.

#### Ejemplo de Solicitud

```json
{
  "email": "usuario@example.com",
  "password": "password123"
}
```

### Respuestas

### Éxito

- **Código:** 200 OK
- **Contenido:**
  ```json
  {
    "token": "jwt_token"
  }
  ```

### Errores

#### Error 400 - Bad Request

- **Causa:** Falta el email o la contraseña.
  - **Contenido:**
    ```json
    { "error": "Email y contraseña son obligatorios" }
    ```

#### Error 401 - Unauthorized

- **Causa:** Credenciales inválidas.
  - **Contenido:**
    ```json
    { "error": "Credenciales inválidas" }
    ```
- **Causa:** Usuario no activado.
  - **Contenido:**
    ```json
    { "error": "Usuario no activado" }
    ```

#### Error 500 - Internal Server Error

- **Causa:** Error del servidor o errores específicos de Sequelize.
  - **Contenido:**
    ```json
    {
      "error": "Error al crear usuario",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```
- **Causa:** Error general del servidor.
  - **Contenido:**
    ```json
    {
      "error": "Error al iniciar sesion",
      "detalle": "Mensaje de error"
    }
    ```

## Obtener Usuarios

```http
GET /api/usuarios
```

#### Parámetros de la Solicitud

Sin Parámetros.

#### Headers de la Solicitud

Se debera incluir Authorization header con jwt creado con el usuario en el metodo `POST /usuarios/login`

### Respuestas

### Éxito

- **Código:** 200 OK
- **Contenido:**
  ```json
  [
    {
      "id": 1,
      "rol": "admin",
      "email": "usuario@example.com",
      "empleadoId": 1,
      "activo": true
    },
    {...}
  ]
  ```

### Errores

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

- **Causa:** Error general del servidor.
  - **Contenido:**
    ```json
    {
      "error": "Error al obtener los usuario",
      "detalle": "Mensaje de error"
    }
    ```

## Confirmar Usuario

```http
POST /api/usuarios/confirmar
```

#### Parámetros de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `email` (string): El email del usuario.

#### Headers de la Solicitud

Se debera incluir Authorization header con jwt creado con un usuario de tipo **Admin** en el metodo `POST /usuarios/login`

#### Ejemplo de Solicitud

```json
{
  "email": "usuario@example.com"
}
```

### Respuestas

### Éxito

- **Código:** 202 Accepted
- **Contenido:**
  ```json
  "Usuario con mail: usuario@example.com activado exitosamente"
  ```

### Errores

#### Error 400 - Bad Request

- **Causa:** Falta el email.
  - **Contenido:**
    ```json
    { "error": "Email es obligatorio" }
    ```
- **Causa:** Usuario ya activado.

  - **Contenido:**
    ```json
    { "error": "Usuario ya esta activado" }
    ```

- **Causa:** Usuario con ese email no existe.
  - **Contenido:**
    ```json
    { "error": "Usuario con ese mail no existe" }
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

- **Causa:** Error general del servidor.
  - **Contenido:**
    ```json
    {
      "error": "Error al activar usuario",
      "detalle": "Mensaje de error"
    }
    ```

# Endpoint `/api/empleados`

Esta API permite la gestión de empleados en un sistema. Incluye la creación de nuevos empleados, obtención de un empleado y de la lista de empleados.

## Registrar Empleado

```http
POST /api/empleados
```

#### Parámetros de la Solicitud

La solicitud debe ser de tipo JSON y debe incluir los siguientes campos en el body:

- `nombre` (string): El nombre del empleado.
- `cedula` (string): La cédula del empleado (debe tener 8 dígitos).
- `rol` (string): El rol del empleado.

#### Ejemplo de Solicitud

```json
{
  "nombre": "Juan Perez",
  "cedula": "12345678",
  "rol": "admin"
}
```

### Respuestas

#### Éxito

- **Código**: 201 Created

  - **Contenido**:

    ```json
    {
      "id": 1,
      "nombre": "Juan Perez",
      "cedula": "12345678",
      "rol": "admin",
      "createdAt": "2024-06-01T00:00:00.000Z",
      "updatedAt": "2024-06-01T00:00:00.000Z"
    }
    ```

#### Errores

#### Error 400 - Bad Request

- **Causa**: La cédula no tiene 8 dígitos.
  - Contenido:
    ```json
    { "error": "Cedula invalida, deben ser 8 numeros" }
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

#### Error 500 - Internal Server Error

- **Causa:** Error al crear el empleado.
  - Contenido:
    ```json
    {
      "error": "Error al crear empleado",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```

## Obtener Empleados

```http
GET /api/empleados
```

### Respuestas

#### Éxito

- **Código**: 200 OK

  - **Contenido**:

    ```json

        [
          {
            "id": 1,
            "nombre": "Juan Perez",
            "cedula": "12345678",
            "rol": "admin",
            "Telefonos": [
              {
                "telefono": "987654321"
              }
            ]
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

- **Causa:** Error al obtener los empleados.
  - Contenido:
    ```json
    {
      "error": "Error al obtener los empleados",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```

## Obtener Empleado

```http
GET /api/empleados
```

### Respuestas

#### Éxito

- **Código**: 200 OK
  - **Contenido**:
    ```json
    {
      "id": 1,
      "nombre": "Juan Perez",
      "cedula": "12345678",
      "rol": "admin",
      "Telefonos": [
        {
          "telefono": "987654321"
        }
      ]
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

#### Error 500 - Internal Server Error

- **Causa:** Error al obtener el empleado.
  - Contenido:
    ```json
    {
      "error": "Error al obtener el empleado",
      "detalle": ["Detalle del error de Sequelize"]
    }
    ```

# Endpoint `/api/camiones`

# Modelos

## Usuarios

#### Campos del Modelo

- `id` (INTEGER): Clave primaria autoincremental.
- `empleadoId` (INTEGER): ID del empleado asociado al usuario. Este campo es obligatorio y único.
- `rol` (ENUM): Rol del usuario, que puede ser 'admin' o 'normal'. Este campo es obligatorio.
- `email` (STRING): Correo electrónico del usuario. Este campo es obligatorio y único.
- `password` (STRING): Contraseña del usuario. Este campo es obligatorio.
- `activo` (BOOLEAN): Estado de activación del usuario. Por defecto, es `false`.

#### Relaciones

- Empleados - Usuarios
  - Relación uno a uno (1:1) donde un usuario tiene un empleado asociado.

## Empleados

## Camiones

## Telefonos

## Servicios

## HistoricoUsoCamion

## Autor

- Gianluca Cavajani - cavajanig@gmail.com
