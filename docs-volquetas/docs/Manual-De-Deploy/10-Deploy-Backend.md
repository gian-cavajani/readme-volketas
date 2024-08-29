## En la instancia Backend

Para hacer el deploy en la instancia de Backend necesitamos: clonar el repo de Github, instalar y configurar git y npm, todo eso lo cubrimos en [Configuracion inicial del servidor](06-Configuracion-inicial-del-servidor.md 'wikilink'), [Configurar NGINX](07-Configurar-NGINX.md 'wikilink'), lo siguiente lo estaremos cubriendo en esta guía: actualizar las variables de entorno, instalar pm2.

1.  Primero debemos clonar el repo siguiendo los pasos en [ Configuracion inicial del servidor](06-Configuracion-inicial-del-servidor.md 'wikilink')
2.  Una vez clonado el repositorio en el servidor necesitamos actualizar las variables de entorno de la siguiente manera para asegurar un correcto funcionam:

    1.  DB_HOST: es el servidor de nuestra base de datos. En este caso esta hosteado en RDS, anteriormente era una instancia de EC2 pero decidimos migrar.
    2.  DB_PORT: es el puerto configurado para la Base de datos PostgreSQL, por defecto Postgres usa este puerto
    3.  DB_USER: el usuario de la base de datos
    4.  SECRETO: es una palabra secreta que utilizamos para crear un hash para las contrasenas con la libreria bcrypt
    5.  DB_PWD: es la contrasena para el acceso a la base de datos
    6.  DB_NAME: es el nombre de la base de datos a la que nos vamos a conectar
    7.  PORT: el puerto donde estara corriendo la aplicacion en localhost, luego haremos un proxy inverso con este puerto para que el trafico venga desde el puerto 80 y el 443.

    <!-- -->

        DB_HOST=volquetas.cagqhjhrcymf.us-east-1.rds.amazonaws.com
        DB_PORT=5432
        DB_USER=postgres
        SECRETO=palabrasecreta
        DB_PWD=perro-2310
        DB_NAME=volquetas
        PORT=3000

3.  Lo siguiente es instalar pm2 para dejar corriendo el servidor de node siempre que la instancia este prendida, ademas de esto pm2 provee otras caracteristicas como logging, chequeo de uso de CPU/Memoria/etc. Para instalar de forma globalmente haremos:

<!-- -->

       npm install -g pm2

3.  Para iniciar pm2 con el proyecto de node vamos a iniciar el archivo base donde la aplicacion esta corriendo en mi caso es en \~/apps/volquetas/index.js y adicionalmente uso la flag --name para darle un nombre al proceso:

<!-- -->

       pm2 start apps/volquetas/index.js --name "api-volquetas"

4.  Ahora pm2 esta corriendo pero en el caso de que el servidor se reinicie la aplicacion no volvera a iniciar. Para que pm2 inicie automaticamente debemos hacer lo siguiente:

<!-- -->

       pm2 startup
       pm2 save

5.  Puedo verificar que la aplicacion esta corriendo con el comando:

<!-- -->

       pm2 list

![Pasted image 20240827122514.png](../Deploy%20Backend/7c2ca9e08379657de50d1dcfadd6a1b2f03fba01.png 'wikilink') 6. Como ya habíamos configurado nginx lo único que debemos hacer es reiniciar el proceso para que tome los nuevos cambios ya que ahora el puerto 3000 esta siendo utilizado.

       sudo systemctl restart nginx

### Hacer nuevos deploys:

Si queremos hacer un nuevo deploy de nuestra aplicación en el servidor tenemos que hacer es lo siguiente:

1.  Debemos clonar el repo, y actualizar el proceso pm2

<!-- -->

    cd ~/apps/volquetas
    git pull https://github.com/gian-cavajani/volquetas.git

![Pasted image 20240827130441.png](../Deploy%20Backend/b1461aead48e5ab44f6edb35c09d325a89b5220d.png 'wikilink') 2. Ahora que tenemos los nuevos cambios debemos reiniciar el proceso de pm2 con:

    pm2 restart "api-volquetas"

![Pasted image 20240827131027.png](../Deploy%20Backend/940505a6ee3d09f0c21abb23551b663d9ce7efc5.png 'wikilink') 3. No es necesario reiniciar nginx a menos que los archivos de configuración o los archivos estáticos a los que nginx esta sirviendo hayan sido cambiados, este es el caso para la aplicación de react pero no para la de node.
