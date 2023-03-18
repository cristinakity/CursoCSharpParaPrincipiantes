[Parte 10][1]
Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco, 
esta es la parte 10: Instruccion IF en C#

En C# la instruccion IF es en realidad una instruccion condicional y en C# existen 2 tipos de instrucciones condicionales:
IF y SWITCH en esta leccion hablaremos a cerca de IF en el proximo video hablaremos de SWITCH
<next>
[Parte 10][2]
En esta lección veremos:
- La instruccion IF
- IF ELSE
- Las diferencias entre double amperson && y un amperson
- Diferencias entre doble pipe || y un pipe |

vamos al ejemplo!
[x]

Para entender la instruccion if escribamos un programa simple en C#

Quiero que el usuario instrodusca un numero y vamos a decidir si esl numero es 1, 2 o tres utilizando la instruccion if, ok..

entonces, primero necesito preguntarle al usuario pro el numero y para hacer esto pondremos un mensaje en la consola:
[ Console.WriteLine("Escriba un numero: ") ] 
El usuario escribira el numero y necesitamos leer ese numero, asi que utilizaremos
[ Console.ReadLine(); ]
Y si nos fijamos readLine leera el numero pero como un string, si..
ahora, una vez que leido el numero desde la consola necesitamos assingarlo a una variable int y digamos que escribo esto en el codigo
[ int numero = Console.ReadLine() ]
pero como vemos tenemos un error de compilacion porque readLine regresara el numero introducido por el usuario, pero en formato string y el tipo de dato de la variable numero es entero..
el error es: el tipo de dato string nose puede convertir implicitaamente a int...

Si no les queda claro lo que significa la conversion implicita por favor hechenle un vistaso a la Parte 7 Converssiones de tipos de datos de este curso.

bien, entonces necesitamos convertir string a int y para hacerlo podemos llamar al metodo Parse dentro de la clase int:
[ int numero = int.Parse(Console.ReadLine()); ]
este metodo parse, tomo un string como parametro y retorna un int

Esperamos que el usuario introduzca un entero asi una vez que el usuario escribio el numero, podemos ahora comparar si el numero es igual a uno
[ if( numero == 1 ) ]
y como estamos seguros que es uno mostramos el siguiente mensaje en pantalla
[ Console.WriteLine("Tu numero es igual a uno."); ]

Hay que analizar como es que esta instruccion if funciona
-Primero necesitaremos una expresion booleana, lo cual significa que necesitamos evaluar si algo sera verdadero o falso
Si  esta expresion es verdadera... el bloque de codigo siguiente entre  corchetes sera ejecutado {} Si la instruccion es falsa entonces el codigo no sera ejecutado

Bien, corramos el ejemplo:
Esta pidiendo que escribamos un numero, escribire el 1 y presiono enter...
como vemos muestra el mensaje dento de la instruccion if porque la condicion se cumplio numero es igual a 1

Muy bien, ahora agregemos mas lineas de codigo a este programa...
evaluaremos si el numero es 2 y si el numero es 3

Entonces:
[ if (numero == 2)]
Si el numero es dos mostramos el mensaje
[ Console.WriteLine("Tu numero es igual a dos."); ]

Lo mismo para el numero 3:
[ if (numero == 3)]
Si el numero es tres mostramos el mensaje
[ Console.WriteLine("Tu numero es igual a tres."); ]

corramos el programa para probar el codigo:
"Escriba un numero"
Ahora en lugar de poner 1,2 o 3 voy a escribir 10 y si presiono enter, si estoy introducciendo un valor entero pero no me muestra ningun mensaje en pantalla.

Veamos el codigo:
entonces escribimos el numero 10 asi que la variable numero tiene el valor de 10...
Cuando el el progrmaa llega a esta linea... evalua 10 es igual a 1 es falso y no ejecuta esta parte del codigo...
Continuamos y ahora validara: 10  es igual a 2 tambien es falso omite esta parte del codigo
y por ultimo evalua 10 es igual a 3 tambien es falso y por lo tanto tampoco ejecutara esta seccion del codigo

y como ya no hay mas codigo, pues aqui finaliza la ejecucion del programa.

Entonces ahora lo que quiero que este programa haga es que si el usuario escribe algun otro numero diferentes de 1,2 y 3... muestre en pantalla un mensaje diciendo:
"Tu numero no se encuentra entre los numeros uno, dos y tres"
¿como hacemos eso?
pondremos otro if
[ if( numero != 1 && numero != 2 && numero != 3) ]
si todas estas condiciones se cumplen mostrare este mensaje en la consola:
[ Console.WriteLine("Tu numero no se encuentra entre los numeros uno, dos y tres") ]

Que va a pasar si el usuario escribe el numero 5... todas estas condiciones seran falsas
numero ==1, numero == 2 o numero ==3
 y entrara en este bloque de codigo.
Asi que se evaluara si 5 no es igual a 1 y despue si 5 no es igual  2 y lo mismo para validar si 5 no es igual a 3, todas las condiciones se cumplen, en ete if estamos evaluando multiples condiciones con el operador Y && entonces en este caso con una sola condicion que sea falsa... todo este bloque se evaluara como falso, para que esta serie de condiciones se cumplan utiliznado el operador &&... todas las condiciones deben ser evaluadas a true.

