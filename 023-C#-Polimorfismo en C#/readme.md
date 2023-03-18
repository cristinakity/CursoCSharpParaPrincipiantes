# Contenido

[TOC]

# Parte 23 - Polimorfismo en C#

## Pre - requisitos

- [ ] Agregar el siguiente codigo esto a visual studio antes de empezar
  
```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class Program
{
    public static void Main()
    {
        Empleado emp = new Empleado();
        emp.ImprimirNombreCompleto();
    }
}
```

## [Parte 23][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 23: Polimorfismo en C#

## [Parte 23][2]

Em esta leccion veremos
* Sobreescritura de metodos virtuales
* Polimorfismo

Veamos un ejemplo

### [vs][01]

En la parte 21 vimos la Herencia y en la parte 22 Ocultamiento de metodos vimos que una variable de tipo base puede apuntar a una referencia de una clase derivada.  Si aun no has visto la parte  21 Herencia de este tutorial es altamente recomendable que lo veas antes de continuar con esta leccion.

En este ejemplo ya tengo un ejemplo de una clase simple llamada `Empleado`, la cual tiene dos propiedades `Nombre`  y `Apellido`, y tambien tiene un metodo `ImprimirNombreCompleto()`.

Digamos que tenemos 3 tipos de empleados diferentes en la empresa:
- Empleados de tiempo completo
- Empleados de medio tiempo
- Y Empleados temporales

Y cada uno va tener un `Nombre`, `Apellido` y podra imprimir su nombre completo, entonces todos esos miembros de clase ya existen en la clase base `Empleado`, entonces vamos agregar las clases derivdadas.

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado emp = new Empleado();
        emp.ImprimirNombreCompleto();
    }
}
```

Ya creamos la clase `EmpleadoDeMedioTiempo`la cual herada de `Empleado`, de igual manera vamos a crear las otras dos clases

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado emp = new Empleado();
        emp.ImprimirNombreCompleto();
    }
}
```

Si vemos el ejemplo es muy simple, tenemos una clase base `Empleado` y tres clases derivadas: `EmpleadoDeMedioTiempo`, `EmpleadoDeTiempoCompleto` y `EmpleadoTemporal`.

Por la herencia sabemos que todos los miembros de la clase base seran heredados a las clases derivdas y obviamente las clases derivadas podran hacer uso de los miembros de la clase base.

En la el metodo `Main` voy a crear un arreglo de empleados 

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
    }
}
```

Y como es un arreglo empecemos agregar elementos en cada posicion del arreglo:

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
    }
}
```

El primer elmento del arreglo es de tipo `Empleado` agregemos otro valor para el segundo elemento:

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
    }
}
```

¿Es esto posible?, si como vimos en la leccion anterior a una variable de la clase base se le puede asignar una instancia de una clase derivada, dicho de otra forma una variable de tipo base puede apuntar a un objeto o instancia de tipo clase derivada.  Y podemos hacer esta asignacion porque una clase derivada cumple con las responsabilidades de la clase base, lo cual significa que una clase derivada puede hacer lo mismo que la clase base.

De igual manera vamos agreagr el tercer elemento al arreglo:

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
    }
}
```

Y por ultimo el cuarto elemento sera un `EmpleadoTemporal`

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();
    }
}
```

Como todas estas clases heredan de `Empleado` podemos asignar las instancias a una variable de la clase base `Empleado` como se ve aqui en la asignacion de valores a este arreglo el cual es un arreglo o una coleccion de datos de la clase `Empleado`

Ahora digamos que utilizo un ciclo para recorrer cada uno de los elementos del arreglo `empleados`

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {

        }
    }
}
```

Recordemos que todas las clases derivadas estan heredando los metodos de la clase base asi que en este `foreach` puedo acceder al metodo `ImpirmirNombreCompleto()`


