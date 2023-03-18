# Contenido

[TOC]

# Parte 26 - ¿Porque usar propiedades en C#?

## [Prerequisitos]
Copiar este codigo a C# primero

```csharp
public class Estudiante
{
    public int Id;
    public string Nombre;
    public int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
    }
}
``` 

## [Parte 26][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 26: ¿Porque usar propiedades en C#?

## [Parte 26][2]

En esta leccion veremos
* La necesidad de las propiedades.

## [Parte 26][3]

Marcar los campos de una clase como públicos y exponerlos afuera de la clase es una mala práctica porque perdemos el control sobre qué valores pueden tomar y retornar estos campos.

Por ejemplo, aquí al lado derecho podemos ver los problemas que podemos tener con los campos definidos como públicos.Y tenemos cuatro puntos aquí que nos gustaría validar acerca de estas propiedades, el primero es que el id, no puede ser negativo que el nombre no puede ser nulo, que si el nombre no está definido, es nulo, retorne sin nombre.Y el otro es que la calificacion aprobatoria debe ser de sólo lectura, o sea que no nos permita asignar cambiar el valor de la calificacion aprobatoria.

Y bueno, aquí como tenemos los campos expuestos al `id` se le está designando el valor de -101 cuando no deberia tener un valor negativo.Esa sería una de las validaciones que queremos. 
El `nombre` también se está asignando como `nulo` cuando en el punto 2 decimos que el nombre no puede ser nulo.
Y aparte le estamos asignando un valor a la `CalificacionAprobatoria` cuando dice que debe ser de sólo lectura, entonces no debe poder tomar valores y también al momento de imprimir los valores en pantalla, se va a mostrar vacío en lugar del nombre.

Este `Console.WriteLine` va a mostrar en pantalla  `id` igual a `-101`, después va a mostrar,`nombre`, igual a vacío o nada, coma y luego `CalificacionAprobatoria` igual a 0 y lo que queremos es que si el nombre está nulo, que retorne `sin nombre`.

Muy bien. Entonces estos son los problemas que tenemos al declarar todos los campos como públicos, como vemos al lado derecho están algunas reglas que debemos estar siguiendo a la hora de crear un valor o una instancia para la clase `estudiante` y al tener todos los campos como públicos, todas esas reglas, pues no se están tomando en cuenta, sino que cada quien puede asignarle el valor quiera entonces vamos a ver todo esto en un ejemplo

### [vs][01]

```csharp
public class Estudiante
{
    public int Id;
    public string Nombre;
    public int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
    }
}
``` 

Tengo la clase de estudiante con `Id` y `nombre` y `promedio` y todos estos campos son campos públicos.

Muy bien. Entonces creamos una instancia para esta clase.

```csharp
public class Estudiante
{
    public int Id;
    public string Nombre;
    public int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();

    }
}
``` 

Ya creamos la instancia que se da una variable llamada `est`.Y ahora nuestra primer regla de negocio nos dice que el `id` no debe ser negativo, entonces vamos a asignarle un `id`.

```csharp
public class Estudiante
{
    public int Id;
    public string Nombre;
    public int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
    }
}
``` 

Y como vemos aquí el tener los campos públicos y que  pueden ser accedidos directamente podemos asignarle lo que queramos así que ahorita `id` vale -101 pero la regla de negocio decía que no debemos poder asignar un valor negativo.

De igual manera vamos asignarle uno nombre al estudiante.

```csharp
public class Estudiante
{
    public int Id;
    public string Nombre;
    public int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
    }
}
``` 

La segunda regla que teníamos era que el `nombre` no puede ser nulo. Y como vemos aquí, porque el campo es público y puede ser accedido de donde sea, le podemos asignar el valor de `nombre` igual a `null` sin ningún problema.

Muy bien y por último, vamos a asignar un valor al campo CalificacionAprobatoria.
```csharp
public class Estudiante
{
    public int Id;
    public string Nombre;
    public int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;
    }
}
``` 

Lo que hicimos aquí fue cambiar la calificación aprobatoria a cero, entonces con esto digamos que al NO estar validando esta regla es ahora los alumnos van a poder pasar aunque tengan calificación de cero, eso creara un problema en nuestro sistema porque este valor debería ser de sólo lectura

[01:58]

Ahora mostremos estos valores en pantalla

