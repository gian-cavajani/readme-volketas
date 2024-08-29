Nginx es un web server que provee un monton de funcionalidades como logs de acceso, proxy reverso, manejo de certificados y sus configuraciones, etc. Nosotros lo usaremos para que el archivo estatico de HTML junto con los archivos js generados en el build queden siempre disponibles, ademas para configurar un dominio y sus certificados.

1.  Primero debemos instalar nginx en el servidor:

<!-- -->

    sudo yum install -y nginx

2.  El siguiente paso es crear un directorio para alojar el build un estandar para los sitios de frontend es usar /var/www/html/nombre-sitio/build. Por tanto

<!-- -->

       mkdir /var/www/html/volquetas-react/

3.  Ahora debemos decirle a nginx que archivos debe mirar para hostear en los diferentes puertos. Para ello vamos a crear una nueva configuracion en `/etc/nginx/conf.d/react.conf`
4.  Para nuestra instancia frontend deberia configurarse asi:

    1.  listen 80 -\> es el puerto de escucha, vamos a estar usando HTTP porque aun no tenemos el certificado.
    2.  server_name -\> es el dominio que previamente compramos y configuramos para apuntar a esta IP, en mi caso volquetas.site
    3.  root -\> es el directorio donde nuestro archivo html se encuentra, en nuestro caso /var/www/html/volquetas-react/build

    <!-- -->

        server {
             listen 80 ;
             listen [::]:80 ;
             server_name volquetas.site ;
             root /var/www/html/volquetas-react/build ;
             index index.html index.htm ;
             location / {
                     try_files $uri $uri/ =404 ;
             }
        }

5.  Para la instancia Backend la configuracion varia un poco ya que no se utiliza un archivo, si no que vamos a hacer un proxy_pass o proxy inverso desde el puerto 3000 hacia el 80, se deberia ver asi:

    1.  Explicare solo aquellas configuraciones distintas a la configuracion de react para no repetir.
    2.  En location configuraremos: proxy_pass que es desde que puerto esta funcionando la app node y al cual se rutearan las requeste que vengan por el puerto 80.
    3.  proxy_http_version 1.1; -\> es la version de HTTP, la 1.1 asegura compatibilidad.
    4.  proxy_set_header Upgrade \$http_upgrade; -\> Ajusta el header Upgrade con lo enviado por el cliente, es para manejar las conexiones websocket.
    5.  proxy_set_header Connection 'upgrade'; -\> parecida a la configuracion anterior es para mantener la conexion abierta para permitir actualizaciones de protocolo como por ejemplo con websocket.
    6.  proxy_set_header Host \$host; -\> esto asegura que el backend pueda manejar las solicitudes segun el host y que setee el host del cliente a el header Host
    7.  proxy_cache_bypass \$http_upgrade; -\> Esta directiva asegura que las solicitudes que contienen la cabecera Upgrade no usen la caché. Esto es importante para asegurar que las conexiones WebSocket no se vean afectadas por el almacenamiento en caché.

    <!-- -->

        server {
         server_name api.volquetas.site;

         location / {
             proxy_pass http://localhost:3000;
             proxy_http_version 1.1;
             proxy_set_header Upgrade $http_upgrade;
             proxy_set_header Connection 'upgrade';
             proxy_set_header Host $host;
             proxy_cache_bypass $http_upgrade;
         }
         listen 80;
         server_name api.volquetas.site;
        }

6.  Ahora si vemos en cualquiera de las dos instancias en el archivo /etc/nginx/nginx.conf, podremos observar que la configuracion esta siendo referenciada a este directorio:
    ![Pasted image 20240827103658.png](../Configurar%20NGINX/8dca240e82d251d6aaebe0aeb6d778b751dc3cb1.png)
7.  Para habilitar la configuración y recargar nginx ejecutamos el siguiente comando:

<!-- -->

       sudo nginx -t && sudo systemctl reload nginx

8.  Por ultimo para que nginx inicie automaticamente al iniciar el servidor debemos hacer el siguiente comando:

```
    sudo systemctl enable nginx
```

. Estos archivos (react.conf y node.conf) se actualizaran automaticamente un vez se instale el certificado, lo cual haremos en la seccion de: [Configurar Certificados](11-Configurar-Certificados.md). Esto con el fin de poder manejar solicitudes HTTPs, porque hasta el momento solo se podran hacer request via HTTP lo cual es inseguro y no recomendado. 10. Ahora Nginx quedo pronto para alojar nuestro sitio, el siguiente paso es crear el build y moverlo a la carpeta designada. Lo haremos en [Deploy Build React](08-Deploy-Build-React.md)
