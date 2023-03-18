# Contenido

[TOC]

# Parte 21 - Herencia en C#

## [Parte 21][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 21: Herencia en c#

## [Parte 21][2]

Em esta leccion veremos
* ¿Porqué usar herencia?
* Ventajas de la herencia
* Sintaxis de la herencia
* Y algunos conceptos relacionado con la de herencia

## [Parte 21][3]
¿Porqué usar herencia?

Si vemos estas dos clases tenemos la clase `EmpleadoDeTiempoCompleto` y la clase `EmpleadoDeTiempoParcial` que basicamente son dos tipos de empleados que puede tener una empresa, sin importar que sea un empeado de tiempo completo o de tiempo parcial, tenemos ciertas cosas comunes entre ambos tipos de empleados como el nombre, apellido, email y el metodo imprimir nombre completo y la mayoria del codigo esta repetido o digamos que el mismo codigo existe en ambas clases, entonces entre estas dos clases solo existe una pequeña diferencia que el empleado de tiempo completo tiene el campo `SalarioAnual` y el empelado de tiempo parcial al ser de tiempo parcial no tiene un salario fijo anual, si no que se le paga por hora  y por eso es que tnemeos el campo `PagoPorHora`, en este ejemplo simple esta es la unica diferencia entre estas dos clases, pero en realiadad en el mundo laboral nos podemos encontrar con clases mas complejas y muchas diferencias entre clases similares, pero para proposito de este tutorial tenemos estas dos clases solo con un campo diferente y esto nos va ayudar a ilustrar el porque necesitamos la herencia en programacion.

Como en estas dos clases la mayoria del codigo esta repetido, podemos hacer una abstraccion osea sacar los valores generales o genericos de ambas clases, el codigo que tienen en comun y con esto crear una clase base.

## [Parte 21][4]

Tener la clase base nos va ayudar a no repetir codigo y rehusarlo, el codigo de la clase base sera reutilizado en las clases dereviadas.

Tambien el tener codigo reutilizable significa que tendremos que probar menos codigo, el testing o las pruebas en programacion son muy importantes para asegurar que el codigo esta funcionando como deberia de funcionar, entonces si aplicamos la herencia y movemos codigo reutilizable a una clase base, esto tambien va a mejorar la forma como tendremos que probar este codigo porque en lugar de probar lo mismo en dos clases diferentes, solo lo probaremos en una clase.

Otra ventaja de la herencia es que al tener menos codigo tambien se disminuyen los posibles errores de codigo.

La herencia promuebe la reutilizacion de codigo y de este modo podemos ahorrar mucho tiempo, en escribir codigo, probar codigo y corregir errores.

Si vemos la diapositiva y comparado con el el codigo de la dispositiva anterior, ahora en lugar de tener codigo repetido por cada tipo de empleado, ahora tenemos una clase base llamada empleado con todo ese codigo que tenian en comun las dos clases y esta vez para las clases derevidas que serian la clase `EmpleadoDeTiempoCompleto` y `EmpleadoDeTiempoParcial` solo tenemos los campos correspondientes y unicos para cada clase.

Veamos un ejemplo de como hacer esto.

### [vs]-01

Primero vamos a crear la clase base `Empleado`

```csharp
using System;

public class Empleado
{

}


public class Program
{
    public static void Main()
    {

    }
}
```

En esta clase base vamos a tener las propiedaes en comun que eran el nombre, apellido, email y el metodo ImprimirNombreCompleto()

```csharp
using System;

public class Empleado
{
    string Nombre;
    string Apellido;
    string Email;

    public void ImprimirNombreCompleto()
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

Todo este codigo es codigo en comun entre los diferentes tipos de empleados, ahora voy a crear una de las clases derevidas `EmpleadoDetiempoCompleto`

```csharp
using System;

