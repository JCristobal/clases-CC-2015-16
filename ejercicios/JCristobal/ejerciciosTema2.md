**José Cristóbal López Zafra - Ejercicios del [tema 2](http://jj.github.io/CC/documentos/temas/PaaS)**

##Ejercicio1

###Darse de alta en algún servicio PaaS tal como Heroku, Nodejitsu, BlueMix u OpenShift.

 Accedemos a la web de [OpenShift](https://www.openshift.com/) y nos registramos.

[Dentro](http://i.imgur.com/pM22hgv.png) podremos gestionar nuestras aplicaciones o cambiar la configuración, por ejemplo.

##Ejercicio2
###Crear una aplicación en OpenShift y dentro de ella instalar WordPress. 

Dentro de OpenShift vamos al botón ["Add Aplication..."](https://openshift.redhat.com/app/console/application_types) para crear nuestra primera apliación.

Escogemos de la lista WordPress:

![lista de aplicaciones](https://i.gyazo.com/6d4c4b5a4f4c95317d32d871a5d3138f.png)

Escogemos el nombre que queremos, y nos queda:

![aplicación](http://i.imgur.com/AhXucv0.png)


Vamos a nuestra aplicación mediante el enlace que nos da y nos registramos en WordPress:

![WordPress](http://i.imgur.com/PfKMINP.png)

Y ya está instalado, configurado y disponible para publicar entradas:

![entrada0](http://i.imgur.com/6vm3VUi.png)

##Ejercicio3
###Crear pruebas para las diferentes rutas de la aplicación


##Ejercicio4
###Instalar y echar a andar tu primera aplicación en Heroku.

Instalamos el cinturon de heroku con `wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh ` y `heroku login`

Nos logueamos y clonamos una [aplicación de ejemplo](https://github.com/heroku/node-js-getting-started): `git clone git@github.com:heroku/node-js-getting-started.git`.

La instalamos y arrancamos con `npm install` y `npm start`. Podemos ver que se está ejecutando en http://localhost:5000/

Y para desplegar en Heroku:

`heroku create`
`git push heroku master`
`heroku open`

Accedemos al [dashboard de Heroku](https://dashboard.heroku.com/apps) y comprobamos que [la hemos creado](https://i.gyazo.com/2b43b50d4da76fb9a65008b883217770.png).

En mi caso puedo ver la aplicación desplegada en: https://dry-meadow-8186.herokuapp.com/ 

##Ejercicio5
###Usar como base la aplicación de ejemplo de heroku y combinarla con la aplicación en node que se ha creado anteriormente. Probarla de forma local con foreman. Al final de cada modificación, los tests tendrán que funcionar correctamente; cuando se pasen los tests, se puede volver a desplegar en heroku.
####Como en todos los ejemplos anteriores, se puede cambiar “node” y “heroku” por la herramienta que se haya elegido.

Para probarla en local ejecutamos `foreman start web` (con `web: python script.py` dentro del archivo *Procfile*)

![preba con foreman](https://i.gyazo.com/76fc316245f393826a4522a19376d927.png)


Cremos la aplicación (especificando el buildpack python) en Heroku con `heroku apps:create --region eu --buildpack heroku/python periodicointeractivo-heroku1-1`.

![app creada](https://i.gyazo.com/cd7c6d39b1d23fb19f604b195379771d.png)

Después tendremos que modificar el *Procfile* para ajustar la ejecución de la aplicación. Primero nos lo descargamos `heroku git:clone -a periodicointeractivo-heroku1-1` y añadimos un archivo *Procfile* con `web: python script.py`. 

Guardamos cambios ( `git add Procfile` `git commit` y `git push heroku master`)

[Aplicación con cambios guardados](https://i.gyazo.com/44e75f6ee25b60a90b25415b12ae22c5.png)



