# Contenido

[TOC]

# Parte 29 - Diferencias entre clases y estructuras en C#

## [Parte 29][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 29: Diferencias entre clases y estructuras en C#

## [Parte 29][2]

Em esta leccion hablaremos a cerca de las
* Diferencias entre clases y estructuras

## [Parte 29][3]

En la parte 28 de esta serie de video comprendimos que las estructuras son muy similares a las clases.  Se utiliza la palabra reservada struct para crear una estructura a diferencia de la clases que se utiliza la palbra reservada `class` para crear clases.

Al igual que las clases las estructuras pueden tener campo, propiedades, constructores y métodos.

Sin embargo, existen varias diferencias entre las clases y las estructuras de las cuales hablaremos en esta lección.

## [Parte 29][4]

Una estrucura es value type o tipo de valor mientra que una clase de reference type o tipod de referencia.

Todas las diferencias que son aplicables a los value types o reference types también aplican para las clases y estructuras.

Hasta ahora no hemos hablado mucho de los value tipes pero hay algunos value types en c# uno de ellos son las estructuras y otros son algunos tipos de datos como `int`, `boolean`, etcétera. Y con respecto a los reference types, también hay otros reference types en c#, de momento ya hemos visto las clases, pero también están las interfaces y los delegados que también de los cuales hablaremos más adelante.

Entonces, las estructuras hacer value type o tipos de valor, estas se alamcenan en el stack o la pila de la memoria, estas son almacenadas en el stack mientras que las clases se almacenan en el heap o el monton.
¿Bueno se preguntaran que es stack y el heap? Pues cada vez que corremos un programa todas las variables, todos los objetos, todas las instancias se van a almacenar en la memoria de la computadora mientra que la aplicacion se este ejecutanto, Y esta memoria de la computadora va a ser lógicamente dividida por el runtime de .Net en el stack y el heap.

## [Parte 29][6]

Si vemos esta diapositiva y digamos por ejemplo que tengo una clase simple con dos propiedades, 

### [vs]-01
```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {

    }
}
```
y vamos a escribir un programa muy simple 

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 0;

        if(i == 10)
        {
            int j = 20;
            Cliente c1 = new Cliente();
            c1.Id = 101;
            c1.Nombre = "Homero";
        }
    }
}
```
Este es un programa muy simple para ilustrar cómo estas variables `i`, `j`, `c1` son creadas en memoria.  Si vemos el tipo `int` al ser una estrucutra pues tambien es value type por lo tanto este valor va ser almacenado en el **stack**.  Y si ponemos el mouse sobre `int` vemos que nos dice que es una estructura que viene de `System.Int32`, entonces la palabra reservada `int` es en realidad un alias de la estrcutura `System.Int32` entonces podemos utilizar `System.Int32` en lugar `int` y es perfectamente valido y tendra el mismo comportamiento, pero es mas facil escribir solamente `int` que el nombre completod e la estrcutura y aparte en otros lengaujes tambien se utiliza simplemente `int`en general es mas conveniente utilizar el alias `int`.

## [Parte 29][6]
Entonces, si regresamos a la diapositiva y si vemos el código aquí, la variable `i` y la variable `j` son enteros que vienen de una estructura `System.Int32` y si regresamos a la diapositiva, vemos que estos valores van a ser almacenados aquí en la pila o en el stack de la memoria.

### [vs]-01
Pero por otro lado si vemos la variable `c1` es una clase, al ser una clase es reference type, entonces para los tipos de dato de referencia tendremos dos cosas en la memoria una variable de referencia en el stack y el objecto con todos los valores creado en el heap o el monton.

Si vemos el diagrama en la dispositiva esto es loq ue esta pasanndo cuadno creamos la variable `c1` esta es una variable de referencia que apunta a una posicion de memoria del heap donde esta el objecto realmetne almacenado, y en el heap tendremos la instancia donde se guardan todos los valores de la variable `c1`.

Cuando hablamos de objecto he instancias, hay dos cosas que existiran en la memoria una es la variable de referencia del objecto y otra es el objecto en si.  Entonce los objectos son diferente de las variables de referencia del objeto, no son lo mismo.  Si lo pensamos de otra manera las vairalbes der referencia del objeto serian solo apuntadores que nos indican donde esta almacenada la instancia del objeto.  Entonces en el stack se guardan los value type y las variables de referencia del objecto y los objectos en si se guardan en el heap de la memoria.

Volvamos a las demas diferencias entre clases y estructuras 

## [Parte 29][4]

Las estructuras se almacenan en el stack(la pila), mientras que las clases se almacenan en el heap(el montón).

[05:54]
Los tipos de valor mantienen su valor en memoria cuando son declarados mientras que los tipos de referencia mantienen una referencia a un objeto en la memoria.

Esto es lo que acabamos de ver:

## [Parte 29][6]

Value types se guarda en el stack donde mantienen el valor, mientras que reference types solo guardan la varible de referencia en el stack y el objeto en si se guarda en el heap.

## [Parte 29][4]

Los tipos de valor son destruidos inmediatamente después de que ya nadie los utiliza o de que pierden el scope, mientas que en los tipo de referencia solo la variable de referencia es destruida después de que se pierde el scope, el objecto se destruirá después por el garbage collector. (Hablaremos del garbage collector o recolector de basura en próximas lecciones.)


### [vs]-01

Si vemos este progrma el scope de estas variables sera dentro del metodo `Main()`, las llaves desde que se abren hasta donde se cierran estan creando el scope que es donde van a existir estas variables, entonces por ejemplo la variable `i` va a estar disponible durante la ejecucion de esta seccion o este scope del codigo, y si vemos la variable `j` esta solo va a existir dentro del `if` lo cual significa que el scope para la variable `j` es dentor de estas llaves y va a ser destruida tan pronto como el runtime termine de ejecutar la linea final del `if`.

Digamos por ejemplo que tengo otra linea de codigo aqui:

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 0;

        if(i == 10)
        {
            int j = 20;
            Cliente c1 = new Cliente();
            c1.Id = 101;
            c1.Nombre = "Homero";
        }
        Console.WriteLine("Hay caramba");
    }
}
```

