# Contenido

[TOC]

# Parte 25 - Sobrecarba de metodos en C#

## [Parte 25][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 25: Sobrecarba de metodos en C#

## [Parte 25][2]

Em esta leccion veremos
* ¿Qué la sobrecarga de metodos? 

Solo para tenerlo en mente la sobre carga es conocida tambien como el `Overloading`.

Veamos un ejemplo

### [vs][01]
Digamos, por ejemplo, que ya tengo una función llamada `sumar`, y esta función va a recibir 2 números enteros `int primerNumero` y  `int segundoNumero`, y lo que va a hacer esta función es sumar estos 2 números e imprimir el resultado de la suma en pantalla.

```csharp
using System;

public class Program
{
    public static void Main()
    {

    }

    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
}
```

Muy bien tengo una función llamada sumar y digamos ahora que quiero agregar otra funcion con el mismo nombre.

¿Es esto posible?, si pero Ambos funciones deben ser diferentes en el número o el tipo de parámetros.

```csharp
using System;

public class Program
{
    public static void Main()
    {

    }

    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
    
    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
}
```

Y vean esto, ahora que tenemos 2 funciones exactamente iguales la segunda funcion esta subrayada rojo porque tenemos un error y el error es porque la clase Program ya tiene definido un miembro de clase igual osea que ya hay un metodo con el mismo nombre, número de parámetros y tipo de parámetro. 

Entonces, como dije antes, para poder tener 2 funciones que se llaman igual, estas deben de ser diferentes en el número o el tipo de parámetros.

Vamos a cambiar un poco la segunda función para que en lugar de sumar 2 números pueda sumar 3 numeros.

```csharp
using System;

public class Program
{
    public static void Main()
    {

    }

    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
    
    public static void Sumar(int primerNumero, int segundoNumero, int tercerNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero + tercerNumero}");
    }
}
```

Con este cambio, el código ya no marca error. Y esto, básicamente, es la sobrecarga de funciones, entonces en este caso la función sumar está siendo sobrecargada y tiene 2 sobrecargas, o sea, tiene 2 definiciones de la misma función con el mismo nombre pero diferente número de parámetros.

También puede se puede sobre cargar un metodo o funcion cambianto el tipo de parámetros los párametros.

En este ejemplo simple agregamos un tercer parámetro creando asi una sobrecarga del metodo `Sumar`.

Con este cambio, ahora si intento llamar a la función `Sumar` dentro del método `main` lo que va a pasar es que me me va a mostrar las sobrecargas entonces al escribir el nombre de la función sumar y abrir el paréntesis, vamos a ver aquí que hay un número 2, el cual significa que esta función tiene 2 sobrecargas, Y si vemos la definición de estas sobrecargas, aquí vemos que en la primera está recibiendo dos valores enteroes y en la segunda sobrecarga está recibiendo 3 valores enteros.

Así que las funciones pueden ser sobrecargadas basandonos en el número de parámetros.

Muy bien. Ahora vamos a crear otro sobrecarga para esta función, `Sumar`.


```csharp
using System;

public class Program
{
    public static void Main()
    {

    }

    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
    
    public static void Sumar(int primerNumero, int segundoNumero, int tercerNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero + tercerNumero}");
    }
    
    public static void Sumar(int primerNumero, int segundoNumero, int tercerNumero, int cuartoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero + tercerNumero}");
    }
}
```

Cree otra sobrecarga que ahora recibe cuatro números enteros. 
Entonces ahora si vuelvo al método `main` y vuelvo a ver el cuántas diferentes versiones o diferentes sobrecargas de la función, `sumar`, existen ahora en lugar de ver el número 2, aquí estamos viendo el número 3 porque ahora este método tiene 3 diferentes versiones o sobrecargas.

Básicamente una función puede ser sobrecargada basándonos en el número de parametros que recibe.

Pero Por otro lado, digamos que quiero sumar 2 números de tipo float. ¿Podemos hacer eso con el mismo metodo?, si vamos hacerlo:

```csharp
using System;

public class Program
{
    public static void Main()
    {

    }

    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
        
    public static void Sumar(float primerNumero, float segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
}
```

Si vemos estos 2 métodos, los 2 tienen el mismo nombre y el mismo número de parámetros, pero tienen diferente tipo de parámetros.

En el primer método `sumar` los parámetros son de tipo entero y en el segundo, que como vemos son de tipo `float`.

Ahora, si llamamos este método desde el método main, vamos a ver quién va a tener 2 sobrecargas también, y con lo cual podemos ver que los métodos o funciones también pueden ser sobrecargados, basándonos en el tipo de parámetros.

