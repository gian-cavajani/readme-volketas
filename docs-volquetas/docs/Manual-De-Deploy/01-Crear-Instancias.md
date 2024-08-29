## Ingreso a AWS Academy

En nuestro caso utilizaremos el AWS Learner labs con los 100USD de credito que la facultad ORT nos brinda, para configurar nuestro entorno de produccion.

1.  Como paso Inicial se debe ingresar a https://www.awsacademy.com/vforcesite/LMS_Login, Alli se debera seleccionar el boton de "Student Login".
    ![Pasted image 20240826175603.png](../Crear%20Instancias/515355b705a2eaef0bfd34063452eefbc9331364.png "wikilink")
2.  Seguidamente se utilizaran las credenciales de acceso
    ![Pasted image 20240826175728.png](../Crear%20Instancias/b3920b3e6acb0078f832145c3fd12f5c46105d41.png "wikilink")
3.  Una vez dentro se deberá ir a la sección de Courses -\> Modules -\> AWS Academy Learner Lab -\> Launch Academy Learner Lab
4.  Aquí cliqueamos en "Start Lab".
    ![Pasted image 20240826175515.png](../Crear%20Instancias/caa1475de1056f0fb22c2f0287adcae31ed853de.png "wikilink")
5.  Al cliquear en "Start Lab" el icono Rojo se debería transformar a verde.
    ![Pasted image 20240826180116.png](../Crear%20Instancias/b41510145bed24131410e5e3c1e27f9fe1ce0edc.png "wikilink")
6.  Cliqueamos en "AWS" y nos redirigirá a la pagina de AWS.

## Crear Instancias EC2

1.  Una vez dentro de la consola de AWS. Nos dirigimos a la barra de búsqueda y buscamos "EC2", hacemos click en la misma.
    ![Pasted image 20240826180430.png](../Crear%20Instancias/253812068979b7e2d356e1d8db93fa7802f7ec2e.png "wikilink")
2.  Cuando el Panel de EC2 cargue, seleccionamos "Lanzar la instancia", lo cual entrara en el panel de creacion de una nueva instancia.
    ![Pasted image 20240826180610.png](../Crear%20Instancias/83b358512c4600d6cca67c526fadc48d3717aeee.png "wikilink")

Aca tenemos varias opciones, iremos una por una para no dejar lugar a dudas o especulaciones:
![Pasted image 20240826180726.png](../Crear%20Instancias/1ce49ab9b5602fa547128535f1079b76112a040f.png "wikilink")

1.  En el lado derecho tenemos un panel de "Resumen" que de forma dinámica ira cambiando a medida que modificamos las opciones.
2.  En el lado izquierdo tenemos las opciones en si mismas.
3.  Como primera opción tenemos "Nombre y Etiquetas", esto es un nombre identificador del servidor. En mi caso le puse el nombre "Ejemplo-Deploy"
    ![Pasted image 20240826181150.png](../Crear%20Instancias/9cb7b7adb1f26dd8ac0bd95369890fde527d5e02.png "wikilink")
4.  No seleccione tags/etiquetas ya que a mi parecer con el nombre de la instancia es suficiente para poder identificar el servidor de manera efectiva. Pero en caso de tener muchos servidores se podrían agrupar con diferentes tags vinculadas.
5.  En la siguiente opción "Imágenes de aplicaciones y sistemas operativos (Imagen de máquina de Amazon)", Podremos elegir el tipo de Sistema operativo que sera utilizado en nuestra instancia. Tiene un buscador en caso de que el SO de
    preferencia no este entre los predeterminados. En mi caso elegí Amazon Linux.
    Este panel también nos brinda mas información acerca del tipo de SO y especificaciones.
    ![Pasted image 20240826181543.png](../Crear%20Instancias/8f0ca109e3e1443fa6ed41a97b55f91b434c37d7.png "wikilink")
