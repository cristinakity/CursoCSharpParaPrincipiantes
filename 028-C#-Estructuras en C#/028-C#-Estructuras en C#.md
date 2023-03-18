# Contenido

[TOC]

# Parte 28 - Estructuras en C#

## [Parte 28][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 28: Estructuras en c#

## [Parte 28][2]

En esta leccion hablaremos acerca de las estructurdas

## [Parte 28][3]

En la parte [Parte 19](https://www.youtube.com/watch?v=aa4yXwuDz24&t=3s&ab_channel=KudvenkatSpanish) de esta serie de videos vimos introduccion a las clases en C# y aprendimos que las clases pueden tener:

1. Campos privados
1. Propiedades publicas
1. Constructores
1. Metodos 

Al igual que las clases, las estructuras tambien pueden tener todo esto.

Veamos un ejemplo

### [vs]-01
[00:29]

Para crear una clase tendremos que utilizar la palabra reservada `class` seguida del nombre de la clase `Cliente`

Para crear una clase, por ejemplo si quiero crear la clase `Cliente` utilizamos la palabra reservada a `class`.

```csharp
using System;

public class Cliente
{

}

class Program
{
    public static void Main()
    {
        
    }
}
```

Pero digamos que quiero crear la estructura `Cliente` entonces tengo que usar la palabra reservada, `struct`(stroact).

```csharp
using System;

public struct Cliente
{

}

class Program
{
    public static void Main()
    {
        
    }
}
```
Y como ya sabemos, una clase puede tener Campos privados y de igual manera, las estructuras pueden tener campos privados.

Digamos que en este ejemplo nuestra estructura del cliente va a tener 2 campos privados, un campo privado de tipo int y otro campo privado de tipo string para guadar el nombre.

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;
}

class Program
{
    public static void Main()
    {
        
    }
}
```

Y para encapsular estos campos una clase puede tener propiedades, lo mismo aplica para una estrucutra, entonces parar crear una propiedad para el campo `_id` lo haremos de la siguiente manera:

Como `_id` es int la propieadad debe ser `int`

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {

    }
}

class Program
{
    public static void Main()
    {
        
    }
}
```

En el descriptor de acceso `get` vamos a tener lo siguiente:

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get
        {
            return this._id;
        }
    }
}

class Program
{
    public static void Main()
    {
        
    }
}
```

Y es necesitamos poner un descriptor de acceso `set`

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }
}

class Program
{
    public static void Main()
    {
        
    }
}
```

OK, esta es la propiedad para el campo `_id`, vamos a hacer lo mismo para el campo `_nombre`, Para crear esta propiedad, en realidad no necesitamos escribir el código, podemos hacer uso de él re factoring, que ya es parte de visual Studio.

Entonces, para crear la propiedad automáticamente usando el refactor de visual Studio, lo que hay que hacer es dar click derecho sobre la porpiedad privada y hacer cliek en la primer opcion de menu _"Acciones rápidas y refactorizaciones.."_ se abrirá otro menú con mas opciones y una de las opciones es _"Encapsular campo..(y usar propiedad)"_, al dar click en esta opcion visual studio va a crear la propiedad por nosotros muy similar al a que ya creamos manualmente:


```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }
}

class Program
{
    public static void Main()
    {
        
    }
}
```

Si vemos la propiedad auto generada por el refactor de visual Studion vemos que tenemos el símbolo de igual mayor el cual se llama **lambda operator**, este lambda operator en realida lo que esta haciendo aqui es creando un **lambda expresion** y no vamos a explicar a detalle que es una lambda expresion, pero solo deben de saber que lambda expresion se utiliza para crear funciones anonimas, entonces si tratamos de explicar este codigo lo que esta pasando es que el descriptor de acceso `get` es una funcion y en lugar de poner el contenido de la funcion entre las llavess como en la propiedad `Id`, estamos utiliznado lambda expresion para generar una funcion anonima y el contenido del metodo get ahora esta definido por estas funcion anonima, osea lo que sigue depsues de `=>(lambda operator)` es el contenido del `get`, lo miso para el `set`.

Entonces, utilizando estas funciones anónimas o lambda expresión, podemos simplificar el código y básicamente por eso lo están usando aquí, por eso es que el refractor de visual Studio sugiere que se haga de este modo.