```csharp
public class Estudiante
{
    public int Id;
    public string Nombre;
    public int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

[02:42]

> Corramos el programa, que tenemos aqui?
> Id= -101, Nombre=  , Calificacoin aprobatorioa=0
>
> Id no deberia ser negativo, el nombre no deberia poder ser asignado como Nulo y si vemos la diapositiva otra vez:

## [Parte 26][3]

Si el nombre no fue definido se debe retornar:  `Sin Nombre`

[3:20]

### [vs][01] 

Y en el resultado nombre esta vacio, pero segun la regla deberiamos ver aqui `Sin  Nombre`

Y de igual manera para la calificacion aprobatoria nadie deberia poder cambiarle el valor por lo cual deberia ser de solo lectura

[03:29]

Digamos que al tener todos los campos publicos, estos se pueden cambiar facilmente y con esto se rompen todas las reglas de negocio que tenemos, otra forma de decirlo es que estas reglas simplemente se omiten.

[03:47]
Una forma de evitar que se rompan estas reglas de negocio es cambiando lo campos a privados, y tener algun tipo de sistema implementado para controlar como acceder y obtener datos de los campos.
[03:55]

Veamos cómo hacer eso.

Bueno, en los programas que no tienen propiedades, lo que se usa son los metodos `getters` y `setters` que viene de las palabras en inglés, `Get` y `SET`.

Get para obtener el valor y set para asignarle valor.

Los métodos get y set han existido desde que desde la creación de la programación orientada a objetos.

## [Parte 26][3]

Recordemos que hemos visto la herencia y el polimorfismo, que son 2 de los pilares principales de la programación orientada a objetos

## [Parte 26][4]

Y el encapsulamiento es otro de los pilares. 

¿Bien, y cómo conseguimos implementar el encapsulamiento?, Pues, básicamente, el encapsulamiento en los lenguajes de programación que no tienen propiedades se consigue utilizando los métodos `getters` y `setters`.

En C# y en los lenguajes de programacion de .net como visual basic .net sí existen las propiedades, pero hablaremos de ellas en próximas lecciones. 
Así que, de momento vamos a ver como se conseguia el encapsulamiento antes de la existencia de las propieades, esto lo haremos utilizar los métodos: getters y setters.

[04:55]

## [vs][01]

Por ejemplo, digamos que no quiero que nadie pueda asignar un valor negativo al campo Id.

¿Y cómo haremos esto? Pues primero que nada vamos a marcar todos los campus como privados porque no queremos que nadie tenga acceso directo a estos campos, Al cambiar los campos de públicos a privados, éstos van a dejar de estar expuestos a que puedan ser utilizados fuera de esta clase.

```csharp
public class Estudiante
{
    private int Id;
    private string Nombre;
    private int CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

Bueno, y ahora que están privados, vamos a seguir las convenciones de nombres dentro de c#. Dentro de c# existen las buenas prácticas que ya son conocidas por la mayoría de los programadores, y una de ellas es acerca del naming convention o más bien que vendrían siendo las convenciones de cómo nombrar campos, métodos, etcétera. Dentro de c#, y una de estas naming Convention es que para los campos privados se le agregue el _ antes del del nombre.


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

Ahora que los campos son privados, estos no pueden ser accedidos fuera de la misma clase esto debido al modificador de acceso, hablaremos de modificadores de acceso en proximas lecciones.

Entonces, si los campos no pueden ser accedidos y necesitamos que se le pueda asignar un valor al `_id` y también obtener ese valor, ¿Qué es lo que vamos a hacer? Pues tendremos que crear los métodos para poder asignarle valor y para poder obtener el valor, estos serían los métodos `getter` y `setter`.

[5:56]

Vamos a crear el método `SetId(int id)` para asignarle valor a este campo `_id` es de tipo privado, pero el método será público y mediante este método, que sería nuestro `setter` vamos a poder asignarle un valor.


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id){

    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

Creamos el método `SetId(int id)`, el cual va a recibir como parámetro un valor entero llamado `id`, que obviamente este lo vamos a utilizar para asignarle el valor a nuestra campo privado `_id`.

Pero antes de asignar el valor, podemos revisar que se está recibiendo y de este modo aplicar las reglas de negocio. Por ejemplo, una de las reglas de negocio que teníamos era que no se pudiera asignar un valor negativo.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id){
        if(id <= 0){

        }
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

Sí `id` es menor o igual a cero, lo que podemos hacer en este caso al ser un valor no permitido, es lanzar una excepción indicando que se intento asignar un valor no permitido para el campo `id`. 

Aún no hemos visto nada sobre excepciones y hablaremos a detalle sobre estas en próximas lecciones, las excepciones no son otra cosa más que condiciones para errores, O sea, que podemos lanzar de respuesta al usuario un error basado en cierta condición y el cual nos va a indicar que algo no estaba funcionando como nosotros esperamos. Así que, de momento sólo vamos a poner este código para agregar la validación y de este modo retornar un error condicionado osea una excepcion.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id){
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

De otra forma, si el número no es un número negativo, pues lo único que vamos a hacer es asignarle el valor que estamos recibiendo en el método `SetId` el cual es un entero llamado `id`, solo vamos a asignarle este valor al campo privado `_id`.


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id){
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

Este método sólo va a asignarle un valor, ahora si queremos leer ese valor, tendremos que hacer un método `getter` o en este caso vamos a crear un método llamado `GetId()` para retornar el valor.

[07:25]
 
```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.Id = -101;
      est.Nombre = null;
      est.CalificacionAprobatoria = 0;

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

Muy bien, ahora tenemos un método `GetId()` el cual lo único que va a hacer es retornar el `id`, por eso tenemos la instruccion `return` y estamos retornando el valor del campo privado `_id`, el tipo de retorno de este método debe ser un `int`, osea el mismo tipo que el campo privado `_id`. 

Con estos cambios que hemos hecho en el código, ahora cada vez que alguien quiera asignarle un valor al campo privado `_id` lo tiene que hacer a través del método `SetId(int id)` y lo mismo para cuando alguien quiera obtener el valor del campo privado `_id`, tiene que hacerlo a través del método `GetId()` el cual va a retornar el valor. Entonces, con estos métodos getter y setter lo que estamos haciendo, es controlando la forma comos se ingresan y se leen datos para nuestras variables privadas de la clase.

[08:15]

Vamos al método `Main` y veamos cómo inicializar estos valores bueno, en este caso nada más vamos a inicializar el `id`, más adelante vamos a crear los sette y getter para el nombre y la calificación aprobatoria, de momento nada más vamos a inicializar o asignarle un valor al id y a leer ese valor, veamos cómo hacerlo.


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.

      Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 
En este caso, al poner la variable de la clase `Estudiante` `est` y luego el punto, el intellisense me está mostrando los métodos que forman parte de esta clase, el método GetId y SetId, como vemos aquí, pero ya no me esta mostrando ningun campo de la clase directamente para asignarle u obtener el valor porque los ya no son publicos.

Vamos a asignarle el valor -101 al `id` y veamos lo que pasa al correr el código.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(-101);

      //Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

Bien antes de correr el código, recordemos que no deberíamos de poder asignar un valor negativo al id y es lo que estamos haciendo, intentando pasarle el valor -101 al método `SetId`.

¿Qué es lo que va a pasar?, Si vemos el código del metro `SetId` lo que va a hacer es validar si el `id` que está recibiendo es menor o igual a cero,   que en este caso esa validacion es verdadera porque estamos pasándole -101, el cual es menor o igual a cero, entonces va a entrar a esta línea donde está lanzando una excepción y tendríamos que ver ese error en la pantalla.

> Corramos el codigo y vemos 
> Unhandled Exception: System.Exception: El id del estudiante no puede ser un numero negativo
> Con este mensaje la persona que este usando la clase Estudiante puede saber que no debe asignarle un valor negativo al campo id

Por otro lado, si le asignó un valor positivo. 

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      //Console.WriteLine($"Id={est.Id}, Nombre={est.Nombre}, Calificacoin aprobatorioa={est.CalificacionAprobatoria}");
    }
}
``` 

> Si volvemos a correr el código, veremos que no tenemos ninguna excepción.
> Press any key to continue . . .

Bien, ahora que no tenemos ninguna excepción, si quiero mostrar el valor de `id`, ¿Cómo hacemos esto? Pues agreguemos el codigo para mostrar el valor del id en pantalla.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
    }
}
``` 

Para mostrar el valor del `id` en la pantalla. Lo único que hicimos es llamar al método `GetId()` que existe dentro de la clase `Estudiante`, y este metodo lo único que está haciendo es, si vemos el código este tiene un `return` y está retornando el campo `_id`.

> Si volvemos a correr el código, veremos que no tenemos ninguna excepción.
> El id del estudiante es 101

De igual manera, podemos crear los métodos `setter` y `getter` para los demás los demás campos privados de la clase.

[10:30]
Creemos el metodo set para el campo nombre:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {

    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
    }
}
``` 

