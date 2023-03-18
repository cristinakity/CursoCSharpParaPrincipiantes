# Contenido

[[TOC]]

# Parte 14 – Ciclo do…while en C #

## [Parte 14][1]

Hola bienvenidos a Pragim Technologies yo soy Cristina Carrasco,
esta es la parte 14: Ciclos en C#, en esta leccion hablaremos del ciclo do...while

## [Parte 14][2]

En la parte 13 hablamos del ciclo While.
Y en proximas lecciones hablare de los ciclos for y foreach

Veamos un ejemplo

### [x]

En la parte 13 vimos el ciclo while.
Hicimos un programa muy simple donde el usuario introducia un numero limite o numero final y utilizan un ciclo while mostrabamos en pantalla los numero pares hasta llegar al numero que el usuario introdujo.
Si tienen dudas sobre como funciona el ciclo while por favor revisen el video anterior, La parte 13 de este tutorial.

Hagamos ese mismo programa, pero veamos como crear la version mejorada utilizando el ciclo do... while

Entonces:

```csharp
Console.WriteLine

```

Preguntare al usuario que ingrese su numero limite

```csharp
Console.WriteLine("Por favaor ingrese el numero limite:")
```

Una vez que el usuairo ingrese el numero limite, necesitamos leer ese numero y almacenarlo en una variable

```csharp
Console.WriteLine("Por favaor ingrese el numero limite:")
int numeroLimite = Parse.Int(Console.ReadLine());
```

Bien, ya tenemos el numero limite, ahora necesitamos el numero inicial

```csharp
Console.WriteLine("Por favaor ingrese el numero limite:")
int numeroLimite = Parse.Int(Console.ReadLine());

int numeroInicial = 0;
```

Y el ciclo while, mientras qeu numeroInicial sea menor o igual que el numeroLimite,
Vamos a mostrar en pantalla los numeros pares

```csharp
int numeroInicial = 0;
while(numeroInicial <= numeroLimite){
    Console.WriteLine(numeroInicial + " ");
    numeroInicial = numeroInicial+2;
}
```

Este programa es igual al que hicimos en la leccion anterior, si tienen alguna duda de como funciona por favor revisen la leccion anterior.

Ok, entonces que hace este progrma?

### [Run]

> Le pide al usuario el numero limite,
> [10 enter]
> he imprime los numero pares hasta llegar a ese numero

### [VS]

_[2:30]_
Hagamos este programa mas interactivo, con el el codigo actual si quiero imprimir los numeros pares hasta 20 tengo que cerrar el programa y correrlo otra vez.

Asi que quiero que el usuario pueda dedicir cuando el programa debe dejar de correr.

Entonces vamos a preguntarle al usuario si quiere continuar y el programa seguira corriendo hasta que el usuario decida ya no continuar.

Para hacer eso, tendremos que preguntarle al usuario si quiere continuar

```csharp
while(numeroInicial <= numeroLimite){
    Console.WriteLine(numeroInicial + " ");
    numeroInicial = numeroInicial+2;

Console.WriteLine("¿Desea continuar? Si o No")
//Y para leer la respuesta almacenamos el valor en una variable
string continuar = Console.WriteLine();
//Y ademas vamos a validar si el usuario escribio Si o No, 
//cual quier otra cosa sera invalida y tendremos que preguntar otra vez 
//hasta que el usuario responda Si o No
if(continar != "Si" && continuar != "No")
//Si continuar no es ni Si o No, sabemos que el valor ingresado es invaldo
{
    Console.WriteLine("Escribio un valor invalido.  Por favor responda Si o No");
}
```

_[4:58]_
Ok, que tanto vamos ejecutar estas lineas de codigo (desde desea cotinar hasta el if), hasta que el usuario ingrese Si o No, mientras que el usuario ingrese otro valor queremos que esto siga mostrandose en pantalla y para hacer eso podemos utilizar un ciclo do

```csharp
//Queremos que esto se repita, ponemos el do aqui
do{
    Console.WriteLine("¿Desea continuar? Si o No")
    string continuar = Console.WriteLine();
    if(continar != "Si" && continuar != "No")
    {
        Console.WriteLine("Escribio un valor invalido.  Por favor responda Si o No");
    }
    //Se va repetir hasta cuando? hasta que el usuario escribia si o no
}while(continar != "Si" && continuar != "No")
```

_[6:00]_
Tenemos un error poruqe la variable continuar no existe fuera del ciclo asi que solo debemos delcararla antes del do, he inicializarla en vacio.

```csharp
//la variable continuar debemos declararla fuera del ciclo
string continuar = "";
do{
```

_[6:18]_
si vemos este codigo es un codigo muy simple donde utilizamos un ciclo do... while, y lo que va hacer el do es ejecutar esta parte del codido osea todo lo que este dentro del ciclo do hasta que la condicion dentro del while se cumpla o sea verdadera.

Muy bien, entonces corramos este programa para ver que pasa:
_[6:45]_

### [Run]

