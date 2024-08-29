# Proyecto

Proyecto de gestor de volquetas en node.js con postgressql.

[Repositorio del proyecto en node](https://github.com/gian-cavajani/volquetas)

[Repositorio de la documentacion](https://github.com/gian-cavajani/readme-volketas)

#### Relacionado:

Repositorio del Proyecto frontend en Reactjs: [Frontend](https://github.com/davidLB890/volquetasFront)

## Librerias NPM utilizadas

#### Librerias de Produccion:

-   bcryptjs: `version: 2.4.3`
-   cors: `version: 2.8.5`
-   dotenv: `version: 16.4.5`
-   express: `version: 4.19.2`
-   jsonwebtoken: `version: 9.0.2`
-   pg: `version: 8.11.5`
-   sequelize: `version: 6.37.3`
-   validator: `version: 13.12.0`

#### Librerias de Desarrollo:

-   nodemon: `version 3.1.1`

## Variables de Entorno

Para ejecutar este proyecto, es necesario agregar las siguientes variables al archivo `.env`:

**PORT**: Especifica el puerto en el que está corriendo el servidor.

Ejemplo: `PORT=3000`

**SECRETO**: Secreto utilizado para generar el hash de las contraseñas. Es una cadena de texto que se usa para la encriptación y debe mantenerse segura

Ejemplo: `SECRETO=miSecretoSuperSeguro`

**DB_USER**: Usuario de la base de datos. Es el nombre de usuario que se usa para conectarse a la base de datos.

Ejemplo: `DB_USER=miUsuarioBD`

**DB_PWD**: Contraseña de la base de datos. Es la contraseña asociada con el usuario de la base de datos.

Ejemplo: `DB_PWD=miContraseñaSegura`

**DB_HOST**: Host de la base de datos. Es la dirección del servidor de la base de datos.

Ejemplo: `DB_HOST=localhost`

**DB_NAME**: Nombre de la base de datos. Es el nombre de la base de datos a la que se conectará la aplicación.

Ejemplo: `DB_NAME=nombreDeMiBaseDeDatos`

### Ejemplo de archivo `.env`

A continuación se muestra un ejemplo de cómo debería verse el archivo `.env` con las variables de entorno configuradas:

```env
PORT=3000
SECRETO=miSecretoSuperSeguro
DB_USER=miUsuarioBD
DB_PWD=miContraseñaSegura
DB_HOST=localhost
DB_NAME=nombreDeMiBaseDeDatos
```

### Consideraciones de Seguridad

Nos aseguramos de agregar el archivo .env al archivo .gitignore para evitar que las credenciales y secretos sean expuestos en el repositorio de _Github_.

```gitignore
.env
```