public class Empleado
{
    string Nombre;
    string Apellido;
    string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto


public class Program
{
    public static void Main()
    {

    }
}
```

Y esta clase derivada va heredar de `Empleado`

```csharp
using System;

public class Empleado
{
    string Nombre;
    string Apellido;
    string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{

}


public class Program
{
    public static void Main()
    {

    }
}
```
Esta es la sitaxis para la herencia, despues del nombre de la clase derivada agregamos dos puntos y el nombre de la clase base.  Y lo que va a pasar es que cualquier cosa que exista en la clase base tambien estara disponible en la clase derivada.

Esta clase derivada solo va a tener una propiedad unica que es una variable de tipo `float` para almacenar el `SalarioAnual`

```csharp
using System;

public class Empleado
{
    string Nombre;
    string Apellido;
    string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    float SalarioAnual;
}


public class Program
{
    public static void Main()
    {

    }
}
```
[05:06]

De igual manera podemos crear la clase `EmpleadoDeTiempoParcial`

```csharp
using System;

public class Empleado
{
    string Nombre;
    string Apellido;
    string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    float PagoPorHora;
}

public class Program
{
    public static void Main()
    {

    }
}
```

Entonces la clase `EmpleadoDeTiempoParcial` tambien va hererar de la clase `Empleado` por lo tanto tambien va a heredar cualquier cosa que exista en la clase `Empleado`.

Por ahora agamos los campos de la clase base publicos para que esten disponibles en las clases derivadas porque recordemos que si un miembro de clase no tiene el modificador de acceso este sera privado por default y privado significa que solo peude ser accesido dentro de la misma clase.

Algo importante es que lo recomendable es no hacer los campos de la clase publicos si no crear propiedades para acceder a estos, pero hablaremos de propiedades en proximas lecciones por ahora tendremos campos publicos para que estos sean heradados a las clases derivadas, pero tomen en cuenta que no es recomendable tener los campos publicos sino utilizar propieades.

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    float PagoPorHora;
}

public class Program
{
    public static void Main()
    {

    }
}
```

Tambien haremos publicos los campos de las clases derivadas

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {

    }
}
```

Ya lo he dicho en los videos anteriores pero solo como recordatorio que hablaremos de los modificadores de acceso en proximas lecciones, por ahora solo estamos utilizando el modificador de acceso publico para demostrar como funciona la herencia y hay que concentrarnos en este video sobre la herencia.

Entonces ya tenemos una clase base `Empleado` y las clases derivadas `EmpleadoDeTiempoCompleto` y `EmpleadoDeTiempoParcial`, ahora que tenemos esto es hora de crear nuestras instancias.

En el metodo `Main()` voy a crear una isntancia para la clase `EmpleadoDeTiempoCompleto`

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();

    }
}
```

Ahora veamos la magia de la herencia, etonces `EmpleadoDeTiempoCompleto` no tiene el metodo `ImprimirNombreCompleto()`, ni tampoco tiene los campos nombre, apellido o email, la clase `EmpleadoDeTiempoCompleto` solo tiene un campo llamado `SalarioAnual`, pero si pongo punto despues del la instancia que creamos


```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.
    }
}
```

El intellisense nos esta mostrando los otros miembros de clase que pertenecen a `Empleado`, osea que `EmpleadoDeTiempoComppleto` tiene acceso a los miembros de clase de `Empleado` y esto es debido a la herencia

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
    }
}
```

Como vemos el ejemplo somo capaces de inicializar los campos `Nombre` y `Apellido` aun cuadno estos campos no estan presentes en la clase `EmpleadoDeTiempoCompleto`, pero como esta clase esta heredando de la clase `Empleado` es por esto que podemos acceder a los miembros de la clase `Empleado`

Asi como puedo inicializar campos heredados tambien puedo llamar al metodo `ImprimirNombreCompleto()`

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.ImprimirNombreCompleto();
    }
}
```
[07:22]

Como vemos podemos llamar metodos de la clase base aun cuando estos metodos no existen en la clase derivada.  Tambien podemos utlizar los campos propios de la clase `EmpleadoDeTiempoCompleto`

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();
    }
}
```

Veamos esto, no podremos tener acceso a los miembros de la otra clase derivada `EmpleadoDeTiempoParcial`, si intengo acceder a `ETC.PagoPorHora` pues este campo no existe en esta clase

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {

    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.Pa
        ETC.ImprimirNombreCompleto();
    }
}
```
Entonces con la herencia tendemos una clase base y muchas clases derivadas, y cada clase derivada tendra acceso los campos de la clase base y a sus propios campos, pero no a los campos de las demas clases derivadas.

De cierta forma podriamos decir que la clase `EmpleadoDeTiempoCompleto` es en realidad una especializacion de la clase `Empleado`, en esencia tiene todas las capacidades que la clase base y tambien las especificas definidas por esta misma clase.

