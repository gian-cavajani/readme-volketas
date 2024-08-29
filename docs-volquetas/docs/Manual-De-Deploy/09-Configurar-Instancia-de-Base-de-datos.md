En principio habíamos configurado la base de datos en una instancia EC2 pero decidimos cambiarla a RDS.

1.  Vamos a la consola de AWS y buscamos RDS en el buscador:
    ![Pasted image 20240827132530.png](../Configurar%20Instancia%20de%20Base%20de%20datos/6d0cde66183f6f01a1b10497c9f53470a37b75e0.png "wikilink")
2.  Nos lleva a la pestaña de Amazon RDS, aquí clickeamos en "Crear Base de datos"
    ![Pasted image 20240827132717.png](../Configurar%20Instancia%20de%20Base%20de%20datos/117c0a5ccf62dfacda0b07ba5b38e9481a1060f5.png "wikilink")
3.  Aquí tenemos varias opciones para crear la nueva instancia RDS:
    1.  Elegimos "Creación Estándar"
    2.  Motor PostgreSQL.
        ![Pasted image 20240827132944.png](../Configurar%20Instancia%20de%20Base%20de%20datos/f9f2484e6dfe843e20a4b3ae259254e7437483f0.png "wikilink")
    3.  Elegimos la ultima version disponible en mi caso la 16.4-R1
    4.  Y la Capa gratuita de Plantilla
        ![Pasted image 20240827134933.png](../Configurar%20Instancia%20de%20Base%20de%20datos/31085672a94384f7d8df1985eb2d1ac51e9c21a5.png "wikilink")
    5.  La pestaña de "Disponibilidad y durabilidad" no esta disponible para la capa gratuita.
        ![Pasted image 20240827135730.png](../Configurar%20Instancia%20de%20Base%20de%20datos/0ea9a7616d3f08cfabb91456e1f80f2d9d4dc174.png "wikilink")
    6.  En "Configuración"
        1.  Elegimos un identificador en mi caso le pongo "volquetas"
        2.  nombre de usuario maestro dejamos postgres ya que lo tenemos configurado de esa manera en local y en la instancia de EC2
        3.  Elegimos la administración de credenciales "Auto-administrado" ya que queremos elegir nuestra propia contrasena.
        4.  Elegimos una contraseña que usaremos para conectarnos a la instancia.
            ![Pasted image 20240827140138.png](../Configurar%20Instancia%20de%20Base%20de%20datos/52f71722a94b8cfa7426269ccff38dd5ea00c8be.png "wikilink")
    7.  El siguiente apartado tiene para elegir el tipo de instancia similar a como hicimos en EC2. para la capa gratuita solo tenemos dos opciones, elegimos la mas potente.
        ![Pasted image 20240827140458.png](../Configurar%20Instancia%20de%20Base%20de%20datos/3ace157b40c0a51fbda9410f6259c1944816d942.png "wikilink")
    8.  En "Almacenamiento" elegimos SSD de uso general, 20GB de almacenamiento y auto escalado por si nos pasamos de los 20GB, por defecto el Umbral son 1000GB lo dejamos de esta manera de todas formas no vamos a llegar a tal cifra.
        ![Pasted image 20240827140641.png](../Configurar%20Instancia%20de%20Base%20de%20datos/2ff430a96e1178f5560971d6acc647bdedd242f3.png "wikilink")
    9.  En "Conectividad"
        1.  Elegimos conectarse a un recurso informático de EC2, para que la instancia de Node se conecte directamente.
        2.  Tambien elegimos la instancia con la que nos estaremos conectando a la Base de datos
            ![Pasted image 20240827141141.png](../Configurar%20Instancia%20de%20Base%20de%20datos/2b7bd3574078bc845ec8b5024b3915737b944e8c.png "wikilink")
        3.  En "Grupos de subredes" seleccionamos "configuración automática"
        4.  En "Grupos de seguridad" seleccionamos "Crear nuevo" y le ponemos un nombre, en mi caso le puse "acces0-psql-rds"
            ![Pasted image 20240827141652.png](../Configurar%20Instancia%20de%20Base%20de%20datos/1815e8442ec0f8f9b1059f21f5664d4a94d82fea.png "wikilink")
        5.  Para entidad de certificación elegimos la que tenga mas años
        6.  Por ultimo Puerto de la Base de datos elegimos 5432 que es el default para postgres
            ![Pasted image 20240827141904.png](../Configurar%20Instancia%20de%20Base%20de%20datos/07139e1b8d59f60efc528e9a6663828fd92ff358.png "wikilink")
    10. En etiquetas no agregamos nada ya que no son necesarias, con el nombre de la instancia es suficiente para identificarla.
    11. En "Autenticación de bases de datos" elegimos Autenticación con contraseña.
    12. En "Supervisión" no elegimos ningún campo, esto es para el monitoreo.
        ![Pasted image 20240827142220.png](../Configurar%20Instancia%20de%20Base%20de%20datos/734ad850b2492610f08428df36288e5e51889f17.png "wikilink")
    13. En "Configuración adicional" elegimos lo siguiente:
        1.  Nombre de la base de datos: "volquetas"
        2.  Grupos de parametros: default.postgres16
        3.  Copias de seguridad por un dia por si pasa algo y queremos hacer rollback.
            ![Pasted image 20240827142605.png](../Configurar%20Instancia%20de%20Base%20de%20datos/2cb449270cbb331e75b29e211713407ab637115e.png "wikilink")
        4.  Replicacion de copias de seguridad, no la seleccionamos, esto seria en caso de tener Alta disponibilidad para crear una replica en otra zona.
        5.  Habilitamos el Cifrado.
        6.  Y lo siguiente lo dejamos todo por defecto
            ![Pasted image 20240827142746.png](../Configurar%20Instancia%20de%20Base%20de%20datos/033e3cda3c357e9767583a7359ff74b11366ffdb.png "wikilink")
    14. Por ultimo damos click a "Crear base de datos"
        ![Pasted image 20240827142857.png](../Configurar%20Instancia%20de%20Base%20de%20datos/0e417f929943c132178842c5b207c02d9a5a8c43.png "wikilink")
    15. La creación de la instancia de base de datos puede demorar un rato, luego de que este finalizado ajustaremos los security groups.
        ![Pasted image 20240827152519.png](../Configurar%20Instancia%20de%20Base%20de%20datos/5fc1aa43465d31ce1e118e9ea9de5af209db0ec6.png "wikilink")

