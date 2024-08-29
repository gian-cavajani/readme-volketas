## Configuración Inicial

Como demostramos en esta [seccion anterior](04-Configurar-Putty.md 'wikilink') ya estamos dentro de nuestra instancia, a continuación demostraremos la configuración inicial que debemos hacer para que el servidor se pueda usar en producción:

1.  Una vez dentro de la instancia lo primero que debemos hacer es actualizar los paquetes del sistema para evitar vulnerabilidades y tener las ultimas mejoras:

<!-- -->

       sudo yum update -y

![Pasted image 20240827080341.png](../Configuracion%20inicial%20del%20servidor/ed98bfbc9e1680e8b68f121d0593eff365e8fa1d.png 'wikilink') 2. En nuestro caso no tenemos ningún update de paquetes pero nos salta un mensaje de que podemos actualizar la version de linux a una mas reciente.

       sudo dnf upgrade --releasever=2023.5.20240819

3.  Hacemos un reboot del servidor para estar seguros que se haya actualizado correctamente. Lo cual nos echara de la terminal.

<!-- -->

       sudo reboot

![Pasted image 20240827080756.png](../Configuracion%20inicial%20del%20servidor/ff49d38459774a81564a8d42df173aedd1f35c1b.png 'wikilink') 4. Volvemos a entrar y verificamos que no nos saltan los mensajes que hay versiones nuevas y al hacer : `cat /etc/os-release` podemos ver que tenemos la ultima version.
![Pasted image 20240827080936.png](../Configuracion%20inicial%20del%20servidor/0b205fa0b482fb2452125e977f147f3e8d3115b3.png 'wikilink')

4.  Luego de esto nos toca instalar algunos paquetes para poder trabajar en el servidor. En prinicipio instalaremos git, vim, nodejs y npm para hacer el seteo inicial de nuestro proyecto de nodejs. Dejamos que se instalen las dependencias, no deberia tardar mucho.

<!-- -->

       sudo yum install -y git vim nodejs npm

## Configurar git y github para clonar el repositorio.

Ahora debemos configurar git en el servidor y nuestro repositorio remoto en github para poder clonarlo.
\### Configurar el repositorio remoto.
Para empezar debemos tener un repositorio en github, para esto debemos seguir la siguiente serie de pasos.

1. Para configurar un nuevo repo en github debemos ir a la pantalla de inicio y clickear en "New"
2. ![Pasted image 20240827084245.png](../Configuracion%20inicial%20del%20servidor/892f112e452034dd89f74d54f50ad3d82f9b8df5.png 'wikilink')
3. Ahora debemos elegir la configuración inicial del repositorio
4. Repository name: el nombre que le queremos dar al repo
5. Description: es opcional pero le voy a poner algo informativo para recordar en un futuro de que se trataba.
6. Elijo "Private" para que solo yo y la gente a la que le doy permiso tenga acceso.
7. Es una buena practica agregar un README file, pero lo estaremos pusheando de local asi que no lo marco.
8. Sin .gitignore, en caso que sea un proyecto con variables de entorno, archivos pesados o directamente hay cosas que no nos interesa que esten en el repo remoto pero si en el local deberiamos agregar un .gitignore. En mi caso no lo necesito.
9. Y licencia ninguna ya que no es software que vaya a distribuir.
10. Le damos a "Create Repository"
    ![Pasted image 20240827084721.png](../Configuracion%20inicial%20del%20servidor/d1c67df749aa857fd8e1eb9fb6d7b39ab3e71876.png 'wikilink')
11. Ahora tenemos la opción de crear un repo nuevo o pushear un repo remoto, en mi caso voy a crear un repo desde mi local y luego hacer un push.![Pasted image 20240827084827.png](../Configuracion%20inicial%20del%20servidor/45a3b35e49d04267b71f30def7a125a24f92b0b4.png 'wikilink')
12. Mi repo solo tendra un archivo readme en formato markdown.
13. Siguiendo las instrucciones desde mi repo local en mi maquina hago lo siguiente para hacer un "push" al repo remoto:

    mkdir prueba-deploy-local
    echo "# Archivo readme de mi repo" > README.md
    git init
    git add README.md
    git commit -m "Primer commit en local"
    git branch -M main
    git remote add origin https://github.com/gian-cavajani/prueba-deploy.git
    git push -u origin main