Podriamos ver a las clases derivdas como especializaciones de la clase base, si lo comparamos por ejemplo en le mundo de la medicina tenemos Medigos generales y despues tenemos a los especialistas, Medigo genera podria ser una clase base, lo que tienen en comun todos los medicos y una especialida por ejemplo Cardiologo podria ser una clase derivada de la clase Medico general, visto de esta forma un Cardiologo puede realizar lo  mismo que un Medico General y ademas sus las actividades correspondientes a la especializacion de Cardiologia. 

De momento el metodo `ImprimirNombreCompleto` no tiene ninguna implementacion, osea no esta haciendo algo, asi agregemos un poco de codigo igual que en los ejemplos que hemos estado viendo anteriormente.

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo={this.Nombre} {this.Apellido}");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();
    }
}
```

>Si corremos el codigo, un objeto de EmpleadoDeTiempoCompleto es creado, y despues inicializamos los campos nombre, apellido y saliarioAnual, para posteriormente  imprimir el nombre completo y es lo que estamos viendo aqui como resultado
>Nombre completo = Homero Simpson

[09:27]

De igual manera voy a crear una instancia para la clase `EmpleadoDeTiempoParcial`, y veremos que cualquier cosa de la clase base `Empleado` existira en la clase `EmpleadoDeTiempoParcial`, entonces como sabemos tenemos una clase base y una clase derivda y esto es la herencia, pero tambien puede llamarse clases padre o parent en ingles y clase hija o child en ingles.  Entonces si escuchan hablar de herencia en programacion la clase base, parent o padre es el mismo concepto y la clase derivada, child o derived tambien se trata del mismo concepto.

Muy bien entonces creemos una instancia de la clase `EmpleadoDeTiempoParcial`

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo={this.Nombre} {this.Apellido}");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();

        EmpleadoDeTiempoParcial ETP = new EmpleadoDeTiempoParcial();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.PagoPorHora = 400;
        ETP.ImprimirNombreCompleto();
    }
}
```

>Si corremos el codigo ahora podremos ver los dos nombres completos de ambos empleados, cada uno viene de difernte clase, pero ambas clases derivan o heredan de la clase base `Empleado` por lo tanto tienen accesos a sus campos y metodos.  
Basicamente la herencia nos permite reutilizar el codigo
>Nombre completo = Homero Simpson
>Nombre completo = Ned Flanders

[10:32]

## [Parte 21][5]

¿Porqué utilizar la herencia?

Bueno primero hay que saber que en la Programacion Orientada a Obejetos hay 4 conceptos, tambien llamadoso pilares y estos conceptos o pilares son los fundamentos basicos de la programacion orientada a objetos

La programacion orientada a objeteos es un paradigma de programacion, que significa esto pues siemplemente que es una forma de programar, entonces lo que debemos tener en mente es que la Herencia es uno de esos 4 pilares, los demas pilares o conceptos son el encapsulamiento, la abstracción y el polimorfismo.  El polimorfismo esta muy ligado a la herencia, asi que antes de aprender sobre poliformismo debemos aprender que es la herencia.

Entonces dicho esto la herencia es uno de los cuatro pilares de la programacion orientada  a objetos y esto la convierte en un concepto muy importante dentro de la programacion y mas si estamos aprendiendo c# porque es un lenguaje orientado a objetos.

Tambien la herencia nos permite reutilizar codigo en lugar de tener codigo dos veces o mas repetido, podmemos hacer una abstraccion, osea tomar los campos genericos o repetidos de todass estas  clases y crear una clase base, de este modo tenemos el codigo escrito solo una vez y reutilizado en las clases hijas o derviadas.

Y otra de las razones del porque utilizar herencia es que al tener codigo reutilizable estos nos reduce el tiempo de codificacion o de escribir codigo y ademas nos dara menos posibilidad de errores.  Y hablando de errores tambien si hay un erro pues solo hay que arreglarlo en la clase base a diferencia de no tener herencia si todo esta en las clases especificas si tentemos el mismo metodo repetido en cada clase y con el mismo error, pues tendriamos que arreglar o modificar mucho codigo.

Ya hemos visto como aplicar la herencia en nuestro codigo, y la forma es crear una clase base con todo el codigo en comun, osea con los campos, metodos, propiedades y depsues crear las clases derivadas las cuales van a heredar de esta clase base y ademasestas clases derivadas solo tendran los metodos, propiedades y campos propiso de estas.

