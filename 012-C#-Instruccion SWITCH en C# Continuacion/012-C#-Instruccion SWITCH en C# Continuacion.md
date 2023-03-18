[Parte 12][1]
Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco, 
esta es la parte 12: Instruccion switch en C# - Continuacion.
en la parte 10 ya hemos visto la instruccion if  y en la parte 11 vimos la introduccion a la instruccion switch y en esta parte escribiremos un pequeño programa simulando la compra de un cafe utilizando las isntruccions switch, goto y break asi que vamos al ejemplo:

[x]
Muy bien, entonces quiero escribir un programa muy simple que le permita a la gente comprar cafe y le muestre la cuenta,
asi que primero vamos a mostrarle el menú al usuario:
[
Console.WriteLine()
]
esta cafeteria vende tres tamaños de cafe, chico, mediano y grande.
entonces en el mensaje preguntare que tamaño de cafe quieren

[
Console.WriteLine("Por favor elija que cafe quiere: \n1=chico, 2=Mediano, 3=Grande");
]
El usuario tendra que escribir el numero correspondiente al tamaño del cafe y presionar enter.

Despues de que el usuario eligio un tamaño de cafe pues necesitamos saber cual fue la eleccion del usuario, asi que creemos una variable para almacenar este valor: digamos eleccionDelUsuario

[
Console.WriteLine("Selecciones el tamaño para su cafe: 1=chico, 2=Mediano, 3=Grande");
int eleccionDelUsuario = int.Parse(Console.ReadLine());
]
Entonces Console.ReadLine leera el numero en formato string y con el metodo parse dentro de la clase int convertimos el string a int con esto ya podemos asignar el valor que leimos de la consla a la variable eleccionDelUsuario.

Bien, ahora ya que sabemos que cafe eligio el usuario tambien necesitamos asignarle un precio al cafe seleccionado y digamos que tal vez el cafe chico cuesta 20 pesos el mediano 30 y el grande 35
Entonces voy a crear la variable costoTotalDelCafe
y la voy inicializar en cero
[
int costoTotalDelCafe = 0;
]

Lo siguiente que haremos es poner una instruccion switch validando la eleccion del usuario:
[
switch(eleccionDelUsuario){
}
]
Si el usuario eligio 1 sabemos que este es el cafe chico y el cafe chico dijimos que costaria 20 pesos
[
switch(eleccionDelUsuario){
	case 1:
}
]
entonces podemos decir que el costo total del cafe son costotalDelCafe += 20
[
switch(eleccionDelUsuario){
	case 1:
		costoTotalDelCafe += 20;
		break;
}
]
y hagamos los mismo para los otros dos tamaño, mediano y grande
[
switch(eleccionDelUsuario){
	case 1:
		costoTotalDelCafe += 20;
		break;
	case 2:
		costoTotalDelCafe += 30;
		break;
	case 3:
		costoTotalDelCafe += 35;
		break;
}
]
Si el usuario eligio alguna otra opcion aparte de 1, 2 0 3...
lo que le mostraremos en este caso sera un mensaje de error diciendo que su eleccion es invalida.
[
switch(eleccionDelUsuario){
	case 1:
		costoTotalDelCafe += 20;
		break;
	case 2:
		costoTotalDelCafe += 30;
		break;
	case 3:
		costoTotalDelCafe += 35;
		break;
	default:
		Console.WriteLine("Su eleccion es invalida.");
		break;
}
]

Ok, si vemos el codigo hemos escrito un programa muy simple, este muestra un menu al usuario el usuario selecciona su opcion del menu y despues de eso dependiendo de lo que el usuario eligio estamos calculando la cuenta o lo que se tiene que pagar por el cafe.
En cambio si la opcion proporcionada por el usuario no es ninguna del menu, en ese caso le mostramos el mensaje "Su eleccion es invalida."
Ok, entonces corramos el ejemplo:
le esta preguntando al usuario que ingrese su eleccion, pongo 2 presiono enter y termina le ejecucion del programa y no le estoy mostrando nada de vuelta al usuarios solo estoy calculando el total pero no se lo estamos mostrando al usuario, entonces vamos y mostremos el total al usuario
[
Console.WriteLine($"¡Gracias por su compra!\nSu total a pagar es: {costoTotalDelCafe}");
]
Entonces si corremos este programa otra vez:
Nos pide que elijamos una opcion, digamos que pong 3 cafe grande y presiono enter, ahora si nos muestra en pantalla el total a pagar 35 pesos.

Muy bien ahora hagamos este progrma un poco mas interactivo, permitiendole al usuario comprar muchos cafes, no solo uno.  Porque si vemos con el codigo actual si quisiera comrpar otro cafe tendria que ejecutar el programa cada vez que quiera comprar otro cafe.

