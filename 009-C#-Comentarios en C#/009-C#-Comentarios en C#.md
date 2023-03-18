[Parte 9][1]
Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco, 
esta es la parte 9: Comentarios en C#
<next>
[Parte 9][2]
En esta lección veremos:
- Comentarios de una sola linea
- Comentarios de multiples lineas
- Introduccion a los comentarios XML de documentacion

Hay mucho que aprender sobre los comentarios XML para la documentacion, de los cuales hablaremos en proximas lecciones.

[Parte 9][3] 
Entonces que son los comentarios en general, 
Los comentarios basicamente son utilizados para documentar que hace nuestro programa.

Por ejemplos: Si hay una parte del codigo algo compleja y queremos que otros programadores sepan que es lo que esa parte especifica de codigo hace..
podemos simplemente comentar ese bloque o lineas de codigo.

Y hablando de comentarios en C# existen 3 formas de agregar comentarios a nuestro codigo :
 - Podemos comentar una linea en especifico
 utilizando doble diagonal invertida
 - O podemos comentar multiples lineas utilziando diagonal invertida astericos para iniciar apartir de esta linea y asterisco diagonal invertida para indicar la linea final de los comentarios.
 
 <veamos un ejemplo >
 Digamos que tengo un codigo como este:
  
 Console.WriteLine("Hello"); 
 Console.WriteLine("Hello");
 Console.WriteLine("Hello");
 ]
 Y puedo comentar la primer linea,  utilizando la sintaxis para comentarios de una sola linea:
 [
 //Console.WriteLine("Hello"); 
 Console.WriteLine("Hello");
 Console.WriteLine("Hello");
 ]
 y cuando corramos este programa, esa linea sera ignorada por el compilador..
 [ Seleccionar codigo: 
 //Console.WriteLine("Hello");  
 ]  Este es el comentario de una linea
 y tabien podemos comentar las siguientes dos lineas:
  [
 //Console.WriteLine("Hello"); 
 //Console.WriteLine("Hello");
 //Console.WriteLine("Hello");
 ]
 Pero si queremos comentar todas estas lineas en lugar de utilizar comentarios de una sola linea podemos hacer uso de los comentarios multilineas
 Diagonal invertida y asterisco para el inicio del comentario
  [
 /*Console.WriteLine("Hello"); 
 Console.WriteLine("Hello");
 Console.WriteLine("Hello");
 ]
 y para finalizar el comentario asterisco y diagonal invertida
  [
 /*Console.WriteLine("Hello"); 
 Console.WriteLine("Hello");
 Console.WriteLine("Hello");*/
 ]
 Este bloque entero de codigo sera tratado como un comentario y por lo tanto sera ignorado por el compilador
 
 Muy bien, entonces dependiendo de la situacion necesitaremos comentar multiples lineas si queremos agregar un comentario ms grande o comentar un bloque completo de codigo o 
 podemos simplemente comentar una sola linea.
 
 Algo importante sobre los comentarios de codigo:
 No comenten cada linea de codigo que creen esa no es la manera digamos optima o de seguir las mejores practicas de programacion al momento de crear sistemas...
 de hecho es una mala practica, llenar todo de comentarios o escribir comentarios obvios.
 Lo recomendable es... si creemos que una parte parciular del codigo es muy compleja o digamos que no se explica por si misma, en este caso si es una buena practica poner un comentario que nos explique de manera sencilla que hace el codigo, de otra manera si el codigo es muy simple pues estariamos agregan un comentario innecesario o sin sentido.
 
 Por ejemplo si tengo el siguiente codigo:
 string ciudad igual a Mexico
 [ string ciudad = "Mexico"; ]
 y tenemos una validacion aqui:
 [if (ciudad == "Mexico") ]
 Y queremos tal vez mostar un mensaje en pantalla 
 [if (ciudad == "Mexico")
 {
	Console.WriteLine($"Ciudad seleccionada: {ciudad}")
 }
 ]
 Si alguien pone un comentario aqui: 
 [
 // Si la ciudad es Mexico
 if (ciudad == "Mexico")
 {
	Console.WriteLine($"Ciudad seleccionada: {ciudad}")
 }
 ]
 No es necesario hacer esto porque el If por si solo nos dice que esta haciendo,
 dicho con otras palabras: Si el codigo se explica por si solo es una clara señal de que no hay necesidad de agregar un comentario explicando el codigo...
 Y es esto el porque de la recomendacion de utilizar comentarios solo si el codigo es algo complejo de entender a simple vista.
 Y en codigos como este:
 [
 // Si la ciudad es Mexico
 if (ciudad == "Mexico")
 {
	Console.WriteLine($"Ciudad seleccionada: {ciudad}")
 }
 ]
 No es necesario crear este tipo de comentarios porque solo es perdida de tiempo.
 
 Ok... ASi que basicamente hay dos manera de comentar codigo:
 1 - Una es utilizando el boton del menu para comentar lineas:
 Si quiero comentar esta linea, primero la selecciono  o me posiciono en la linea
 [ string city = "Mexico"; ]
 y despues presiono el boton del menu: 
 [//string city = "Mexico"; ]
 esto agreagara automaticamente las diagonales invertidas 
 y si queremos descomentar la linea podemos hacer uso tambien del bonton para descomentar:
 [string city = "Mexico"; ]
 
 En caso que los botones no aparezcan aqui en en la barra de menu, podemos acceder a ellos de varias maneras:
 En el menu Editar > Avanzadas   y aqui podemos ver las dos opcioe spara comentear y descomentar el codigo...
 
 Otra forma de acceder a estos botones en caso que no se aparezcan aqui en la barra de herramientas es accediendo al menu: Ver > barra de herramientas > Editor de texto..
 En este caso esta visible asi que tiene la palomita de que esta seleccionada, pero si la removemos se quitaran los botones de la barra, en caos que nos pase esto solo hay que segurarnos de que este seleccionada la barra de herramientas editor de texto del menu barra de herramietnas que esta en el menu ver.
 Y en caso de que si este seleccionada la barra pero aun asi no se vean los botones puede ser porque los botones fueron removidos al modificar las opciones de la barra, para eso hay que darle click a este boton y abrir el menu agregar o quitar botones y aqui se ven seleccionados los botones para los comentarios y tambien otros que se estan visualizando actualmente en la barra.
 
 2 - Y la segunda manera es presionando la combinacion de teclas para agregar comentarios:
 Si ponemos el mouse encima del boton podremos ver cuales son las teclas de acceso directo en este caso para comentar son:
  (control + k)  <-- esto deja al IDE esperando por la segunda combinacion de teclas... 
  si vemos parte de abajo aqui donde tenemos esta barar de estatus al precionar control + k, aparece un mensaje indicando que Visual Studio esta esperando por la segunda combinacion de teclas
  despues presionamos:
  (control + c) y con esto se comentara la linea o el bloque de codigo seleccionado o en todo caso si no fue seleccionado nada se comentara toda la linea en donde  se encuentre el cursor actualmente.
[Parte 9][3] 
Si volvemos al adiapositiva podemos ver los accesos rapidos del teclado:
Ctrl+k, ctrl+c  <--- para comentar
y
Ctrl+k, ctrl+u  <--- para descomentar
Y hay que recordar que:
No debemos comentar cada línea de código.  Debemos escribir comentarios solo para los bloques de código que son difíciles de entender.

[ x ]
Y acerca de los comentarios de documentacion o los comentarios XML, solo les dare una breve introduccion en este momento, pero hablaremos de ellos en proximas lecciones.

Muy bien entonces digamos que quiero hacer uso de la clase
 [Console]
 y en el momento en que escribo Console y si pongo el mouse encima, vemos que el intellisense nos muestra una informacion sobre esta clase... 
 lo que dice aqui es para que sirve esta clase, si vemos el mensaje nos esta indicando que esta clase:
 "Representa los flujos de entrada, salida  y error estandar para las aplicaciones de consola."
 Y.. ¿de dónde viene esta informacion?
 Si vamos a ver la definicion de esta clase, dando click dereco > Ir a definicion o precionando F12...
 Esto en realidad viene del Assembly o la Dll dentro del framework donde se encuentra la clase Console... 
 Similar mente nosotros podemos crear nuestra propias clases:
 Asi que creemos por ejemplo una clase...
 Hablaremos de clases a detalle en proximas lecciones asi que por ahora solo creemos una clase simple, sin preocuparnos por los conceptos de clase:
 [
 publc class ClaseDeEjemplo
 {
 }
 ]
 No hay que preocuparnos del contenido de esta clase... 
 Dejenme crear una instancia de esta clase:
 [
 static void Main()
 {
	ClaseDeEjemplo
 }
 ]
 y miren cuando pongo el mouse encima de la case... no hay ningun mensaje, hay una informacion, pero pareciera incompleta, no es como el mensaje de la clase Console...
 El Intelisense no me esta mostrando para que sirve esta clase... porque no hemos agregado esa informacion la clase, y para hacerlo necesitaremos crear los comentarios de documentacion o comentarios XML.
 Y la manera como podemos saber para que sirve esta clase... es utilizando los comentairos de documetacion XML..
 Y si volvemos a la diapositiva:
 
[Parte 9][3] 
Podemos ver que triple diagonal es lo que demos utilizar para agregar estos comentarios:

[x]
Entonces volviendo al codigo lo unico que tenemos que hacer es teclear las 3 diagonales invertidas encima del nombre de la clase:
[
///
public class ClaseDeEjemplo 
{
}
]
Y automaticamente agrego unos tags o elementos XML:
[
/// <summary>
/// 
/// </summary>
public class ClaseDeEjemplo 
{
}
]
summary tags que en español significa algo como resumen o sumario, en pocas palabras seria una breve explicacion o documentacion de para que sirve la clase.
 
[
/// <summary>
/// Esta es una clase de ejemplo con un comentario de documentacion XML de ejemplo.
/// </summary>
public class ClaseDeEjemplo 
{
}
]
Y ahora si vuelvo aponer el mouse encima de la clase:
[
static void Main()
{
	ClaseDeEjemplo
}
]
Podre ver que el contenido del Intellisense ha cambiado, mostrando la informacion o la documentacion que acabmos de escribir dentro de los tags de Summary en la Clase de Ejemplo y esto es parte de lo que podemos hacer con los comentarios XML o comentarios de documentacion en .NET

[Parte 9][3] 
Entonces resumiendo en C# hay tres formas de comentarios:
 1 - una sola linea...
	que se crea agreagando doble diagonal invertida, son utiles cuando queremos comentar como el nombre lo indica una sola linea de codigo
 2 -tambien tenemos los comentarios multi linea. que se crean agreagndo /* al inicio y */ al final de el bloque de codigo que queramos comentar, dependiendo de la circunstancia sera el tipo de comentario que agregemos al codigo 
 3 - Y la tercer manera de agregar comentarios o mas bien documentacion a nuestros programas es utilizando la triple diagonal invertida para crear comentarios XML o comentarios de documentacion.
 
[Parte 9][4] 
Muchas gracias por ver este video, y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Que tengas un excelente dia :)