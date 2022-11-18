# Documentación Examen 1ª Evaluación DAW
El motivo de esta memoria se adjuntaran todos los archivos realizados durante el examen de la primera evaluación de DAW.  
He realizado durante el examen un total de 3 archivos diferentes donde he ido documentando lo que he ido realizando durante cada uno de ellos.  
## Index
1. Ejercicio 2: SSH
2. Ejercicio 3: Command Line
3. Ejercicio 4: Virtualhost
## Ejercicio 2: SSH
`Enunciado:` Documenta todos los pasos realizados en un archivo MarkDown.  
Accede mediante ssh a la máquina que se muestra en la imagen.  
Deberás ir a /var/www y crear una carpeta que contenga como nombre tu nombre propio,  
crea un archivo llamador "ejercicio2.txt"
### Accedemos al servidor mediante SSH
Con el usuario que nos han idicado anteriormente, utilizaremos el siguiente comando añadiendo la IP del servidor
```
ssh usuario@192.168.0.168
```
![Acceso](https://github.com/odembiliov/Examen1triDAW/blob/main/accesossh.png)  
Una vez hemos accedido mediante ssh a la máquina , iremos a */var/www* y una vez dentro crearemos una carpeta con nuestro nombre
```
cd /var/www
mkdir olaya
```
y por último dentro de este crearemos un archivo con el nombre *ejercicio2.txt*
```
sudo nano ejercicio2.txt
```
### Resultado
En la siguiente imagen se muestra el resultado del ejercicio completo.  
Al final de este hemos tenido que poder haber creado dentro de una carpeta, en una máquina que no es la nuestra, un archivo txt.  
![Archivo](https://github.com/odembiliov/Examen1triDAW/blob/main/ejercicio2.png)
## Ejercicio 3: Command Line
`Enunciado:` Documenta todos los pasos realizados en un archivo MarkDown.  
En la máquina del ejercicio anterior, en la carpeta con tu nombre, descarga dentro de ella, mediante comandos,
la siguiente imagen:
https://iesalandalus.org/ciclos/semipresencial/daw-sp/daw.png  

Para empezar accederemos a la carpeta que hemos creado en el servidor en el ejercicio anterior
```
cd /var/www/olaya
```
A continuación utilizaremos el siguiente comando para descargar dentro de nuestra carpeta la imagen del link que nos
ha indicado
```
sudo wget https://iesalandalus.org/ciclos/semipresencial/daw-sp/daw.png  
```
### Resultado
En la siguiente imagen se muestra el resultado del ejercicio completo.  
Al final de este ejercicio, hemos tenido que acceder dentro de la carpeta que hemos creado en el ejercicio anterior,  
y una vez dentro de esta descargar la imagen a través de la url que nos indicaba el enunciado del ejercicio.  
![Descarga](https://github.com/odembiliov/Examen1triDAW/blob/main/descarga.png)  
## Ejercicio 4: Virtualhost
`Enunciado:` Documenta todos los pasos realizados en un archivo MarkDown.  
Crea en tu máquina un virtualhost donde escribiendo "daw.ejercicio4.com" nos envíe a una web local que simplemente 
contenga tu nombre.  
No cierres la máquina al acabar el examen para poder comprobar su funcionamiento.

## Creando nuestra propia web
Para empezar vamos a crear una carpeta para nuestra web dentro de _/var/www/_  
En este caso le hemos llamado _examen_ pero puedes llamar a la carpeta como quieras.
```
sudo mkdir /var/www/examen/
```
Ahora que tenemos el directorio creado para nuestra web, vamos a crear un HTML dentro de esta
```
cd /var/www/examen
sudo nano index.html
```

## Configuración del archivo de configuración de VirtualHost
A continuación, accederemos al directorio donde estan almacenados los archivos de configuración y haremos una copia 
del archivo *000-default.conf*
```
cd /etc/apache2/sites-available
sudo cp 000-default.conf examen.conf
```
A continuación editaremos el archivo
```
sudo nano examen.conf
```
Dentro de este fichero añadiremos las siguientes lineas de código
```
ServerAdmin yourname@ejercicio4.com
DocumentRoot /var/www/examen/
ServerName daw.ejercicio4.com
```
* **ServerAdmin**: Los usuarios de Apache te pueden buscar en el caso de que hubiera algun problema.
* **DocumentRoot**: Directiva para apuntar la ruta donde estan alojados los archivos de nuestra web.
* **ServerName**: Garantiza que las personas lleguen al sitio correcto en lugar del predeterminado.
Después de configurar nuestro sitio web, debemos activar el archivo de configuración de hosts virtuales para habilitarlo.
```
sudo a2ensite prueba.conf
```
`Dato:` En el caso de que no hayas activado la nueva configuración te pedira que la actualices -> _sudo systemctl reload apache2_
  
Para acabar, comprueba buscando en el navegador tu _**ServerName**_. 
### Fallos al hacer el ejercicio
En el caso que nos saliera un error cuando accedamos desde el ordenador, tendremos que seguir los siguientes pasos:
#### Modifica los host local con la dirección elegida 
Deberemos acceder a la carpeta que contiene el archivo hosts y modificarlo
```
cd /etc/
sudo nano hosts
```
Dentro del archivo hosts deberemos agregar nuestro dominio.
```
127.0.0.1 daw.ejercicio4.com
```
Ahora si navegamos a nuestro dominio podremos visualizar nuestra página.
### Resultado
En la siguiente imagen se muestra el resultado del ejercicio completo.
Al final de este ejercicio hemos tenido que poder acceder 
introduciendo en nuestro buscador del navegador *daw.ejercicio4.com* al html que hemos creado con nuestro nombre.  
![Funciona](https://github.com/odembiliov/Examen1triDAW/blob/main/funcionaej4.png)

## Bibliogrfia
https://github.com/odembiliov/UD1-GitHub-y-MarkDown/blob/main/Actividades/InstalacionApache.md  
https://github.com/odembiliov/UD1-GitHub-y-MarkDown/blob/main/Actividades/TareaSSH.md  
