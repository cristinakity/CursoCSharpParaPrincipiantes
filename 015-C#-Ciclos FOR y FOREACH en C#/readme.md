# Contenido

[TOC]

# Parte 15 – Cicos for y foreach en C#

## [Parte 15][1]

Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco,
esta es la parte 15: Ciclos `for` y `foreach` en C#

## [Parte 15][2]

En esa leccion hablaremos  del ciclo `for` y `foreach`,
en la parte 13 vimos el ciclo while
y en la parte 14 vimos el ciclo do..while

## [Parte 15][3]-01

Veamos un ejemplo del ciclo `for` para entenderlo mejor

### [vs]-01

Para esto voy a crear un arreglo de enteros, si los arreglos son algo nuevo para ti por favor revisa la [parte 8 - Arreglos en C#](https://www.youtube.com/watch?v=0XQXwSd56AY) de este tutorial.

```csharp
    int[] numeros = new int[3];//arreglo entero de tamaño 3

    //le voy agregar tres valores
    numeros[0] = 101;
    numeros[1] = 102;
    numeros[2] = 103;
```

Muy bien hemos inicializado el arreglo con los valores 101,102 y 103
Si quisiera mostrar en pantalla todos los valores que hay en el arreglo puedo hacer uso de un ciclo ya sea el while, do.. while o ciclo `for`.

Para poner en contraste las diferencia entre los ciclos hagamos un ciclo while primero y despues hagamos lo mismo con el un ciclo `for`

Para mostrar los datos del arreglo utilizando un ciclo while:

```csharp
   //creare una variable de tipo entero
   int i = 0;//la cual sera el contador para el ciclo
   while(i < number.Length)//y si vemos la longitus del arreglo es 3,0 < 3 = true
   {
       //si se cumple la condicion imprimimos el valor del arreglo
       Console.WriteLine(numero[i]);
       //y despues necesito incrementar el contador i
       i++;
   }
```

### [Run]-01

> Bien, si corremos el codigo veremos  el resultado:>
> 101
> 102
> 103

Veamos el codigo que esta pasando, primero cree un contador para llevar la cuenta de en que posicion del arreglo vamos, entonces en la condicion del while se valida el contador que vale cero es menor que el total de elementos en el arreglo, asi que cero es menor que tres... si verdadero por lo tanto se ejecuta el codigo dentro del while, osea se muestra en pantalla el primer valor y despues se incrementa el contador en 1, ahora estaremos en la posicion 0+1 = 1, posicion 1 del arreglo la cual contiene el valor 101 y en la proximoa vuelta del ciclo la validacion cera es 1 menor que 3 = si, asi que otra vez imprimimos en pantalla el valor de numeros en la posicion del contador, numeros[1] el cual contiene el valor 102,
despues se incrementa nuevamente el contador ahora va tener valor de 2, y cuando llega a la validacion del while pregunta 2 es menor que 3, si se cumple la condicion, imprime numeros en la posicion 2, el cual contiene el valor 103, se incrementa el contador una ultima vez y cuando llega a la condicion del while validamos ahora 3 < 3 es falso y termina la ejecucion del ciclo. Y asi es como obtenemos este resultado en pantalla.

### [vs]-02

Si miramos al ciclo while..
veremos que aqui estamos inicializando la variable i que nos sirve de contador.
En esta otra parte estamos validando la condicion para que se ejecute el ciclo
Y en esta parte al final estamos incrementando el contador de 1 en 1
Entonces inicializar, validar la condicion he incrementar el valor todo esto se hace en diferentes partes del codigo par aun ciclo while.

Bien, entonces veamos el ejemplo si hacemos lo mismo pero con con un ciclo `for`

```csharp
   for(int j = 0; j < numeros.Lenght; j++)
   {
       Console.WriteLine(numero[j]);
   }
```

Si vemos este ciclo `for`:
Estamos haciendo la inicializacion aqui... validando la condicion aqui en seguida he incrementando el contador justo despues de la validacion, todo en la misma linea.

Se ve un poco diferente que el ciclo while, pero los fundamentos del ciclo son basicamente los mismos: en ambos necesitamos una variable o contador, evaluar una condicion he ir incrementando el contador, en el ciclo while se hace todo essto en diferentes partes del codigo y en el ciclo `for` se hace todo en la misma seccion del codigo.

Ahora si vamos y corremos el programa, tendrimos que ver impresos los mismos resultados dos veces, estamos iterando el arreglo dos veces con diferentes ciclos cada vez.

### [Run]-02

> Bien, si corremos el codigo veremos  el resultado:
> 101
> 102
> 103
> 101
> 102
> 103

## [Parte 15][3]-02

En el ciclo while inicializamos, validamos la condicion he incrementamos el contador en diferentes secciones del codigo; mientras que en el ciclo `for` hacemos todo eso en la misma seccion del codigo.

### [vs]-03

Bien ahora veamos como hacer lo mismo utilizando un ciclo `foreach`

```csharp
   foreach(
```

Basicamente `foreach` es utilizado para iterar colecciones de datos
por ejemplo si tengo una coleccion de numeros, de strings,
o una coleccion de DateTimes, basicamente cualquier coleccion de datos
Osea si tenemos una coleccion de algo, podemos utilizar un ciclo `foreach` para iterar sus datos

Al utilizar `foreach` no existe la posibildiad de obtener errores como:
valor fuera del indece,index outofrange exception
Por no tenmos que escribir el indice nosotros ni saber cuando elementos existen dentro de la coleccion.

Por ejemplo si tuviera que iterar los datos con un ciclo `for`, si tuviera que iterar la coleccion de datos numeros, recordemos que numeros es un arreglo de enteros lo cual lo convierte en una coleccion de datos enteros
Si tengo que iterar estos datos con un ciclo `for`, tengo que saber cuantos elementos contiene esta coleccion, de lo contario podria ser que me pase del total de datos en el arreglo y de este modo tendre una excepcion o un error en el codigo, un index out of range exception, o en español indice fuera del rango.

Y esta es la ventaja de utilizar `foreach`, no existe la posibilidad de este error ya que el ciclo `foreach` ya sabe hasta cuando tiene que seguir iterando los elementos de la coleccion.

Explicado esto veamo como crear un ciclo `foreach`:

```csharp
   foreach(int numero in numeros)
   {
       Console.WriteLine(numero);
   }
```

Que va a pasar en este codigo, `foreach` va a iterar cada uno de los elementos de la coleccion y uno por uno va ir asignado el valor en la variable declarada en el `foreach`, en cada vuelta numero va estar cambiando el valor al valor del siguiente elemento del ciclo.

Bien entonces si correo el codigo otra vez ahora obtenedre los valores del arreglo numeros o de la coleccion de enteros numeros, impresos en pantalla igual que los otros ciclos, comentemos los otros ciclos para ver el resultado

```csharp
   foreach(int numero in numeros)
   {
       Console.WriteLine(numero);
   }

   //for(int j = 0; j < numeros.Lenght; j++)
   //{
   //    Console.WriteLine(numero[j]);
   //}
   
   //int i = 0;//la cual sera el contador para el ciclo
   //while(i < number.Length)//y si vemos la longitus del arreglo es 3,0 < 3 = true
   //{
   //    //si se cumple la condicion imprimimos el valor del arreglo
   //    Console.WriteLine(numero[i]);
   //    //y despues necesito incrementar el contador i
   //    i++;
   //}
```

### [Run]-03

> Bien, si corremos el codigo veremos  el resultado:
> 101
> 102
> 103

### [Vs]-03

Muy facil iterar con un ciclo `foreach` y evitar salirnos del indice de la coleccion.

Y por otro lado con el ciclo `for` necesitamos saber cuantos valores hay o la longitud de la coleccion para eviatar intentar obtener un valor de un indice mas grande que la coleccion

Por ejemplo si el arreglo es de 3 elementos sabemos que el indice mayor sera 2, porque los arreglos empiezan en 0 entonces para un elemento de 3 solo podemos tener los indiices 0,1,2 <-- estos serian todos los indices que puedo iterar
Si intento iterar el indice numero 4 tendremos un error, porque el indice 4 solo seria valido para arreglos de minimo 5 elementos.

Veamos esto en un ejemplo, voy a cambiar la condicion para que el ciclo `for` sea <=

```csharp
   //foreach(int numero in numeros)
   //{
   //    Console.WriteLine(numero);
   //}

   for(int j = 0; j <= numeros.Lenght; j++)
   {
       Console.WriteLine(numero[j]);
   }   
```

Vamos a compilar y vemos que la compilacion fue correcta, no tenemos ningun error en compilacion, pero tendremos uno en runtime.

_[8:15]_

### [Run]-04

> si correo esto codigo:
> Error indexoutofrange exception

Lo que esta pasando es que la longitud del arreglo es 3 y si intentamos iterar desde 0 hasta 3 hay 4 elementos, elemento 0, 1, 2 y el elemento 3, cuando este ciclo intenta iterar el elemento con indice 3 este no existe  y por eso tenemos ese error de runtime

### [Vs]-04

Entonces el problema que podriamos llegar a tener al utilizar `for` para iterar una coleccion es _indice fuera de rango_ y una forma de evitar este error es utilizar `foreach` en lugar de un `for`.

Por ejemplo agregemos otro elemento arreglo

```csharp
    int[] numeros = new int[3];

    numeros[0] = 101;
    numeros[1] = 102;
    numeros[2] = 103;
    numeros[3] = 104;
```

Tenemos que modificar el tamaño del arreglo

```csharp
    int[] numeros = new int[4];
    .
    .
    .

    // Descomentar foreach
   foreach(int numero in numeros)
   {
       Console.WriteLine(numero);
   }

   // Comentar for
   //for(int j = 0; j <= numeros.Lenght; j++)
   //{
   //    Console.WriteLine(numero[j]);
   //}
```

Si corro este codigo no tengo que hacer ninga modificacion al ciclo `foreach`, este ya sabe cuantos elementos hay en el arreglo asi que no tenemos que especificarselo.

### [Run]-05

> Como vemos ahora tenemos el 4 elmento tambien siendo mostrado en pantalla y no modificamos nada del `foreach`
> 101
> 102
> 103
> 104

### [Vs]-05

Y esta seria la ventaja que tendriamos al utilizar ciclo `foreach`

## [Parte 15][4]

Si vemos el ciclo `foreach` es utilizado parar iterar o recorrer cada uno de los elementos dentro de una coleccion de datos, y las colecciones serian datos como los arrays o arreglos, arraylist, hashtables, diccionarios y todos los que existen dentro de generics, generics es una parte del .net framework que englobla varios tipos de colecciones de datos _genericas_, pero bueno no hay que preocuparnos por esto en este momento el tema de colecciones y generics lo veremos mas adelante.

[10:03]

### [Vs]-06

Tambien les quiero hablar de dos _palabras reservada_ o _keywords_ muy importantes que se pueden utilziar cuadno trabajamos con ciclos:

1. `break`
2. `continue`

## `break`

Anteriormente ya vimos una de las formas de utilizar el `break`, cuando vimos los ejemplos de la instruccion `switch`, si utilizamos `break` en cualquiera de los `case` dentro del `switch` lo que hace es que termina la ejecucion el `switch`.

Si estamos dentro de algun ciclo, puede ser cualquiera `for`, `foreach`,`do..while`, `while` y por alguna razon quieres salir del ciclo podemos hacer uso de la _palabra reservada_ `break`, veamos un ejemplo.

```csharp
for(int i=1; i <= 20; i++){
    Console.WriteLine(i);
}
```

Si vemos este codigo es un programa muy simple el cual mostrara en pantalla los numeros desde 1 al 20.

### [Run]-06

> 1
> 2
> .
> .
> .
> 20

Digamos que solo quiero imprimir los numeros hasta el 10 pero no puedo modificar la condicion `i <= 20`, para esto podemos hacer uso de la _palabra reservada_ `break`

[11:20]

```csharp
for(int i=1; i <= 20; i++){
    Console.WriteLine(i);
    if(i == 10)
    {
        break;
    }
}
```

Que es lo que hace este codigo, pues empieza en 1 mientras que i sea menor o igual que 20 va ir imprimiento los nuemros en pantalla, pero despues de imprimir cada uno esta validando en este `if`, si i es igual a 10, cuando i aumente a 10 es cuando el codigo dentro del `if` sera ejecutado y este `break`, si vemos esta de alguna forma ligada al `for`, el break sabe que va a detener la eejeccion de este `for`, al llegar a este punto se ejecuta el `break` y termina la ejecucion del `for` para continuar con el resto del codigo fuera del `for`, en nuestro caso no hay mas codigo asi que aqui termina la ejecucion del programa..

Corramos el programa para ver que efectivamente solo mostrara los valores hata el 10 y no hasta el 20 como la condcion del ciclo.

### [Run]-07

> 1
> 2
> .
> .
> .
> 10

Tan pronto como la condicion del `if` es verdadera entra al `if` y se ejecutar la instruccion del `break` con lo cual termina la ejecucion o nos salimos del ciclo `for`.

Y asi es como funciona la instruccion `break` dentro de cualquier ciclo.

## `continue`

Ahora pasemos a la otra _palabra reservada_ que es `continue`

¿Cuando utilizar `continue`?
[13:04]

Digamos que quiero mostrar en pantalla numeros pares desde el 0 hasta el 10, pero no quiero incrementar el valor de dos en dos

```csharp
for(int i=0; i <= 20; i++){
    Console.WriteLine(i);
}
```

Si corro este programa tal como esta ahorita, mostrara los numeros del 0 al 20

### [Run]-08

> 0
> 1
> .
> .
> .
> 20

### [Vs]-07

Pero yo quiero mostrar solo los numeros pares hasta llegar al 20,
¿Como hago esto?
Hay varias formas de hacerlo la mas simple seria sumar de dos en dos

```csharp
for(int i=0; i <= 20; i = i + 2){
    if()
    Console.WriteLine(i);
}
```

Y si lo corremos obtendremos el resultado esperado, mostrar en pantalla numeros pares hasta llegar al 20

### [Run]-09

> 0
> 2
> .
> .
> .
> 20

### [Vs]-08

Pero como quiero mostrarles la importancia y funcionamiento de la _palabra reservada_ `continue` mostraremos los numeros pares de otra forma.

```csharp
for(int i=0; i <= 20; i++){
    if(i % 2 != 0)
    {
        continue;
    }
    Console.WriteLine(i);
}
```

Veamos que esta pasando en este codigo, en el `if` estamos haciendo uso del operador _mod_ que en c# es el `%`, lo que hace este operador es decirnos si un numero es divisible entre otro.

¿cómo has esto?
Pues nos retorna el residuo de la division, para saber si un numero es divisible entre 2 tenemos que saber si el residuo de ese numero entre 2 es cero
Por ejemplo 4/2 = 2.0 por lo tanto no hay residuo, residuo se refiere a la parte decimal, en cambio si divdimos 5/2 tenemos 2.5 asi que el residuo no es cero
El operador _mod_ retornara 0 si el numero es divisible y si no entonces retornara un 1.

Entonces basicamente lo que esta pasando en ese `if` es que estamos validando si el numero NO es divisible entre dos, si el residuo de esa division NO ES CERO
Y ¿porqué entre dos?, pues porque los numeros pares son los divisibles entre dos.  Osea esta es una forma de saber si el numero es par o no.

Muy bien, volvamos a la explicacion de `continue`, entonces cuando el numero no sea par o no sea divisible entre dos, se va a ejecutar lo que esta dentro del `if` osea la instruccion `continue`
y ¿qué es lo que va a pasar en este punto?
Pues imaginemos que es como un salto, se va a saltar el resto de la ejecucion del `for` y se va a mover a la siguiente iteracion.

Osea va dejar de ejeecutar el resto del codigo que esta dentro del ciclo y va a continuar otra vez ejecutando el ciclo para el siguietne valor, si antes `i` valida 1 y como 1 no es par, se ejecutara `continue` y ahora volvemos a otra iteracion del ciclo ahora `i` vale 2, como 2 si es par no se ejecuta el codigo dentro del `if` y se imprime el valor 2 en pantalla, despues viene otra vez ahora `i` vale 3, 3 no es par asi que ejecutamos `continue`, nos saltamos el resto del codigo donde se imprime el valor en pantalla y ahora `i` vale 4 y asi sucesivamente.

Entonces para cada numero impar se ejecuta el `continue` y se hace un salto del resto del codigo o se omite esta ejecucion, podemos decir que despues del `continue` se deja de correr el codigo restante dentro del ciclo y nos movemos al siguiente valor.

Ejecutemos el codigo:

### [Run]-10


> 0
> 2
> .
> .
> .
> 20

Espero que con esta explicacion haya podido quedar claro que hace la _palabra reservada_ `continue`, como vimos esta puede ser utilizada cuando sea que por alguna razon queramos saltarnos codigo dentro de un ciclo, con alguna condicion especifica.

## [Parte 15][5]

Muy bien, esn esta seccion hemos visto:

* ¿Cómo utilizar for?
* Las diferencias entre los ciclos for y while
  * En el ciclo while tenemos la declaracion, condicion y el incremento en diferentes partes del codigo y en el ciclo for temeos todo en el mismo lugar.
  
Tambien vimos

* ¿Cómo utilizar el ciclo foreach?
  * y como utlizando foreach evitamos la exception _indice fuera del arreglo_
  * Como con foreach podemos iterar cualquier tipo de coleccion de datos.
* , y las palabras reservadas
  * break: salir del ciclo.
  * continue: Saltarte a la siguiente iteracion.

## [Parte 15][6]

Esto es todo por hoy muchas gracias por ver este video, y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Y como siempre te deseo quee tengas un dia genial :)