[Part 5][1]
Hola bienvenidos a Pragim Technologies mi nombre es Cristina Carrasco, 
esta es la parte 5: Operadores comunes en C#

Como en cualquier otro lenguaje de programacion C# tambien tiene operadores comunes
<next>
[Part 5][2]
Y podemos clasificar estos operadores en:
	- De asignacion o igualdad
	- Aritmeticos
	- De Comparacion
	- Condicionales
	- Ternario
	- Y De uso combinado de NULL
	
Entonces el operador de asignacion en C# el signo igual (=), y similarmente tenemos operadores los aritmeticos que son el signo de suma, de resta, multiplicacion, etc.

Veamos un ejemplo simple de como usar estos operadores. 

[x]

Tenemos un programa simple aqui,
<escribir int i>
por ejemplo si creamos una variable de tipo entero y queremos iniciarlizarla (osea asignarle un valor al momento de crearla) con un valor de 10, puedo utilizar el operador de asignacion o igualdad
<escribir = 10; >
Igual que en C o C++ la forma de asingarle una valor a una vairable en C# es utilizando el operador de asignacion o igualdad el simbolo =
y podemos utilziar el signo igual para asingarle valor a cualquier tipo de varible por ejemplo si quiero asignarle un valor a una variable booleana:
bool b = true;

[Part 5][2]
Como vimos el signo igual es el operador de asignacion o igualdad en C#

Tambien tenemos algunos operadores arimeticos en C# como el suma, de resta y como el nombre lo indica esa es la operacion que realizan.

Por ejemplo si queremos sumar dos numero tendremos que utilizar el simbolo de mas o suma, y muy similar para una resta utilizaremos el simbolo de menos o de resta

Tambien existen estos dos operadores
</, %>
si tenemos que dividir dos numeros y como sabran al dividor dos numeros tenemos dos resutlados uno es cociente y el otro es el residuo o el resto

Si divido 10/2 obtendre 5 como cociente y 0 como residuo

Dependiendo de que operador utilizemos, si utilizamos / (diagonal) obtendremos el cociente que es 5 en el ejemplo que mencione

Y si utilizamos % porcentaje obtendremos el residuo de la division que era zero en el ejemplo de dividir 10/2

Vamos hacer un ejemplo simple de esto
[x]

Por ejemplo si tengo un numerador
<int numerador = 10;>
y un denomindaor
<int denominador = 2>

<int resultado = numerador 
Y utilizo la diagonal
/ denominador;>

y al utilziar la / obtendremos el cociente y no el residuo

Entonces si muestro en pantalla este resultado
<Console.WriteLine(
Y utilizaremos string interpolation para mostrar el resultado
"Resultado = {resultado}");>

entonces si corremos este programa, veremos que si dividimos 10 / 2 obtendremos 5 como cociente

Si queremos el cociente hay que utilizar el signo diagonal que seria el signo de division

Por otro lado si lo que queremos es el residuo, solo cambiamos el signo / (diagonal) por % (porcentaje)
<cambiar el signo en el codigo>
<correr el programa>
Esto nos dara el residuo o resto de la division, el residuo de 10 / 2 es 0, entonces utilizaremos el signo % porcentaje para obtener el residuo,

[Part 5][2]
Entonces estos son 4 operadores aritmeticos muy simples, los mismos utilizados en otros lenguajes de programacion, + para sumar, - para restar, / (digaonal) para dividir y obtener el cociente,  % para dividir y obtener el residuo.

[3:50]
Los operadores de comparacion, ya vimos el signo de igual que sirve para asignar valores, pero si queremos comparar dos valores entonces tendremos que utilziar el dos signos de igual

[x][4:00]
Por ejemplo:

Digamos que tengo:

int numero = 10;

Si quiero validar en mi programa si numero es giual a 10
entonces tengo que escribir lo siguiente:
if (number = 10)
{
}

Si vemos tenemos un error porque = es solo para asignar valores no para comparar, para esto tendriamos que usar  ==
entonces si estamos utilziando == entonces etamos comparando valores no asignando un valor.

En este ejemplo estamos validando que numero sea igual a 10, pero si quisieramos validar que el numero no sea igual a 10, o que sea diferente de 10, podemos hacerlo con el signo de admiracion y el signo de igualacion, != esto siginficia diferente de, o no igual a 

y esta expresion 
<seleccionar valores entre parentesis>
siempre regresaran un valor booleano, falso o verdadero.

En este caso regresaria un false porque el numero es 10 y estoy validando si numero es difernete de 10

[Parte 5][02]
Entonces utilizarmos == para comparar dos valores y saber si son iguales, y != para saber si estos dos valores son diferentes.

Muy similar a esta comparacion tenemos 
> mayor que
>= mayor igual que
< Menor que
y
<= menor igual que

Esto es muy similar a cualquier otro lenguaje de programcion, como C, C++ o Java


Y otro operadores muy importantes que tenemos en C# son los operadores Condicionales:
AND
y
OR
Basicamente si tengo que validar dos condiciones  entonces puedo utilizar el operador AND &&  