6.  En la siguiente opción tenemos "Tipo de Instancia", para la version gratuita de AWS solo la t2.micro esta disponible, básicamente tiene 1 Core de CPU, 1GB de Memoria y nos da la información de el estimado del gasto por hora. Pero en caso de tener la version completa de AWS se podría elegir un sistema con mejores especificaciones.
    ![Pasted image 20240826181946.png](../Crear%20Instancias/374339c9214434aeff8a1f405bfb81f47a56f6d5.png "wikilink")
7.  En "Par de claves (inicio de sesion)" podremos crear o utilizar un par de claves ya existente para acceder remotamente a la instancia.![Pasted image 20240826182254.png](../Crear%20Instancias/57cb8c79dce4d0eb3b644bf19832b815882dc765.png "wikilink")
    1.  En nuestro caso clickeamos en "Crear un nuevo par de claves"
    2.  Nos generara el siguiente panel:
    3.  Aqui elegimos un nombre descriptivo para el par, en mi caso "llaves-deploy"
    4.  "RSA" como tipo de algoritmo para la creacion de las keys.
    5.  Y en mi caso .ppk ya que utilizo putty para ingresar remotamente al servidor.
    6.  Por ultimo cliqueamos en "Crear Par de Claves"
    7.  Nos generara un archivo descargable(clave privada-private key) que guardaremos en algun directorio seguro para utilizar luego al momento de conectarnos![Pasted image 20240826182610.png](../Crear%20Instancias/3d43398cadb1377d0e71b0f3fe3d84af17561d36.png "wikilink")![Pasted image 20240826182722.png](../Crear%20Instancias/c3593bafda14d76cc6a24cfcd0d944514f541f7b.png "wikilink")
8.  La siguiente opcion refiere a la configuracion de red, en principio creamos un grupo nuevo con todo chequeado, luego haremos la configuracion detallada de las reglas de entrada/salida una vez la instancia se haya creado. Esto es una suerte de reglas de firewall que podremos configurar.![Pasted image 20240826183016.png](../Crear%20Instancias/d4daaf74b5924e9783f54b68a2ab2325890055b2.png "wikilink")
9.  El siguiente panel refiere al "Almacenamiento"
    ![Pasted image 20240826183722.png](../Crear%20Instancias/7f5032a57b8f6503b2147e747b24d7a84e3c25aa.png "wikilink")
    1.  Aquí podremos elegir el tipo de disco duro, la capacidad, la velocidad de escritura, si queremos cifrarlo/encriptarlo y si queremos eliminarlo al eliminar la instancia o no(esto es util en caso de querer migrar el disco duro a otra instancia).
    2.  En nuestro caso dejamos todo por default, es un SSD de 20GB sin encriptar(por defecto 8GB).
    3.  Tambien podemos agregar otro volumen en caso de querer otro disco.
10. Por ultimo tenemos "Detalles Avanzados", nosotros dejaremos todo en default, ya que ninguna de las opciones entra en el scope de nuestras necesidades.
11. Por ultimo verificamos en el panel de "Resumen" que todo sea como lo deseamos y cliqueamos en "Lanzar Instancia".![Pasted image 20240826183928.png](../Crear%20Instancias/0789c5bd11a8b68f7e2d4652905513d01e87eabb.png "wikilink")
12. Esto tomara unos segundos pero al finalizar deberíamos poder ver un recuadro verde con un aviso de que se inicio correctamente.![Pasted image 20240826184049.png](../Crear%20Instancias/a50b054b96c14fbec78ffe899566d9071bc7d1f0.png "wikilink")
13. Podremos hacer una verificación adicional en el panel de instancias, cliqueando en "Ver todas las Instancias":![Pasted image 20240826184141.png](../Crear%20Instancias/d379cc5cc7ca52369a42b06c84fb722311769800.png "wikilink")
14. Como se puede observar, tenemos 4 instancias y la ultima es la que acabamos de crear, la cual esta en estado "Inicializando" esto puede tomar unos minutos ya que se esta configurando la Instancia.
15. Para las siguientes configuraciones del manual estaremos utilizando las otras tres instancias que en nuestro caso refieren al proyecto en Node.js el "Backend", el proyecto React el "Frontend" y a la Base de datos en postgres.
