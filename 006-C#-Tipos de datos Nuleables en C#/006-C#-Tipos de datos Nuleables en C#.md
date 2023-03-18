[Part 6][1]
Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco, 
esta es la parte 6: Tipos de datos nuleables en C#
<next>
[Part 6][2]
En esta leccion veremos:
	- Tipos de datos nuleables en C#
	- Y operador de uso combinado de NULL

 <next>
[Part 6][3] 
En C# los tipos de datos pueden estar en dos diferentes categorioas, Value types (tipos de datos de valor) o reference types (tipos de datos de referencia)

En la leccion anterior ya vimos los value types, que son los tipos de datos incluidos en C# como entero, double, float, decimal, etc.?

Tambien aparte de estos tipos de datos incluidos en C#, tenemos otros value types como structs o estructuras y los enumeradores o enums.

La otra clasificacion para los tipos de datos  es C# es Reference types o tipos de datos de referencia, ya hemos visto un tipo de dato de referencia.. el tipo de dato string, string es en realidad una Clase, 

y algunos ejemplos de reference types son las interfaces, clases, delegados, arreglos, etc.

Hablaremos de las diferencias entre Value types y reference types en detalle en proximas lecciones,
hastas ahora lo que debemos entender es que en C# los tipos de datos puedes dividirce en dos categorias: 
    value types 
    y reference types 

ejemplos de value types: int, double, etc.
ejemplos de reference types : interface, class, delegados, etc

Y otra cosa que hay que tomar en cuenta hasta ahora es que el valor predeterminado para reference types es null
 y el valor predeterminado para value types es algo correspondiente a cero
 
 por ejemplo si es un valor int o entero el valor predeterminado sera cero y este no podra almacenar valores nulos, hay que ver un ejemplo de esto
 
 [x]
 
 Por ejemplo: yo les dije que string que en realidad es una clase.. es un tipo de dato de referencia o reference type..
 
 Asi que si escribo esto
 
 <string nombre = null>
 
 el codigo compilara sin ningun problema porque los tipos de datos de referencia pueden almacenar valores nulos 
 
 Pero por otro lado si creo una varaible que sea value type.. puede ser una variable entera
 <int i = null>
 
 y si vemos esto tenemos un error: <leer el error>
 
 entonces si es una variable de valor o value type y por lo tanto no la podemos inicializar a null
 al contrario de los tipos de datos de referencia, los cuales si pueden ser inicializados a null.
 
 Esta es una de las diferencias mas importantes entre los tipos de datos de valor y los de referencias,
 hay mas diferencias entre estos dos tipos de datos pero hablaremos de esto en proximas lecciones.


bien, ahora si queremos asingarle un valor nulo a un value type, ¿Como lo haria? y es esto posible en C#?
... Clao que si, en C# los value types pueden ser divididos en dos tipos mas:
	- No nuleables
	- nuleables
	
si volvemos a la presentacion:

[Part 5][3] 
Por default los tipos de datos de valor o value types son no nuleables, osea no aceptand nulos, para hacerlos nuleables tenemos que utilziar el signo de interrogacion

[x]
Si tengo que hacer que esta variable i acepte nulos, solo tengo que agregar el signo de interrogacion aqui despues dle nombre del tipo de dato 
y ahora miren esto... ya no tenemos el error y esta variable puede aceptar un null como valor

Esto significa que si queremos que un tipo de dato de valor acepte null o que sea nuleable solo hay que poner el signo de interrogacion al lado del tipo de dato esto lo hara nuleable.

Y ¿porque C# introdujo esta funcion al lenguaje?
en realidad hay algunas razones del porque una de estas es que por ejemplo si tenemos un formulario como este:

<
Nombre:

Apellido:

Eres mayor de edad:
>  

donde el usuario tiene que proporcionar su nombre, apellido los cuales son datos obligatorios, mientras que Eres mayor de edad es un campo opcional y los posibles valores serian si o no, y como este campo es opcional el usuario podria elegir no responderlo.

Si el usuario no responde si es mayor o no, entonces ¿como guardariamos ese valor? 

entonces digamos que tenemos una variable boolean

<bool eresMayorDeEdad = >

Esta variable solo puede ser true o false, porque si vemos es un bool y como no tenemos el signo de interrogación pues no acepta nulos, 

