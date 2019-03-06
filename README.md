# Config-Xampp-con-puertos-diferentes

### Pasos que se deben de seguir para configurar XAMPP con puertos distintos a los establecidos y con contraseña root diferente a la establecida. Ayuda también cuando los puertos esta ocupados.

#### _Requisitos:_
* Tener instalado XAMPP

####_Pasos:_
1.- Iniciar XAMPP
![alt text](Images\Inicio_xampp.png)
***

2.- Damos click en el botón _Config_ del **Apache**. Abrimos el archivo "Apache (httpd.conf)"
![alt text](Images\Config1.png)
***

3.-	Buscamos las lineas **ServerName localhost:_puerto_** y **Listen:_puerto_** en el archivo. En **_puerto_** ponemos el que nosotros queremos.(En este caso es 8282)
![alt text](Images\Config2.png)
![alt text](Images\Config3.png)
***

4.- Toca mysql, damos click en el botón _Config_ de **Mysql**. Abrimos el archivo "my.ini"
![alt text](Images\Config4.png)
***

5.- Buscamos las lineas **Port  = _puerto_** que aparece en dos líneas del archivo. En **_puerto_** ponemos el que nosotros queremos. (En este caso es 8383).![alt text](Images\Config5.png)
***

6.- Buscamos el archivo **Config.inc.php** que se encuentra en la dirección _C:\xampp\phpMyAdmin_ y cambiamos la linea **127.0.0.1** a **127.0.0.1:8383**. En mi caso es 8383 el puerto, se debe de poner el puerto con el cual haya configurado mysql.
![alt text](Images\Config.inic.png)

***
7.- Iniciamos **Apache** y **Mysql** y aparecerán en verde.
![alt text](Images\Xampp.png)

***
8.- En un navegador ponemos **localhost:8282**, aparecerá lo siguiente. El 8282 es el caso que se configuró aquí pero se deberá poner el puerto que configuraron en el paso 3.
![alt text](Images\localhost.png)

***
9.-Tambien podremos abrir phpmyadmin, damos click en el y aparecerá lo siguiente.
![alt text](Images\phpmyadmin1.png)
![alt text](Images\phpmyadmin2.png)

***
10.- Volvemos al panel de Xampp y damos click en **Shell**.
![alt text](Images\Shell.jpg)
Se verá lo siguiente.
![alt text](Images\Shell2.png)

***
11.- Ingresamos **mysql -u root -p** (ENTER), nos pedirá contraseña, le damos enter nadamas y se verá lo siguiente.
![alt text](Images\root1.png)

***
12.- Estando ahí ingresamos lo siguiuente.
**mysql> use mysql;
mysql> update user set password=PASSWORD(“root”) where User=’root’;
mysql> flush privileges;
mysql> quit.**

Donde password=PASSWORD(“root”) en la parte root es la nueva contraseña.

Volvemos abrir el archivo que mencionamos en el punto 6 y en donde dice password ponemos la nueva contraseña que asignamos al root.
![alt text](Images\pass.png)
***
13.- Nos salimons con **exit;** y volvemos a introducir **mysql -u root -p** con la nueva contraseña cuando se pida.
![alt text](Images\root2.png)

***
14.- Creamos una base de datos **CREATE database folios;** y la usamos **use folios;**
![alt text](Images\root3.png)

***
15.- Creamos una tabla **CREATE table factura2;**
![alt text](Images\tabla.png)

***
16.- Verificamos en phpmyadmin que se ha creado la base de datos y la tabla.
![alt text](Images\show.png)

***
17.-