[11:17]

## [Parte 20][6]

Hemos visto un ejemplo de cual es la sintaxis para la herencia, entonces tenemos una clase base con su implemantacion y despues en la clase derivada debemos pner : ClaseBase depsues del nombre para indicar que esta hereda de la ClaseBase.

Ya hemos visto esta sintaxis en el ejemplo que creamos

### [vs][01]
[Mostrar el ejemplo]

## [Parte 20][6]

* En este ejemplo ClaseDerivada hereda de ClaseBase.
* C# soporta herencia de solo una clase.
    Esto es algo muy importante dentro de la programacion en C#, entonces solo podemos hererar de una clase osea despues de los dos puntos solo podemos tener 1 clase la cual sera nuestra clase base
    [Mostrar ejemplo en vs]

### [vs][01]

Digamos que tengo otra clase 

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo={this.Nombre} {this.Apellido}");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class A
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();

        EmpleadoDeTiempoParcial ETP = new EmpleadoDeTiempoParcial();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.PagoPorHora = 400;
        ETP.ImprimirNombreCompleto();
    }
}
```

¿Puedo hacer que la clase `EmpleadoDeTiempoParcial` herede tambien de la clase `A`?

```csharp
public class EmpleadoDeTiempoParcial : Empleado, A
{
    public float PagoPorHora;
}

public class A
{
}

```

Si intentamos compilar la solucion tendremos un error, y el error es que una clase no puede tener muchas clases base, entonces hay que recordar que una clase solo puede tener una clase base o una clase padre.  Pero la herencia mult-nivel o jerarquica si es posible en C#. Por ejemplo `EmpleadoDeTiempoParcia` esta heredando de la clase `Empleado`, entonces podemos hacer uqe la clase `A` herede de `EmpleadoDeTiempoParcial`


```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo={this.Nombre} {this.Apellido}");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class A : EmpleadoDeTiempoParcial
{

}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();

        EmpleadoDeTiempoParcial ETP = new EmpleadoDeTiempoParcial();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.PagoPorHora = 400;
        ETP.ImprimirNombreCompleto();
    }
}
```

Y ahora esta clase `A` va a tener todas las propieades de la clase `Empleado` y tambien las de la clase `EmpleadoDeTiempoParcial`, Si vamos y creamos una instancia de `A` podremos ver las propiedades de las otras clase listas para poder utilizarlas al creaar una instancia de la clase `A`

```csharp
public class Program
{
    public static void Main()
    {
        A A1 = new A();
        
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();

        EmpleadoDeTiempoParcial ETP = new EmpleadoDeTiempoParcial();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.PagoPorHora = 400;
        ETP.ImprimirNombreCompleto();
    }
}
```

Al crear el objeto `A1` este va  a tener acceso a todos los campos y metodos de `EmpleadoDeTiempoParcial` y como `EmpleadoDeTiempoParcial` hereda de `Empleado` y pues por ende la clase `A` Tambien tendra acceso a los campos y metodos de `Empleado`

```csharp
public class Program
{
    public static void Main()
    {
        A A1 = new A();
        A1.
        
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();

        EmpleadoDeTiempoParcial ETP = new EmpleadoDeTiempoParcial();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.PagoPorHora = 400;
        ETP.ImprimirNombreCompleto();
    }
}
```

Entonces que una clase herede de muchas clases al mismo tiempo NO ES POSIBLE, pero que una clase pueda tener herencia jerarquica o miltinivel esto si es posible osea que clase `A` herede de `EmpleadoDeTiempoParcial` y `EmpleadoDeTiempoParcial` herede de `Empleado`, como vemos hay una jerarquia o un multi-nivel de las clases.

## [Parte 20][6]

* C# soporta herencia de múltiples interfaces.
  * Pero aun no hemos hablado de las interfaces hablaremos de estas en proximas lecciones, por ahora solo queria hacer enfasis que la herencia multiple hablando de clases no es posible pero hablando de interfaces si es posible.
* Otro punto sobre la herencia para tomar en cuenta es que la clase derivada es una especialización de la clase base, esto ya lo vimos en los ejemplos donde teniamos `Empleado` en general y depues tipos de empleados especifivos, entonces como vemos las clases derivadas son especializaciones de la clase base.


* La clase base es automáticamente instanciada antes que la clase derivada.  Este es otro concepto muy importante dentro de la herencia.

### [vs][01]

Vamos a remover la clase `A`

```csharp
using System;