Si quieren saber más acerca de lambda expresión y funciones anónimas en c#, les sugiero que vayan a [https://learn.microsoft.com.](https://learn.microsoft.com.) escriban _expresiones lambda_ en el buscar y chequen la documentación oficial ahí directo en la página de Microsoft.

[Link expressioens lambda](https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/operators/lambda-expressions)

Si comparamos el código de la propiedad autogenerada con la propiedad que creamos nosotros, vemos que básicamente están haciendo lo mismo, salvo que la autogenerado está utilizando lambda expressions y nosotros lo estamos haciendo a pie, poniendo las llaves y luego retornando el valor, pero ambas están haciendo lo mismo, en el `get` vemos que hace un return de `_nombre` y en el `set` tenemos que le va signar el valor recibido en `value` a la variable `_nombre` y es lo mismo que está pasando en la propiedad que creamos nosotros, sólo que he escrito de una forma simplificada.

Muy bien. Ahora nuestra estructura contiene campos privados y propiedades públicas.

Una clase también puede tener un constructor para inicializar los campos de la clase. De igual manera, la estructura también puede tener un constructor para inicializar los campos de la estructura `_id` y `_nombre`. 

Como ya sabemos, el constructor de una clase debe tener el mismo nombre que la clase, entonces, el constructor de una estructura deberá tener el mismo nombre que la estructura.  También sabemos que un constructor no puede tener un valor de retorno, entonces vamos a crear el consultor para esta estructura.

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }
}

class Program
{
    public static void Main()
    {
        
    }
}
```

Bien, ya creamos el constructor y como vemos le estamos pasando dos parámetros para inicializar los campos de la estructura, entonces el primer parámetro es un entero que es el `id` y se lo estamos asignando al campo privado `_id` y también estamos recibiendo el `nombre`, que es un `string` y lo estamos asignando al campo `_nombre` para inicializar el nombre.

Al igual que las clases, pueden tener métodos o funciones, también las estructuras pueden tener métodos en funciones. Entonces, agreguemos un método a esta estructura para que muestre en pantalla los datos del cliente.

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }

    public void MostrarDatosDelCliente()
    {
        Console.WriteLine($"Id={this._id}, Nombre={this._nombre}");
    }
}

class Program
{
    public static void Main()
    {
        
    }
}
```

Muy bien y con esto hemos creado nuestra estructura. Si vemos es casi idéntica que una clase, la única diferencia es que tenemos la palabra reservada `struct` en lugar de `class`. Si este codigo tuviera la palabra reservada `class` sería una clase, pero como tiene la palabra reservada `struct` es una estructura.

Veamos cómo utilizar esta estructura.

Para crear una instancia de una clase. Por ejemplo, de esta calse tendremos que poner `Cliente c= new Cliente()`, Para crear la instancia de una estructura tendremos que seguir exactamente la misma sintaxis.

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }

    public void MostrarDatosDelCliente()
    {
        Console.WriteLine($"Id={this._id}, Nombre={this._nombre}");
    }
}

class Program
{
    public static void Main()
    {
        Cliente c = new Cliente(
    }
}
```

Así creamos las la instancia de la estructura. Y si vemos, para crear esta instancia podemos proporcionarles los dos parámetros requeridos por el constructor que creamos, los cuales se utilizan dentro de la estructura para inicializar los campos `_id` y `_nombre`

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }

    public void MostrarDatosDelCliente()
    {
        Console.WriteLine($"Id={this._id}, Nombre={this._nombre}");
    }
}

class Program
{
    public static void Main()
    {
        Cliente c = new Cliente(101, "Homero");
    }
}
```

Con esto ya inicializamos la estructura y si quiero ver el los datos de este cliente, pues puedo simplemente llamar al método `MostrarDatosDelCliente()`.

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }

    public void MostrarDatosDelCliente()
    {
        Console.WriteLine($"Id={this._id}, Nombre={this._nombre}");
    }
}

