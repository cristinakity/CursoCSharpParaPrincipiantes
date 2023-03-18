[Parte 013][1]
Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco, 
esta es la parte 13: Ciclos en C#
<next>
[Parte 013][2]
En esta lección hablaremos acerca del ciclo while

en C# hay 4 diferentes tipos de ciclos while, do, for, foreach

En proximas lecciones hablaremos de los demas ciclos, en esta lecciones solo veremos el ciclo while, asi que veamos un ejemplo

[notepad]
Haremos un pequeño programa que le solicite al usuario un numero, el cual sera el numero final o numero limite que mostraremos en pantalla:

[
Mostrar numeros pares hasta llegar al numero:
10
0 2 4 6 8 10
]

Entonces le pediremos al usuario que escriba el numero limite, 
"mostrar numeros pares hasta llegar al numero" y si el usuario ingresa el nuemro 10, 
el programa debera mostrar en pantalla: cero, dos, cuatro, seis, ocho y diez.

Muy bien,entonces escribamos el programa
[x]
Queremos preguntarle al usuario el numero limite:
[
Console.WriteLine("Mostrar numeros pares hasta llegar al numero:");
int numeroLimite = int.Parse(Console.ReadLine());
]

ya tenemos el nuemro limite ahora necesitamos mostrar esos numero en pantalla, iniciando con el cero hasta el numero que el usuario ingreso, osea hasta el limite

Entonces voy a crear una variable con el numero inicial:
[
int inicio = 0;
]

Y para el while pondremos:
[
while(inicio <= numeroLimite){
	
}
]

Que necesitamos hacer dentro del while, mostrar los numeros pares en pantalla:
[
while(inicio <= numeroLimite){
  Console.WriteLine(inicio);
	
}
]

Y despues necesitamos incrementar inicio mas 2, de este modo iremos obteniendo los numeros pares.
[
while(inicio <= numeroLimite){
	Console.WriteLine(inicio);
	inicio = inicio + 2;
}
]

Que esta pasando con este codigo:
	Primero tenemos la condicion while... y dentro de los parentesis una expresion booleana, si esa expresion es verdadera el codigo dentro del while se seguira ejecutando y solo se dentra esta ejecucion hasta que la expresion sea falsa.
	
	Entonces primero se evalua si inicio que vale cero es menor o igual qeu numero limite, si nuemro limite fue 10, le validacion seria si 0 es menor o igual que 10... esta expresion si se cumple, entonces muestra el valor de inicio y despues sumale 2, entonces ahora inicio vale 0 +2  = 2, y otra vez se evalua si inicio que ahora vale 2 es menor o igual que  10, es verdadero porque 2 es menor o igual que 10, y asi continua el cliclo hasta que inicio valga 10, cuando inicio vale 10 se evalua 10 es menor o igual que 10, verdadero se muestra 10 en pantalla y despues se suma 10 +2 y ahora inicio vale 12, en este caso la concion sera falsa porque 12 no es menor o igual a 10 y aqui es donde la ejecucion del while terminara y el codigo seguira su ejecucion despues del while.
	
Entonces corramos este progrma control+f5
	
Escribimos el numero limite:
10

vemos el resultado en pantalla, bien..

Ahora veamos que pasa si se me olvido sumarle dos a la variable inicio:
[
while(inicio <= numeroLimite){
	Console.WriteLine(inicio);
	//inicio = inicio + 2;
}
]

Si no tenemos esa linea de codigo la variable inicio siempre sera cero y cero siempre sera menor o igual a 10 por lo tanto esa condicion siempre sera verdadera y nunca saldra del while.

Antes de correr este programa vamos abrir task manager y asi les puedo mostrar el procesador.

El procesador actualmente esta trabajando a [Revisar porcentaje ne la maquina]

Bien, corramos este programa:
Nos muestra le mensaje para escribir el numero limite, escribamos el numero 
10

y lo que esta haciendo es imprimir un monton de ceros.
y veamos como el uso del procesador se incrementa, esto proque el programa tiene un ciclo que nunca termina porque inicio siempre vale cero y cero siempre sera menor o igual que 10, 

Cerremos el programa y veamos como el uso del procesador baja automatica.

Por esta razon es muy importante que tengamos esa condicion y asegurarlos que el ciclo while no sera infinito.
[
while(inicio <= numeroLimite){
	Console.WriteLine(inicio);
	inicio = inicio + 2;
}
]

Bueno, y debemos tener dentro de los ciclos while alguna forma de que la condicion del while se convierta en false en un determinado momento de la ejecucion y con esto evitar un ciclo while SIN FIN.


Si vemos el resultado que mostramos en pantalla, cada valor se muestra en una linea nueva, pero yo quiero ver el resultado uno despues de otro en la misma linea.

Vamos a correr el ejemplo:
ctrl+f5
el limite de 10
y vemos que se muestra 0 y en la siguiente line al el numero 2, pero yo quiero que se muestren todos los numero en la misma linea para eso solo cambio WriteLine por Write:
[
while(inicio <= numeroLimite){
	Console.Write($"{inicio} ");
	inicio = inicio + 2;
}
]

Corremos otra vez el programa y como vemos ahora el resultado se muestra como esperamos.


En esta lecciones hemos visto como utilizar ciclo while para mostrar la lista de numeros pares.

[Parte 13][2]
En la proxima leccion hablaremos a cerca de Do.. While

[Parte 13][3]
Revisemos el While loop:
Como vemos el ciclo while primero valida la condicion y si esta es verdadera entonces ejecuta el codigo dentro del while, y seguira la ejecucion siempre que la condicion sea verdadera, cuando la condicion sea falsa la ejecucion del ciclo while terminara.

Y es muy importante cambiar la variable dentro de la condicion para que el while tenga un fin, de lo contraria el codigo seguira ejecutandose en un ciclo infinito y eso no es bueno para ningun programa, ni para el procesador de la computadora.

[Parte 13][4]
En la proxima leccion hablaremos del ciclo do.. while

[Parte 13][5]
Y despues veremos las diferencias entre ciclo while y do...while
Y despues veremos las diferencias entre ciclo while y do...while

[Parte 13][6] 
Eso es todo por hoy muchas gracias por ver este video, y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Que tengas un excelente dia :)