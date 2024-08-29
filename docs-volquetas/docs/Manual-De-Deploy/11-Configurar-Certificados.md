Lo siguiente es configurar los certificados para poder tener conexiones seguras HTTPS/SSL. Esto es para poder darle privacidad y seguridad al usuario encriptando la conexión.

## Instalar y configurar certbot.

1.  Para instalar los certificados primero debemos instalar el package de certbot, para ello ejecutamos el siguiente comando:

<!-- -->

       sudo yum install python3-certbot-nginx

![11-August-2024(21hrs_1304).png](../Configurar%20Certificados/c0268bc8741ef944118248a6deef41e2e308da79.png "wikilink")
2. Una vez instalado debemos ejecutar el siguiente comando y seguir los pasos:

       sudo certbot --nginx

3.  Tenemos que hacer esto tanto para la instancia de React como para la de Node.
4.  En la instancia de React elegimos 1: volquetas.site que era el dominio que habiamos comprado para utilizar. En el caso de la instancia del backend estaremos utilizando el subdominio api.volquetas.site
5.  Luego hacemos un reload del proceso de nginx ya que la instalación de el nuevo certificado con certbot --nginx modifica las configuraciones de nginx.
    ![11-August-2024(21hrs_4421).png](../Configurar%20Certificados/fdb032b44d6eb7a9edfc71ceb67840aea528a154.png "wikilink")

### Nuevas Configuraciones de Nginx

Ahora si vamos al archivo de configuración de nginx en la instancia de React, podemos ver que se agregaron un montón de lineas que refieren al puerto 443 que es el que sera utilizado por el trafico HTTPS. Ademas routea al directorio donde están las claves privadas y el cert chain completo.
![Pasted image 20240827101259.png](../Configurar%20Certificados/9a27e54a0741877604074c8ee17200900b1df967.png "wikilink")

Lo mismo sucede al instalar los certificados en la instancia de Node, el archivo de configuración fue modificado de igual manera:
![Pasted image 20240827102137.png](../Configurar%20Certificados/62162d1be97b6a94e26506f91b1d2a7993d0e71c.png "wikilink")

### Auto renovar certificados

Los certificados emitidos por certbot tienen una validez de 3 meses como podemos observar aqui:
![Pasted image 20240827144624.png](../Configurar%20Certificados/4631c326b9d3f650aaaef1888b6907bd8a8522a8.png "wikilink")

Para hacer la renovación automática podemos crear un cronjob de la siguiente manera:
1. En la linea de comandos escribimos lo siguiente:
2. Esto es para instalar cronie, lo cual nos permitirá crear cronjobs

       sudo yum install cronie

3.  Ahora debemos activar el daemon de cron para que los cron jobs se ejecuten en secundario

<!-- -->

       sudo systemctl start crond

4.  Ahora hacemos que el daemon se inicie al iniciar la instancia con:

<!-- -->

        sudo systemctl enable crond

5.  Por ultimo ejecutamos lo siguiente:

<!-- -->

     crontab -e

6.  Lo que nos llevara a un editor de vim y agregamos el siguiente cronjob cada un mes para que renueve los certificados, luego guardamos y salimos del editor: ![Pasted image 20240827145349.png](../Configurar%20Certificados/d8c5c4e21b74d0d9c2e63a44e68a84fbb2818ba6.png "wikilink")
7.  Por ultimo verificamos que el cronjob haya quedado correctamente guardado con:

<!-- -->

       crontab -l

<figure>
<img
src="../Configurar%20Certificados/1cf3212332abb6d9359016be32e6ca0abcadb609.png"
title="wikilink" alt="Pastedimage20240827145434.png" />
<figcaption
aria-hidden="true">Pastedimage20240827145434.png</figcaption>
</figure>