Entonces, ¿qué va a pasar aquí con la memoria? si vemos en el stack se va a crear `i`, se va a crear la variable `j`, también se va a crear la referencia al objeto con la variable `c1`, la variable de referencia y aparte se va a crear en el hep, el objeto en sí con los valores id = 101 nombre=Homero. Pero al explicar la parte de los scopes y cómo es que van a ser creadas las variables, si vemos el código como `j` está en un scope más pequeño `j` va a vivir menos en la memoria que y `i`, entonces `i` va a vivir toda el scope the `Main` pero `j` sólo va a existir en el scope del `if`, si vemos le `if` es una partecita de todo el código de `Main`.  

Dicho esto tan pronto como la ejecucion llegue a la linea despues de la llave de cierre del `if` la variable `j` sera destrudia de la memoria o del stack que es donde esta almacenada.

Entonces los tipos de valor o value types seran destruidos tan pronto como pierdan el scope, osea tan pronto como dejen de ser necesarias, si ya no se esta ejecutando este `if` ya no se necesita las variables creadas dentro del `if`.

Cuando la ejecucion llegue a la linea final de `Main` tambien la variable `i` sera destruida.  Pero en el caso de la variable `c1` y del objecto en memoria de `Cliente`
al ser reference type, el objeto no sera destruido al perderse el scope, lo que se va a destruir es la variable de referencia al objeto, osea `c1` sera destruida inmediatamtne pero el objecto en el heap no sera destruido, el scope de `c1` es el `if` al igual que la variable `j`, entonces `j` y `c1` van a perder el scope al mismo tiempo y seran destruidas pero como `c1` apunta a una referencia donde esta un objeto este objeto no va a ser desturido inmediatemante si no que el garbage collector o recolector de basura sera quien se encargue de destruirlo despues, el garbage collector va estarse ejecutanto mientras corramos el programa, y cuando se de cuenta que nadie esta haciendo referencia a ese objeto o que nadie esta apuntado a ese objeto es cuando lo va a destruir o remover del heap.  Hablaremos a detalle del garbage collector mas adelante en proximas lecciones.

Hay que recordar que los value types o tipos  de valor se almacenan en el stack o la pila de la memoria y los reference types o tipos de referencia son almacenados en el heap o el monton de la memoria.

Tambien los value types se destruyen inmediatamente cuando pierden el scope y lo reference types se destruye la variable de referencia al objeto pero el objeto en si sera destruido despues por el garbage collector.

Estas son las diferencias importantes que hay que tomar en cuenta cuando se habla de tipos de datos de valor y tipos de datos de referencia.  Volvamos a las demas diferencias entre clases y estrucutras.


## [Parte 29][4]

Cuando pasamos el valor de una estructura a otra estructura, se crea una nueva copia y si modificamos algo en alguna de las estructura esos cambios no se verán reflejados en la otra.

Esta es otra diferencia importante entre los value types y reference types, ¿Qué es lo que pasa cuando copias un value type? ¿Y qué es lo que pasa cuando copias un reference type?Veamos un ejemplo.

### [vs][01]


```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 10;
        int j = i;
    }
}
```

