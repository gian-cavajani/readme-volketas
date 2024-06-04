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
