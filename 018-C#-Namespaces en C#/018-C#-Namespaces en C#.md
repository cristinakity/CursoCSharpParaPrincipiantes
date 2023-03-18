# Contenido

[TOC]

# Parte 18 - Namespaces en C#

## [Parte 18][1]

Hola bienvenidos a Pragim Technologies yo soy Cristina,
esta es la Parte 18: Namespaces en c#

## [Parte 18][2]

Em esta leccion veremos
* Los basico sobre los namespaces
* Usar alias
* Diferentes miembros para los namespaces

Veamos un ejemplo

## [Parte 18][3]

¿Por qué utilizar namespaces?, ¿Cuál es la ventaja de utilizarlos?

Basicamente tenemos dos ventajas principales al utilizar los namespaces, estos nos ayudan a organizar el codigo, y nos proporcionan una forma de evitar conflictos de nombres en nuestras aplicaciones, especialmente si tememos proyectos muy grandes.

Y que significa esto, pues veamos un ejemplo

### [vs]-01

Digamos que estoy trabajando en un proyecto

### [Notepad++]-01

```notepad
ProyectoA
    EquipoA
    EquipoB
```

Tenemos el proyectoA con los equipos A y B trabajando en este.  Entonces digamos si quisiera organizar el codigo por Equipos podria decir que quiero el namespace ProyectoA.EquipoA para que todo el codigo creado por el equipoA quede en ese namespace y aparte otro namespace ProyectoA.EquipoB para el codigo creado por el equipoB, esta seria una forma de organizar el codigo por namespaces.

Pero si nos vamos aun ejemplo mas realista lo que hacen las empresas, se puede organizar el codigo por funcionalidad, por ejemplo si estuvieramos creando un sistema podriamos crear el namespace Proyecto.Ventas para almacenar todo lo referente a las Ventas y de este mismo modo podriamos tener Proyecto.Compras y tener todas las clases relacionadas a las compras.

Asi que los namespaces nos ayudan a organizar el codigo.

Antes de crear un ejemplo para ver como funcionan los namespaces y como nos ayudan a organizar codigo, veamos como Microsoft utiliza los namespaces.

Entonces incluso microsoft utiliza los namespaces para organizar su codigo, en este caso el codigo dentro de .net framework.

Por ejemplo desde la parte 1 hemos utilizado la clase Console.


```csharp
public static Main()
{
    Console.WriteLine("Hola");
}
```

Si vemos esta clase `Console` y ponemos el mouse encima vemos que esta clase viene del namespace `System.`, si le doy click derecho he ir a definicion, podemos ver que viene del namespace `System`

De igualmanera como microsoft utiliza los namespaces para organizar el codigo nostros podemos hacer lo mismo y crear nuestros propios namespaces.

Si tememos el EquipoA y el EquipoB y queremos organizar el codigo para estos Equipos dentro del ProyectoA tendriamos que hacer lo siguiente:

```csharp
public static Main()
{
    Console.WriteLine("Hola");
}

namespace ProyectoA
```

y dentro de este quiero crear otro namespace

```csharp
public static Main()
{
    Console.WriteLine("Hola");
}

namespace ProyectoA
{
    namespace EquipoA
    {

    }
}
```

Todas la clases que pertenecen al EquipoA deberan ser creadas dentro del namespace EquipoA.

Digamos por ejemplo quie quiero tener una clase

```csharp
public static Main()
{
    Console.WriteLine("Hola");
}

namespace ProyectoA
{
    namespace EquipoA
    {
        class ClaseA
        {
            public static Imprimir()
            {
                Console.WriteLine("Equipo A Metodo Imprimir");
            }
        }
    }
}
```

Entonces tenemos la ClaseA que esta dentro del namespace EquipoA, si alguien quisiera utilziar esta clase tendria que utilizar ProyectoA.EquipoA.ClaseA.

Entonces en le metodo Main si quiero hacer uso del metodo Imprimir dentro de la ClaseA, tendria que hacer lo siguiente