Pongamosle al programa algo como un bucle para que se quede cliclado o repitiendo lo mismo;
para esto utilizaremos la instruccion goto, 
con esto el usuario estara comprando cafe hasta que el decida ya no comprar mas, 
y cuando el usuario decida ya no comprar el programa terminara la ejecucion.

Veamos como hacer esto:
En lugar de que se tenga que correr el programa cada con cada compra del cafe lo que queremos es que al final cuando el usuario haya temrminado de comrpar todos los cafes, se muestre la cuenta con el total de todo lo que compro.
Asi que antes de mostrar el tota le preguntaremso al usuario si desea comprar otro cafe, y la respuesta a esta pregunta sera si o no
[
Console.WriteLine("¿Desea comprar otro cafe? Si o No");
string seguirComprando = Console.ReadLine();
]


y para validar la respuesta del usuario podriamos utilizar un if u otro switch es cuestion de gustos cualquier opcion es correcta.  
En etes caso utilizaremos otro switch porque es el tema del cual estamos aprendiendo en este video.
Entonces el codigo quedaria de la siguiente manera
pondemos otro switch para la variable seguir comprando
[
switch(seguirComprando){
}
]
Si vemos en el primer switch la variable que estamos validando es eleccionDelUsuario y esta varaible sabemos que es de tipo int entonces en los case las opciones deben ser valores int.
Dicho esto en este segundo switch la  variable que validaremos es de tipo string, entonces en los cases debemos de poner valores string, 
lo que quiero decir con esto es que los cases tienen que cuadrar con el tipo de variable que estamos comparando de lo contrario tendremos un error de sintaxis.
Entonces pongamos el codigo para cuando el usuario seleccione que si quiere continuar, la letra s entre comillas dobles
[
switch(seguirComprando){
	case "s":
}
]
Si el usuario selecciono Si, significa que quiere continuar comprando, asi que tendremos que mostrarle el menu otra vez, para esto tendremos que poner una etiqueta o label por su nombre en ingles, esta etiqueta tiene que estar justo antes de mostrar el menu:

[
Inicio:
Console.WriteLine("Selecciones el tamaño para su cafe: 1=chico, 2=Mediano, 3=Grande");
int eleccionDelUsuario = int.Parse(Console.ReadLine());
]
Y que es un label o etiquesta, es un marcador o una bandera, entonces este marcador se llama Inicio y antes de seguir hablando de labels volvamos al switch,
entonces si el usuario decide seguir comprando:
[
switch(seguirComprando){
	case "Si":
		goto Inicio;
}
]
le indicamos al programa que vaya a (go to) la etiqueta que se llama Inicio.  Al llegar aqui la ejecucion del codigo se movera directamente a donde esta la etiqueta Inicio y continuara la ejecucion otra vez hasta volver a llegar a este switch.

Muy bien y que es una etiqueta o label, es un tipo de marcador o bandera en el programa que le indica a que parte del programa podemos cambiarnos en un determinado momento, en este caso el label nos permite regresar atras en las lineas y repetir ciertos codigo, igual podriamos tener codigo mas abajo y crear un label para irnos mas abajo en el codigo.
Entonce los labels son marcadores que nos permiten saltar entre lineas de codigo.

Y no hay que confundirse con otro tipo de labels que se usan en c# para programacion de aplicaciones de windows y tambien existen los labels en programacion web las cuales son elementos que se usan para mostrar texto que describe a otros elementos, asi que este es un concepto muy diferente a las etiquetas que estamos viendo hoy las cuales sirven para saltar entre lineas de codigo.

Muy bien si vemos el codigo cuando el usuario seleccione que si quiere comprar otro cafe, se ejecutara esta parte del codigo donde le estamos indicando al programa que salte aca a esta otro linea de codigo y volvemos a mostrar el menu para que siga comprando mas cafe.