Muy bien, ahora si vemos este codigo es un codigo realmente muy simple, pero digamos que este codigo es ineficiente porque si vemos las condiciones de este if todas son excluyentes unas de otras, osea si una se cumple las otras es obvio que no se van a cumplir.. asi que si el numero es igual a 1, sabemos que numeor no puede ser 2 o 3 porque ya es uno.
Dicho esto... en este caso en lugar de utilizar if y despues otro if y otro podemos hacer uso de else if
utilizando else if este programa se hara mucho mas rapido porque con los if separados.. independientemente de que alguna condicion se cumpla... el programa evaluara todas las condiciones... y en este caso al ser mutuamente excluyentes en realidad no tenemos que evaluar las demas condicoines una vez que alguna de estas se cumpla.

entonces para agregar else if solo haremos pequeños cambios al codigo y quedara de la siguiente manera
[
if (numero == 1)
{
	..
}
]
y aqui en lugar de poner el if separado solamente agregaremos else y pondremos el if enseguida del else
[
if (numero == 1)
{
	..
}else if (numero == 2){}
]
lo miso para validar si numero es igual a tres
y la final no necesitamos validar si numero no es igual a 1 2 y tres si no que solo dejaremos el else
[ } else (dejar las condiciones aqui){ ... } ]
de este modo si no se cumple ninguna de las condiciones anteriores el programa ejecutara solo esta parte del codigo

y que va a pasar aqqui... pues si numero es igual a uno, osea si esta condicion es verdadero... ejecutara esta parte del codigo y el resto nisiquiera sera evaluado.

si todos estos if son falsos... pues entonces el ultimo else ya no necesitamos evaluar que numero no sea igual a 1 2 y 3 porque si ninguna de las demas condiciones se cumple significa que numero no es ni 1, ni dos ni tres... entonces al final solo validamos si no es ninguno de estos numeros por lo tanto no necesitamos estas condiciones aqui en el else porque el else ya engloba estas validaciones.

Bien.. si corremos este programa funcionara exactamente igual que el anterior, solo que el codigo es mas eficiente
 [ run program ]
digamos por ejemplo que pongo 5 enter y vemos la respuesta esperada que esta en el else final del codigo

Ok, este es el if simple donde solo validamos si se cumple esta condicion ejecuta este bloque de codigo y tambien tenemos if -- else if  y else al final tambien.

En los if simples podemos tener multiples condiciones separadas por && 
Por ejemplo digmaos que quiero que el usuario ingrese un numero y si el numero es 10 o 20 quiero que muestre un mensaje en pantalla indicando que el numero es 10 o 20
¿Como hacemos esto?
Si el numero es igual a 10 o igual a 20... esta es una condicion OR.
[ if (numero == 10 || numero == 20)]
Si tenemos varias expresiones booleanas separadas por OR en este caso cuando cualquier condicion sea verdadera el la condicion en el if sera evaluada como verdadero y por lo tanto el boque de codigo que despues del if sera ejecutado.

Asi que mostraremos el mensaje:
[ Console.WriteLine("El numero es diez o veinte."); ]

[else 
{

}]
Si no.. podriamos poner cualquier otro mensaje que queramos en la condicion else 

Entonces si esta condicion se cumple.. esta seccion del codigo sera ejecuta si no esta otra parte del codigo.

Por otro lado tambien tenemos or pero con un solo pipe |
[ if (numero == 10 | numero == 20)]

al igual con el operador y -and tenemos && doble amperson y un solo amperson
y cual es la diferencia entre estos dos operadores

de las dos formas con  || o | pipe si la condicion se cumple se ejecuta esta parte del codigo, pero la diferencia es  
que cuando tenemos  || si la primer condicion se cumple ya no evaluara las demas condiciones, porque con OR si una condicion es verdadera toda la expresion sera verdadera.

y con un solo pipe... aun i la primer condicion es verdadera.. runtime seguira evaluando las demas condiciones 

Entonces si es un solo pipe ira a validar todas las condiciones siempre y si tienemos doble pipe con la primer condicion que encuentre verdadera alli dejara de evaluar el resto de condiciones y el if sera verdadero.
Asi que obviamente || sera mas rapido en casi todos los escenarios sobre todo donde alguna condicion verdadera este antes que otras condiciones la recomendacion es simpere utilizar doble pipe por esto mismo.

Y muy similar para && y &
si cambiamos la condicion
[ if (numero == 10 && numero == 20)]
para que este codigo se ejecute.... ambas condiciones deben ser verdadera, asi que en este caso && dejara de revisar el codigo en cuanto encuentre la primer condicion evaluda a falso y mandara la ejecucion al else directamente.

Asi que si esta condicion es false [numero == 10] no tiene sentido revisar la otra condicion ya sabemos que el if ser evaluado como false.

entonces && detendra la evaluacion de la expresion dentro del if si la primer condicion es falsa y el if sera evaluado como false
un solo amperson evaluara todas las condiciones dentro del if sin importar que la primer condicion sea falso.

[parte 10][3]

&& y || son conocidos como operadores de cortocircuito porque detienen la evaluacion una vez que encuentran una condicion logica que de lugar a omitir las demas condiciones en caso de  || con el primer true que encuentre el resto de la expresion no se evalua... y en el caos del  && con el primer false que encuentre el resto de la expresion no sera evaluada...
por esto se conocen como operadores de cortocircuito

[parte 10][2]
En conclusion tenemos:
 - If simpe, si la condicion se cumple ejecuta este bloque de codigo
 - If elses, cuando tenemos validaciones mutuamente excluyentes y queremos evaluar una condicion despue de otra sin que se ejecuten muchos if simples independientes.
  y tambien vimos las diferencias entres doble y un ampersons asi  como las diferencias entre doble y un solo pipe
 
[Parte 10][4] 
Esto es todo por hoy.  
Muchas gracias por ver este video, y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Que tengas un excelente dia :)