El metodo `SetNombre` deber recibir el nombre, asi que recibe una variable llamada `nombre` de tipo `string`, ahora las reglas de netocio que tenemos para este campos es que no puedemos asignarle un valor nulo ni tampoco un valor vacio, entonces vamos a validar esto.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
    }
}
``` 
[11:43]

Muy similar como hicimos con el `id`, si queremos retornar el valor de `nombre`, solo tenemos que crear el metodo `GetNombre()` el cual retornara un string.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){

    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
    }
}
``` 

En este caso, en el método `GetNombre()` tenemos que agregar una validación o una regla de negocio, y la validación es si el nombre está vacío o es nulo regresaremos el valor `string` `"Sin nombre"`. 

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){
        if(string.IsNullOrEmpty(this._nombre))
        {
            return "Sin nombre";
        }
        else
        {
            return this._nombre;
        }
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
    }
}
``` 

Si vemos los requerimientos otra vez:

## [Parte 26][3]

Aqui en el punto 4 tenemos que: Si el nombre no fue definido se debe retornar `"Sin Nombre"`

### [vs][01]

Si alguien quiere obtener el valor del campo `_nombre` tiene que hacerlo atravez del metodo `GetNombre()`, y dentro del metodo estamos validando si el campo `_nombre` es nulo o vacio vamos a retornar el `string` `"Sin nombre"` y si el campo tiene algun valor vamos a retornar el valor del campo.

[13:18]

También podremos utilizar el operador ternario en lugar de tener este `if else`.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){
        return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
    }
}
``` 

