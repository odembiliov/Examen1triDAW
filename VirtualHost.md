# Ejercicio 4 -> VirtualHost
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
En el caso que nos saliera un error cuando accedamos desde el ordenador, tendremos que seguir los siguientes pasos:
## Modifica los host local con la dirección elegida 
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
![Funciona](https://github.com/odembiliov/Examen1triDAW/blob/main/funcionaej4.png)