public class Empleado
{
    public string Nombre;
    public string Apellido;
    public string Email;

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo={this.Nombre} {this.Apellido}");
    }
}

public class EmpleadoDeTiempoCompleto : Empleado
{
    public float SalarioAnual;
}

public class EmpleadoDeTiempoParcial : Empleado
{
    public float PagoPorHora;
}

public class Program
{
    public static void Main()
    {
        EmpleadoDeTiempoCompleto ETC = new EmpleadoTiempoCompleto();
        ETC.Nombre = "Homero";
        ETC.Apellido = "Simpson";
        ETC.SalarioAnual = 300_000;
        ETC.ImprimirNombreCompleto();

        EmpleadoDeTiempoParcial ETP = new EmpleadoDeTiempoParcial();
        ETP.Nombre = "Ned";
        ETP.Apellido = "Flanders";
        ETP.PagoPorHora = 400;
        ETP.ImprimirNombreCompleto();
    }
}
```

Cada vez que se crea la instancia de una clase derivada, automaticamente se crea una instancia de la clase base, entonces antes de que el constructor de la clase derivada sea ejecutado se esta creando la instancia de la clase base y se esta ejecutando el contructor de la clase base.

Y esto tiene mucho sentido porque si vemos el metodo `ImprimirNombreCompleto()` es un metodo de instancia, si lo metodos y la diferencia entre metodos de instancia y metodos estaticos son conceptos nuevos para ti  te sugiero que veas la parte 20 - Miembros de clase estaticos y de instancia de estos video tutoriales.

Entonces como les decia `ImprimirNomobreCompleto()` es un metodo de instancia dentro de la clase base y como vimos en la leccion anterior para llamar a un metodo de instancia es neceario crear la instancia de la clase primero, y si vemos en el metodo `Main` lo que estamos haciendo es creando una instancia de la clase derivada `EmpleadoDeTiempoCompleto`, pero el metodo `ImprimirNombreCompleto()` esta presente en la clase base, y si este metodo tiene que estar disponible para el objeto `ETC` es obvio que tiene que existir una instancia de la clase base incluso antes que se cree la instancia de la clase dervidad.

Cuando estamos creando la instancia de la clase Derivada lo que esta pasando es que primero se esta creando la instancia de la clase base, entonces los constructors de la clase base son llamados antes de llamar al constructor de la clase derivda.  Veamos un ejemplo de esto:

[16:44]

Primero vamos a remover el codigo del ejemplo de herencia y agregemos otro ejemplo

```csharp
using System;