En caso contrario si el usuario ya no quiere comprar mas cafe:
[
switch(seguirComprando){
	case "Si":
		goto Inicio;
	case "No":
		
}
]
Simplemente queremos salir del switch, el unico codigo que necesitamos para cuando el usuario no quiera seguir comprando cafe es break; no vamos hacer mas calculos ni preguntar otra vez, daremos por concluida la compra asi que solo ponemos el break para salir del switch
[
switch(seguirComprando){
	case "Si":
		goto Inicio;
	case "No":
		break;
}
]
Y si el usuario puso cualquier otra opcion, osea escribio s o n, cualquier otro valor que haya escrito osea default, mostraremos el siguiente mensaje:
[
switch(seguirComprando){
	case "Si":
		goto Inicio;
	case "No":
		break;
	default:
		Console.WriteLine("Por favor escriba una opcion valida. Si=s, No=n");
}
]
Y pues tenemos que irnos atras a preguntarse si quieres seguir comprando cafe, entonces necesitamos otro label o etiqueta para volver.
[
switch(seguirComprando){
	case "Si":
		goto Inicio;
	case "No":
		break;
	default:
		Console.WriteLine("Por favor escriba una opcion valida. Si o No");
		goto DeseaComprar;
}
]
Agrego la etiqueta justo antes de preguntar si desea comrpar otro cafe
[
DeseaComprar:
Console.WriteLine("¿Desea comprar otro cafe? Si o No");
string seguirComprando = Console.ReadLine();
]

Ok, entonces si el usuario no escribio si o no el programa saltara a esta linea y volvera a preguntar otra vez.

Algo que podemos notar aqui en el codigo es que cada case termina con un break, excepto cuando utilziamos goto....
Entonces no necesitamos escribir break cuando tenemos la instruccion goto, si lo ponemos:
[
switch(seguirComprando){
	case "Si":
		goto Inicio;
	case "No":
		break;
	default:
		Console.WriteLine($"Elegiste {seguirComprando} la cual no es una opcion valida.\nPor favor escriba una opcion valida. Si o No");
		goto DeseaComprar;
}
]
El intelisense lo pone subrayado en verde porque no es una instrucion incorrecta pero si pongo el muse encima vere el mensaje que indica que este codigo nunca sera alcanzado, 
osea no hay forma de que esta linea de codigo sea ejecutada por el programa.
y analizemos porque no sera ejecutada esta linea de codigo... el usuario selcciona s que si queire seguir comprando cuando llemos al switch se evalua que selecciono el usuario fue la s entra aqui y depues corre goto lo cual hara un salto a esta otra linea de codigo y en realidad despues de goto no continua la ejecucion sino que salta a otra linea de codigo.
Ese codigo jamas sera ejecutado asi que no es necesario y no necessitamos tampoco salir del switch porque la instruccion goto nos esta haciendo salir de el.

Bien, entonces corramos la aplicaciones y veamos si funciona sin errores y como esperamos que funcione:

Seleccione el tamaño de su cafe:
escribo 3 y presiono enter
ahora tengo el mensaje: Desea comprar otro cafes
escribo un valor invalido qwerwet y presiono enter
Vemos el mensaje: Elegiste qwet la cual no es una opcion valida, por favor escriba una opcion valida, si o no
Ahora escribo Si, si quiero comprar otro cafe 
ahora comprare un cafe mediano: escribio 2 y presiono enter 
entonces ahora ponder S en mayusculas y presiono enter
Vemos el mensaje: Elegiste SI la cual no es una opcion valida

Pero para nosotros s minuscula y S mayuscula significa que si quiero seguir comprando, pero para la computadora esto es es tan obvio, asi que hagamos un pequeño cambio en el progra para que acepte este valor:

Sin importar si el usuario utilizo mayusculas o minusculas, nosotros podemos validar los datos de otra manera, entonces puedo valisar case SI con mayusculas y NO con mayusculas
[
switch(seguirComprando){
	case "SI":
		goto Inicio;
	case "NO":
		break;
	default:
		Console.WriteLine($"Elegiste {seguirComprando} la cual no es una opcion valida.\nPor favor escriba una opcion valida. Si o No");
		goto DeseaComprar;
}
]
Entonces sin importar que como ingreso el valor el usuario yo voy a convertir este valor a mayusculas y para eso hay un metodo extension de los stings que convierte el texto en mayusculas y es ToUpper el cual convertir todas las letras de ese string a mayusculas:
[
switch(seguirComprando.ToUpper()){
	case "SI":
		goto Inicio;
	case "NO":
		break;
	default:
		Console.WriteLine($"Elegiste {seguirComprando} la cual no es una opcion valida.\nPor favor escriba una opcion valida. Si o No");
		goto DeseaComprar;
}
]
Ahora no importa como haya escrito la palabra el usuario para el programa sera el mismo Si con mayusuculas o minusculas.

Hablaremos a detalle de las funciones para  manipular strings en proximas lecciones, en este modulo solo utilizamos la funcion para convertir a mayusculas, ToUpper y es la unica que utilizaremos por ahora.

Muy bien corramos el programa otra vez,
Para el tamayo del cafe pondre una instruccion invalida: 564
Vemos el mensaje indicando que la opcion no es valida y enseguida el mensaje si deso comprar otro cafe.

