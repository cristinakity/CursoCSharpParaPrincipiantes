# Contenido

[TOC]

# Parte 24 - Diferencia entre sobrescribir y ocultar un metodo en C#


## Pre - requisitos

- [ ] Agregar el siguiente codigo esto a visual studio antes de empezar
  
```csharp
using System;

public class ClaseBase
{
    public void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

## [Parte 24][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 24: Diferencia entre sobrescribir y ocultar un metodo en c#


## [Parte 24][2]

Em esta leccion veremos
* La diferencia entre sobrescribir y ocultar un metodo

Veamos un ejemplo

### [vs][01]

En este ejemplo como podemos ver tenemos una clase base con un metodo `Impirmir` el cual mostrara en pantalla el mensaje _"Metodo Imrpimir de la clase base"_

Ahora voy agregar otra clase para heredera de esta

```csharp
using System;

public class ClaseBase
{
    public void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{

}

public class Program
{
    public static void Main()
    {
    }
}
```

Esta `ClaseDerivada` tambien va a tener un metodo `Imprimir()`

```csharp
using System;

public class ClaseBase
{
    public void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase derivada");
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

En la leccion anterior Parte 23 hablamos sobre el polimorfismo, que era la forma en que una variable de la clase base podia invocar un metodo sobrescrito de la clase derivada en runtime o tiempo de ejecucion, entonces les sugiero ver el la parte 23 - Polimorfismo antes de continuar ocn este video.

Para implementar el polimorfismo aqui, primero voy a marcar el metodo  `Imprimir()` de la `ClaseBase` como `virtual`

```csharp
using System;

public class ClaseBase
{
    public virtual void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase derivada");
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```
Al marca el metodo como `virtual` en la clase base esto le indica a las clases derivadas que pueden sobrescribirlo.

Entonces ahora en la clase derivada voy a utilizar la palabra reservada `override` para sobrescribir el metodo `virtual` de la clase base.

```csharp
using System;

public class ClaseBase
{
    public virtual void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public override void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase derivada");
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Esto es la sobrescritura, estamos sobrescribiendo la implementacion de la clase base en la clase derivada.

Muy bien ahora si voy y creo una variable de la clase base que haga referencia a la clase derivada.

```csharp
using System;

public class ClaseBase
{
    public virtual void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public override void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseBase cb = new ClaseDerivada();
    }
}
```

Entonces como lo hemos visto en las lecciones anteriores una variable de la clase base puede ser igual a una instancia de la clase derivada, esto gracias a la herencia, si tienes duda acerca de esto te recomiendo ver la parte 21 - Herencia y la parte 22 - Ocultamiento de metodos de este tutorial.

Ya tenemos la variable de la clase base, ahora vamos a invocar al metodo `Imprimir()`

```csharp
using System;

public class ClaseBase
{
    public virtual void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public override void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseBase cb = new ClaseDerivada();
        cb.Imprimir();
    }
}
```

Entonces si vemos la variable de tipo `ClaseBase` esta haciendo referencia a la `ClaseDerivada`, pero gracias al polimorfismo al llamar al metodo `Imprimir()`, lo que va ha pasar es que se llamara al metodo sobrescrito en la clase derivada y no al metodo del tipo de la variable osea al de `ClaseBase`, esto porque en runtime el programa sabe que apesar de ser una variable de `ClaseBase` esta apuntado a `ClaseDerivada` y esta tiene una sobrescritura para el metodo.

>Si corremos esto, veremos el mensaje de la clase derivada
>Metodo Imrpimir de la clase derivada

Entonces como vimos en runtime el metodo sobrescrito en la `ClaseDerivada` es el que se llama apesar de uqe la variable es de tipo `ClaseBase`, y esto es basicamente sobrescribir un metodo.

## [Parte 24][3]
[3:36]

En la sobreescritura de métodos una variable de la clase base apuntando a un objeto de la clase derivada: invocara al método sobrescrito en la clase derivada

Como vemos en este ejemplo la variable `cb`  que es de tipo  `ClaseBase` toma el valor de una instancia de la clase derivada y al llamar al metodo imprimir esta invocara el metodo sobrescrito en la clase hija o derivada.

Esto es lo que pasa en la sobrescritura de metodos.

### [vs][01]

Veamos el ocultameinto de metodos:
¿Como ocultamos un metodo?

Para ocultar un metodo debemos utilizar la palabra reservada `new`


```csharp
using System;