### Grupos de seguridad:

Ahora chequearemos el security group creado tanto para la base de datos como para la conexión a la misma desde la instancia de node y copiaremos la url para utilizarla en las variables de entorno de node:
1. El siguiente Grupo de seguridad "ec2-rds-1" muestra que tiene una regla de salida para permitir la conexion hacia la instancia RDS. este grupo esta siendo utilizado por la instancia de node:  
![Pasted image 20240827160433.png](../Configurar%20Instancia%20de%20Base%20de%20datos/640c131a05c153b147063a3b57fe0657a44b4509.png "wikilink")![Pasted image 20240827161013.png](../Configurar%20Instancia%20de%20Base%20de%20datos/b7052fb8758122a56f78281d0e45537e5536743f.png "wikilink")
2. Por otro lado podemos ver que la instancia de RDS tiene estos grupo de seguridad:
1. El primero es para permitir el transito entrante desde cualquier instancia que este vinculada a la VPC
2. El segundo es para permitir el trafico saliente.
![Pasted image 20240827161149.png](../Configurar%20Instancia%20de%20Base%20de%20datos/8a67c71db6b68a5bb2ed97405aa34d071b787b39.png "wikilink")
3. Como ultimo paso copiaremos el endpoint para usarlo en las variables de entorno en la instancia de node que serán usadas para configurar el string de conexión a la base de datos.  
![Pasted image 20240827160325.png](../Configurar%20Instancia%20de%20Base%20de%20datos/531d41707e23a85e9801770cdb99202e853efa73.png "wikilink")