```csharp
public static Main()
{
    ProyectoA.EquipoA.ClaseA.Imprimir();
}

namespace ProyectoA
{
    namespace EquipoA
    {
        class ClaseA
        {
            public static Imprimir()
            {
                Console.WriteLine("Equipo A Metodo Imprimir");
            }
        }
    }
}
```

>Si correo el programa veremos en pantalla el mensaje 
>Equipo A Metodo Imprimir

Podemos utilizar el namespace completo como en el ejemplo o podemos agregar un `using` con los namespaces.

```csharp
using ProyectoA.EquipoA;

public static Main()
{
    ClaseA.Imprimir();
}

namespace ProyectoA
{
    namespace EquipoA
    {
        class ClaseA
        {
            public static Imprimir()
            {
                Console.WriteLine("Equipo A Metodo Imprimir");
            }
        }
    }
}
```

Hagamos una copia del namespace ProyectoA, para agregar al EquipoB

```csharp
using ProyectoA.EquipoA;

public static Main()
{
    ClaseA.Imprimir();
}

namespace ProyectoA
{
    namespace EquipoA
    {
        class ClaseA
        {
            public static Imprimir()
            {
                Console.WriteLine("Equipo A Metodo Imprimir");
            }
        }
    }
}

namespace ProyectoA
{
    namespace EquipoB
    {
        class ClaseA
        {
            public static Imprimir()
            {
                Console.WriteLine("Equipo B Metodo Imprimir");
            }
        }
    }
}
```

Si vemos como quedo el codigo tenemos la ClaseA en ProyectoA.EquipoA y tambien tenemos la ClaseA dentro de ProyectoA.EquipoB, si quisiera llamar al metodo Imprimir dentro de la ClaseA del EquipoB ¿Cómo hago esto?, hay dos maneras.

Una es utilizar el nombre completo con todos los namespaces.

```csharp
using ProyectoA.EquipoA;

public static Main()
{
    ClaseA.Imprimir();
    ProyectoA.
}
```

Y cuadno pongo el punto podemos ver que ahora hay dos namespaces, EquipoA y EquipoB.

```csharp
using ProyectoA.EquipoA;

public static Main()
{
    ClaseA.Imprimir();
    ProyectoA.EquipoB.ClaseA.Imprimir();
}
```

> Si corremos este ejemplo podremos ver los dos mensajes que vienen de cada clase y namespace correpondiente
>Equipo A Metodo Imprimir
>Equipo B Metodo Imprimir

Bien, digamos que quiero agregar otro using para el EquipoB en lugar de poner el nombre completo para la clase

```csharp
using ProyectoA.EquipoA;
using ProyectoA.EquipoB;

public static Main()
{
    ClaseA.Imprimir();
    ClaseA.Imprimir();
}
```

Como vemos esto nos genera un conflicto porque ambos namespaces contiene la misma clase.  El error dice que hay una referencia ambigua osea que el compilador no sabe cual de las dos clases queremos utilizar.

Hay dos formas de arreglar este problema, una es utilizando los nombres completos para ambas llamdas 

```csharp
//using ProyectoA.EquipoA;
//using ProyectoA.EquipoB;

public static Main()
{
    ProyectoA.EquipoA.ClaseA.Imprimir();
    ProyectoA.EquipoB.ClaseA.Imprimir();
}
```

Con esto se arregla el conflicto de nombres.

Pero si no quisiera estar llamando mis clases de esta manera porque es un nombre muy largo, lo que puedo hacer es utilizando alias para los namespaces.

```csharp
using PAEA = ProyectoA.EquipoA;
using PAEB = ProyectoA.EquipoB;

public static Main()
{
    PAEA.ClaseA.Imprimir();
    PAEB.ClaseA.Imprimir();
}
```

Podemos resolver la ambiguedad entre los nombres de las clases utilizando el nombre completo con todos los namepaces o asignando directivas de alias a los namespaces.

