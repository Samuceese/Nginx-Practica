# Como configurar tu servidor Nginx

## Estructura de archivos

1. **Carpeta conf**  
   - Creamos una carpeta conf, donde copiamos el archivo `nginx.conf` que es la configuración de nginx por defecto

   <img src="./imagenes/nginxConf" alt="archivos" style="padding-left:40px; padding-bottom:30px">

2. **Carpeta sites-available**  
   - Creamos una carpeta sites-available y creamos los archivos de configuración de nuestros dominios que usaremos en el futuro

   <img src="./imagenes/sites-available.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

   - Esto en un ejemplo de configuración que voy a utilizar para mi primer dominio usando samuel.conf
   <img src="./imagenes/samuelConfpng" alt="archivos" style="padding-left:40px; padding-bottom:30px">

2. **Carpeta website**
    - Creamos una carpeta website, que será el directorio que alojará los dominios para cada dominio
    <img src="./imagenes/website.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

    - Dentro de cada respectivo dominio crearemos nuestros respectivos html básico (index) y con sus respectivos errores que a su vez son html
    -Ejemplo del dominio samuel.com con su index.html y su error_404.html
    <img src="./imagenes/samuel.com.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    <img src="./imagenes/index.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    <img src="./imagenes/error.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

3. **Privado**
    - Para el dominio privado con SSL, crearemos una carpeta 'privado' donde alojaremos los anteriormente mencionados html y errores para dicho dominio
    <img src="./imagenes/privado.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

4. **Scripts**
    - Crearemos una carpeta scripts que a su vez tendrá dentro un fichero.sh (en mi caso entrypoint.sh) que se encargará de ejecutar los comandos para habilitar los sitios, activar el módulo SSL y reiniciar el servicio de Nginx. 
    <p>
    <img src="./imagenes/scripts.png" alt="archivos" style="padding-left:40px; padding-bottom:30px"></br>
    <img src="./imagenes/entrypoint.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

5. **Certificados y contraseñas**
    - Crearemos las carpetas de certificados(certs) y contraseñas(htppasswd) para posteriormente añadir los archivos de autentificacion, la clave pública y la privada
    <img src="./imagenes/directorios.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

6. **Docker-compose**
    - Crearemos un fichero llamado docker-compose.yml en el cual se establece la configuración necesaria para ejecutar nuestro contenedor Apache
    <img src="./imagenes/docker-compose.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    <img src="./imagenes/codDocker.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

7. **Generación de los certificados SSL**
    - Para la generación de los certificados previamente mencionados, deberemos tener instalado OpenSSL y ejecutaremos el siguiente comando
    `openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout seguro.key -out seguro.crt`
    (En mi caso es seguro)
    - Una vez hecho el comando deberás introducir una serie de atributos como pais,provincia,pais...
    - Si todo es correcto generará los certificados automáticamente (introducirlos en el directorio certs)
    <img src="./imagenes/certificados.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

8. **Host**
    - Modificaremos el fichero host ubicado en `C:\Windows\System32\drivers\etc\host` y añadiremos las IP de los dominios a usar
    <img src="./imagenes/host.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

9. **Despliegue del contenedor**
    - Para levantar el contenedor utilizaremos el comando: `docker-compose up -d`
    - Si no se ha generado bien siempre lo podemos tirar abajo con `docker-compose down`

10. **Generación del .htpsswd**
    - Ahora crearemos el fichero .htpasswd dentro del directorio htpsswd que hemos creado anteriormente
    - Abriremos nuestro navegador de confianza y pondremos la siguiente URL `https://bcrypt-generator.com/` que nos dirijirá a Bcrypt, una página donde nos encriptará nuestra contraseña
    - En el fichero creado pondremos nuestro usuario:lacontraseñaencriptada
    <img src="./imagenes/htpsswd.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">

**Ejemplo de los dominios**
    </br>
    <img src="./imagenes/ejsamuel.com.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    - Dominio `samuel.com`
    <img src="./imagenes/ejcortes.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    - Dominio `www.cortes.com`
    <img src="./imagenes/seguronet.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    - Dominio `seguro.net`
    <img src="./imagenes/pivadonet.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    - Dominio `seguro.net/privado`
    <img src="./imagenes/seguroprivada.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">
    <img src="./imagenes/error404.png" alt="archivos" style="padding-left:40px; padding-bottom:30px">










    















