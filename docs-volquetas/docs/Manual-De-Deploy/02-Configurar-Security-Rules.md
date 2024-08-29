Pasaremos a demostrar como crear Security Rules para las distintas instancias.

## Crear nuevo Grupo de Seguridad

En el panel de instancia podemos ver los detalles de los grupos de seguridad configurados para esa instancia. Esta instancia ya tiene un Grupo de seguridad configurado con muchas reglas de entrada/salida, a continuación demostraremos como asignar estas reglas y su razon.![Pasted image 20240826195809.png](../Configurar%20Security%20Rules/34ee618e61bbec420739a50e1ad70c31bc75b875.png 'wikilink')

1.  En la imagen de arriba se puede observar un panel a la izquierda donde dice "Red y seguridad" y debajo "Security Groups" allí es donde deberemos clickear para configurar las reglas de entrada. Tambien debemos recordar la IPV4 publica ya que la estaremos usando para validar los cambios. Para la demostración de funcionamiento de este manual, luego de tomar la captura desvincule el grupo de seguridad de la IP.
    En este caso: 18.208.241.74 es una IP elástica por lo que estamos seguros al guardar y utilizar esta IP ya que no va a cambiar. Después de configurar los security groups [Configuraremos las IP elasticas](03-Configurar-IPs-Elasticas.md).
    -   la URL http://18.208.241.74/api llama a un método GET que tiene devuelve una respuesta con un mensaje que viene del servidor donde nos dice en que puerto corre el entorno de desarrollo. Como se ve en la imagen de abajo esta url no es alcanzable. Esto es porque desactivamos el bypass del firewall para el puerto 80(HTTP) y el 443(HTTPS) en las reglas de entrada. A continuación demostraremos como crear un nuevo grupo para activar la conectividad.
        ![Pasted image 20240826201550.png](../Configurar%20Security%20Rules/e7d75ccb3db6a4d4836123ad693129f6747e8d33.png 'wikilink')
2.  Una vez en el panel de "Grupos De Seguridad" clickeamos en "Crear grupo de seguridad". Ignorar los grupos ya creados.![Pasted image 20240826200901.png](../Configurar%20Security%20Rules/9d501a8c6bce5e3010ade197e306ba44b4d6494f.png 'wikilink')
3.  Aqui tenemos varias opciones. La primera son los "Detalles basicos". ![Pasted image 20240826202722.png](../Configurar%20Security%20Rules/9200c180295dea339070e70f83d981fa11e2a198.png 'wikilink')
    -   Elegimos un nombre descriptivo que podamos referenciar luego, y una descripcion (opcional), en la VPC elegimos la predeterminada.
4.  Ahora tenemos que agregar las "Reglas de entrada", para agregar una nueva cliqueamos en "Agregar Regla".
5.  Como primera regla quiero permitir el trafico entrante por el puerto 80 el cual es el predeterminado para el protocolo HTTP.
6.  Ademas elegimos los IP permitidos para llegar al puerto HTTP, en nuestro caso permitimos todos los IP. Podemos observar que debajo de todo nos aparece un aviso de que todos los IP pueden acceder y que no es recomendado. Pero a nosotros no nos interesa ya que tenemos otro tipo de validaciones de seguridad en nuestra aplicacion.
7.  Por ultimo agregamos una descripcion (opcional) que sirve de referencia.![Pasted image 20240826203227.png](../Configurar%20Security%20Rules/6658c325152f8f123bf5b01f0f3588d0aa843e89.png 'wikilink')
8.  Siguiente a esto voy a agregar todos los puertos de entrada necesarios para mi instancia Backend.![Pasted image 20240826203616.png](../Configurar%20Security%20Rules/f3e604a085de0b38d4984d1ebff489477db2b5d0.png 'wikilink')
9.  Ahora para las reglas de salida configuraremos a donde el servidor puede llegar. Las opciones son las mismas. Asi que pasare a agregar el puerto 5432 que es el puerto de la base de datos postgresql. Ya hay una regla predefinida como PostreSQL pero si pusieramos TCP 5432 seria lo mismo(a modo informativo lo muestro en la imagen pero luego lo voy a borrar y solo voy a dejar uno).![Pasted image 20240826203902.png](../Configurar%20Security%20Rules/389c331fecedb61113a65b8ddb3a6a5489b1e446.png 'wikilink')
10. Por ultimo agregariamos Etiquetas es opcional pero lo voy a hacer porque son utiles para referenciar.![Pasted image 20240826204117.png](../Configurar%20Security%20Rules/42ef95092a6d15556bbfd21c15f2cd5254f030c8.png 'wikilink')
11. Cliqueamos en "Crear grupo de seguridad" y nos deberia mostrar una pantalla como la siguiente:![Pasted image 20240826204211.png](../Configurar%20Security%20Rules/72c057e03d08ce0cb08ae20238ee0ea6e4913030.png 'wikilink')

### Vincular grupo de seguridad a la instancia

1.  Para vincular el grupo de seguridad con nuestra instancia backend nos dirigimos a la pestana de "Instancias"
2.  Seleccionamos la instancia con click derecho y paso seguido cliqueamos "Seguridad"-\> "Cambiar Grupos de seguridad"![Pasted image 20240826204749.png](../Configurar%20Security%20Rules/5d8670fcbc0d5a20190f59c16d9683ee315a98bb.png 'wikilink')
3.  Al cargar esta pestana podemos ver que no tenemos grupos asociados.
    ![Pasted image 20240826205018.png](../Configurar%20Security%20Rules/7bb332ed51728df1e59e5064cefc32612c2b2ce9.png 'wikilink')
4.  Para cambiar esto vamos al buscador y seleccionamos el grupo de seguridad recien creado (Manual-Deploy) y "Agregar grupo de seguridad".
    ![Pasted image 20240826205106.png](../Configurar%20Security%20Rules/9be88e13f93cf80c0bec8162f1a598420457c06e.png 'wikilink')
5.  Por ultimo clickeamos en "Guardar"
6.  Para validar los cambios vamos a la pestana de instancias nuevamente y chequeamos las reglas de entrada/salida. Como se puede observar las reglas se guardaron correctamente y quedaron asociadas a la instancia: ![Pasted image 20240826205345.png](../Configurar%20Security%20Rules/fea38e4e9cce7f4839b0e6219e3c0c8881699eda.png 'wikilink')
7.  Ahora debemos validar que el puerto 80/443 sean alcanzables para ello volvemos a http://18.208.241.74/api y https://api.volquetas/api ambos puertos estan funcionando correctamente:
    ![Pasted image 20240826205528.png](../Configurar%20Security%20Rules/e33523479d4563393d11bc4ed3eb73f398250fa5.png 'wikilink')
    ![Pasted image 20240826205555.png](../Configurar%20Security%20Rules/942717cc6681e7f5ca9f83323dc9711711441e6e.png 'wikilink')