public class ClaseBase
{
    public virtual void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public new void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseBase cb = new ClaseDerivada();
        cb.Imprimir();
    }
}
```
[04:04]
Cuando utilizamos la palabra reservada new en un metodo de una clase derivada lo que va a pasar es que este metodo dentro de la clase derivada va a ocultar al metodo de la clase base.

Muy bien ahora veamos en el metodo `Main()` que va ha pasar, tenemos una variable de tipo `ClaseBase` la cual apunta a una instancia de la `CalseDerivada` y estamos llamando al metodo `Imprimir()`, todo queda exactamente igual que en el ejemplo de sobrescritura que acabamos de hacer.

Como vemos `cb` apunta a una instancia de la `ClaseDerivada` pero en este caso como `cb` es de tipo `ClaseBase` al llamar al metodo `Imprimir()` se llamara al de la `ClaseBase`

Entonces si una variable de la ClaseBase esta apuntando a una clase derivada y la clase derivada esta ocultando al metodo, entonces el metodo de la clase base sera el que se invocara.  Esto es ocultamiento de metodos.

> Si coreemos este codigo veremos el mensaje de la clase Base
> Metodo Imrpimir de la clase base

Como la variable es de tipo `ClaseBase` y el metodo esta siendo ocultado por la clase derivada, al llamar Imprimir se llamara el de la `ClaseBase`

## [Parte 24][3]
Si vemos los dos ejemplso la unica diferencia entre Sobreescritura `Overriding` y Ocultamiento de metodos es que en sobreescritura utilizamos la palabra reservada `overrride` y en el ocultamiento utilizamos la palabra reservada `new`

Entonces esto en el lado izquierdo es Sobreescritura de metodos
y esta parte del lado derecho es ocultamiento de metodos

El resto del codigo es igual, la unica diferencia es la palbra reservada new o la palabra reservada override, si tenemos `override` en el metodo al crear una variable del tipo base que toma como valor una instancia de la clase hija o derivada, si llamamos a un metodo, al estar sobresescrito se llamara al metodo de la clase hija, osea que sobreescribira la funcionalidad de la clase base, de este modo sin importar que la variable sea del tipo Base, va ignorar el codigo dentro de la clase base, porque la clase hija lo esta sobrescribiendo.

Y cuando ocultamos metodos no pasa esto, si ocultamos un metodo dentro de la clase hija, este metodo sera accedido solo mediante una variable de la clase hija, si creamos una variable de  la clase padre y llamamos a un metodo que esta oculto en la clase hija, al no estar sobreescrito si no oculto, lo que va ha pasar es que el metodo de la clase base sera el llamado, el compilador mira el codigo y valida que el mismo metodo exist en ambas clases pero al no estar sobreescrito no es necesario sobreescribir el codigo de la clase base, y este es el metdoo que llamara al de la clase base.

Entonces Si tenemos variables de la clase base apuntando a una clase derivada existen estos dos escenario:
- Quiero llamar al metodo del hijo aunque tengo una variable de base.
  - En ese caso lo que podemos hacer es sobrescribir el metodo en la clase derivada para asi darle una nueva implementacion y no utilizar el codigo de la clase base
- Quiero llamar al metodo de la clase base y no al del hijo
  - En este caso no es necesario sobreescribir, podemos simplemente utilziar la palabra reservada new para ocultar el metodo.


### [vs][01]

Vamos a poner otro ejemplo, que tal si tengo el metodo oculto pero quiero llamar al metodo de la clase hija y no de la clase base, en ese caso lo que podemos hacer es simplemente crear la variable de la clase hija:

```csharp
using System;

public class ClaseBase
{
    public virtual void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public new void Imprimir()
    {
        Console.WriteLine("Metodo Imrpimir de la clase derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseBase cb = new ClaseDerivada();
        cb.Imprimir();
        
        ClaseDerivada cd = new ClaseDerivada();
        cd.Imprimir();
    }
}
```

> Como vemos tenemos los resultados esperados
> Metodo Imrpimir de la clase base
> Metodo Imrpimir de la clase derivada


## [Parte 24][6]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.