[10:02]

Hay dos propositos para utilziar las directivas de alias el primero es para resolver o evitar ambiguedad entre los nombres y el otro proposito es, si los nombres de los namespace soy muy largos y no queremos estar utilizando nombres tan largos, pues podemos simplementes crear un alias con algun acronimo o mas corto.

[10:25]

Ok, muy bien... voy a remover ProyectoB y dejar solo esto:

```csharp
using ProyectoA.EquipoA;

public static Main()
{
    ClaseA.Imprimir();
}
```

Y hagamos algunos cambios al codigo y agregemos mas namespaces o mas usings

```csharp
using System;
using ProyectoA.EquipoA;
using System.Collections;
using System.Configuration;

public static Main()
{
    ClaseA.Imprimir();
}
```


Muy bien, aqui tenemos `ClaseA.Imprimir()` y si nos preguntamos de donde es que viene esta clase?, a simple vista no lo sabemos porque no estamos utilziando el nombre completo con todo y los namespaces, entonces a simple vista mirando el codigo no podemos saber de cual de todos los `usings` que estan aca arriba proviene esta `ClaseA`, puede venir de `System`, de `ProyectoA.EquipoA` o de `System.Configuration`.

A menos que vaya y ponga el mouse encima de la clase y vea el nombre completo con todos los namespaces en realidada no se de donde es que viene esta clase, en cual de todos los namespaces esta incluida.

Entonces algunas personas creen que no es bueno tener los usings aca arriba si no que es mejor utilizar le nombre completo para saber de donde es que vienen las clases, entonces aqui se dividen las opiniones en quienes creen que hay que utilziar el nombre completo y quienes creen que hay que utilizar usings porque poner los nombres completos con todo y namespaces nos haria escribir mucho codigo, por un lado tenemos que a simple vista no sabemos de donde viene cada clase y por otro lado tenemos que hay que escribir mucho codigo al utilizar siempre los nombres completos.

Asi que esto es como una discusion, algunas personas prefieren utilizar las directivas `using` y no tener que poner todo el nombre de la clase completo, pero la desventaja seria que no sabriamos de donde viene esa clase a menos que pongamos el mouse encima y veamos el nombre completo.

Por otra parte una forma de utilizar la directiva `using` y de alguno podo poder saber de donde vienen las clases es crear alias 

```csharp
using System;
using PAEA = ProyectoA.EquipoA;
using System.Collections;
using System.Configuration;

public static Main()
{
    ClaseA.Imprimir();
}
```

Al crear el Alias PAEA puedo llamar a la clase con este alias y el nombre de la clase.

```csharp
using System;
using PAEA = ProyectoA.EquipoA;
using System.Collections;
using System.Configuration;

public static Main()
{
    PAEA.ClaseA.Imprimir();
}
```

Y de este modo no estamos escribiendo un nombre muy largo ni tampoco estamos perdiendo el hilo de cual es  el origen de esta clase.  Digamos que los alias en los  `usings` vendrian a ser un punto neutral o intermedio entre poner el nombre completo y por ende escribir mucho codigo o utilizar la directiva `using` y perder el hilo del origen de la clase.

Asi que aqui al agregar el alias solo con ver el codigo ya se que `ClaseA` viene de `PAEA` y se que `PAEA` es un alias de `ProyectoA.EquipoA`.  Y esto nos permite escribir nombres mas cortos y que sea facil de identificar de donde viene la `ClaseA`

[13:06]
## [Parte 18][3]
¿Por qué utilizar namespaces?
- Son utilizados para organizar nuestros programas
- Y tambien nos proporcionan asistencia para evitar conflictos entre nombres de clases.

## [Parte 18][4]
Otro concepto importante es que los namespaces no corresponden directametne a un archivo, directorio o ensamblador.

¿Qué quiero decir con esto?