```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

Si vemos el codigo las clases derivada o hijas no tienen el metood `ImprimirNombreCompleto()` por lo tanto en el `foreach` el metodo `ImprimirNombreCompleto()` que sera llamado es el de la clase base `Empleado`

> Si corremos el programa veremos impreso Nombre spacio Apellido 4 veces porque son los valores por default que tienen inicializados los campos en la clase base y el metodo `ImprimirNombreCompleto` de la clase base esta mostrando esos dos valores separados por un espacio.
> Nombre Apellido
> Nombre Apellido
> Nombre Apellido
> Nombre Apellido

Si vemos el codigo las clases derivadas no tiene su propio metodo para `ImprimirNombreCompleto()` por ende en el dentro del `foreach` se esta llamando el metodo de la clase base `Empelado`.

Digamos que tenemos un requerimiento donde debemos mostrar despues del nombre completo entre parentesis que tipo de empleado es; si es de Tiempo Completo, de Medio Tiempo o Temporal.

¿Cómo podemos hacer esto?, podemos crear para cada clase derivada un metodo `ImprimirNombreCompleto()` que haga lo correspondient para cada clase.

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio Tiempo)");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
}

public class EmpleadoTemporal : Empleado
{    
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

De igual manera puedo hacer lo mismo para las otras clases derivadas

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio Tiempo)");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Tiempo Completo)");
    }
}

public class EmpleadoTemporal : Empleado
{   
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Temporal)");
    } 
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

Muy bien entonces cada clase derivada tiene ahora su propia implementacion del metodo  `ImprimirNombreCompleto()` 

Si tenemos el codigo asi, lo que vimos en la leccion anterior es que el nuevo metodo en la clase derivada va a ocultar al metodo de la clase base. Si exist eun metodo igual en ambas clases derivad y base, el metodo de la clase base sera ocultado por el metodo de la clase derivada.  Pero como estamos utilizando una variable o un arreglo del tipo de la base `Empleado` en realidad vamos a estar llamando al metodo oculto osea al metodo `ImprimirNombreCompleto()` de la clase `Empleado` y no al metodo de la clase derivada esto porque el tipo de la variable que estamos utilizando es `Empleado` y no la especializacion o la clase derivada.

> Si corremos el codigo podemos ver el mismo resultado que antes, entonces los metodos de las clsas derivadas estan siendo ignorados porque estamos llamando al metodo oculto al tener la variable de tipo base `Empleado`
> Nombre Apellido
> Nombre Apellido
> Nombre Apellido
> Nombre Apellido

Tambien si vemos el codigo tenemos warnings, de que estamos ocultado miembros de la clase base. Y nos dice que si estamos ocultandolo intencionalmente pues que utilicemos la palabra reservada `new`, pero en este caso esa no es nuestra intencion, nuestra intencion es **sobreescribir** la implementacion que nos da la clase base y tener nuestra propia implementacion diferente en las clases derivadas y para eso debemos utilizar la palabra reservada `override` y antes de hacer esto debemos marcar el metodo de la clase base como `virtual`


```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public virtual void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Medio Tiempo)");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Tiempo Completo)");
    }
}

public class EmpleadoTemporal : Empleado
{   
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Temporal)");
    } 
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

Cuando marcamos un metodo de la base como virtual esto le indica a la clase derivad que puede ser **sobreescrito** u **override** si asi lo queremos.

Entonces lo que podemos hacer es por ejemplo, si elimino el metodo `ImprimirNombreCompleto()` de la clase derivada `EmpleadoDeMedioTiempo` y escribo `override` espacio vemos que el intellisense nos esta diciendo que metodos d ela clase base `Empleado` pueden ser sobrescritos

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public virtual void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    override 
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Tiempo Completo)");
    }
}

public class EmpleadoTemporal : Empleado
{   
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Temporal)");
    } 
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

Y si selecciono `ImprimirNombreCompleto()` de la lista de metodos uqe pueden ser sobresescritos, pues automaticamente se va agregar el codigo para sobrescribir ese metodo.

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public virtual void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    public override void ImprimirNombreCompleto()
    {
        base.ImprimirNombreCompleto();
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Tiempo Completo)");
    }
}

public class EmpleadoTemporal : Empleado
{   
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Temporal)");
    } 
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

Muy bien ya tenemos el metodo sobreescrito `ImprimirNombreCompleto()` en la clase derivada `EmpleadoDeMedioTiempo` le voy agregar la implementacion


```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public virtual void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    public override void ImprimirNombreCompleto()
    {
        Console.WriteLine($"{Nombre} {Apellido}(Medio Tiempo)");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Tiempo Completo)");
    }
}

public class EmpleadoTemporal : Empleado
{   
    public void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Temporal)");
    } 
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

De igualmanera podemos sobreescribir el metodo `ImprimirNombreCompleto()` en las otras clases, simplemente agregado la palabra reservada `override`

```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public virtual void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    public override void ImprimirNombreCompleto()
    {
        Console.WriteLine($"{Nombre} {Apellido}(Medio Tiempo)");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
    public override void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Tiempo Completo)");
    }
}