Pero si vemos el requerimiento en el formulario o los datos que le pedimos al usuario, Eres mayor de edad es opcional entonces si el usuario no proporciona ese valor y el campo de tipo bool solo acepta si o no, esto significa que no podemos almacenar el valor cuando el usuario no ingrese ese dato y que valor deberiamos inicializarlo, si o no?, si lo inicializamos con false estamos indicando que el usuario dijo que NO es mayor de edad y no es asi, para resolver esto deberiamos poder almacenar valores nulos en esta variable:

porque el campo Eres mayor de edad.. puede tener 3 respuestas, si, no, o el usuario no respondio.

Si el usuario no respondio, o no selecciono si o no, entonces deberiamos guadar null en esta variable.

De otro modo tendriamos el problema de no diferenciar cuando el usuario de verdad selecciono algo o el usuario no respondio la pregunta, en caso de que dejaramos un valor predeterminado en lugar de poner null que seria lo mas certero en este caso.

y esto es porque estos nuleables value types son tan importantes.

Otra razon del cual son tan importantes es porque las bases de datos no tiene el concepto de tipos de datos de referencia o de valor, en bases de datos como sql por ejemplo tenemos varchar, bit, int, cualquiera que sea el tipo de dato podemos almacenar nulos en cualquier columan de una tabla o para cualquier tipo de dato,
pero value types y reference types son solo conceptos dentro de C# entonces cuando tenemos que trabajar con C# y bases de datos;
Si no existieran los value types nuleables tendriamos que trasnformar los datos que pudieran venir nulos desde la base de datos, 
por ejemplo si en la base de datos tenemos un valor int que puede ser nuleable y en C# no existiera int nuleable(int?) tendriamos que transformar este valor antes de pasarlo de la base de datos a C# y definir un valor default por ejemplo cero, pero aqui seguiriamos con el problema de que ¿si en verdad el usuario guardo cero? o no guardo nada en ese campo.

Con estos  value types nuleables: no tenemos que hacer esa conversion, 
osea si en la base de datos el campo EsMayorDeEdad es un valor bit (si o no) y aparte puede ser nulo
Al trabajar con el desde c# no tendriamos que hacer ninguna conversion de datos entre nulos y no nulos, si no que solamente tendremos que utilizar bool y el signo de interrogacion esto nos facilitara trabajar con datos que vienen desde alguna base de datos.


Estas son alguans de las razones porque los value types tienen la opcion de ser nulos utilizando el signo de interrogacion.

Entonces continuiando con el ejemplo yo puedo convertir esta variable EresMayorDeEdad a un tipo de dato nuleable...

<bool? eresMayorDeEdad = null;>

entonces con este campo donde el usuario podria o no seleccionar una opcion, lo podemos inicializar en null.

Y digamos que queremos validar si el usuario selecciono o no un valor para esta variable 

<if(EresMayorDeEdad == true)
{
	Console.WriteLine("El usuaio es mayor de edad");
}else if(!EresMayorDeEdad.Value)
{
	Console.WriteLine("El usuaio no es mayor de edad");
}

Si vemos el intellisence, .Value en realidad regresa un tipo de dato boolean, no un nuleable bool, 

podemos tener si !EresMayorDeEdad.Value o  EresMayorDeEdad == false 

