En este documento se documentaran los pasos para crear una aplicacion AWS serverless, el procedimeinto esta separado en 5 modulos.

Módulo 1: alojamiento web estático con implementación:
Pasos:
1) Crear un repositorio en github al cual se va a subir el proyecto
2) crear un directorio donde se va a montar los archivos de la aplicación web
3) clonar los archivos de la aplicacion web Wildrides desde un repositorio de git, ingresando a la linea de comandos de git (git bash) desde el directorio previamente creado y ejecutando el sigueinte comando: git clone https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
Los archivos clonados en el directorio deben verse como en la siguiente imagen:
![image](https://github.com/user-attachments/assets/109acc75-39e2-4e8d-8ece-374f3d9d704c)
Dentro de estos archivos hay varios codigos en HTML que seran desplegados en aws para la creación dels ervicio web.
4) Subir el contenido del directorio al repositorio de github creado en el paso 1, usando los comandos:
git remote add origin https://github.com/usuario/nombre-del-repositorio.git
git add .
git commit -m "new files"
git push
5) Habilitar el alojamiento WEb en la consola de AWS Amplify
En la consola de AWS Amplify se da click en la opcion crear nueva aplicación:
![image](https://github.com/user-attachments/assets/e65b740e-572f-4475-a608-09ed114fe874)
Luego se selecciona el tipo de repositorio, ene ste caso github
![image](https://github.com/user-attachments/assets/451b13db-c903-4a9c-8889-1659443f4ca6)
Se abrira una ventana emergente, donde se pedira ingresar las credenciales de github para vincular el repositorio con AWS Amplify.
![image](https://github.com/user-attachments/assets/214f3790-e7fb-40c7-bf8b-367b5f22fdad)
Una vez la cuenta de github ha sido comprobada, se debe seleccionar el repositorio que se quiere vincular,desde la lista desplegable.
![image](https://github.com/user-attachments/assets/927b9d25-626a-46cb-94cb-932bc4a78ef1)
Luego se da clik en siguiente hasta finalizar la configuración y se valida que la aplicación aparezca en el menú de AWS Amplify, cada vez que se detecte un commit en uno o mas archivos del repositorio en github vinculado, este sera actualizado de forma automática en AWS Amplify.
Para probar que todo este configurado de manera correcta, se debe dar click en la aplicación montada en AWS Amplify, esto abrira un menú con los detalles de la aplicación donde se ´peude encontrar un link bajo el titulo "dominio"
![image](https://github.com/user-attachments/assets/35ab48c2-46c3-4643-a89c-c19159fe596c)

 el cual al darle click abrira la aplicación desplegada, la cual se deve ver asi

![image](https://github.com/user-attachments/assets/e7df9671-d7d6-471c-9299-8f167aef4ce9)