```csharp
using System;

public class Program
{
    public static void Main()
    {
        Sumar(3.25,2.83);
    }

    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
        
    public static void Sumar(float primerNumero, float segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
}
```

Y podríamos agregar otro método que también tome 2 parámetros, o sea, con el mismo número de parámetros.que el primer parámetro sea un entero y el segundo sea 
 

```csharp
using System;

public class Program
{
    public static void Main()
    {
        Sumar(3.25,2.83);
    }

    public static void Sumar(int primerNumero, int segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
        
    public static void Sumar(float primerNumero, float segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }

    public static void Sumar(int primerNumero, float segundoNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero}");
    }
}
```

Si intento llamar otro otra vez el método desde el método `main` vamos a poder ver que ahora tiene 3 opciones para llamar este método que va a ser la primera donde es recibe 2 variables enteras, la segunda, donde recibe 2 variables de tipo `float` y la tercera, donde recibe una variable de tipo `Int` y otra de tipo `float`.

Entonces, un método puede ser sobrecargado, basándonos en el número y en el tipo de parámetros.

Un método también puede ser sobrecargado, basándonos en el tipo de modificador del parámetro. 
¿Y a qué nos referimos con el tipo de modificador de parámetros? En la parte 17 de este tutorial Ya hemos visto los tipos de parámetros dentro de los métodos en C#.  Los cuales pueden ser parámetros por valor, parámetros por referencia, el modificador de parámetro `out` y el modificador de parámetro `in`.

Entonces, es posible sobrecargar un método por el tipo de parámetro y vamos a ver el ejemplo, cómo hacer estoÑ

```csharp
using System;

public class Program
{
    public static void Main()
    {
        Sumar();
    }

    public static void Sumar(int primerNumero, int segundoNumero, int tercerNumero)
    {
        Console.WriteLine($"Suma = {primerNumero + segundoNumero + tercerNumero}");
    }
    
    public static void Sumar(int primerNumero, int segundoNumero, out int suma)
    {
        suma = primerNumero + segundoNumero;
        Console.WriteLine($"Suma = {suma}");
    }
}
```

Bueno, entonces este sería un tipo de parámetro o tipo de modificador de parámetro, en lugar de que sea un parámetro por valor, al ponerle `out`, va a ser un parámetro de salida o parámetro de tipo `out` y aunque los 2 métodos estén recibiendo el mismo número de parámetros y en los 2 métodos los parámetros son enteros; Estamos creando la sobrecarga, al agregarle el modificador del parámetro `out` en la en el segundo método.

Si tienen dudas acerca de los tipos de parámetros en los métodos y acerca de los modificadores de parámetros, por favor, revisen en la parte de 17 de este tutorial, tipos de parámetros dentro de los métodos C#.

Muy bien, Entonces. Ahora si vemos ambos métodos son muy muy similares la única diferencia es que en el primer método el `tercerNumero` es un parámetro `int` y se esta pasando por valor o value type, y en el segundo método tenemos el parámetro suma que es un parametro entero y de salida. 

Entonces con esto vemos que un método también se puede sobrescribir basándonos en el tipo de parámetro que no es lo mismo que el tipo de dato, el tipo de dato es `Int`. El tipo de parámetro es: Si son de entrada, de salida, si se pasan por refernecia o por valor.

Ahora si intento llamar al método en el método `main`, vamos a ver que hay 2 sobrecargas para este método, es la primera donde me pide 3 valores enteros que se están pasando por valor. Y en el segundo, que me está pidiendo 2 valores enteros por valor y un valor entero de tipo salida.

Podemos sobrecargar una metodo o funcion basandonos en el tipo de parametro.

## [Parte 25][3]

Sobrecarga de funciones y sobrecarga de métodos son términos intercambiables o sea que significan lo mismo.

La sobrecarga de métodos permite una clase, tener muchos métodos con el mismo nombre pero con diferente firma o signature. Eso es lo que acabamos de ver en los ejemplos que estuvimos haciendo.

En c# los métodos funciones pueden ser sobrecargados basándonos en el número, el tipo de dato y el tipo de parámetros.

Si vemos lo que es la firma de un método entonces y la definición de cómo se realiza la sobrecarga en C#.
Básicamente es que en C# los métodos se pueden sobrecargar, si cambiamos la firma del método, o sea, si cambiamos el tipo de parámetro, el tipo de dato o el número de parámetros que recibe y Obviamente el nombre tiene que ser el mismo para que sea una sobrecarga. 

Entonces, si vemos la firma del método ¿qué incluye? pues incluye 
* el nombre del método, 
* el tipo de parámetro del tipo de dato y 
* el número de parámetros que tiene el método. 

