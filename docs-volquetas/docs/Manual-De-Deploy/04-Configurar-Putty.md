Personalmente(Gianluca) uso Putty en el trabajo por lo que estoy acostumbrado a su funcionamiento. Por esto y por las ventajas que ofrece es que voy a utilizar Putty para conectarme remotamente a las instancias.

## Instalar Putty

1.  Para instalar putty en windows que es mi sistema operativo(Si usaramos linux podemos conectarnos desde cualquier terminal con el comando ssh) debemos ir a https://www.putty.org/ donde podremos descargar el cliente.![Pasted image 20240826210357.png](../Configurar%20Putty/0ad1a26777411c444895cb6dad5292b8c2465748.png 'wikilink')
2.  Nos lleva a esta pagina de descargas y elegimos la misma para nuestra arquitectura, en mi caso 64bit x86![Pasted image 20240826210535.png](../Configurar%20Putty/67baa7f735104b284442f5d189639360e9859ab3.png 'wikilink')
3.  Una vez descargado abrimos el instalador .msi e instalamos putty. Como se demuestra a continuación.
4.  Cliqueamos Next
    ![Pasted image 20240826210823.png](../Configurar%20Putty/bec8afce965b993a36171ae4d99b82d6b6376194.png 'wikilink')
5.  Elegimos carpeta y Next
    ![Pasted image 20240826210848.png](../Configurar%20Putty/b98ad027cd51c83b8512d7a99b86585ad897613f.png 'wikilink')
6.  Install
    ![Pasted image 20240826210935.png](../Configurar%20Putty/29978b4316507f4d784b5b32ffe560099b95b2ed.png 'wikilink')
7.  Finish
    ![Pasted image 20240826211015.png](../Configurar%20Putty/4824363e92df2847ee51039ee795d44d1d63299a.png 'wikilink')

## Configurar Putty

1.  Una vez instalado debemos configurarlo para poder conectarnos a nuestra instancia.
2.  Abrimos Putty y deberiamos ver algo asi, (ignorar las "Saved Session", ya crearemos una nueva):
    ![Pasted image 20240826211146.png](../Configurar%20Putty/dd451f9348f4792f59eb6cbbe5206ca3b475715f.png 'wikilink')
3.  Ya que configuramos el puerto 22 para ser usado con SSH en: [Configurar Security Rules](02-Configurar-Security-Rules.md 'wikilink') ahora podemos acceder remotamente a nuestra instancia donde tenemos Node.js corriendo con el backend. Para acceder y crear una sesión nos dirigimos al recuadro de Host Name(or IP address) y colocamos la [IP Elastica](03-Configurar-IPs-Elasticas.md 'wikilink') del servidor y Port 22.
4.  Opcionalmente pero muy recomendado es agregar un nombre a la conexión en "Saved Sessions" cliquear en "Save".
    ![Pasted image 20240826211928.png](../Configurar%20Putty/7bbb2436b2526a02531be09262e237580d0aca90.png 'wikilink')
5.  Si cliqueo en Open no va a funcionar, esto funcionaria en el caso de no haber creado un par de claves. Ya que las creamos debemos configurar la clave privada para que putty la envie al servidor para chequear que quien se esta conectando es alguien que tiene la clave privada cada vez que nos conectamos. Esto lo hace comparando el par de claves publica-privada. Para ello en el panel izquierdo vamos a "Connection" -\> "SSH" -\> "Auth" -\> "Credentials"
    ![Pasted image 20240826212314.png](../Configurar%20Putty/93ff734ca953664fc040e9b3d2f388724751d015.png 'wikilink')
6.  Como se puede observar no tenemos ninguna clave. Como recordaran, al momento de crear la [instancia](01-Crear-Instancias.md 'wikilink') descargamos la clave privada en un lugar seguro, ahora debemos buscar esa clave cliqueando en el primer "Browse".
    ![Pasted image 20240826212504.png](../Configurar%20Putty/d22be1562fdb55e93bdf90a90f0837be2e20180a.png 'wikilink')
7.  Yo había creado "llaves-deploy" para la conexión con la instancia del manual. Pero en este caso quiero conectarme a la instancia de node para la que ya tenia una clave privada llamada "keyFrontBackTest.ppk". Selecciono la misma.
8.  Para guardar los cambios y no repetir este proceso cada vez que quiero loguearme vuelvo al panel de "Session" que es el panel predeterminado y Cliqueo en save nuevamente.
    ![Pasted image 20240826212932.png](../Configurar%20Putty/a7b2e2f3ae654d2709d6ca5fb5ad3b4c5b36a8a3.png 'wikilink')
9.  Ahora si, entramos a la instancia clickeando "Open".
10. Por ultimo debemos ingresar con algún usuario al servidor, de forma predeterminada Amazon linux tiene el usuario "ec2-user", así que nos logueamos con este (Aclaración: puede ser el caso que para otras distribuciones de linux el usuario predeterminado pida una contraseña, alternativamente como otro método de protección podemos crear una para cualquier usuario o podemos crear un usuario nuevo, pero no entra dentro del scope del proyecto).
    ![Pasted image 20240826213230.png](../Configurar%20Putty/27bdee6973c7de567badc13ea6f8d18fa2e5f9cb.png 'wikilink')
11. Al ingresar podemos ver que hay varios mensajes que descriptivos.
    1. "Authenticating with public key"keyFrontBackTest" esto significa que esta chequeando la key que le pasamos contra la key que tiene en el servidor.
    2. "A newer release of Amazon Linux is available"... Quiere decir que tenemos nuevas actualizaciones para hacer pero lo haremos en la siguiente seccion.
    3. "Last Login: ..." La ultima vez que accedi, dice 02:11 AM pero es porque esta seteado con el huso horario UTC.
12. Pero todo esto no es para esta seccion, lo importante es que ya estamos dentro del servidor listos para configurar la instancia.
