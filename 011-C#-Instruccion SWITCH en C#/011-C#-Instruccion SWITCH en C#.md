[Parte 11][1]
Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco, 
esta es la parte 11: Instruccion Switch en C#

<next>
[Parte 11][2]
En la parte 10 de este curso vimos la instruccion IF asi que en este video veremos la instrucccion:
- La instruccion Switch
- La instruccion break
- La instruccion go-to

[Parte 11][3] 
¿Cuando debemo utilizar la instruccion Switch?
Para darnos una idea, muchos if-else anidados o juntos pueden ser reemplazados por una sola instruccion switch.

Si vemos esto en el lado izquierdo tenemos multiples if elses los cuales son reemplazados por una instruccion switch.

Veamos el ejemplos
[x]
Vamos a pedirle al usuario que introduzca un numero:
[Console.WriteLine("Por favor escriba un numero: ")]
Vamos a leer el numero y guardarlo en una variable
[int numero = int.Parse(Console.ReadLine());]
Entonces lo que estmaos haciendo aqui es leer un numero desde la consola con el metodo ReadLine dentro de la clase Console, este numero vendra como un string asi que tenemos que convertirlo a int para eso utilziamos el metodo Parse dentro de la clase int, con todo esto ya tendremos el numero listo en la variable que se llama numero para empezar a utilizarlo en el switch.

Primero hagamos el ejemplo utilizando if:  Si el numero es igual a 10 mostrare un mensaje diciendo Su numero es 10, si el numero es 20 mostrare un mensaje diciendo su numero es 20  y lo mismo si el numero es 30, entonces utilizan if el codigo quedaria ais:
[
if(numero == 10){
	Console.WriteLine("Su numero es 10");
}else if(numero = 20){
	Console.WriteLine("Sun numero es 20");
}else if(numero = 30){
	Console.WriteLine("Sun numero es 30");
}
]
Y si el numero no es ni 10, ni 20 ni 30 pondremos un else al final y mostraremos el mensaje: su numero no es 10, 20 0 30.

[
if(numero == 10){
	Console.WriteLine("Su numero es 10");
}else if(numero = 20){
	Console.WriteLine("Su numero es 20");
}else if(numero = 30){
	Console.WriteLine("Su numero es 30");
}else{
	Console.WriteLine("Su numero no es 10, 20 o 30");
}
]

Muy bien, si hechamos un vistazo a este programa pues en realidad es un programa un simple vamos a correrlo para ver los resultados.

El programa me esta solicitando un numero voy a ingresar 20 y presionar enter.
Y vemos como resultado el mensaje: Su numero es 20.
¿Que esta pasando aqui?, pues si analizamos el programa
Ingresamos el numero 20 entonces la variable numero vale 20 
Y cuando llegamos al primer if, este if esta validando si numero que ahora vale 20 
es igual a 10 al ser falso pasa al siguiente bloque else-if y valida 20 es igual a 20 esta condicion se cumple y se muestra el mensaje en pantalla terminando aqui estos ifs, entonces al cumplirse esta condicion el resto ya no sera evaluado porque son ifs anidados mutuamente excluyentes, o sea si uno se cumple los demas no seran cumplidos.

Bueno explicados estos ifs lo siguiente es que todos estos ifs pueden ser reemplazados con la instruccion switch, veamos como hacer esto:
En lugar de poner todos estos ifs-else if reemplacemoslos por una instruccion switch
[
switch()
]
y que voy a evaluar pues la variable numero, entonces
[
switch(numero){
}
]
y se qu el valor de numero pueden ser cualquier numero entero asi que estos seran mis instrucciones case o dicho de otra manera mis condiciones
[
switch(numero){
	case 10:
		
}
]
Entonces cuando numero sea igual a 10 lo que voy hacer es:
[
switch(numero){
	case 10:
		Console.WriteLine("Su numero es 10.");
}
]
y con esto tengo el switch donde estoy validano la variable numero y en el primer caso a evaluar es cuando numero valga 10 si esto se cumple el progrmaa va imprimir este mensaje... y algo importante aqui es que debemos poner un break al final del case.
[
switch(numero){
	case 10:
		Console.WriteLine("Su numero es 10.");
		break;
}
]
Entonces si vale 10 va entrar mostrar el mensaje he inmediatametne despues con este break va a salir del switch, esto es lo que estamos indicando con el break que termine de validar o ejecutar el switch.