class Program
{
    public static void Main()
    {
        Cliente c = new Cliente(101, "Homero");
        c.MostrarDatosDelCliente();
    }
}
```

> Y si corremos este código, debemos de ver el id y el nombre del cliente.
> Id=101, Nombre=Homero

Hay otra forma cómo podemos crear la instancia e inicializar los campos, podemos simplemente crear la instancia con el construtor vacio y despues inicializar los valores mediante las propiedades.

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }

    public void MostrarDatosDelCliente()
    {
        Console.WriteLine($"Id={this._id}, Nombre={this._nombre}");
    }
}

class Program
{
    public static void Main()
    {
        Cliente c = new Cliente(101, "Homero");
        c.MostrarDatosDelCliente();

        Cliente c2 = new Cliente();
        c.MostrarDatosDelCliente();
    }
}
```

> Si probamos este codigo, pues tendremos de resultado valores vacios
> Id= , Nombre=

Podemos inicializar los valores utilizando las propiedades.

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }

    public void MostrarDatosDelCliente()
    {
        Console.WriteLine($"Id={this._id}, Nombre={this._nombre}");
    }
}

class Program
{
    public static void Main()
    {
        Cliente c = new Cliente(101, "Homero");
        c.MostrarDatosDelCliente();

        Cliente c2 = new Cliente();
        c2.Id = 102;
        c2.Nombre = "Ned";
        c.MostrarDatosDelCliente();
    }
}
```

> Y si corremos el codigo veremos
> Id=102, Nombre=Ned

La diferencia entre estas dos instancias es que en la primera estamos utilizando el constructor para inicializar los campos, `_id` y `_nombre` y en la segunda instancia estamos utilizando un constructor que no recibe parámetros que es el construtor por default, y se están utilizando las propiedades para inicializar los campos de la estructura.

Otra forma de hacer esto mismo y que fue introducida apartir de C# 3.0  es utilizando la sintaxis de inicializadores de obejtos, de la siguiente manera

```csharp
using System;

public struct Cliente
{
    private int _id;
    private string _nombre;

    public int Id
    {
        get { return this._id; }
        set { this._id = value; }
    }

    public string Nombre { get => _nombre; set => _nombre = value; }

    public Cliente(int id, string nombre)
    {
        this._id = id;
        this._nombre = nombre;
    }

    public void MostrarDatosDelCliente()
    {
        Console.WriteLine($"Id={this._id}, Nombre={this._nombre}");
    }
}

class Program
{
    public static void Main()
    {
        Cliente c = new Cliente(101, "Homero");
        c.MostrarDatosDelCliente();

        Cliente c2 = new Cliente();
        c2.Id = 102;
        c2.Nombre = "Ned";
        c.MostrarDatosDelCliente();

        Cliente c3 = new Cliente
        {
            Id = 103,
            Name = "Bart"
        };
        c2.MostrarDatosDelCliente();
    }
}
```

Como vemos, utilizando la sintaxis de los inicializadores de objetos En lugar de tener varias líneas de código, primero, una donde se llama el constructor, luego otra donde se llama cada una de las propiedades, independientemente, se puede hacer todo en un mismo sitio, crear la instancia sin llamar al constructor, y ahí mismo pasarle los todas las propiedades, o los o los campos, todo lo que sea público se pueden estar pasando los valores directamente ahi, separados por coma nada más y de esta forma se simplificaría el como se inicializan los campos de una clase o estructura.

## [Parte 28][3]

La sintaxis de inicializadores de objetos, introducida a partir de C# 3.0 puede ser usada para inicializar ambos una estructura o una clase.

Hasta hora hemos visto las similitudes entre una clase y una structura, Pero debemos de tomar en cuenta que hay varias diferencias entre las clases y las estructuras, de las cuales hablaremos en las próximas elecciones.

## [Parte 28][4]

Vemos este ejemplo es parecido al codigo que escribimos, Pero aquí, en la parte izquierda, tenemos una clase y en la parte derecha tenemos una estructura. Y la única diferencia que vemos aquí es que en el lado izquierdo estamos utilizando la palabra reservada `class` para crear la clase y en el lado derecho estamos utilizando la palabra reservada `struct` para crear la estructura, en todo lo demas el codigo es exactamente el mismo.

Y como ya mencioné antes, existen algunas diferencias muy importantes entre clases y estructuras, De las cuales hablaremos en la próxima lección.

## [Parte 28][5]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.