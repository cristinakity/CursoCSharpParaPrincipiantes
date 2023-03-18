# Contenido

[TOC]

# Parte 22 - Ocultamiento de metodos en C#

## Pre - requisitos

- [ ] Agregar el siguiente codigo esto a visual studio antes de empezar
```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class Program
{
    public static void Main()
    {

    }
}
```

## [Parte 22][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 22: Ocultamientos de metodos en c#

## [Parte 22][2]

Em esta leccion veremos
* Ocultamiento de métodos
* Como invocar un método oculto

Veamos um ejemplo

### [vs][01]
En la leccion anterior creamos un clase Base llamada `Empleado` y tambien creamos 2 clases derivadas o hijas: `EmpleadoDeTiempoCopmleto` y `EmpleadoDeTiempoParcial`, las cuales heredaban de la clase `Empleado`.

Si no has visto la leccion anterior Parte 21 - Herencia en C#, es muy recomendable que la veas antes de ver esta leccion

Muy siguiendo con el ejemplo, aqui tengo una clase `Empleado` y vamos a crear una clase derivada

```csharp
public class EpleadoDeMedioTiempo : Empleado
{

}
```

Y de la misma manera voy a crear la clase `EmpleadoDeTiempoCompleto`

```csharp
public class EpleadoDeTiempoCompleto : Empleado
{

}
```

Muy bien, Ahora vamos a crear un objeto de `EmpleadoDeTiempoCompleto` en metodo `Main`

```csharp
public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
    }
}
```

Y por la herencia ya sabemos que una clase derivada tendra acceso a las propiedades de la clase base, esto nos va permitir inicializar el Nombre y el Apellido

```csharp
public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();
    }
}
```

De igual manera podemos crear un objeto para `EpleadoDeMedioTiempo`

```csharp
public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    }
}
```

Si corremos esto, ¿que es lo que va a pasar?, pues se van a inicializar los valores para ambas clases derevidas y se mostrar en pantalla el nombre completo utilizando el metodo `ImprimirNombreCompleto()` de la clase base

>Ejecutemos el codigo, veremos lo resultados esperados..
>Homero Simpson
>Ned Flanders

Ahora digamos que nos piden de requerimiento que al imprimir el nombre de un empleado de tiempo completo pongamos entre parentesis la palabra `(temporal)` para identificar que es un empleado temporal.

Lo que podemos hacer para lograr esto es: en la clase de `EmpleadoDeMedioTiempo` puedo agregar un metodo `ImprimirNombreCompleto()`

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    }
}
```

Al hacer esto, si vemos el codigo la clase `EmpleadoDeMedioTiempo` hereda de la clase `Empleado` y la clase base `Empleado` tiene el metodo `ImpirmirNombreCompleto()` y a su vez la clase derivada  `EmpleadoDeMedioTiempo` tiene su propio metodo  `EmpleadoDeMedioTiempo`, al hacer esto ¿Que pasa?, pues el metodo en la clase derevida va a _ocultar_ el metodo de la clase blase.

Entonces ahora cuando llame `ETP.ImprimirNombreCompleto()` el codigo que se va a ejecutar sera el que esta en la clase hija `EmpleadoDeMedioTiempo` y no el que viene herado de `Empleado`

Ahora vamos agregarle entre parentesis la palabra temporal al metodo de la clase hija.

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    }
}
```

> Ahora con este cambio si corremos el codigo veremos que ahora para los empleados de medio tiempo veremos un texto extra el cual nos ayuda a identificar que es un empleado temporal.
> Homero Simpson
> Ned Flanders(Medio tiempo)

Este es el comportamiento esperando.  Regresemos al codigo.

Si vemos el metodo `ImprimirNombreCompleto()` en la clase `EmpleadoDeMedioTiempo`, esta subrayado de color verde y si ponemos el mouse encima podemos ver el mensaje:
> _'`EpleadoDeMedioTiempo.ImprimirNombreCompleto()`' oculta el miembro heredado '`Empleado.ImprimirNombreCompleto()`'. Use la palabra clave new si su intención era ocultarlo._

Entonces lo que vemos aqui en esta advertencia es que si queremos intencionalmente ocultar el metodo de la clase base, tendremos que utilizar la palabra reservada `new`, que si recordamos es la misma que se usa para crear las instancias de las clsases.

Entonces como si queremos intencionalmente ocultar el metodo de la clase `Empleado` y en su lugar utilizar el de la clase `EmpleadoDeMedioTiempo`, como si queremos ocultarlo vamos agregar la palabra reservada o palabra clave `new`:


```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public new void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    }
}
```

Despues de agregar la palabra `new` al metodo para indicar que intencionalmente estamos ocultando el metodo de la case base, si corremos el programa el resultado sera el mismo, pero si vemos ahora ya no esta subrayado de color verde por lo tanto ya no tenemos la advertencia que se mostraba antes.

> Corramos el programa
> Homero Simpson
> Ned Flanders(Medio tiempo)

Basicamente si queremos ocultar a un miembro de la clase base, tendremos que crear el mismo miembro de clase en la clase hija y utilizar la palabra reservada `new` para indicar que el ocultamiento del metodo fue intencional.

Si vemos el codigo utilizando la palabra reservada `new` hemos ocultado el metodo de la clase base, asi que cada vez que llamemos al metodo `ImprimirNombreCompleto()` desde un objecto de la clase `EmpleadoDeMedioTiempo` se va estar llamando al metodo propio de la clase y no al de la clase base `Empleado`, pero digamos que por alguna razon quiero llamar al metodo de la clase base y no al de la clase dervida

¿Cómo podemos hacer esto?, hay varias formas de hacerlo.