Si vemos este ejemplo, tenemos la variable `i` que vale 10 y luego la varialbe `j` que vale igual a `i` osea estamos copiando una estructura a otra estructura.  Entonces, lo que va a pasar aquí en este ejemplo al ser estas variables estructuras por lo tanto son value types y vamos a tener en el stack de la memoria `i=10` y después en el mismo stack de la memoria va a estar `j=10` entonces en realidad, cuando pasamos el valor de `i` a la variable `j` se está creando otra otro valor en el stack de la memoria o una copia de `i`. Asi que cada variable va a estar apuntando a diferentes lugares de memoria. 

Ambas van a existir en el stack, cada una con su propio valor, o sea, se va a crear una copia del valor de `i` o mas bien se va a pasar  el valor, por eso son value type, porque se pasa el valor cuando se asigna una variable a otra, se pasa el valor. Entonces como estamos pasando nada más, el valor de 10 en el Stack va a estar creada `i=10` y también va a estar `j=10`.

Dicho esto si despues modifico el valor de `j`, por ejemplo: 

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 10;
        int j = i;
        j = j + 1;
    }
}
```

Entonces lo único que hice fue incrementarle uno a `j`, entonces ahora `j=j+1`. Y si mostramos los valores en pantalla, veremos que `i` va seguir valiendo 10, osea que cambios hecho en `j` no afectan el valor de `i`.

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 10;
        int j = i;
        j = j + 1;
        Console.WriteLine($"i={i}, j={j}");
    }
}
```

>Corramos el ejemplo y comov emos i vale 10 y j vale 11
>i=10, j=11

Entonces, modificaciones hechas a la variable `j`, no van a afectar el valor de `i` esto porque cuando pasamos una variable de value type a otra se crea una copia.  Y operaciones hechas en una variable no van a afectar a la otra porque son dos copias diferentes.

Pero por otro lado veamos que pasa cuando copiamos un tipo de referencia.
Como sabemos una clase es un tipo de referencia. Asi que voy a crear una instancia de `Cliente`:

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 10;
        int j = i;
        j = j + 1;
        Console.WriteLine($"i={i}, j={j}");

        Cliente c1 = new Cliente();
        c1.Id = 101;
        c1.Nombre = "Homero";
    }
}
```

Ya cree una instancia de `Cliente`, ahora voy a crear otra variable de tipo `Cliente` y le voy asignar el valor de `c1`:

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 10;
        int j = i;
        j = j + 1;
        Console.WriteLine($"i={i}, j={j}");

        Cliente c1 = new Cliente();
        c1.Id = 101;
        c1.Nombre = "Homero";

        Cliente c2 = c1;
    }
}
```

Al igual como copiamos `j=i` que son de value types, estamos haciendo lo mismo, `c2=c1` que son reference types. Cuando copio el valor de un reference type a otro reference type.Lo que va a pasar es que no va a crear una copia del objeto, sino que sólo va a crear una copia de la variable de de referencia al objeto, Y ambas copias de la variable van a apuntar a la misma referencia o al mismo objeto almacenado en el heap o el monton.

## [Parte 29][6]

Si vemos aquí en el segundo diagrama, en la parte de abajo tenemos creadas la variable de referencia al objeto `c1` y la variable de referencia al objeto `c2` y ambas apuntana la misma referencia de memoria o la misma posición del heap dónde está guardado el objeto.  En este caso dos variables apuntan al mismo objeto, al ser asi, obviamente si hago cambio en `c2` se veran reflejados en `c1` y viceversa, veamos esto en un ejemplo.

### [vs][01]

Si vemos el código como `c2` es igual `c1` y el nombre es de `c1` es Homero, Por lo tanto, el hombre es de `c2`, va a ser Homero también, porque comparten el mismo valor en estos momentos, pero si más adelante cambiamos el nombre de `c2` y vamos a hacer esto para ver qué pasa.

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 10;
        int j = i;
        j = j + 1;
        Console.WriteLine($"i={i}, j={j}");

        Cliente c1 = new Cliente();
        c1.Id = 101;
        c1.Nombre = "Homero";

        Cliente c2 = c1;
        c2.Nombre = "Ned";

        Console.WriteLine($"c1.Nombre={c1.Nombre}, c2.Nombrre={c2.Nombre}");
    }
}
```

## [Parte 29][6]

Ahora estamos cambiando el valor del objeto, entonces, si vemos el cómo se están almacenados en memoria. Como ambas apuntan al mismo objeto. En realidad, no importa el nombre de de que variable mostremos en pantalla, o sea, si es el nombre de `c1`, o el nombre de `c2`. Ambos van a estar apuntando a la misma posición de memoria. Por lo tanto, van a tener el mismo valor.

### [vs][01]

> Ejecutemos el codigo y veamos que ambas clases tienen el mismo nombre
> c1.Nombre=Ned, c2.Nombre=Ned

Como vemos en los ejemplos, cuando creamos una copia de un value type se va a crear una copia de la variable en el stack o la pila de la memoria y tendremos dos variables con diferentes valores, pero cuando creamos una copia de un reference type se va a crear una copia de la variable de referencia al objeto en el stack y ambas variables van a estar apuntando al mismo objeto en el heap o en el montón de la memoria.

Esto es una diferencia muy importante entre value type y reference types y, obviamente, entre clases y estructuras, porque las clases son reference type y las estructuras son value types.


## [Parte 29][5]

Otra diferencia es que las estructuras no pueden tener destructores mientras que las clases si.

### [vs][01]

Muy bien como sabemos, las clases pueden tener destructores y el destructor es similar a un constructor, nada más que tiene la tilde de la eñe al inicio y no pueden tener moficadores de acceso, vamos a crear un destructor para esta clase `Cliente`.

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }

    ~Cliente
    {        
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Ya está creado el destructor y si compiló el programa todo va a estar ok, no voy a tener ningún error porque las clases pueden tener destructores. 

En cambio si cambio la palabra reservada `class` por `struct` para convertir esto en una estructura:
 
```csharp
using System;