> Primero ingreso el numero limite:
> 10
> Muestra los numero pares hasta llegar al 10 y ahora me pregunta si quiero continuar,
> Escribo un valor invalido: asdfadsf
> Muestar el mensaje que es un valor invalod si quiero continuar si o no,
> Otra vez escribo algo invalido
> ewr
> y vuelve a preguntar si deseo continuar,

### [VS]

Como vemos ahora el programa esta dentro del ciclo, ejecutandose una y otra vez, mientras que yo no escriba Si o No el programa seguira corriendo el ciclo do..while
entonces y si escribo Si.
_[7:15]_
Si, Pue el programa terminara porque despues del do ya no tenemos mas codigo, asi que saldra del ciclo do.. while y alli terminara la ejecucion del programa.
_[7:18]_
Pero que quiero que pase en realidad? pues deberia preguntarme otra vez cual es mi numero limite, si el usuario queire continuar el programa deberia ejecutarse otra vez, dicho esto lo que significa es que esta parte inicial del programa tambien deberia estar dentro de un ciclo, para que se este ejecuando, siempre y cuando el usuario quiera continuar ejecutando el programa.
_[7:38]_
Muy bien dicho esto pues agregemos otro do..while

```csharp
do{
    Console.WriteLine("Por favaor ingrese el numero limite:")
    int numeroLimite = Parse.Int(Console.ReadLine());
    ...
```

Que tanto vamos a ejecutar esto

```csharp
...
}while(continar != "Si" && continuar != "No")
}while(continar == "Si")//Mientras que el usuairo quiera continuar
```

_[8:14]_
Y tenemos un problema aqui, es el mismo que antes, la varaible continuar debe ser declarada fuera del ciclo while.
[mover variable al inicio]
_[8:48]_
Ahora si corremmos este programa:
> Por favor ingrese el numero limite:
> 0 2 4 Continuar?
> dasfasdfdasf //escribo un string invalido
> Invalido
> Continuar?
> SI
> 10
> 0 2 4 6 8 10 //imprime los numeros pares hasta el 10
> No//Vuelve a preguntar si deseo continuar
> //y la ejeecucion del programa termina

_[9:23]_
Muy el programa funciona, pero tenemos un pequeño error, corramos el programa otra vez:
Por favor ingresa el numer limite:
5
0 2 4 Continuar?
//Digamos que escribio SI todo en mayusculas
SI
//Nos dice que es un valor invalido.
[9:39]
Entonces que esta pasando aqui:
Si vemos el codigo fuente, continuar espera que valga Si con S mayuscula y la i minuscula, si ponemos SI mayuculas al llegar a estar comparacion, esto se evalua SI en mayusculas es diferente de Si(ese mayuscula i minuscula), la respuesta es verdadera si es diferente de Si por lo tanto nuestra respuesta es invalida.
[10:15]
Entonces para arreglar esto lo que podemos hacer es convertir lo que leemos de la consola en mayusculas y compararlo contra mayusculas:

```csharp
{
    continuar = Console.ReadLine().ToUpper;
    ...
    if (continuar != "SI" %% continuar != "NO")
    ...
    while (continuar != "SI" %% continuar != "NO")
    ...
    while (continuar == "SI")
}
```

### [Run]

Corramos el programa,
> Escribo el valor limite 10,
> quiero continuar si,
> pongo otro valor 4
> quiero continuar sI
> pongo otro valor 12
> quiero continuar Si
> pongo otro valor 6
>
> Y como vemos el proga esta funcionando sin importar si escribimos Si con mayuscula o minusculas, porque recuerden la comparacion esta convirtiendo todo a mayusculas y comparando mayusculas con mayusculas.
>
> Quiero continuar: No
>
> y termina la ejecucion

Muy bien, entonces facilmente mente podemos crear ciclos
utilizando do.. while y si recordamos en la parte 12
"Instruccion switch en c# Continuacion", escribimos un pequeño programa para comprar cafe donde hicimos un ciclo similar a este pero no utilizamos do..while, lo que utilizamos fue la isntruccion goto y recordemos que es preferible evitar utilizar esta instruccion, porque cuando la utilizamos la ejecucion del programa puede saltar de un lugar a otro haciendo el programa un poco mas complejo y dificil de debugear y por esto es que se recomienda evitar utilizar goto.

Bueno dicho esto, en realidad el programa para comprar cafe que hicimos usando goto puede ser cambio o mejorado utilizando el ciclo do..while.

Si no recuerdas cual era el programa para comprar cafe y si necesitas una explicacion mas detallada de como funciona ese codigo porfavor echale un vistazo a la parte 12 "Instruccion switch en c# Continuacion" de este tutorial, ok?

### [VS]

Pero bueno seguimos y aqui tengo ese codigo:

```csharp
using System;

class Program
{
    static void Main()
    {
            int costoTotalDelCafe = 0;
        Inicio:
            Console.WriteLine("Selecciones el tamaño para su cafe: 1=chico, 2=Mediano, 3=Grande");
            int eleccionDelUsuario = int.Parse(Console.ReadLine());
            switch (eleccionDelUsuario)
            {
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
        DeseaComprar:
        Console.WriteLine("¿Desea comprar otro cafe? Si o No");
            string seguirComprando = Console.ReadLine();
            switch (seguirComprando.ToUpper())
            {
            case "SI":
                goto Inicio;
            case "NO":
                break;
            default:
                Console.WriteLine($"Elegiste {seguirComprando} la cual no es una opcion valida.\nPor favor escriba una opcion valida. Si o No");
                goto DeseaComprar;
            }
        
        Console.WriteLine($"¡Gracias por su compra!\nSu total a pagar es: {costoTotalDelCafe}");
    }
}
```

