## En la instancia del frontend.

Descubrimos que tenemos un problema de memoria al hacer el npm run build (lo que debería generar los archivos estáticos a partir del proyecto React). Esto se debe a que la instancia tiene una memoria RAM muy reducida. Por lo que como alternativa estamos generando el build en local y transfiriéndolo al servidor mediante SFTP con Winscp.

Mensaje de error:
![Pasted image 20240827091906.png](../Deploy-Build-React/1a0c92faaf5e3431e003fadc35e713412c9e2a44.png 'wikilink')
\## Crear variables de entorno:

Antes de hacer el build debemos configurar las variables de entorno, para ello vamos al directorio del repo y creamos un archivo .env con los siguientes valores, esto indica a donde estará apuntando el frontend para hacer requests a la api:

    REACT_APP_API_URL=https://api.volquetas.site/api/

<figure>
<img
src="../Deploy-Build-React/c26e76341a0daa72b86a4205223d72dc95d6c804.png"
title="wikilink" alt="Pastedimage20240827105313.png" />
<figcaption
aria-hidden="true">Pastedimage20240827105313.png</figcaption>
</figure>

## Winscp:

1.  Como paso inicial debemos instalar y descargar Winscp, para ello nos dirigimos a https://winscp.net/eng/download.php
2.  Ami siempre me gusto utilizar los archivos portables para no tener que instalar nada en la maquina, para ello vamos a "OTHER DOWNLOADS"
    ![Pasted image 20240827092303.png](../Deploy-Build-React/e895e442e7638ca745120220a328775f0215699d.png 'wikilink')
3.  y clickeamos en el botón Download de "Portable Executables"
    ![Pasted image 20240827092336.png](../Deploy-Build-React/7f2e83e700517c7d1ae0298eb0176b44322dd5ae.png 'wikilink')
4.  Se descargara WinScp
    ![Pasted image 20240827092401.png](../Deploy-Build-React/698b7d9792575c37af2642ea1ac719d92dbe00f9.png 'wikilink')
5.  Ahora debemos ir a Winscp -\> Tools -\> Import Sites
    ![Pasted image 20240827092821.png](../Deploy-Build-React/a26d76fcf88206dada4794f82598ff7b66e57482.png 'wikilink')
6.  Elegimos las conexiones que queremos importar desde Putty y clickeamos OK:
    ![Pasted image 20240827092857.png](../Deploy-Build-React/115ef541e45eb59f994516ad934b9a52eadf01c0.png 'wikilink')
7.  Ahora podemos ver que se me crearon duplicados porque ya tenia las conexiones importadas, seleccionamos la conexión de react e ingresamos al servidor con el protocolo SFTP.
    ![Pasted image 20240827093035.png](../Deploy-Build-React/3c3303a25b2b1000771ae382e0636440f25c40e9.png 'wikilink')
8.  Nos pedirá nuestro usuario:
    ![Pasted image 20240827093055.png](../Deploy-Build-React/585cf0bf82ac05b49532fe88ba3191c5b1d38d3b.png 'wikilink')
9.  Y estamos dentro, ahora copiamos desde la pantalla izquierda (local) hacia la pantalla derecha (el servidor) el archivo build previamente creado con npm run build en nuestra maquina.
    ![Pasted image 20240827093205.png](../Deploy-Build-React/4f948c903115b33c0fecf8851c73baa8cc39c9cb.png 'wikilink')
10. Verificamos que el build este en nuestra instancia en el directorio /home/ec2-user/build:
    ![Pasted image 20240827093330.png](../Deploy-Build-React/534ae0d0a5e6d89acf8088a72f795da794407ba9.png 'wikilink')
11. El siguiente paso es hacer el deploy con [nginx](07-Configurar-NGINX.md 'wikilink'). Para ello habíamos instalado nginx y actualizado su archivo de configuración previamente.

### Mover archivos a carpeta de nginx

1.  Ahora que tenemos configurado Nginx y el build en el servidor debemos copiar el mismo con los archivos estáticos a la carpeta donde la configuración de nginx va a buscar los archivos en nuestro caso:

<!-- -->

    sudo cp -r build /var/www/html/volquetas-react/

2.  sudo systemctl reload nginx -\> resetea el proceso de nginx y aplica la nueva configuración/cambios.
3.  sudo systemctl enable nginx -\> hace que nginx se levante al levantar el servidor
    ![Pasted image 20240819162127.png](../Deploy-Build-React/fd615dbfb79d080ee95f3804e294e3e93c355376.png 'wikilink')

### Script para deploy automático

Para simplificar el proceso de deploy cree un script sencillo en shell para hacer el autodeploy, luego de que los archivos build esten en el servidor, este se encuentra en \~/scripts/autodeploy.sh:

    #!/bin/sh

    #script para hacer el deploy automaticamente una vez el build esta en el server.
    sudo cp -r ~/build /var/www/html/volquetas-react/
    sudo systemctl reload nginx
    sudo systemctl enable nginx

<figure>
<img
src="../Deploy-Build-React/01278bf0e3eb2d2cdff33f558f564e97907bd6e0.png"
title="wikilink" alt="Pastedimage20240819163050.png" />
<figcaption
aria-hidden="true">Pastedimage20240819163050.png</figcaption>
</figure>
