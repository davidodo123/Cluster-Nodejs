# Despliegue cluster con NodeJS y Express #

- Lo primero que vamos ha hacer es intalar nodejs ya que no esta instalado.
![Instalar Node.js](assets/img/instalarnodejs.png)


## Proyecto Sin cluster ##

- Hay que crear una carpeta para el proyecto, se inicia con npm init para crear una estructura de carpetas automaticamente.
![Creamos carpeta y hacemos un init](assets/img/init.png)
- Se Hace un npm install expres para instalar el proyecto: 
![Descargamos Express](assets/img/express.png)
- Despues de esto creamos con nano un archivo app.js y añadimos el siguiente contenido y se ejecuta node:
![Datos de la aplicación](assets/img/aplicacionDatos.png)
- En mi caso, sale un error, que sucede por que la instalacion de node es una version antigua, sale por predeterminado, asi que busco la version mas reciente
- Borrar node.
![Borrar Node](assets/img/BorrarNode.png)
- Reinstalarlo, con una version mas actual 
![Reinstalar](assets/img/Reinstalar.png)
- Comprobamos
![Comprobamos versiones](assets/img/comprobamos.png)
- Borramos expres por si da fallos
![Borrar expres y instalarlo](assets/img/borramosexpress.png)
- Ya funcionaria y estaria la aplicacion escuchando por el puerto dicho "3000", para acceder tenemos que saber la ip y poner :3000


## Funcionamiento en Web ##

- Escribimos Hello World:
![Hello](assets/img/Helloworld.png)
- Comprobacion Web
![Final Contar](assets/img/finalcount.png)
![Final Count mas grande](assets/img/finalmasgrande.png)
- Se puede ver que va lento y cuando abrimos otra pagina vuelve a subir 
![Tiempo del mas grande](assets/img/tiempo1.png)
![Tiempo de la otra pagina](assets/img/tiempo2.png)
Como se ejecuta como unico proceso, sale asi.


## Proyecto Con cluster ##

- Hay que crear el archivo y se modifica con los siguientes datos: 
![Segunda App](assets/img/segundaapp.png)
- Ejecutamos la app:
![Ejecutamos segunda App](assets/img/Ejecutamos2app.png)
- Comprobamos otra vez los tiempos. 
![Lenta](assets/img/lenta.png)
![Rapida](assets/img/rapida.png)
- Esta diferencia es porque se crean varios procesos workers al mismo puerto, entonces las peticiones se distribuyen entre ellos, permitiendo atender a multiples sulicitudes.


## Metricas de rendimiento##

-Instalamos loadtest
![Instalamos loadtest](assets/img/instalamosloadtest.png)
- Comprobamos con "loadtest http://localhost:3000/api/500000 -n 1000 -c 100"
![Comprobamos load](assets/img/comprobamosload.png)
- Ahora lo comprobamos con mas solicitudes "loadtest http://localhost:3000/api/50000000 -n 1000 -c 100"
![Comprobamos load con mas solicitudes](assets/img/massolicitudes.png)

- Ejecutamos la otra aplicacion que si tiene clusters, utilizamos node y comprobamos: 
![Comprobamos load con cluster](assets/img/loadcloster1.png)
![Comprobamos load con cluster y mas solicitudes](assets/img/loadcloster2.png)


## Uso de PM2 para administrar un clúster de Node.js ##

- Necesitmos instalarnos pm2 y conprobamos
![Instalacion pm2](assets/img/pm2.png)
