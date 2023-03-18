[Parte 8][1]
Hola bienvenidos a Pragim Technologies mi nombre es Cristina Carrasco, 
esta es la parte 8: Arreglos en C#
<next>
[Parte 8][2]
En esta lección veremos:
- Que son los arreglos
- Y cuales son las ventajas y desventajas de usar arreglos

Veamos un ejemplo 
[x]
Ahora si creo una variable de tipo entero
< int i = 10 ;>
solo puedo almancenar un valor entero,
entonces si quiero almacenar mas de 1 valor enteror en esta variable <señalar i> no es posible aqui es donde entran los arreglos a solucionar este problema.

Si queremos almancer un grupo de datos con tipos de datos similares en una sola variable, podemos hacer uso de los arreglos

Por ejemplo:
Digamos que quiero almacenar una coleccion de numeros pares,
para hacer eso puedo crear un arreglo de enteros y almacenar mis numeros pares.

Veamos como crear un arreglo:
asi que por ejemplo quiero almacenar 3 numeros pares y como ya sabemos los numeros pares son enteros, asi que puedo crear un arreglo de enteros con una longitud o tamaño de 3, porque solo voy almacenar 3 valores, 
asi que vamos a ver como crear un arreglo de enteros.
Ahora para crear un arreglo de enteros como vemos aqui <int i = 10> este es el tipo de datos <int > y este es el valor que se le asigna < = 10>, entonces pare crear el arreglo de enteros debemos poner 
<int[] > estos corchetes indican que vamos a crear un arreglo, 
vamos a ponerle un nombre significativo al arreglo <int[] numerosPares = .. remover la parte del 10>
Y sabemos que queremos crear un arreglo, este es el tipo < seleccionar int > y estos corchetes indican que es un arreglo.. 
un arreglo es un grupo de tipos de datos similares, en este caso un grupo de enteros, 
Cuantos enteros queremos almacenar? 1,2 5, 10...
asi que tenemos que especificar el tamaño o la longitud y para hacerlo:
utilizamos la palabra reservada < new > 
<int[] numerosPares = new >
y despues el tipo de dato int[, abrimos corchetes y aqui entre los corchetes es donde debemos especificar el tamaño del arreglo
<int[] numerosPares = new int[3];>
en este caso lo que quiero es crear un arreglo de enteros y alamcenar 3 numeros,
entonces ¿Cóomo almaceno estos tres numeros?

Los arreglos estan basados en indices enteros, empezando desde 0 (cero)
Asi que el primer elemento se encuentra en la posicion 0
< numerosPares[0]  >
asi que numerosPares en la posicion cero es igual a:  0
< numerosPares[0] = 0 >
porque el primer numero par es 0
[2:39]
Numero par en la posicion 1, osea el segundo numero par que queiro almacenar, sera igual a 2
he igualmente hacemos lo mismo para almacenar el tercer numero par el cual sera almacenado en la posicion 2
<numerosPares[2] = 4;>

Y digamos por ejemplo que quiero imprimir el segundo numero par:
< Console.WriteLine($"Segundo numero par: {numerosPares[1]}"); >

y qué es lo que va ha pasar?
en esta ubicacion <numerosPares[1]> almacenamos el numero par 2, asi que este sera mostrado en pantalla si corremos este programa.

<Ctrl+ f5.. para correr el programa>

en la posicion 1 almacenamos el numero entero 2 y lo estamos mostrando en pantalla

Este es un ejemplo muy simple de un arreglo, ok

Ahora cual es la ventaja de utilizar arreglos?
Obviamente un arreglo es una coleccion de tipos de datos similares, asi que si quieres almacenar un grupo de tipos de datos similares puedes hacer uso de arreglos, pueden ser enteros, float, doubles, strings, cualquier tipo de dato; 
por ejemplo si quieres almacenar los nombres de tus amigos, un grupo de nombres de amigos.. puedes hacer uso de un arreglo de strings 

¿Cuál es la ventaja de usar arreglos?
La ventaja es que son fuertemente tipados, lo cual significa que si el arreglo es de tipo entero, solo puede almacenar enteros
Y si tratamos por ejemplo de alamcenar otro tipo de dato, damos que accidentalmente 
<numerosPares[0] = ""> tratamos de almacenar un string como "Hola", sabemos que este valor es de tipo string, pero este arreglo es de tipo int y podemos ver este valor marcado con rojo indicando que hay un error 
Si vemos el mensaje de error este dice: que no podemos convertir implicitamente de string a entero, porque sabemos que numerosPares es un arreglo de enteros.

Los arreglos son fuertemente tipados, no permite violaciones de tipos de datos, es decir si definimos que una variable es de tipo int no podemos asignarle valores string.

El hecho de que los arreglos sean fuertemente tipados es un muy buen beneficio y nos daremos cuenta de esta ventaja mas adelante cuando estemos comparando arreglos con otras coleciones de datos disponibles aqui en .NET
Hasta entonces no se preocupen por esto, solo hay que tener en mente que los arreglos son fuertemente tipados y esta es una de sus ventajas sobre otras colecciones de datos.

Bien, y ¿Cuáles son las desventajas de utilizar arreglos?
La primer desventaja es que una vez que inicializamos el arreglo ya no le podemos cambiar el tamaño.

Por ejemplo en este caso el tamaño de este arreglo es 3, asi que si intento almacenar un cuarto valor en la posicion 3
<numerosPares[3] = 6 >
Si compilamos esto vemos que no hay errores de compilacion, pero en realidad tendremos un error de runtime.
<correr programa>
Y obviamene es un Indice fuera de los limites o IndexOutOfRage exception
Esto nos esta indicando que intentamos almacenar un valor fuera del tamaño del arreglo, el arreglo solo puede tener 3 elemento y estamos intentando agregar un cuarto elemento y esto no es posible
debido a que no tenemos la posicion 3, la cual representa el cuarto elemento porque arreglos inician en la posicion 0, entonces el indice  queda fuera del tamaño del arreglo lo cual tiene sentido debido a que es un arreglo de 3 elemento y queremos almacenar 4 elementos.

Y esto prueba que una vez que el tamaño del arreglo es especificado, ya no podemos añadir mas elemento o cambiar ese tamaño. 
El tamaño de un arreglo en C# es fijo una vez definido no se puede cambiar.
Esto significa que los arreglo no pueden aumentar de tamaño y es una de sus desventajas.

En .NET tenemos otras colecciones de clases como list, tablas hash, etc. las cuales pueden aumentar su tamaño automaticamente, estaremos hablando de estas mas adelante cuando lleguemos al tema de cada una, hasta entonces no hay que preocuparnos por estas colecciones 

<next>
[Parte 8][3]
Una desventaja es que los arrelgos no pueden aumentar su tamaño una vez inicializados
 y otra deventaja es que dependen de indices para almacenar u obtener valores del arreglo, no hay otra manera de almacenar u obtener los valores,
Pero si estuvieramos utilizando colecciones de clases en estas es muy facil almacenar u obtener sus elementos, no tenemos que depender del indice o la posicion donde se almaceno, estaremos hablando de esto cuando veamos el tema de colecciones de clases en .net.

<volver al codigo fuente>

Por ahora hay que entender que la unica manera de almacenar u obtener valores de un arreglo es por su indice,
por ejemplo digamos que por error yo intento retornar un elemento  y en lugar de escribir 1 escribo 10 y si compilo la solucion no hay ningun error de compilacion, pero cuando ejecute la aplicacion tendre un error de runtime Indice fuera del rango porque la posicion 10 no existe para este arreglo y el error pasa porque tengo que utilizar los indices y por eso es que esta es una desventaja.

Arreglos son muy buenos porque son fuertemente tipados, pero una vez que defines un arreglo para que almacene un tipo de dato determinado ya no puedes almacenar otro tipo de dato en ese arreglo y esta es la mayor ventaja de los arreglos;
las desventajas son que una vez que defines el tamaño ya no se puede cambiar y la otra desventaja es que la unica forma de asignarle valores a un arreglo o de consultar los valores almacenados es utilizando el numero de indice el cual puede causarnos errores y algo complicado de usar y por otro lado si utilizamos alguna de las colecciones de clases que estan disponibles en .NET estas ya continen algunos metodos que nos facilitan almacenar y obtener los elementos de estas colecciones de las cuales hablaremos mas adelante.

La mayoria del tiempo en .NET si necesitamos almacenar un grupo de elementos que son de tipos de datos similares estaremos utilizando los generics los cuales veremos mas adelante,

[Parte 8][3] 
 asi que hasta este punto lo que debemos entender es que un arreglo es una coleccion de tipos de datos similares, hay ventajas de utilizar arreglos la cual es que son fuertemente tipados y desventajas que no pueden crecer en tamaño automaticamente como otras colecciones de datos y la otra desventaja es que depende del indice para almacenar u obtener sus valores.
 
[Parte 8][4] 
Esto es todo por hoy muchas gracias por ver este video, y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Te deseo que tengas un excelente dia :)