public struct Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }

    ~Cliente
    {        
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Si compilo el código ahora voy a tener un error y el error dice que sólo las las clases pueden tener destructores.  Esta es otra diferencia importante entre clases y estructuras.

## [Parte 29][5]

Otra diferencia es que las estructuras no pueden tener un constructor explicito sin parámetros mientras que las clases si.  Veamos un ejemplo:

```csharp
using System;

public class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }

    public Cliente()
    {
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Bien, lo que hicimos fue crear un constructor sin parametros explicitó. Esto significa que nosotros lo definimos por eso es explicito y no recibe ningún parámetro, recordemos que por default si no ponemos este constructor explícito de igual manera un constructor igual será creado por c# de manera implicita, sin que lo definamos, osea no lo vamos a ver en codigo pero podra ser llamado aunque no lo hayamos definido explicitamente.

Las estructuras no pueden tener un constructor sin parametros declaraod explicitamente, osea no podemos agregarle un constructor sin parametros a una estructura.  Para probar esto solo voy a cambiar la palabra reservada `class` por `struct` para convertir esta clase en una estructura.

```csharp
using System;

public struct Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }

    public Cliente()
    {
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Si compilo este codigo veremos que hay un error que dice que las estructuras no pueden tener un constructor sin parametros declarado explicitamente. 

## [Parte 29][5]

Esta es otro diferencia entre clases y estructuras. Y tiene sentido porque las estructuras no tienen el concepto de variables de referencia de objeto ni tampoco tiene referencias, entonces no necestian un constructor sin parametros ni tampoco un destructor, pero una clase si necestia tenerlos.

[18:08]

Ejemplos de estructuras que tenemos en c# son los tipos de datos `int` y `double`, los cuales son alias para estructuras, si hablamos de `int` este es solo un alias para la estructura `System.Int32`, y `double` es un alias para la estructura `System.Double`.

Las estructuras no pueden ser heredadas, pero ambas estructuras y clases pueden heredar de interfaces. Las clases si pueden ser heredadas.

Una clase o una estructura no pueden heredar de una estructura, esto significa que una estructura no puede ser usada como base, esto se debe a que las estructuras son tipos sellados o sealed types.  

¿Qué son los tipos sellados o sealed types?, veamos un ejemplo:

### [vs][02]

```csharp
using System;

public sealed class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }

    public Cliente()
    {
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Para crear una clase como `sealed type`, solo tenemos que agregarle la palabra reservada `sealed`.  

Cuando marcamos una clase como sellada o `sealed` esta clase ya no podra ser heredada, o ya no podra ser usada como clase base para otra clase.  Si intento que `Program` herede de `Cliente` tendremos un error de compilacion:

```csharp
using System;

public sealed class Cliente
{
    public int Id { get; set; }
    public string Nombre { get; set; }

    public Cliente()
    {
    }
}

public class Program : Cliente
{
    public static void Main()
    {
    }
}
```

Si vemos el error: Program no puede derivar del tipo sellado Cliente.  Pero si remuevo la palabra reservada `sealed` de la clase `Cliente` y compilo, no tendremos ningun error.

Recordemos que para prevenir que una clase pueda ser usada como clase base, o prevenir que una clase pueda ser heredada utilizamos la palabra reservada `sealed`.  De hecho esta una pregunta comun en las entrevistas de trabajo: ¿Cómo prevenir que una clase pueda ser heredara? O ¿Cuál es el significado de la palabra reservada sealed? y las estructuras son tipos sellados asi que no pueden ser heredadas.

## [Parte 29][7]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.