###[vs][01]
Si vemos este proyecto que tenemos aqui y se llama IntroduccionACsharp,
dentro de el tenemos estos namespaces `ProyectoA` con `EquipoA` y `ProyectoA` `EquipoB` tambien, y demas tenemos la clase `Program`

Si yo Compilo esta solucion,

[click derecho en proyecto y Compilar Solucion]

Lo que esta pasando es que todo este codigo de c# es copilado y nos va a generar un assembly para ver el resultado de la compilacion tendremos que abrir la carpeta del proyecto.

[click derecho> Abrir carpeta en el explorador de archivos]

Y si vamos a la carpeta bin > debug

Aqui es donde tenemos el assembly del proyecto que es el archivo `IntroduccionACsharp.exe`

En este assembly tenemos la compilacion de todo este codigo, entonces dentro del archivo  `IntroduccionACsharp.exe` tenemos `ProyectoA.EquipoA`, `ProyectoB.EquipoB`, como vemos el assembly es el mismo pero puede contener diferentes namespaces y diferentes clases.

Ahora esta misma aplicacion la podemos escribir  de una manera diferente, por ejemplo para las clases dentro del namespaces `ProyectoA.TeamA` puedo agregar un nuevo proyecto

[Click derecho en la solucion Agregar > Nuevo Proyecto]

Proyecto de C#, Biblioteca de clase o Clas Library
Le voy a poner de nombre `ProyectoA.EquipoA`

Entonces que tenemos aqui pues lenguaje de programacion C#, plataforma Windows, tipo de proyecto Biblioteca (Library) y el nombre del proyecto es `ProyectoA.EquipoA`

Y tenemos aqui el nuevo proyecto si vemos es una biblioteca de clases y se llama `ProyectoA.EquipoA` y voy a renombrar esta clase `Class1` por `ClaseA`

Si vemos aqui y la `ClaseA` esta creada y tiene un namepasce `ProyectoA.EquipoA`,
entonces primoer voy a copiar el codigo para esta clase que esta dentro del otro proyecto `IntroduccionACsharp`

```csharp
namespace ProyectoA.EquipoA
{
    public class ClaseA
    {
        public static void Imprimir()
        {
            Console.WriteLine("Equipo A metodo Imprimir");
        }
    }
}
```

 y ahora lo que voy a hacer es en el otro proyecto en la clase  `Program`  voy a remover el namespace que teniamos de `ProyectoA.EequipoA`

 Y voy hacer lo mismo para `ProyectoA.EquipoB`, entonces primoer agregamos el nuevo proyecto que sera una biblioteca de clases

[click derecho en proyecto y Compilar Solucion]

Selecciono el tipo de proyecto y de nombre le voy aponer `ProyectoA.EquipoB`, igualmanera voy a renombrar `Class` por `ClaseA` y voy a copiar otra vez el contenido de `ProyectoA.EquipoA.ClaseA` que esta en el proyecto `IntroduccionACsharp`
muy bien entonces depsues de copiar esto ya no necesitamos el namespace en el proyecto `IntroduccionACsharp` asi que tambien vamos a remover esa seccion de codigo.

Muy bien, entonces ahora en el proyecto `IntroduccionACshar` solo tenemos la clase `Program` con el meotod `Main`, entonces `ProyectoA.TeamA` y `ProyectoA.TeamB` ya no existen aqui, esos namespaces ya no van a estar presentes en el assembly `IntroduccionACsharp.exe`, entonces voy a remover los usings de esta clase `Program`

```csharp
using System;

class Program
{
    static void Main()
    {
    }
}
```

Vamos a revisar que cambios hicimos: 
1. Creamos otro proyecto llamad `ProyectoA.EquipoA`
2. Copiamos el tenido de ClaseA que estaba en el proyecto `IntroduccionACsharp` al proyecto nuevo que creamos dentro de una clase con el mismo nombre.
3. Removimos el codigo para el namespace `ProyectoA.EquipoA` de proyecto `IntroduccionACsharp`
4. Despues repetimos estos mismo pasos pero para el `ProyectoA.EquipoB`

