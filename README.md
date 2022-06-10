# ExamenSistemas | Adrià Juan de León

![image](https://user-images.githubusercontent.com/98842240/173083398-6debe84f-629a-4931-98bc-fe580a837c9c.png)

___
- Introducción.
___
- ¿Que es Docker?

Docker es un proyecto de código abierto que automatiza el despliegue de aplicaciones dentro de contenedores de software, proporcionando una capa adicional de abstracción y automatización de virtualización de aplicaciones en múltiples sistemas operativos.

- ¿Que es Docker-Compose?

Docker Compose es una herramienta para definir y ejecutar aplicaciones de Docker de varios contenedores. En Compose, se usa un archivo YAML para configurar los servicios de la aplicación. Después, con un solo comando, se crean y se inician todos los servicios de la configuración.

- ¿Que es DockerFile?

Un DockerFile es un documento de texto que contiene todos los comandos que queramos ejecutar en la linea de comandos para armar una imágen. Esta imágen se creará mediante el comando docker build que irá siguiendo las instrucciones.

___
- Primer Paso.
___

El primer paso a realizar es bajarnos el **.war**, en este caso hemos descargado el proyecto del profesor Máximo ya que el nuestro daba errores.

- NOTA: Para ello hemos ido al repositorio del profesor y nos hemos descagado su **.war**.

___
- Segundo paso.
___

El segundo paso es la creación de la carpeta y archivos de **Dcokerfile** y **docker-compose.yml**.

A continuación hemos creado una carpeta con el nombre del proyecto, en este caso la carpeta se llama: **DockerCompose**.

![image](https://user-images.githubusercontent.com/98842240/173104783-00bc7b9a-18c0-48af-b92d-3bf71df3f53e.png)

Dentro de esta carpeta hemos metido la siguiente estructura de archivos:

![image](https://user-images.githubusercontent.com/98842240/173105023-840891a7-fe47-4e54-8109-d75c88824c75.png)

Cuando tengamos todo listo, debemos crear un archivo llamado **Dockerfile** (esto debe estar creado dentro VisualEstudio ya que me deja abrir la carpeta entera).

![image](https://user-images.githubusercontent.com/98842240/173105331-fa6e4774-d8af-4b18-9eb9-b2fa7d7c0b8d.png)

Después de haber creado el **Dockerfile**, debemos añadir la siguiente información dentro del archivo:

![image](https://user-images.githubusercontent.com/98842240/173105765-8857713f-45b5-4b40-a25f-b9c647b55d26.png)

- ANOTACIÓN: En la imagen anterior, la línea dónde pone **COPY** significa que copiará el archivo llamado **LoginWebApp**, este archivo lo tenemos alojado en la carpeta **"target"**, cuando acabe esto, lo copiará en la siguiente ubicación: */usr/local/tomcat/webapps/*.

___
- Creación del archivo **docker-compose.yml**.
___
Ahora vamos a ver como crear el archivo *docker-compose.yml*.

Dentro de este podemos ver la información de cada contenedor que tenemos, ya sea *mysql*, *phpMyAdmin* o *tomcat*.

Este archivo tiene que ser creado igual que el **Dockerfile**, pero en este caso poner de nombre *docker-compose.yml* dentrp del **.yml** hemos añadido lo siguiente:

![image](https://user-images.githubusercontent.com/98842240/173107097-74c41404-4601-4bc7-bfd3-c490ed68901e.png)

Dentro de este archivo hemos añadido las versiones de los archivos, hemos indicado los puertos por donde ataca el archivo y donde queremos que se efectúe el contenedor *(ataca = efectúa su inicialización)*. En mi caso, el puerto de la base de datos es el puerto = `3306` que es el puerto por defecto de *MySQL*. Para *phpMyAdmin* he añadido el puerto = `8081` y para la *web* he añadido el puerto = `8082`.

- NOTA: Para poder desplegar nuestro proyecto en el navegador debemos ejecutar en el buscador de **Google** lo siguiente:

`localhost:*puerto*`

EJEMPLO: 
`localhost:8081 (para visualizar el pphpMyAdmin)`

Una vez logrado poner los puertos debemos crear una carpeta llamada *mysql-dump* y la carpeta *target*. Con estas dos carpetas debemos subir los tres contenedores al mismo tiempo, el comando para ello es:

`docker-compose up -d`

Una vez ejecutado el comando se crearán las imagenes vacías menos la de la carpeta **target**, esta crea una carpeta llamada *LoginWebApp.war* pero nosotros solo necesitamos el archivo **.war**.

Dentro de la carpeta *mysql-dump* tenemos que tener el archivo `USER.sql` que lo tenemos descargado despues de bajarnos todo el repositorio del profesor.

El archivo `USER.sql` debe contener lo siguiente:

![image](https://user-images.githubusercontent.com/98842240/173109243-88fbed0d-b92f-4e7c-8ca7-089bdd479175.png)

A continuación, dentro de la carpeta *target* tenemos que tener el archivo `LoginWebApp.war` junto a la carpeta `LoginWebApp` donde tendremos todo el codigo.

- NOTA: he creado un back up del archivo *.war* llamado `LoginWebApp.war.bck`.

___
- Creación de la imagen de *dockerfile*
___

Para crear la imagen debemos ir al archivo **dockerfile** creado con anterioridad y debemos darle click derecho al código y darle a `build image` como en la captura siguiente:

![image](https://user-images.githubusercontent.com/98842240/173109910-5b9c728c-2f87-4daf-99fb-0a7dbc19b55f.png)

Una vez le demos se nos ejecutará esta ventana:

![image](https://user-images.githubusercontent.com/98842240/173110106-36dec83b-52db-472c-bbb3-b7d054db0ea5.png)

Debemos escribir el nombre de la imagen en minuscula y darle a *enter*.

![image](https://user-images.githubusercontent.com/98842240/173110277-f6f0e01c-139a-4ab0-88ed-2de369d9e82c.png)

Una vez le hayamos dado a enter solo tenemos que esperar a que se complete la imagen con el nombre que hemos proporcionado.

___
- Explicación de como hacer un **Compose Up**.
___

Una vez tengamos el trabajo realizado lo debemos subir los archivos a **docker hub**, para ello vamos a utilizar la herramienta *compose up*

- NOTA: ¿Que es en Docker el comando `Compose Up`? 
- *Es una herramienta para definir y ejecutar aplicaciones Docker multicontenedor que permite simplificar el uso de Docker a partir de archivos YAML, de está forma es mas sencillo crear contendores que se relacionen entre sí, conectarlos, habilitar puertos, volumenes, etc.*


Para ejecutar el Compose Up debemos ir al archivo `.yml` y hacer click derecho y clickar donde pone **Compose up**, como en la siguiente imagen:

![image](https://user-images.githubusercontent.com/98842240/173111037-83758449-31b6-437b-925d-4b34b961f1fa.png)

Una vez le demos tenemos que esperar a que se completen las tres cargas ya que tenemos las tres cargas.

![image](https://user-images.githubusercontent.com/98842240/173111361-3d9dc74e-64eb-46fe-ba0d-1c46b1d8d1dc.png)

Como podemos ver, se ha cargado con exito los tres contenedores. Una vez cargado con exito debemos ir a Docker y visualizar que los contenedores han arrancado con exito, en mi caso ha sido asi:

![image](https://user-images.githubusercontent.com/98842240/173111535-eaf50273-9b9a-46ce-8552-0974caa94da0.png)

Podemos ver que se ha iniciado correctamente.

___
- Verificación del despliegue.
___

Lo primero que haremos será ir al navegador y escribiremos `localhost:8081`, con esto visualizaremos el phpMyAdmin. Para poder iniciar sesion debemos ingresar el usuario: *testuser* y la contraseña: *root*.

![image](https://user-images.githubusercontent.com/98842240/173111984-bf018723-2e24-48ca-af33-a21f1860c3ee.png)

Como podemos ver ingresando usuario y contraseña conseguiremos entrar dentro:

![image](https://user-images.githubusercontent.com/98842240/173112084-d053bdaf-54f8-4d68-9842-cc731af8d8af.png)

- NOTA: **Una vez dentro iremos a *testdb1*, luego "USER", "Columnas" y "Nueva". Aquí crearemos una nueva columna llamada "regdit" con un valor/longitud "20".**

Ahora debemos confirmar que podemos loggearnos de forma correcta para ello vamos a la siguiente URL `localhost:8082/LoginWebApp`

- **Login**
![image](https://user-images.githubusercontent.com/98842240/173112424-286d99e2-2d96-4bfd-8f18-56e92a075ea0.png)

- **Register**
![image](https://user-images.githubusercontent.com/98842240/173112508-c3f5a5a9-37f8-483f-92ca-74250c5e70de.png)

Ahora debemos registrarnos con un usuario que hayamos creado, en mi caso he creado uno con mi nombre:

![image](https://user-images.githubusercontent.com/98842240/173112621-099d8793-3df2-428f-9cb8-b20306dc720f.png)

Una vez creado nos logeamos y debe aparecer lo siguiente:

![image](https://user-images.githubusercontent.com/98842240/173112718-ae38beaa-3e24-47b3-ad2b-c6f457f12d6d.png)

Para comprobar definitivamente si la cuenta se ha creado bien y se ha guardado en la base de datos vamos a ir al "localhost:8081" y veremos i está la cuenta creada. Como podemos ver está creada.
![image](https://user-images.githubusercontent.com/98842240/173112822-52966144-59ca-44c7-82e0-e509ce49ba59.png)

En caso de querer parar haremos el mismo proceso que para hacer el `Compose Up`, pero le daremos a `Compose Down` y se paran todos los contenedores.

___
- Push a **Docker Hub**
___

Lo primero debemos ir a Docker Hub y logearnos con nuestro usuario.

Para hacer un push desde VisualStudio lo que haremos será ir a la extensión "Docker" e inicias sesión con tu cuenta de docker hub en la parte de "Registries", pones tu usernameID y luego tu constraseña y ya.
![image](https://user-images.githubusercontent.com/98842240/173113156-b76bd183-4b69-4ced-8d98-8092240005b6.png)

Ahora debemos hacer el `push` a los tres archivos por separado.

- NOTA: por separado porque al subirlo todo de una da error y solo se sube uno.

Para poder ver mis repositorios en docker hub puedes acceder mediante estos enlaces:

Como podemos observar se ha subido todo completamente a Docker Hub

![image](https://user-images.githubusercontent.com/98842240/173114291-ae0f5408-c7b8-4aae-8dc9-3c7cfa8014c7.png)

___
- Conclusión
___
 El trabajo ha sido dificil de realizar ya que quedaban algunas cosas por repasar del código, ayer mi grupo y yo estuvimos hasta las 4am para poder solucionarlo todo y lo conseguimos, asi que estoy contento con el trabajo realizado y con el resultado. 
 
 Buena suerte para tu futuro Máximo, espero que aprendas mucho y sigas adelante!

___
- tomcat: https://hub.docker.com/r/adriadeleon/tomcat
___
- mysql: https://hub.docker.com/r/adriadeleon/mysql
___
- phpmyadmin: https://hub.docker.com/r/adriadeleon/phpmyadmin
___

Adrià Juan de León