Esto digamos que funciona pero no se ve bien porque en realidad no he comprado ningun cafe, entonces esta parte del switch no esta funcionando como esperamos, asi que volvamos al codigo:

Aqui despues de que escribimos una opcion invalida salidmos dle SWITCH y continuamos hasta estea linea donde preguntamos si queremos compra otro cafe, entonces en lulgar de poner el break para salir del SWITCH podemos simplemente volver a preguntar:
[
switch(eleccionDelUsuario){
	case 1:
		costoTotalDelCafe += 20;
		break;
	case 2:
		costoTotalDelCafe += 30;
		break;
	case 3:
		costoTotalDelCafe += 35;
		break;
	default:
		Console.WriteLine("Su eleccion es invalida.");
		goto Inicio;
}
]
Con esto le decimos al programa que cuando el usuario haya seleccionado un tamaño de cafe  invalido, haga un salto a la etiqueta Inicio que es donde volvemos  a preguntar que tamaño de cafe quiere comprar.

Corramos el programa otra vez:
escribo una opcion invalida 4564, presiono enter
entonces ahora veo el mensaje otra vez preguntandome que tamaño de cafe quiero:
Ahora quiero un cafe grande: 3
Quiero comprar otro cafe?
Digamos que pongo sI una mezcla de mayuculas y minusculas, presiono enter
y otra vez regresamos al inicio, selecciono el tamaño de mi cafes
otro cafe grande 3

En este caso sin importar si escribi mayusuclas y minusculas cuando escribi la palabra si el programa continuo la ejecucion como esperamos, ayora si pongo todo minusculas
si -- como vemos sigue funcionando sin problemas
quiero otro cafe grande 3
Hasta ahora he comprado 3 cafes grandes, entonces el programa esta sumando los cafes y el cafe grande cuesta 35 pesos 3*35 =  105 pesos
Hasta este punto ya termine de comprar todos los cafes que queria asi que escribire que no quiero continuar comprando
no presiono enter
y vemos el mensaje:
Gracias por comprar, total a pagar son 105 pesos, presiono enter y aqui termina la ejecucion del programa.

Este es un progra muy simple, solo estamos utilizando 2 instrucciones switchs.

Volamos a la presentacion:
[Parte 12][2] 
Next 
[Parte 12][3] 
Next 
[Parte 12][4] 
Next 
[Parte 12][5] 
En conclusion.

Si la instrucción break es utilizada dentro de un switch esto indica a C# que debe salir de la ejecución del switch, como vimos en el ejemplo.

Con la instrucción goto podemos saltar a otro case o a una etiqueta especifica.

[x]
Con goto no solo podemos saltar a etiquetas, tambien podemos saltar a otro case:

Por ejemplo si cambio esta linea y digamos que despues de ejecutar este codigo quiero ir a ejecutar el codigo dentro de case 1, solo tendira que cambiar el break por goto case 1;
[
switch(eleccionDelUsuario){
	case 1:
		costoTotalDelCafe += 20;
		break;
	case 2:
		costoTotalDelCafe += 30;
		goto case 1;
	case 3:
		costoTotalDelCafe += 35;
		break;
	default:
		Console.WriteLine("Su eleccion es invalida.");
		goto Inicio;
}
]
[Parte 12][5] 
Entonces utilziando goto podemos saltar  a una etiqueta o algun case dentro del switch...

Pero hay un detalle con goto, en realidad usarlo es una muy mala practica y debemos evitar utilizarlo, es una mala practica porque si la ejecucion del codigo se realiza saltando de una etiqueta a otra debugear este programa se puede volver muy complejo y lo que estabamos haciendo utilizando goto se puede lograr utilizando loops, un loop es un bucle osea algo que se repite.  Mas adelante cuando veamos los loos escribiremos este mismo programa utilizando while y do while, asi que si es posible reemplazar goto por algun bucle es mas conveniente hacerlo de esta menera los programas seran menos complejos de debugear.
Debug significa depurar, aqui en mexico mexicanizamos muchas palabras del ingles por eso decimos debugear pero la palabra en español es depurar.  En caso de que no tengas idea que es debugear pues es cuadno ejecutamos un programa en modo debug o modo depuracion y podemos ir viendo la ejecucion de este linea por linea, revisar que valores tienen las variables y si hay algun error lo podemos corregir.
Es como una ejecuccion paso a paso del programa donde podemos pausar la ejecucion o poner unos puntos donde queremos que el programa se detenga para asi revisar como esta funcionando el codigo.

[Parte 12][6] 

Este es todo por hoy, muchas gracias por estar aqui, y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Que tengas un excelente dia :)