Entonces ahora en lugar de tener todos los namespaces aca en un solo proyecto, lo que tenemos es el codigo mejor organizado cada uno en su respectivo proyecto y al compilar cada cosa quedara en su propio assembly

[17:44]

Entonces si voy y compila la solucion otra vez, lo que pasara es que va a compilar cada cada proyecto en su respectivo ensamblador o assembly, entonces vamos abrir la capreta del proyecto otra vez:

[click derecho> Abrir carpeta en el explorador de archivos]

Y vemos que teenmos ahora otra carpetas mas:
ProyectoA.EquipoA y ProyectoA.EquipoB
Si abro la capreta ProyectoA.EquipoA > y voy al directorio bin>debug
Podremos ver el assembly `ProyectoA.EquipoA.dll`, es .dll porque es una biblioteca de clase o class library, y dentro de esta dll tenemos la `ClaseA` con el metodo `Imprimir()` y para probar esto podemos revisar la dll para estoy

1. Abrir Developer Command Prompt
   1. Inicio > Visual Studio xxx > Developer Comman Prompt for VS xxxx
   2. Escribimos ILDASM.EXE y presionamos enter
2. Se abrira IL DASM que es el Microsfot .Net Framework IL Dissambler
   1. Archivo abrir
   2. Seleccionamos la Libreria y damos click en abrir

Con esto podremos ver que clases y que metodos hay dentro de este assembly.
Vamos a explorar esta DLL y tenemos el `ProyectoA.EquipoA` si lo expandimos podremos ver la `ClaseA` y si expandimos esto podremos ver los metodos dentro de esta clase.
Como nosotros creamos esta biblioteca o dll ya sabemos que hay una `ClaseA` que tiene dentro un metodo Imprimir y aqui lo podemos ver.

De igual manera si volvemos atras en el explorador de archivo tenemos el folder para la biblioteca de clases `ProyectoA.EquipoB` podemos ver el assembly `ProyectoA.EquipoB.dll`

###[vs][02]
Muy bien entonces si vemos la solucion tenemos una solusion con 3 proyectos y ahora cada unos de los Equipos tiene su propio proyecto  con su propia `ClaseA` y lo que vamos hacer es utilizar estas clases dentro del proyecto principal `IntroduccionACsharp` 

Para importar un proyecto dentro de otro hay que hacer click derecho aqui en Referencias > Agregar Referencia

En la pantalla de administrador de referencias, la referencia que vamos agregar es una referencia a otro proyecto para esto voy seleccionar aqui Proyectos y automaticmante me muestra la lista de proyectos disponibles para importar o hacer referencia y lo que voy hacer es simplemente seleccionarlos y darle click en aceptar.

Ahora si expandimos aqui y vemos la lista de referencias que tiene este proyecto ahora vamos a ver la referencia a los otros dos proyectos: ProyectoA.EquipoA y ProyectoA.EquipoB y ahora que las referencias ya fueron agregas ya podemos empezar a hacer uso de estos assemblies en la clase `Program`

```csharp
using System;
using ProyectoA.EquipoA;

class Program
{
    static void Main()
    {
    }
}
```

Y vean esto aunque `ProyectoA` en el assembly `ProyectoA.EqupoA.dll` y tambien tenemos el namespace `ProyectoA` en el otro assembly `ProyectoA.EqupoB.dll`

##[Parte 18][4]
Los namespaces no corresponden directamente a un archivo, directorio o assembly.
Osea pueden ser escritos en diferentes archivos y aun asi pertenecer al mismo namespace. Y con el ejemplo que les acabo de mostrar podemos digmaos entender un poco mas a que se refiere esto, como vimos tenemos dos proyectos cada unos generando sus propio assembly o dll y cada dll con sus propias clases pero ambos utilizando el mismo nombre de namepaces que era `ProyectoA`, digamos que los namespaces se pueden crear en cualquier parte y al momento de crear un programa podriamos pensar que al ser el mismo namespaces que existe en el mismo assembly, que todo el codigo correspondiente a ese namespaces esta junto en un mismo archivo, podriamos pensar eso pero como vimos en el ejemplo esto puede no ser asi, podemos tener proyectos separados compartiendo un mismo namespace.

