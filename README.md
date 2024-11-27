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

 el cual al darle click abrira la aplicación de WildRydes desplegada, la cual se deve ver asi

![image](https://github.com/user-attachments/assets/e7df9671-d7d6-471c-9299-8f167aef4ce9)

Módulo 2: administrar usuarios
Pasos:
1) Crear un grupo de usuarios en Amazon Cognito, este grupo de usuarios sera utilizado por la aplicación para validar tokens de acceso y permitir o denegar el acceso a la aplicación WEB.
Deste este menú se da click en crear grupo de usuarios.

![image](https://github.com/user-attachments/assets/24358172-1acc-42b1-9ee5-d473a6cfdd96)
en en el menú de configuración de la aplicación agregue como nombre de aplicación: WildRydesWebApp y en tipo de aplicación se debe seleccionar aplicación web

![image](https://github.com/user-attachments/assets/2fc58201-f411-463f-b8c0-e952ab07d555)

En el menú de opciones para  identificación del inicio de sesión seleccionar usuario y correo electronico y finalmente crear

![image](https://github.com/user-attachments/assets/23516aba-d824-4329-8e97-c4f2f50695a8)

Se debe cambiar el nombre del grupo de usuarios a WildRydes.

Luego de estos cambios, los grupos de usuarios de Amazon cognito deberian verse como en la siguiente imagen:

![image](https://github.com/user-attachments/assets/0aea37c0-9bc5-49f5-ac57-5f9d5e735e3b)

Al darle click en el nombre se peude ver la información del grupo, aqui es importante copiar y guardad el ID del grupo, ya que este sera requerido mas adelante.

![image](https://github.com/user-attachments/assets/fadb02db-3c98-4b0f-8615-8a8d9504986c)

De igual forma al darle click sobre el nombre de la aplicación, se puede ver su configuración, se debe copiar y guardar el ID de la aplicación, ya que este sera requerido mas adelante.

![image](https://github.com/user-attachments/assets/56a5c84d-5b7e-4498-b844-4eef79747c46)

2) Actualizar el archivo de configuración del sitio WEB

Dentro de los archivos que se descargaron del repositorio github en el modulo 1, hay un archivo llamado config.js, el cual contiene la configuración de la pagina web y debe ser modificado, los campos que se deben modificar son userPoolId: y userPoolClientId:, el valor de userPoolId: corresponde al ID del grupo copiado en el paso anterior y userPoolClientId:corresponde al ID de la aplicación copiado en el paso anterior, de igual forma se debe verificar que la zona horaria sea la correcta, en caso contrario se debe cambiar.

![image](https://github.com/user-attachments/assets/fd47cf09-a7da-4764-b629-8bb94cb881a6)

Se guardan los cambios en el archivo y se actualiza en el repositorio de github, ejecutando los siguientes comandos:

git add .
git commit -m "new_config"
git push

Al actualizar el repositorio en github, la aplicación de AWS Amplify se debe actualizar de forma automática.

3) Validar la implementación.

Dentro de los archivos descargados en el modulo 1, hay uno llamado register.html, al abrir este archivo en algún navegador, se redireccionara a una pagina donde se puede crear una cuenta para acceder a la aplicación WildRydes, aqui se debe ingresar un correo y contraseña.

![image](https://github.com/user-attachments/assets/dc26e741-1f77-4b53-ab9f-c98201e42e05)

Una vez se halla ingresado los valores solicitados, se da click en el boton "lest ryde" y se debe recibir un codigo de confirmación en el correo ingresado.

dentro de lsoa rchivos descargados hay uno que se llama verify.html, al abrirlo en algún navegador, este nso redireccioanra a una pagina donde se puede verificar la cuenta creada ene l pasoa nteriro, utilizando el codigo de verificación que llega al correo.

![image](https://github.com/user-attachments/assets/58e165d0-f934-4c26-b506-59189b355a23)

Se peude verificar si los usuarios hallan sido correctamente creados/validados,desde el menú de cognito, dando clcik en el grupo de usuarios y en el menu de la izxquierda que dice adminsitrar usuarios, deben msotrarse las cuentas de usuario creadas.
![image](https://github.com/user-attachments/assets/c023d520-ddfa-47d8-9794-b948ec43f609)

Módulo 3: backend de servicio sin servidor

Pasos:

1) Crear una función lambda para adminsitrar solicitudes realziadas en la aplicación WEB.

Desde el menú de lambda se da click en el boton "crear neuva función"

![image](https://github.com/user-attachments/assets/fe4e4696-0d0e-4026-8ddd-100a95a4b1a1)

Se mantiene la opción de "crear desde cero", se ingresa el nombre de la función como "RequestUnicorn" y en la configuración de los roles, se indica que se va a usar un rol ya existente, se selecciona el rol LabRole de la lista desplegable y finalmente se da click en crear función.

![image](https://github.com/user-attachments/assets/8813ecdd-e2df-4982-81d3-0d83089e8d48)

![image](https://github.com/user-attachments/assets/43dd2373-6212-4748-9f93-5eabba7f21c2)

El resultado debería verse como en la siguiente imagen:

![image](https://github.com/user-attachments/assets/77e05521-490a-4194-9fc4-c3d70e8c1012)


Al darle click a la función creada se puede ver su configuración, en la parte de abajo esta su codigo fuente, el cual debe ser modificado, remplazandolo con el script que esta en el archivo Lambda-code.txt de este repositorio, finalmente se da click en el boton deploy para poder desplegar la función y aplicar el cambio.

![image](https://github.com/user-attachments/assets/7616216a-75e0-467f-83da-5a3ad5545f0b)

![image](https://github.com/user-attachments/assets/d7a3e6cc-45f0-4550-bbf0-e05e970d42bd)

2) Vlidar la implementación de la función Lambda.

En el menú de Lambda para al configuración del codigo fuente en la aprte de abjo que dice "test events", se da click en el mas para generar un nuevo evento, esto abrira un menú para ingresar el codigo del evento a probar, el codigo que se debe ingresar esta en el archivo test-event.txt adjunto en el repositorio.

![image](https://github.com/user-attachments/assets/2c8a6e6b-4636-4987-8cc6-53c30ab61a76)