Una forma es utilizando la palabra reservada `base` dentro de la clase derivada


```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public new void ImprimirNombreCompleto(){
        //Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
        base.ImprimirNombreCompleto();
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    }
}
```

Si ponemos  el mosue encima de la palabra `base` podremos ver que hace referencia a la clase padre `Empleado`, asi que en este caseo `base.ImprimirNombreCompleto()` hace referencia al metodo dentro de `Empleado` que es la clase base.

Entonces lo que esta pasando aqui es que el mismo metodo `ImprimirNombreCompleto()` de la clase derivada esta llamando al metodo oculto de la clase base, si correos este programa veremos el resultado que teniamos al principio, los dos nombres como los muestra la funcion de la clase base.

>Corramos el programa
>Homero Simpson
>Ned Flanders

Esta es una forma de llamar al metodo oculto, la otra forma es utilizando un casting o convirtiendo un tipo de dato a otro tipo, ya hablamos sobre conversiones entre tipos de datos en la parte 7 de este tutorial si tienes dudas puedes hecharle un vistazo

Vamos regresar el metodo `ImprimirNombreCompleto` de la clase derivada `EmpleadoDeMedioTiempo`a como estaba antes:

```csharp
public class EpleadoDeMedioTiempo : Empleado
{
    public new void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
    }
}

```

Como les decia tambien podemos convertir la clase `EmpleadoDeMedioTiempo()` a la clase `Empleado`, esta conversion es posible gracias a la herencia, como recordamos en la leccion anterior parte 21 Herencia una clase derivda es una especializacion de la clase base y la clase derivda puede hacer lo mismo que la clase base mas las funciones propias de ella misma, y el ejemplo que mencionamba era como un Cardiologo es una especializacion de Medico General, el cardiologo puede hacer lo mismo que un medico general y aparte tambien puede realizar las operaciones propias de un cardiologo.  

Muy similar el `EmpleadoDeMedioTiempo` es una especializacion de `Empleado` y es esta especializacion la que nos permite convertir una calse derivada en una clase base, Para hacer esta conversion podemos utilizar el **operador de conversion** o **cast operator**, hagamos la conversion:

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public new void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ((Empleado)ETP).ImprimirNombreCompleto();
    }
}
```
Y si ponemos el mouse encima de `ImprimirNombreCompleto()` podremos ver que hace referencia a la clase `Empleado`

> Corramos el codigo y deberiamos tener el mismo resultado, ambas isntancias estan llamando al metdoo imprimir dentro de la clase base, entonces con esto probamos que podemos llamar al metodo oculto de la clase base.
> Homero Simpson
> Ned Flanders

Otra forma de llamar a un metodo oculto que es muy similar a lo que acabamos de hacer es de la siguiente manera

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public new void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    }
}
```

Antes de mostrarles la otra forma de llamar al metodo oculto si tenemos este codigo y lo corremos

> Como vemos se esta llamando al metodo `ImprimirNombreCompleto()`de la clase derivada `EmpleadoDeMedioTiempo`
> Homero Simpson
> Ned Flanders(Medio tiempo)

Entonces la otra forma de llamar al metodo oculto en la clase base es en lugar de utilizar un objeto de la clase deriva podemos utilizar uno de la clase base:

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public new void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        Empleado ETP = new EpleadoDeMedioTiempo();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    }
}
```

Si vemos esta forma de crear la instancia, recordemos que un objeto de la clase derivada puede tomor todas las responsabilidades de la clase base, esto nos permite asignar un objeto de la clase a derivada a una variable de la clase base.

Entonces `new EpleadoDeMedioTiempo()`es una instancia de la clase derivada la cual esta siendo almacenada en la variable `ETP` la cual es de tipo `Empleado`, la herencia nos permite esto, asignar objetos derivados a variables del tipo de la base.

>Al correr el codigo podemos ver que se esta llamando al metodo `ImprimirNombreCompleto` de la clase base `Empleado`, probando con esto que podmeos llamar a un metodo oculto
>Homero Simpson
>Ned Flanders

Se estaran pregutando si se puede hacer esto mismo pero al revez:


```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EpleadoDeMedioTiempo : Empleado
{
    public new void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio tiempo)");
    }
}

public class EpleadoDeTiempoCompleto : Empleado
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoDeTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();

        EpleadoDeMedioTiempo ETP = new Empleado();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.ImprimirNombreCompleto();
    } 
}
```

Pues no, no podeos hacer esto, nos dara un error de compilacion, porque un objeto de tipo `Empelado` no puede tomar todas las responsabilidades de un objeto de `EmpleadoDeMedioTiempo`, esto no es posible pero al revez si es posible.

Un variable de clase base puede apuntar a una referencia de una clase derivada, pero una variable de una clase derivada no puede apuntar a una referencia de la clase base, porque la clase base no puede tomar todas la responsabilidades de una clase derivada.

## [Parte 22][3]
En esta leccion hemos visto que si queremos ocultar un miembro de clase debemos utilizar la palabra reservada `new` si no la utilizamos tendremos un warning en el codigo indicando que hay un ocultamiento del miembro en de la clase base.  Y esto va ser de gran ayuda para otro developers que trabajen en el codigo, si un developer ve que alguien utilizo la palabra reservada `new` inmediatamente sabra que ese miembro de clase fue ocultado intencionalmente.

Tambien vimos las diferentes maneras de invocar a un miembro de clase oculto.
- Utilizando la palabra reservada `base` dentro de la clase derivada.
- Otra forma es convirtiendo la clase derivada en la clase base utiliznado el **operador de conversion** o **cast operator** 
- Y la otra forma que vimos es creando una instancia de la clase Derivada y asignarla a una variable de la clase base.

## [Parte 22][4]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.