Muy similar tendremos la instruccion para cuando el numero sea 20:
[
switch(numero){
	case 10:
		Console.WriteLine("Su numero es 10.");
		break;
	case 20:
		Console.WriteLine("Su numero es 20.");
		break;
}
]
lo mismo para cuando el numero valga 30
[
switch(numero){
	case 10:
		Console.WriteLine("Su numero es 10.");
		break;
	case 20:
		Console.WriteLine("Su numero es 20.");
		break;
	case 30:
		Console.WriteLine("S numero es 30.");
		break;
}
]
Tambien queremos mostrar un mensaje en caso que el numero no sea  10, ni 20 ni 30 para esto tenemos la condicion por default dentro del switch
[
switch(numero){
	case 10:
		Console.WriteLine("Su numero es 10.");
		break;
	case 20:
		Console.WriteLine("Su numero es 20.");
		break;
	case 30:
		Console.WriteLine("S numero es 30.");
		break;
	default:
		Console.WriteLine("Su numero no es 10, 20 o 30");
		break;
}
]
La condicion default lo que va hacer es ejecutarse cuando las demas condiciones no se cumplan.

Muy bien, entonces en lugar de tener muchos ifs uno despues de otro ahora estamos utilizando una sola instruccion switch que lo que esta haciendo es:
validando los posibles valores de esta variable numero que es el numero que el usuario ingreso
pra esto dentro del switch estamos evaluando multiples posibles valores para la variable numero, en el primer case decimos cuando esta variable numero vale esto osea 10, depues mostramos en pantalla el mensaje correspondiente y al final del case ponemos la instrucion break para indicar que ya saldremos de la instrucccion switch.
Lo mismo pasa con los demas Cases y todos deben llevar break al final para indicar que alli termina la execucion del switch.

Vamos a correr este programa y digamos que el usuario ingreso el numero 20, entonces entrara directamente al parte donde numero es 20, a esta linea en especifico, ejecuto esta linea donde muestra un mensaje en pantalla y por ultimo ejecuta la linea del break para salir del switch.

Como mencione antes la instruccion break tiene que ir al final de cada case para indicarle la switch que demos salir de el o que ya termino la ejecucion del switch y el resto del codigo ya no sera ejecutado.

Bien pues cambiemos un poco este programa para entender otro concepto: 
Podemos tener muchos cases juntos voy a modificar el programa para que veamos un ejemplo:
[
switch(numero){
	case 10:
	case 20:
	case 30:
		Console.WriteLine("S numero es 30.");
		break;
	default:
		Console.WriteLine("Su numero no es 10, 20 o 30");
		break;
}
]
De este modo cuando numero sea 10, 20 o 30 a como esta el codigo actualmente va ha mostrar el mensaje Su nuemro es 30 <-- como este mensaje esta fijo ha esto se le conoce como hardcode y
tener codigo "harcodeado" es una mala practica y no se recomienda porque nos  da pie a posibles errores.
, pero puedo cambiar un poco el mensaje y utilizar string interpolation podemos arreglar esto
[
switch(numero){
	case 10:
	case 20:
	case 30:
		Console.WriteLine($"Su numero es {numero}.");
		break;
	default:
		Console.WriteLine("Su numero no es 10, 20 o 30");
		break;
}
]
Recuerden para utilizar string interpolation debemos agregar signo de peso al inicio del string y poner las variables entre llaves.  Si tienen dudas sobre string interpolation pueden revisar la parte dos Leer y escribir en la consola de este curso

Bien con esto el codigo se vuelve un poco mas dinamico, no estoy mostrando mensajes independientes si no que hago uso de la variable y puedo juntar los cases como si fueran uno solo.
entonces este case 10 y este otro case 20 no tienen ningun codigo, cuando se evalua si es 10 no hay codigo y despues viene a evaluar si es 20 y tampoco hay codigo y al final evalua si es 30 y este es el codigo que sera ejecutado para cualquiera de los tres valores.

Muy Bien como vemos en el ejemplo es posible combinar cases juntos cuando queremos que el mismo codigo se ejecute para todas estas condiciones, 
y si corremos este programa obtendremos el mismo resultado asi que no hay diferencia para el usuario que esta corriendo el programa pero si hay una diferencia en la estrucutra de switch, es el mismo resultado que si tenemos los ifs juntos con estos ejemplo vemos cmo podemos reemplazar ifs por switch y tambien como podemos combinar cases dentro del switch.

Entonces como vemos cuando tenemos cases juntos no ponemos el break y de este modo el switch sabe que ese case va a ejecutar el mismo codigo que este otro case cuando tenemos ejecuciones individuales unicas de cada case debemos poner break al final.

[parte 11][03]
ok, ya vimos que multiples ifs pueden ser reemplazados por un switch case 

[parte 11][04]
Tambien vimos como multiples cases pueden combinarse para  ejecutar el mismo codigo

[parte 11][05]
Y otro concepto es la instruccion goto, para esto vamos a hacer una practica muy simple simulando tal vez una compra de un cafe y esto va a llevar un poco mas de tiempo asi que lo veremos en el proximo video.
 
[Parte 11][06] 
Muchas gracias por haberme escuchado hoy!

Te deseo un dia genial! :)