# Ejercicio 2 -> SSH
`Enunciado:` Documenta todos los pasos realizados en un archivo MarkDown.  
Accede mediante ssh a la máquina que se muestra en la imagen.  
Deberás ir a /var/www y crear una carpeta que contenga como nombre tu nombre propio,  
crea un archivo llamador "ejercicio2.txt"
## Accedemos al servidor mediante SSH
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