public class EmpleadoTemporal : Empleado
{   
    public override void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Temporal)");
    } 
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```

Que cambios hemos hecho en el codigo hasta ahora, en la classe base pusimos el metodo como `virtual` y en las clases derivadas sobreesccribimos este metodo utilizando la palabra reservada `override`

Entonces ahora que corramos el codigo ¿qué va a pasar?, pues por ejemplo para la variable `empleados` en la posicion [1] que hace referencia a `EmpleadoDeMedioTiempo` lo que va a pasar en runtime es que en lugar de tomar el metodo `ImprimirNombreCompleto()` de la clase base `Empleado`, en lugar de tomar este metodo de base y aunque estemos utilizanod uan variable de tipo `Empleado` va a darse cuenta que la referencia es de tipo `EmpleadoDeMedioTiempo` y que esta clase esta sobreescribiendo el metodo de la clase base, por lo tanto utilizara la sobresescritura del metodo en la clase derivada y esto es lo que se conoce como polimorfismo en la programacion orientada a objetos.

Entonces el Polimorfismos nos permite invocar metodos de la clase derivada a travez de una variable de la clase base en runtime.

> Si correos este codigo veremos que se estan ejecutando los metodos sobreescritos en las clases derivadas
> Nombre Apellido
> Nombre Apellido(Medio Tiempo)
> Nombre Apellido(Tiempo Completo)
> Nombre Apellido(Temporal)

Y por otro lado digamos que por ejemplo para la clase `EmpleadoTemporal` no voy a proporcionar ninguna sobreescritura para el metodo `ImprimirNombreCompleto()`


```csharp
using System;

public class Empleado
{
    public string Nombre = "Nombre";
    public string Apellido = "Apellido";

    public virtual void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}");
    }
}

public class EmpleadoDeMedioTiempo : Empleado
{    
    public override void ImprimirNombreCompleto()
    {
        Console.WriteLine($"{Nombre} {Apellido}(Medio Tiempo)");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{    
    public override void ImprimirNombreCompleto(){
        Console.WriteLine($"{Nombre} {Apellido}(Tiempo Completo)");
    }
}

public class EmpleadoTemporal : Empleado
{   
}

public class Program
{
    public static void Main()
    {
        Empleado[] empleados = new Empleado[4];
        empleados[0] = new Empleado();
        empleados[1] = new EmpleadoDeMedioTiempo();
        empleados[2] = new EmpleadoDeTiempoCompleto();
        empleados[3] = new EmpleadoTemporal();

        foreach(Empleado emp in empleados)
        {
            emp.ImprimirNombreCompleto();
        }
    }
}
```


Entonces ahora para la clase `EmpeladoTemporal`no estoy sobreescribiendo el metodo de la clase base, lo que va a pasar es como no tiene ninguna sobreescritura entonces esa variable va a utilizar el metodo base 

>Si corremos el codigo podremos ver los resultados
> Nombre Apellido
> Nombre Apellido(Medio Tiempo)
> Nombre Apellido(Tiempo Completo)
> Nombre Apellido

Entonces para `EmpleadoDeMedioTiempo` y para `EmpleadoDeTiempoCompleto` se esta llamando la sobrescritura del metodo en las clases derivadas y para `EmpleadoTemporal` al no tener sobreescritura del metodo se hace referencia al metodo de la clase base y esta pasando lo mismo para el primer empleado porque este es una referencia directa de la clase `Empleado`

Todo esto que vimos es el Polimorfismo, si alguien les pregunta sobre polimorfismos pueden responder que polimorfimo nos permite invocar metodos de las clases derivadas utilizando una variable de la clase base en runtime.

## [Parte 23][3]

El Polimorfismo es uno de los 4 pilares de la programación orientada a objetos.

El polimorfismo nos permite invocar métodos de las clases derivadas a través de una variable de la clase base en runtime.

Em la clase base el método es declarado virtual y en las clases derivadas podemos sobrescribir el  mismo método.

La palabra reservada virtual indica que el método puede ser sobrescrito en la clases derivadas.


## [Parte 23][6]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.