public class ClaseBase
{
    public ClaseBase()
    {
        Console.WriteLine("Llamada al constructor de la Clase Base");
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Si vemos ahora tenemos una clase base con su constructor y muy similar podemos crear la clase derivada

```csharp
using System;

public class ClaseBase
{
    public ClaseBase()
    {
        Console.WriteLine("Llamada al constructor de la Clase Base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public ClaseDerivada()
    {
        Console.WriteLine("Llamada al constructor de la Clase Derivada");
    }
}

public class Program
{
    public static void Main()
    {
    }
}
```

Si vemos este codigo es muy simple, tenemos dos clases, una hereda de otra y ambas clases tienen un constructor y en el constructor estan mostrando un mensaje en pantalla. Ahora vamos a crear una instancia de `ClaseDerivada`


```csharp
using System;

public class ClaseBase
{
    public ClaseBase()
    {
        Console.WriteLine("Llamada al constructor de la Clase Base");
    }
}

public class ClaseDerivada : ClaseBase
{
    public ClaseDerivada()
    {
        Console.WriteLine("Llamada al constructor de la Clase Derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseDerivada CD = new ClaseDerivada();
    }
}
```

Entonces estamos creando un objecto llamdo `CD` que para instanciar la `ClaseDerivada`, entonces sabemos que antes de que se cree la instancia de `ClaseDerivada`y se llame a su constructor, primero se va crear la instancia de `ClaseBase` porque sabemos que `ClaseDerivada` herada de `ClaseBase` entonces al crear la instancia de `ClaseDerivada` se va automticamente crear la instancia de `ClaseBase` y se llamara el constructor de la base, todo esto antes de que se cree la instancia de la `ClaseDerivada` y se llame al constructor de esta.

>Si corremos el codigo, como vemos primero tenemos el mensaje de Llamada al constructor de la clase base y despues el mensaje de llamda al constructor de la clase derivada
>Llamada al constructor de la Clase Base
>Llamada al constructor de la Clase Derivada

Y ahora digamos que en la `ClaseBase` tenemos otro constructor, recordemos que esto es la sobrecarga de constructores o tambien llamado overloading, anteriormente ya vimos este concepto en la parte 19 - Introduccion a las clases de este tutorial asi que si tienes dudas puedes hecharle un vistazo a ese video.  Entonces vamos a sobrecargar el constructor

```csharp
using System;

public class ClaseBase
{
    public ClaseBase()
    {
        Console.WriteLine("Llamada al constructor de la Clase Base");
    }

    public ClaseBase(string mensaje)
    {
        Console.WriteLine(mensaje);
    }
}

public class ClaseDerivada : ClaseBase
{
    public ClaseDerivada()
    {
        Console.WriteLine("Llamada al constructor de la Clase Derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseDerivada CD = new ClaseDerivada();
    }
}
```

Si vemos el codigo ahora la `ClaseBase` tiene dos constructores uno que recibe un parametro string y el otro que no recibe ningun parametro.

Muy bien entonces cuando estamos creando la instancia de `ClaseDerivada` en el metodo `Main` que constructor de la `ClaseBase` es el que se esta llamando, por defecto se llama al que no recibe parametros.

Pero digamos que yo quiero que al crear una instancia de `ClaseDerivada` el constructor que recibe un parametro sea el que se llame y poderle pasar un valor a la variable `string mensaje` que es le paremtro que recibe el constructor, la pregunta es ¿Cómo puedo asegurarme de que el constructor que yo quiero sera el que se llame?, podemos contralar esto utilizando la palabra reservada `base`, veamos como hacerlo:


```csharp
using System;

public class ClaseBase
{
    public ClaseBase()
    {
        Console.WriteLine("Llamada al constructor de la Clase Base");
    }

    public ClaseBase(string mensaje)
    {
        Console.WriteLine(mensaje);
    }
}

public class ClaseDerivada : ClaseBase
{
    public ClaseDerivada() : base(
    {
        Console.WriteLine("Llamada al constructor de la Clase Derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseDerivada CD = new ClaseDerivada();
    }
}
```

Al escribir base y abrir parentesis el intellisense me esta mostrando el numero de constructores que tiene la clase base, entonces la palabra reservada `base` hace referencia a la clase de donde esta heredando `ClaseDerivada` que en este ejemplo es la `ClaseBase`, ya sabemos que `ClaseBase` tiene dos constructores y esto es lo que nos esta mostrando el intellisense: un constructor sin parametros y otro que recibe un parametro, el campo `string mensaje`.

Ahora podemos pasar el mensaje que queramos


```csharp
using System;

public class ClaseBase
{
    public ClaseBase()
    {
        Console.WriteLine("Llamada al constructor de la Clase Base");
    }

    public ClaseBase(string mensaje)
    {
        Console.WriteLine(mensaje);
    }
}

public class ClaseDerivada : ClaseBase
{
    public ClaseDerivada() : base("Llamada desde Clase Derivada a construtor especifico de la Clase Base")
    {
        Console.WriteLine("Llamada al constructor de la Clase Derivada");
    }
}

public class Program
{
    public static void Main()
    {
        ClaseDerivada CD = new ClaseDerivada();
    }
}
```

Entonces estamos controlando que constructor de la base sera llamado, todo esto desde la `ClaseDerivada`

> Si corremos esto, veremos que el constructor sin parametros ya no se esta llamando y ahora veremos en pantalla el valor que le estamos pasando al constructor con parametros y despuse la llamada el constructor de la `ClaseDerivada`
>Llamada desde Clase Derivada a construtor especifico de la Clase Base
>Llamada al constructor de la Clase Derivada

Como vimos en el ejemplo es posible controlar desde una clase dereviada a que constructor de la clase base se va a llamar cuando se cree la instancia de la clase hija.

## [Parte 21][7]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.