Lo copio del notepad a visual studio.
_[13:42]_
Si vemos este programa hay unas etiquetas o label aqui (Inicio), si tienes dudas sobre las etiquetas y como utilizar la instruccion goto por favor te recomiendo que veas la parte 12 de este tutorial.
Y tambien tenemos la etiqueta DeseaComprar y veamos esto estamos utilizando goto DeseaComprar para ir a la etiqueta especifica de ese nombre y de igualmanera tenemos goto Inicio para mover la ejecucion del codigo a donde esta la etiqueta Inicio.

### [Run]
> Bien, corramos el programa:
> Vemos el mensaje: "Seleccione el tamaño para su cafe"
> 3
> Pregunta si queremos otro cafe
> Si
> compramos otro cafe grande
> 3
> Quiero comprar otro cafe
> No
> Compre 2 cafes grande y el total a pagar son 70

Entonces este programa de algun modo es como un ciclo, solo con isntruccion switch y goto.

Pero he escrito el mismo programa utilizando el ciclo do...while
_[14:54]_

```csharp
using System;

class Program
{
    static void Main()
    {
        int costoTotalDelCafe = 0;
        string seguirComprando = string.Empty;
        
        do 
        {
            int eleccionDelUsuario = -1;
            do
            {
                Console.WriteLine("Seleccione el tamaño para su cafe: 1=chico, 2=Mediano, 3=Grande");
                eleccionDelUsuario = int.Parse(Console.ReadLine());
                switch (eleccionDelUsuario)
                {
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
                        break;
                }
            } while (eleccionDelUsuario != 1 && eleccionDelUsuario != 2 && eleccionDelUsuario != 3);
            
            do
            {
                Console.WriteLine("¿Desea comprar otro cafe? Si o No");
                seguirComprando = Console.ReadLine().ToUpper();
                if(seguirComprando != "SI" && seguirComprando != "NO")
                {
                    Console.WriteLine($"Tu respuesta {seguirComprando} es invalida.  Por favor intenta de nuevo...");
                }
            } while (seguirComprando != "SI" && seguirComprando != "NO");
        } while (seguirComprando != "NO");
        Console.WriteLine($"¡Gracias por su compra!\nSu total a pagar es: {costoTotalDelCafe}");
    }
}
```

### [Run]
> Corramos el programa:
> Vemos el mensaje: "Seleccione el tamaño para su cafe"
> 3
> Pregunta si queremos otro cafe
> asdfsdf
> Respuesta invalida
> quiero comprar otro cafe?
> Si
> compramos otro cafe grande
> 3
> Quiero comprar otro cafe
> No
> Compre 2 cafes grande y el total a pagar son 70

Como vemos el programa funciona igual, pero en lugar de utilizar goto tenemos un ciclo do...while

Muy bien pues asi es como funciona el ciclo do...while

## [Parte 14][3]

En la seccion anterior hablamos sobre el ciclo While y si recordamos:

El ciclo while primero valida la condicion y si ésta es verdadera entonces ejecuta el codigo dentro del while, y seguira la ejecucion siempre que la condicion sea verdadera, cuando la condicion sea falsa la ejecucion del ciclo while terminara.

Y es muy importante cambiar la variable dentro de la condicion para que el while tenga un fin, de lo contraria el codigo seguira ejecutandose en un ciclo infinito y eso no es bueno para ningun programa, ni para el procesador de la computadora.

## [Parte 14][4]

En el ciclo do...while, la condicion para ejecutar el ciclo se evalua al final del ciclo, esto significa que el codigo dentro del do...while sera ejecutado por lo menos una vez y este tipo de ciclos muchas veces son utilizados para mostrar un menu al usuario como desea continuar si o no, o que opcion de una listas desea ejecutar, si quieres mostrarle un menu de opciones al usuario y en base a la opcion del usuario realizar alguno calculo o mostrar un mensaje en pantalla y continuar ese ejecucion las veces que el usuario quiera... en este caso probablemente puedas utilizar un ciclo do...while.

## [Parte 14][5]

Las diferencias entre el ciclo while y el ciclo do...while son:  While valida la condicion al inicio del ciclo asi que para que el ciclo while sea ejecutado la condicion se debe cumplir, en cambio el ciclo do... while valida la condicion al final lo cual significa que sera ejecutado por lo menos una vez sin importar que la condicion se cumpla o no.

Dicho de otra forma si la condicion es falsa en un ciclo do.. while el codigo sera ejecutado despues evalua la condicion y termina el ciclo, en cambio en un ciclo while la condicion se evalua primero como falsa y el ciclo no se ejecuta.

## [Parte 14][6]

Muchas gracias por ver este video, y recuerden para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Que tengas un excelente dia :)