![Pasted image 20240827085600.png](../Configuracion%20inicial%20del%20servidor/94f065503a9dea55aabb8333ce93120bb224a476.png 'wikilink') 5. Vale aclarar que me pide mi usuario y mi contrasena porque es un repo privado y porque hice push con https y no ssh, en caso de haber hecho con ssh me hubiera pedido la clave generada. 6. Ahora podemos ver el repo en github con el archivo readme creado: ![Pasted image 20240827085953.png](../Configuracion%20inicial%20del%20servidor/15875e911fb551d8e81fc9c489d2264b2d39eb25.png 'wikilink')

### Configurar Git en el servidor y clonar el repo

1.  Luego de instalar git y tener el repo remoto en github tenemos que configurar git para poder clonar. Primero seteamos nuestro usuario, yo voy a usar:

<!-- -->

       git config --global user.name "gian-cavajani"
       git config --global user.email "cavajanig@gmail.com"

2.  Ahora debemos generar un par de claves SSH en el servidor para autenticarnos con github. Yo voy a usar el algoritmo rsa y tendra un tamano de 4096 bits

<!-- -->

       ssh-keygen -t rsa -b 4096

3.  Ahora podemos ver las claves(tanto la publica como la privada) en un directorio oculto haciendo:

    -   Clave Publica:

    <!-- -->

          cat .ssh/id_rsa.pub

    -   Clave Privada:

    <!-- -->

        cat .ssh/id_rsa

    <figure>
    <img
    src="../Configuracion%20inicial%20del%20servidor/26cec01e31cd66be69550582153c87b8b483a84b.png"
    title="wikilink" alt="Pastedimage20240827082909.png" />
    <figcaption
    aria-hidden="true">Pastedimage20240827082909.png</figcaption>
    </figure>

4.  ahora debemos ir a github -\> Settings(SSH and GPG keys) -\> New SSH key.
    ![Pasted image 20240827083114.png](../Configuracion%20inicial%20del%20servidor/d9e1af349ca790a09aa9d49cc0f53f9518d5d884.png 'wikilink')
5.  Debemos elegir las siguientes opciones:
    1.  Como "Title" elegimos alguna referencia para poder identificarla.
    2.  "Key type": "Authentication Key"
    3.  "Key": aca pegamos la public key
    4.  Click en "Add SHH key"
        ![Pasted image 20240827083421.png](../Configuracion%20inicial%20del%20servidor/05e798434cbf90f21da3c4113ac6a51455e6a644.png 'wikilink')
6.  Ahora nos llevara a una pantalla donde nos pedirá nuestra contraseña:
    ![Pasted image 20240827083455.png](../Configuracion%20inicial%20del%20servidor/6e0ab93e149600cb7dd2d5450b142dc2e3c19ba9.png 'wikilink')
7.  Luego de esto deberíamos poder ver nuestra key en github.![Pasted image 20240827084001.png](../Configuracion%20inicial%20del%20servidor/0f5c49faa6e5a105bd8d8831af3e1feb81917ca0.png 'wikilink')
8.  Ahora en el servidor estamos listos para clonar el repositorio remoto que habíamos "pusheado" anteriormente. Tenemos que copiar la url para clonar con SSH:![Pasted image 20240827090229.png](../Configuracion%20inicial%20del%20servidor/b412723bab8c2d576bcffb5aa22906dba92eab6b.png 'wikilink')
9.  y posteriormente en el servidor ingresar:

<!-- -->

       git clone git@github.com:gian-cavajani/prueba-deploy.git

![Pasted image 20240827090705.png](../Configuracion%20inicial%20del%20servidor/669c0c88610ea5ce616a88e4cce82d1e70a499c9.png 'wikilink')
![Pasted image 20240827090832.png](../Configuracion%20inicial%20del%20servidor/807e0fc52c85a387486cf72c12d0f0a1619a45bd.png 'wikilink') 10. Ahora que sabemos como clonar y pushear haremos el deploy de la aplicación de node y react con nginx.