Y si solo una de las condiciones se debe cumplir entonces debo utilizar el operador OR (o)

Vamos a ver un ejemplo de esto
[x]
Digamos que tengo la variable Numero
y tambien tengo OtroNumero 

int numero = 10;
int otroNumero = 20;

Ahora si quiero que numero tenga que ser 10 y que OtroNuemro tenga que valer 20, tendira que cambiar un poco la condicion para agregar ambas validaciones:

if (numero == 10 && otroNumero == 20)

En este caso ambias condicioneds se deben cumplir para que esta seccion de codigo se ejecute, de otra manera culaquier codigo que este aqui dentro dle if, no sera ejecutado.

Console.WriteLine("¡Condiciones cumplidas!");

Si corremos el programa  vemos que las condicoines fueron cumplidas, pero si cambiamos otroNumero a 21

y ejecutamos el codigo otra vez, entonces no se cumplen las condiciones por lo tanto el mensaje no sera mostrado en la consola.

Pero si cambiamos el operador, en lugar de que sea AND, lo cambio por un OR, 

el operador OR es el simbolo de barra vertical o Pipe |, en este caso con OR validamos que cualquiera de las condiciones sea cumplida.
En este caso llega a la primer condicion y numero es igual a  10 por lo tanto la segunda condicion no sera evaludada, solo la primera porque tenemos un OR y para OR solo debe cupmlirse una condicion y con esto ejecutara el codigo dentro del if,

Si corremos el codigo otravez veremos que las condiciones se cumplen.


[Parte 5][02]
Bien entonces los operadores condicionales AND y OR..
Si esto Y esto otro se cupmle... En este caso todas las condiciones deben ser cumplidas.

Si esto O esto otro se cumple... Solo una de las condiciones se tiene que cumplir.

Bien, el siguietne operador del que hablaremos es el operador ternario, que es un operador muy interesante.  

[x]
Hagamos un ejemplo simple para entender este operador ternario, 
Dejemos int numero = 10,
y lo que quiero hacer es crear otra variable digamos:
bool numeroVale10;

ahora 

if(numero == 10 ) {
Entonces quiero que esta variable sea verdadera
	numeroVale10 = true;
Si no quiero que esta varaible sea falsa
}else {
	numeroVale10 = false;
}

Si vemos este codigo: estamos utilziando  el operador de comparacion == y tambien el operador de asigacion =,

y depsues de esto quiero que el codigo muestre un mensaje en pantalla
Console.WriteLine($"Es Numero == 10 - {numeroVale10}")

Si vemos este es un programa muy simple, solo estamos creando una varialbe de tipo entero, asignandole el valor de 10 y aca validamos si numero es igual a 10 entonces asignale el valor verdadero a esta otra variable numeroVale10, si no asignale valor de falso. Y al final mostramos un mensaje en pantalal con esta informacion.

<Correr el ejemplo con Numero = 10>
<correr el ejemplo con Numero = 15>

Ok, entonces veamos este codigo, solo para validar si este numero es 10 o no tenemos varias lineas de codigo, pero podriamos utilizar el operador ternario en lugar de todo este codigo, osea que todo esto puede ser creado en una sola linea,
.. si vemos estas 1,2,3,4,5 lineas de codigo pueden en realidad ser reemplazadas por una sola linea si sabemos como utilizar el operador ternario.

Veamos como funciona este operador:

bool  NumperoVale10 = numero == 10 ? true : false;

y podemos elminar todas esta lineas, si vemos esto son solo 3 lineas de codigo.  

Que fue lo que hicimos:
Declaramos una variables de tipo boolean para almancenar el resutlado del operador ternario, entonces si esta expresion se cumple, regresamos true, si no regresamos false,

Lo que siga desues del sigo de interrogacion es la parte verdadera o que se cumple y  lo que sigue despues de los dos puntos es la parte que no se cumple o falsa.. y ese valor sera alamacenado en esta varaible.
Si correos el programa deberiamos ver el misom resultado que con el codigo anterior, con la unica diferencai que ahora estamos utilziando el operador ternario
<Correr el programa>


[Parte 5][02]
 y este es el operador ternario, me gustaria agregar una cosa es que a este operador
Yo siempre lo he visto como un IF de una linea, osea hace lo mismo que un if pero en una sola linea.

El siguiente operador: De uso combinado de NULL.. hablaremos de este en la siguiente leccion donde tambien hablaremos de tipos de datos nuleables en C#, asi que necesitamos entender los tipos de datos nuleables antes de hablar del operador de uso combinado de null.


[Parte 5][03]
Como vimos en el ejemplo, si no utilizamos el operador ternario tendriamos muchas lineas de codigo,
<next>
[Parte 5][04]
Pero con el operador ternario el tamaño del programa es relativamente mas pequeño osea que tendremos unas pocas lineas de codigo

 <next>
[Part 5][05] 
Esto es todo por hoy, para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Gracias por estar aqui que  tenga un dia genial :)