Y los namespaces pueden ser anidados de dos maneras, a que me refiero con anidados pues que un namespaces exista dentro de otro.

Una forma de anidar los namespaces es escribiendo como aqui
```csharp
namespaces PryectoA.EqupoA 
{
```
Si vemos aqui hay dos namespaces separados por el . pero estan creados con una sola linea de codigo

Y otra forma de anidarlos seria:
```csharp
namespace PryectoA
{
    namespace EqupoA 
    {
```
Osea con dos lineas de codigo, dos namespaces pero uno esta dentro de otro, es lo equivalente a utilizar el punto.

Entonces podemos utilizar . para decir que un namespaces existe dentro de otro o agregarlso separados uno dentro de otro con la palabra reservada namespace el nombre y poner las llaves.

###[vs][01]
Entonces sigamos importando los proyectos al proyectos principal:

```csharp
using System;
using ProyectoA.EquipoA;
using ProyectoA.EquipoB;

class Program
{
    static void Main()
    {

    }
}
```

Y si queremos utilziar `ClaseA` vamos a tener el mismo problema que antes un conflicto de nombres. Y para evitarlo podemos utilizar un alias de namespaces.

```csharp
using System;
using PAEA = ProyectoA.EquipoA;
using PAEB = ProyectoA.EquipoB;

class Program
{
    static void Main()
    {

    }
}
```

Ahora con los alias si quiero utilziar la `ClaseA` dentro de `EquipoA` y `EquipoB` puedo hacerlo agregando el alias.

```csharp
using System;
using PAEA = ProyectoA.EquipoA;
using PAEB = ProyectoA.EquipoB;

class Program
{
    static void Main()
    {
        PAEA.ClassA.Imprimir();
        PAEB.ClassA.Imprimir();
    }
}
```

Y si corro el proyecto podemos ver los mensajes correpsondientes a cada clase.

## [Parte 18][4]

Las directivas de alas para los namespaces: Nos sirven para cuando tenemos nombres de naspaces muy largos y quereos utilizar uno mas corto o un acronimo y esto nos ayuda a que el programa sea mas facil de leer y escribir, tambien otra ventaja de uitlizar los alias es que podemos evitar conflictos entre nombres de clases.

## [Parte 18][5]

Hemos visto este ejemplo de namespace

```csharp
using System;
namespace ProyectoA.EquipoA
{
    public class ClaseA
    {
        public static void Imprimir()
        {
            Console.WriteLine("Equipo A metodo Imprimir");
        }
    }
}
namespace ProyectoA.EquipoB
{
    public class ClaseA
    {
        public static void Imprimir()
        {
            Console.WriteLine("Equipo B metodo Imprimir");
        }
    }
}
```
[22:34]

## [Parte 18][6]
[22:36]
Hemos visto como evitar conflictos o ambigüedad en los nombres utilizando el nombre completo de la clase con todos los namespaces

## [Parte 18][7]
y tambien podemos evitar los conflictos de nombres utilizando las directivas de alias para los usings.

## [Parte 18][8]
Hasta ahora hemos vistos que un namespaces puede contener clases y tambien otros namespaces

### [vs][1] 
Mostrar en el codigo...

Pero ademas tambien puedes contener, interfaces, enums, etc.
## [Parte 18][8]
Entonces un namespaces puede contener:
1. Otro Namespace
1. Clases (class)
1. Interfaces (interface)
1. Estructuras (struct)
1. Enumeradores (enum)
1. Delegados (delegate)

Hablaremos de clases, interfaces, structuras, enumeradores y delegados en proximas lecciones 

## [Parte 18][9]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.