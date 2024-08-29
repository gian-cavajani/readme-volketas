Para tener un dominio y poder utilizarlo en nuestros sitios primero hay que comprarlo, para ello tenemos que registrarlo en un "registrador acreditado" como "Host Gator", "Blue Host", "Name Cheap", etc

1.  Yo elegí HostGator para mi comprar el dominio -\> https://www.hostgator.com/domains, aquí elegimos un nombre de dominio y le damos comprar.
    ![Pasted image 20240827095617.png](../Comprar%20y%20Configurar%20Dominios/7d687739e96b8b6cf1e10b2bac18e896e8ed5c35.png 'wikilink')
2.  Al elegirlo tendremos que llenar datos de facturación
    ![Pasted image 20240827095559.png](../Comprar%20y%20Configurar%20Dominios/7e96cdd0101fe581a84fb94e241dd0143569458e.png 'wikilink')
3.  Y generaremos una factura
    ![Pasted image 20240827095715.png](../Comprar%20y%20Configurar%20Dominios/f80e29c47c1cf5459d084cd89d77fe52be7cf6de.png 'wikilink')
4.  Ahora tenemos que vincular ese dominio a nuestros servidores, para ello vamos a la sección de "Domains" y cliqueamos en "A records", Alli agregaremos la IP publica de nuestro servidor:
    ![Pasted image 20240827095823.png](../Comprar%20y%20Configurar%20Dominios/f3ab9911dff7fa32e15a8e87ee1579211a5f6ca6.png 'wikilink')
5.  Como paso adicional voy a crear un subdominio "api" para nuestro servidor del backend:
    ![Pasted image 20240827100104.png](../Comprar%20y%20Configurar%20Dominios/ac84520d7cb4df41490473e2b52e8ff1503f065a.png 'wikilink')
6.  Por lo que api.volquetas.site va a apuntar al servidor backend y volquetas.site al servidor frontend.
7.  Esto podria llegar a tomar unas horas, en mi caso tardo alrededor de 2 horas.
8.  Ahora debemos configurar el dominio en [Nginx](07-Configurar-NGINX.md 'wikilink'). Pero antes vamos debemos configurar el servidor.