Si no te queda claro como utilizar el operador ternario te sugiero que veas la parte 5: Operadores comunes de este tutorial.

Vamos a probar los metodos para asignar y obtener el nombre.


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){
        return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);
      est.SetNombre(null);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
    }
}
``` 

>Si corremos este codigo
> Unhandled Exception: System.Exception: El nombre no puede ser nulo o vacio

Digamos que no voy asignar el nombre pero si voy a mostrar el nombre en pantalla:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){
        return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
    }
}
``` 

> Si corro el codigo veremos que se muestra
> El id del estudiante es 101
> El nombre del estudiante es Sin nombre

Vemos que el nombres es `Sin nombre` porque esa es la regla que tenemos en el metodo `GetNombre()`

Pero por otro lado si le asignamos un valor al nombre:


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){
        return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
    }
}
``` 

> Si corremos el codigo podemos ver 
> El id del estudiante es 101
> El nombre del estudiante es Homero

Con esto hemos logrado validar las reglas de negocio para el campo id y para el campo nombre, ahora haremos algo similar para aplicar las reglas de negocio para el campo `_calificacionAprobatoria`.

La regla que tenemos para este campo es que debe ser de solo lectura, osea que nadie debe de poder cambiarle el valor a este campo.

En este caso para que sea de solo lectura debemos crear solamente el metodo Get y no el Set, recordemos el Set para asignarle valor y Get para obtener, asi que para que un campo sea de solo lectura entonces debemos de tener solo el metodo Get.  Vamos a crear el metodo `GetCalificacionAprobatoria()`


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public int GetCalificacionAprobatoria()
    {
        return _calificacionAprobatoria;
    }

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){
        return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
    }
}
``` 

Entoncles al no tener metodo SetCalificacionAprobatoria no podemos asignarle una valor a este campo, pero si podemos obtener su valor llamando al metodo get, vamos a mostrar la calificacion aprobatoria en pantalla:


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _CalificacionAprobatoria = 60;

    public int GetCalificacionAprobatoria()
    {
        return _calificacionAprobatoria;
    }

    public void SetNombre(string nombre)
    {
        if(string.IsNullOrEmpty(nombre)){
            throw new Exception("El nombre no puede ser nulo o vacio");
        }
        this._nombre = nombre;
    }

    public string GetNombre(){
        return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
    }

    public void SetId(int id)
    {
        if(id <= 0){
            throw new Exception("El id del estudiante no puede ser un numero negativo");
        }
        this._id = id;
    }

    public int GetId()
    {
        return this._id;
    }
}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      est.SetId(101);
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

> Si corremos el codigo podemos ver 
> El id del estudiante es 101
> El nombre del estudiante es Homero
> La calificacion aprobatoria para el estudiante es 65

Debemos tomar en cuenta no exponer los campos fuera de la clase, osea no declaralos como publicos, porque no tendrmeos control sobre que se le asigna a los campos o si se debe tener acceso a ellos o no.
Si queremos tener un mejor control sobre los campos de una clase debemos encapsularlos y podemos hacerlo utilizando las propiedades, y en el caso de los lenguajes que no tienen propiedades podemos utilizar los metodos getter y setter como lo acabamos de ver en este ejemplo.


## [Parte 26][4]

Los lenguajes de programación que no tienen propiedades utilizan los métodos getter y setter para encapsular y proteger campos.

En este ejemplo utilizamos los métodos `SetId(int id)` y `GetId()` para encapsular el campo `_id`.

Como resultado témenos mejor control sobre lo que asignamos y retornamos para el campo `_id`.

y como sabemos El encapsulamiento es uno de los 4 pilares de la programación orientada a objetos.

En la proxima leccion veremos como utilizar las propieades en c# y con esto implementaremos el encapsulamiento sin utilizar los metodos getter y setter.

## [Parte 26][5]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.