Ahora si cambiamos cualquiera de los 3: tipo de parámetros, tipo de dato o número de parámetros, podemos crear la sobrecarga con el mismo nombre, entonces podemos decir que en C# lo que debemos de cambiar es la firma del método para poder crear sobrecargas de métodos.

¿Y qué queremos decir con la firma de un método? Pues regresamos al Código para verloÑ

### [vs][01]
Bien, como vemos, en este método suma: `Suma` es el nombre, los parámetros o el número de parámetros que recibe este método están aquí, son estas variables, separadas por las comas, después de cada coma se cuenta otro nuevo parámetro, el tipo de dato de cada parámetro viene siendo si es un `int`, si es un `float`, `string`, etcétera y aparte también tenemos los modificadores de parámetros o tipos de parámetros que si es de salida, si es de entrada, si es por referencias o de valor.

## [Parte 25][3]
Muy bien, entonces lo que estamos viviendo aquí en la Diapositiva es lo mismo que vimos allá en el código, o sea, vemos que la firma del método tiene nombre, El método tiene tipo de parámetro, tiene los tipos de datos y también número de parámetros.

Y hablando de la firma del método, debemos de tomar en cuenta que ésta no incluye el tipo de retorno ni el modificador `params` así que nos podemos sobrecargar un método basándonos en el tipo de retorno del método o en el modificador `params`.

### [vs][01]

Si vemos el código, el tipo de retorno `void` no es parte de la firma el método, entonces si cambiamos el tipo de retorno, no podemos sobrecargar el método porque no es parte de la firma.

Pero entonces, para visualizar esto, vamos a crear 2 métodos iguales con el mismo tipo de dato, número y tipo de parámetros, p ero con diferente tipo de retorno:

```csharp
using System;

public class Program
{
    public static void Main()
    {
        Sumar();
    }
    
    public static void Sumar(int primerNumero, int segundoNumero, out int suma)
    {
        suma = primerNumero + segundoNumero;
        Console.WriteLine($"Suma = {suma}");
    }

    public static int Sumar(int primerNumero, int segundoNumero, out int suma)
    {
        suma = primerNumero + segundoNumero;
        Console.WriteLine($"Suma = {suma}");
        return suma;
    }
}
```

Al hacer esto, el compilador nos está mostrando un error, el cual dice que el método sumar ya existe.
Y con esto vemos que no se puede sobrecargar un método basándonos en el tipo de retorno del metodo.

Tampoco es posible sobrecargar una función basándonos en la palabra reservada `params`, veamos que quiero decir con esto:

```csharp
using System;

public class Program
{
    public static void Main()
    {
        Sumar();
    }
    
    public static void Sumar(int primerNumero, int segundoNumero, params int[] numeros)
    {
        var suma = primerNumero + segundoNumero;
        Console.WriteLine($"Suma = {suma}");
    }
}
```

Bien, entonces tengo esta función `sumar` donde recibo 3 parámetros el primero es un entero `primerNumero`, el segundo es un entero `segundoNumero` y el tercer elemento que está recibiendo es un elemento de tipo `params` que los `params` son arreglos y por eso está recibiendo un arreglo de enteros y la variable se llama números.

Muy bien, entonces lo que voy a hacer es crear un método exactamente igual y sólo voy a remover la palabra reservada `params` y veremos qué pasa.

```csharp
using System;

public class Program
{
    public static void Main()
    {
        Sumar();
    }
    
    public static void Sumar(int primerNumero, int segundoNumero, params int[] numeros)
    {
        var suma = primerNumero + segundoNumero;
        Console.WriteLine($"Suma = {suma}");
    }

    public static void Sumar(int primerNumero, int segundoNumero, int[] numeros)
    {
        var suma = primerNumero + segundoNumero;
        Console.WriteLine($"Suma = {suma}");
    }
}
```

Bien, como vemos, el compilador nos está arrojando un error y es el mismo error de hace rato, o sea, que la clase `Program` ya tiene definido un miembro de clase con el mismo nombre y el mismo tipo de parámetros, entonces no podemos tomar en cuenta la palabra reservada `params`, para sobrecargar métodos.

## [Parte 25][3]

Muy bien entonces, como vimos en los ejemplos la firma del método tiene el nombre del método, el tipo de parámetro, los tipos de datos y el número de parámetros.

El tipo de retorno del método que puede ser `void`, `Int`, `String`, etcétera, no se incluye dentro de la firma ni tampoco la palabra reservada `params`, que sería en este caso un tipo de parámetro, pero éste no se toma en cuenta a la hora de sobrecargar metodos. Los demás tipos de parámetros como cuando son de salida, de entrada, o por referencia si se tomane en cunta para la firma de un metodo y para la sobrecarga de metodos.

## [Parte 25][4]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.