<
else {
	if(EresMayorDeEdad == true)
{
	Console.WriteLine("Valor no especificado por el usuario");
}
>

y hay que tomar en cuenta que un boolean nuleable puede almacenar 3 valores, verdadero, falso o nulo.

Eres mayor... si... moestraos en pantalla el usuario es mayor,
Eres mayor es igual a false... moestramos el usuario no es mayuor,

y si no.. la otra posible respuesta es null, lo cual significa que el usuario no especifico ningun valor.

si corremos el codigo, como el valor predeterminaod es null, veremos el mensaje, el usuario no especifico ningun valor o no respondio la pregunta.


Otro concepto del que hablaremos es 
 <next>
[Part 6][4] 
El Operador de uso combinado de Null o null coalesing operator el cual es muy interesante.

[10:25]
[x]

Digamos que por ejemplo tengo un campo llamado 
<int boletosEnVenta> es igual a digamos 10

y tengo otra variable llamemosla
<int boletosDisponibles>

digamos que boletosEnVenta es un tipo de dato nuleable
<int? boletosEnVenta = null> y no tenmos boletso en venta ahora

Entonces si no hay boletos en venta ahora obviamente no habra boletos disponibles

Si boletos en venta es igual a null, boletos disponibles sera igual a cero
<if(boletosEnVenta == null)
{
	boletosDisponibles = 0;
}> 
y si no, entonces boletosDisponibles sera igual a la cantidad de boletos en venta

<
else
{
	boletosDisponibles = boletosEnVenta;
}
>

y al final mostraremos la cantidad de boletos disponibles
<Console.WriteLine($"Boletos disponibles: {boletosDisponibles}")>

Miren esto, tenemos un error aqui y dice que no podemos convertir implicitamente un valor de entero nuleable a entero, lo cual significa que no hay una conversion implicita o mas bien qeu C# no puede convertir automaticamente de tipo int nuleable a tipo int no nuleable, 
Asi que teneoms que ser explicitos al momento de pasar un valor entero nuleable a un entero no nuleable, y una manera de hacer esto es .Value <-- que esto nos regresa el valor entero no nuleable de un int nuleable.

Esa es una manera de arreglar este error, o pedemo utilizar el operador de conversion de tipo de dato o cast operator, hablaremos de conversiones explicitas en otra leccion a detalle, por ahora solo hay que saber que podemos hacer el casting o conversion entre tipos de datos utilizando (int) parentesis y nombre del tipo de dato dentro de los parentesis.

Al poner esto lo que hacemos es convertir el tipo de dato int nuleable a int no nuleable, pero esta es una conversion forzada, estamos obligando al tiop de dato int nuleable a ser un int no nuleable, todo esto para poderselo asignar a la variable boletosDisponibles que es un int no nuleable.

Vamos a correr este codigo y obviamente como boletos en venta es nulo, los boletos disponibles seran Cero.

pero si inicializamos esta variable a algun valor, tal vez 100 boletos en venta 
<int? boletosEnVenta = 100>
Y si lo corremos obviamente los boletos disponibles seran 100, 

Que esta pasando en este codigo?, validamos si boletos en venta es igual a nulo,lo cual falso, boletos en venta no es igual a nulo porque es igual a 100, entonces la ejecucion del codigo entrara en la seccion else, si no, y lo que hacemos aqui es convertir boletosEnVenta a tipo int no nuleable y le asignamos esa conversion a la variable boletosDisponibles, con esto boletosDisponibles valdra 100 y al final lo moestramos en pantalla.

Entonces si es null le asignamos el valor de cero a la variable boletos disponibles porque esta variable no puede almacenar nulos.
Bueno pues.. ¿Necesitamos tantas lineas de codigo solo para hacer eso?, osea solo para pasar el valor de boletosEnVenta a boletosDisponibles  y en caso de que boletosEnVenta sea nulo dejar boletosDisponibles en cero...
La pregunta es para hacer algo tan simple son tantas lineas de codigo, hay una forma mas facil de hacer esto mismo y  es utilizando operador de uso combiando de null o null coleasing operator.

Y la forma de utilizarlo es muy simple:
Solo necesitamos remover todas esta lineas de codigo y poner
<int boletosDisponibles = boletosEnVenta 
signo de interrogacion, signo de interrogacion este es el operador de uso combinado de null
?? 
y el valor que sea que queramos utilizar como valor predeterminado, en este caso cero
0;>

Osea que esta simple linea esta validando si esta variable es nula pon este valor predeterminado, si no es nula utilizar el valor que contenga la variable.
Asi de simple solo una linea y si corremos este codigo obtendremos el mismo resultado que con el codigo anterior, pero en lugar de utilizar if y else estamos ahora utilziando el operador de uso combinado de null ?? el cual es muy simple de utilizar.

[Parte 6][4]
Esto es sin el operador de uso combinado de null y esta parte de aca es con el operador de uso combinao de null..
Aqui podmeos ver la diferencia y el numeor de lineas es 

 <next>
[Part 6][5] 
Esto es todo por hoy, muchas gracias por mirar este video y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Gracias por estar aqui que y  tenga un dia genial :)


