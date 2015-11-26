#Ejercicio 9

- Instalar o darse de alta en un servicio _Redis_ en la nube y realizar sobre �l las operaciones b�sicas desde el panel de control.

- Instalar un cliente de l�nea de �rdenes de _Redis_ o un cliente _REST_ y realizar desde �l las operaciones b�sicas de creaci�n y lectura de informaci�n.

- Ejecutar ejemplos de cualquier lenguaje de programaci�n sobre la instalaci�n realizada.
 
###Pasos realizados para la resoluci�n del ejercicio:

**Nota:** instalaci�n de _Redis_ realizada en _MacOS X_

1. Instalar componentes y dependencias necesarias de _Redis_, utilizando el gestor _Homebrew_:

 `brew install redis`
 
2. Para iniciar el servidor _Redis_

 `redis-server <direccion_config_redis>`
 
3. Para iniciar un cliente de l�nea de comandos e interactuar con el servidor

 `redis-cli`
 
4. Algunos comandos que se pueden ejecutar en _Redis_ son:

 a. Para asignar un valor a una clave (_key_)
 
  `SET test1 "test1"`
  
  Se puede utilizar el comando _SETNX_ (_set if not exists_) para crear y asignar una clave, solo si esta no ha sido definida previamente.
 
 b. Para retornar el valor de una clave asignada previamente
 
  `GET test1`
  
 c. Para eliminar una clave definida
 
  `DEL test1`
  
 d. Para incrementar (de forma at�mica) el valor num�rico de una clave
 
  ```
  SET test2 4
  INCR test2
  ```
  
  En el ejemplo anterior, el valor de "test2" se incrementa a cinco (5)
  
 e. Para el manejo de listas
 
  `LPUSH lista1 "elem1"` para colocar un nuevo elemento al principio de la lista
  `RPUSH lista1 "elem2"` para colocar un elemento al final de la lista
  `LRANGE lista1 0 4` para tomar un subconjunto de la lista, desde la primera posici�n hasta la quinta (si se coloca _-1_, se toman todos los elementos hasta el final de la lista)
  `LLEN lista1` retorna el n�mero de elementos en la lista
  `LPOP lista1` toma el primer elemento de la lista (lo remueve de la misma)
  `RPOP lista1` remueve el �ltimo elemento de la lista y lo devuelve

 f. Para el manejo de conjuntos
 
  `SADD conjunto1 "elem1"` para agregar un nuevo elemento al conjunto
  `SREM conjunto1 "elem1"` para eliminar el elemento identificado como _elem1_ del _conjunto1_
  `SISMEMBER conjunto1 "elem2"` para determinar si el elemento _elem2_ forma parte del _conjunto1_ (devuelve _1_ si pertenece, _0_ si no)
  `SMEMBERS conjunto1` devuelve todos los elementos que pertenecen al _conjunto1_
  `SUNION conjunto1 conjunto2` combina los elementos de los conjuntos y los devuelve como una _lista_
  
 g. Para el manejo de _Hashes_ (tipos complejos)
 
  `HSET test2:4000 atrib1 "val1"` indica que al elemento _test2_ identificado con el "c�digo" 4000, se le va a asignar una variable llamada _atrib1_ con valor _val1_
  `HSET test2:4000 atrib2 "val2"` indica que al elemento _test2_ identificado con el "c�digo" 4000, se le va a asignar una variable llamada _atrib2_ con valor _val2_
  `HSET test2:4000 atrib3 "val3"` indica que al elemento _test2_ identificado con el "c�digo" 4000, se le va a asignar una variable llamada _atrib2_ con valor _val3_
  
  Las instrucciones anteriores son equivalentes a
  
  `HSET test2:4000 atrib1 "val1" atrib2 "val2" atrib3 "val3"`
  
  `HGETALL test2:4000` para obtener todos los valores de atributos del "objeto" _test2_ identificado como 4000
  `HGET test2:4000 atrib2` para obtener unicamente el valor de _atrib2_

 5. Se define un archivo de prueba, llamado [_testRedis.js_](https://github.com/JJ/clases-CC-2015-16/blob/master/ejercicios/AbelFranciscoAgra/2_Uso_de_PaaS/testRedis.js), con algunas pruebas de las funcionalidades b�sicas indicadas en el punto anterior, utilizando _node.js_.
 
  Para ejecutar el programa:
  
  - Instalar la dependencia _redis_ utilizando _npm_
  
   `npm install redis --save`
   
  - Iniciar el servidor _Redis_ (ver punto 2)
  - Ejecutar `node testRedis.js` (o `npm start` si se ha configurado en el archivo _package.json_)
