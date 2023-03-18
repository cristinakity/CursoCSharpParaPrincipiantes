# Contenido

[TOC]

# Parte 19 - Introduccion a las clases en C#

## [Parte 19][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 19: Introduccion a las clases en c#

## [Parte 19][2]

Em esta leccion veremos
* ¿Qué es una clase?
* Proposito del constructor(Constructor)
* Sobrecarga  (Overloading) del constructor
* Entendiendo la palabra reservada this
* Destructores (Destructors)

## [Parte 19][3]

¿Qué es una clase?

Hasta ahora en estos video tutoriales hemos visto tipos de datos simples como los enteros, punto flotantes, boleanos, etc. 
Pero si queremos crear tipos de datos complejos y personalizados entonces tenemos que utilizar las clases.

Y a que me refiero con tipos de datos complejos y personalizados:
Por ejemplo si quiero guardar un numero puedo utilizar un tipo de dato entero y guardarlo en una variable int.
Pero si quiero guardar los datos de un Cliente en este caso un tipo de dato int no es suficiente asi que puedo utilizar una clase, 

y pensando en que tipo de informacion tiene un cliente por ejemplo:
* Nombre
* Apellido
* Fecha de nacimiento
* Email
* etc.

Con estos datos podemos crear una una clase para el cliente y esta clase no solo puede contener datos, sino que tambien puede realizar ciertas acciones como:
* Guardar los datos del cliente
* Imprimir el nombre completo del cliente

En esencia una clase consiste de dos cosas:
1. Datos: Representados por los campos como nombre, apellido, etc.
2. Comportamiento: Representado por los metodos como ImprimirNombre, GuardarCliente, etc.

Entonces una clase tiene un estado y compartamiento, el estado de la clase no es otra cosa que los datos, y el comportamiento no es otra cosa que de que es capaz la clase o que puede hacer la clase, por ejemplo si la clase puede guardar los datos del cliente en una Base de datos este seria un compartamiento.

Muy bien veamos un ejemplo lo cual nos dara un panorama mejor sobre estos conceptos.

### [vs]-01

Ok, ¿Cómo creamos una clase?

Para crear una clase tendremos que utilizar la palabra reservada `class` seguida del nombre de la clase `Cliente`

```csharp
using System;

class Cliente

class Program
{
    public static void Main(){
        
    }
}
```

Y sabamso que el cliente va a tener un nombre y un apellido

```csharp
using System;

class Cliente
{
    string _nombre;
    string _apellido;
}

class Program
{
    public static void Main(){
        
    }
}
```

Estos dos campos representa el estado de la clase osea los datos de la clase.

Para inicializar estos campos podemos hacerlo mediantes el constructor de la clase, entonces ¿cómo creamos el constructor?, pues el constructor es como un metodo pero que se llama igual que la clase.

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public 
}
```
Entonces escribimos public que es el modificador de acceso, hablaremos de modificadores de acceso a detalle en proximas lecciones, entonces este constructor sera publico y despues ponemos el nombre que debe ser igual que el nombre de la clase.

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(
}
```

Y cual es el proposito de los constructores, basicamente nos sirven para inicializar los campos de la clase, mas adelante veremos como llamar a este contructor, por ahora vamos agregar los parametros al constructor para asi con estos poder inicializar los campos de la clase.

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {

    }
}
```

Muy bien este es el constructor, ¿cómo sabemos que es el constructor? pues porque es un metodo que tiene el mismo nombre que la clase y que no retorna ningunt tipo de dato ni tampoco void, como vimos en los metodos pueden retornar tipos de datos int, float, tuplas, etc o retornar void para indicar que no va a tener un `return` o regresar un tipo de dato, en el caso de los constructores no tiene ningun tipo de retorno ni tampoco la palabra `void`.

Entonces la forma de indentificar cual es el constructor de una clase es un metodo que se llama igual que la clase y que no tiene nada de retorno nisiquiera void, pero igual que un metodo un constructor puede recibir parametros.

Entonces le estamos pasando dos parametros a este constructor, nombre y apellido. Ya que el constructor recibe los parametros para inicializar los campos de la clase, lo unico que debemos hacer es parsar a esos valores a los campos:

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        _nombre = nombre;
        _apellido = apellido;
    }
}
```

Podemos hacer referencia al  campo de la clase utilizando el nombre del campo `_nombre`, o tambien podemos hacerlo de la siguiente manera:

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        _apellido = apellido;
    }
}
```

Al utilizar this y escribir el . el intellisence nos muestra los miembros de esta clase, en este momento lo unico que tiene esta clase son los campos `_nombre` y `_apellido`, entonces la palabra reservada `this` esta haciendo referencia a la instancia de esta clase `Cliente`.

Bien entonces podemos hacer uso de los campos o poner la palabra reservada `this` para hacer referencia a la instancia de la clase y asi tener acceso a los campos de la clase.

Basicamente el constructor esta recibiendo dos parametros y estos parametros los estamos pasando a estos dos campos para inicializarlos. Y todo esto va a pasar cuando creemos la instancia de la clase, esto lo veremos un poco mas adelante.

Ok, hasta ahora en la clase `Cliente` tenemos dos campos y un constructor para inicializar estos dos campos.

Entonces podriamos decir que esta clase `Cliente` de momento tiene un estados, representado pos su campos.

Digamos que quiero agregar un comportamiento a esta clase, osea la clase debe ser capaz de hacer algo, por ejemplo quiero que esta clase puede imprimir el nombre completo del `Cliente`, entonces para hacer esto escribamos una funcion.

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        _apellido = apellido;
    }

    public void ImprimirNombreCompleto()
    {
        
    }
}
```

Entonces tenemos un metodo llamado `ImprimirNombreCompleto` que tiene `void` como retorno asi que sabemos que no regresa ningun tipo de dato, y aparte no tiene nada entre los parentesis asi que no recibe ningun parametro, entonces ¿qué va hacer este metodo?, como el nombre lo indica va a imprimir el nombre completo del cliente, entonces vamos agregar el codigo para hacer esto:

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {_nombre} {_apellido}");
    }
}
```
[6:29]

De igual manera en este metodo podemos utilizar los campos asi directamente o podemos utilizar la palabra reservada `this`, para saber que nos referimos a los miembros de la clase.  Y como sabemos `this` hace referencia a una instancia de la clase, de esta clase `Cliente`

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }
}
```

Si vemos ahora la clase `Cliente`, tenemos dos campos, un constructor y un metodo.  Ademas de esto una clase tambien puede tener `Destructores` o `Destructors` y los destructores tendran el mismo nombre que la clase, pero no reciben parametros, ni tampoco pueden tener tipo de retorno y tienen la tilde de l a ñ al inicio, veamos como crear el destructor:

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }

    ~Cliente()
    {

    }
}
```

Normalmente una clase no requiere de un destructor pero alguna veces cuando tenemos muchos objetos que digmaos pueden llegar a consumir muchos recursos, podemos poner un destructor para limpiar estos recuros, y como los limpiamos pues como el nobmre del destructor lo indica digamos "destruyendolos" y como puedes destruir o limpiar un objeto de memoria hay varias formas una de las mas simples es inicializandolos a null o a vacio.

Bien, entonces un destructor puede ser muy util para limpiar recursos, cuando el ciclo de vida de una clase termine, toda la informacion, cosas que quedan en memoria de la clase pueden ser limpiadas dentro del destructor. En el caso de un destructor no necesitamos llamarlo si no que el destructor sera llamado automaticamente por el `Garbage Collector` cuando el GC intente limpiar objetos de la memoria, hablaremos de `destructors` y `Garbage collector` a detalle en proximas lecciones, por ahora solo hay que entender que un destructor tendra el mismo nombre que la clase, no tiene parametros ni valor de retorno, tiene al inicio la tilde de la ñ y son utilizados para limpiar cualquier recurso que la clase tenga almacenado en memoria duerante su ciclo de vida y los destructures son automaticmaente llamados por el `Garbage Collector` cuando este entra en accion para limpiar objetos que ya no son necesarios para el programa que estemos corriendo.

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }

    ~Cliente()
    {
        //Codigo para limpiar los recursos consumidos por estas clase.
    }
}
```

Muy bien ahora si quiero utilizar esta clase `Cliente`, lo podemos hacer en el metodo `Main`, entonces vamos a crear una instancia de esta clase

```csharp
class Program
{
    public static void Main()
    {
        Cliente clienteUno = new Cliente(
    }
}
```

Veamos estos el intellisence nos esta diciendo que para crear una instancia de la clase `Cliente` debemos pasarle dos parametros de tipo string `nombre` y `apellido`, y estos parametro donde estan pues en el construtor, enetonces al utilizar la palabra reservada `new` y despues poner el nombre de la clase lo que estamos llamando aqui es el constructor de la clase, asi que podemos decir que al crear la instancia es cuando se hace la llamada al constructor el cual recibe los parametros `nombre` y `apellido`.  Y que va hacer el constructor con esos parametros pues pasarlos a los campos propios de la clase y de este modo inicializar los campos de la clase.

Digamos por ejemplo que le paso mi nombre:

```csharp
class Program
{
    public static void Main()
    {
        Cliente clienteUno = new Cliente("Cosme","Fulanito");
    }
}
```

Que va ha pasar ahora, pues el nobmre `"Cosme"` se va a pasar al parametro nombre y este a su vez lo va a pasar al campo de la clase `_nombre` de este modo inicializando el campo, lo mismo va a pasar para el campo `_apellido`.
Entonces los parametors enviados en el constructor al crear la isntancia de la clase, seran utilizados para inicialziar los campos dentro de la clase y el constrcutor va ser llamado automaticamente al crear la instancia.

Bien, ¿qué son los constructores?, los constructores son automataticamente llamados al crear la instancia de la clase y cual es su proposito, en el ejemplo que tenemos aqui el proposito del constructor es incializar los campos `_nombre` y `_apellido`.  

Y si queremos mostrar el nombre completo del Cliente pues podemos llamar al metodo `ImprimirNombreCompleto`, ahorao que ya tenemos la instancia de la clase o el objeto de la clase creado podemos utilizarlo para llamar al metodo `ImprimirNombreCompleto`:

```csharp
class Program
{
    public static void Main()
    {
        Cliente clienteUno = new Cliente("Cosme","Fulanito");
        clienteUno.ImprimirNombreCompleto();
    }
}
```

Entonces en esta intancia `ClienteUno` el estado de los campos nombre y apellido va a ser esto que le estamos pasando en el constructor, entonces al llamar al metoodo `ImprimirNombreCompleto` este nos va mostrar el estado actual de la clase el cual es que `_nombre` es igual a `"Cosme"` y `_apellido` es igual a `"Fulanito"`, asi que el constructor nos esta asegurando que las variables `_nombre` y  `_apellido` tendran un valor, por lo tanto si corro este programa deberia ver en pantalla el nombre completo osea nombre espacio apellido que es lo que esta haciendo el metodo `ImprimirNombreCompleto` y como los valores estan siendo inicializados en el constructor esto de cierto modo nos asegura que al llamar al meotdo `ImprimirNombreCompleto` este tendre un valor que fue el que se envio al crear la instancia, y esto prueba que el constructor es utilizado para inicializar datos de la clase.

> Vamos a correrlo y veamos el resultado
> Nombre Completo = Cosme Fulanito

Muy bien, ahora ¿es obligatorio que debamos crear un constructor para la clase?, No necesariamente, por ejemplo vamos a comentar el constructor en esta clase.

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

/*
    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }
*/

    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }

    ~Cliente()
    {
        //Codigo para limpiar los recursos consumidos por estas clase.
    }
}
```

Ahora que comente el constructor vamos a tener un error al crear la instancia de la clase. Y si vemos el error:  dice que _`Cliente` no contiene un constructor que reciba dos parametros_, entonces para arreglar esto ahora debemo utilizar el constructor si ninguna parametro, el intellisence nos sugiere eso:

```csharp
class Program
{
    public static void Main()
    {
        Cliente clienteUno = new Cliente();
        clienteUno.ImprimirNombreCompleto();
    }
}
```

Entonces lo que estamos viendo aqui es que si no definimos un constructor para nuestra clase, el framework de .net genera uno automaticamente para nosotros y este es el constructor por defecto o `default constructor` entonces el constructor por defecto que proporciona .net framework es un constructor sin parametros.

Si vemos este codigo cuando se crea la isntancia y se llama al constructor por defecto este no le asigna ningun valor a los campos `_nombre` y `_apellido`, entonces estos campos estan vacios asi que si corremos otra vez la aplicacion

> [correr aplicacion]
> Nombre completo = 

Como vemos Nombre completo es igual a vacio y pues al no tener un constructor creado para iniciarlizar nuestros campos de clase, si el metodo `ImprimirNombreCompleto` es llamdo tendremos un Nombre Completo vacio, entonces el constructor por default en este caso no nos sirve de mucho porque crea un comportamiento que no queremos en nuestra clase, no queremos mostrar nombre completo igual a vacio.  Entonces si vamos al codigo y descomento el constructor que creamos nosotors.

```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }


    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }

    ~Cliente()
    {
        //Codigo para limpiar los recursos consumidos por estas clase.
    }
}
```

En el momento que descomento este codigo ya tenemos un error al crear la instancia de la clase. Y si vemos el error, ahora nos dice que _`Cliente` no contiene un constrcutro con cero parametros_, lo que esta pasando aqui es que una vez que nosotros creemos un constructor para la clase el constructo `default` ya no sera creado por el .net framework.

Muy bien ahora digamos que queremos podere creare instancias de esta clase sin tener que pasarle los parametros, 
¿Cómo podemos hacer esto?
Podemos escribir otro constructor que no tome ningun argumento:


```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Clietne()

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }


    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }

    ~Cliente()
    {
        //Codigo para limpiar los recursos consumidos por estas clase.
    }
}
```

Podemos definir el constructor vacio y despues hacer que este constructor llama el otro constructor utilizando la palabra reservada `this`


```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Clietne() : this(

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }


    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }

    ~Cliente()
    {
        //Codigo para limpiar los recursos consumidos por estas clase.
    }
}
```

Entonces puedo hacer que este constructor vacio llame automaticamente al constructor que si recibe parametros y asiganarle valores por defecto a los campos:


```csharp
class Cliente
{
    string _nombre;
    string _apellido;

    public Clietne() : this("No se proporciono un Nombre","No se proporciono un Apellido")
    {

    }

    public Cliente(string nombre, string apellido)
    {
        this._nombre = nombre;
        this._apellido = apellido;
    }


    public void ImprimirNombreCompleto()
    {
        Console.WriteLine($"Nombre completo = {this._nombre} {this._apellido}");
    }

    ~Cliente()
    {
        //Codigo para limpiar los recursos consumidos por estas clase.
    }
}
```

Lo que etamos haciendo aqui es: Si alguien crea una instancia de la clase y llama al constructor sin parametros, osea si alguien quiere crear una instancia de `Cliente` sin pasarle los parametros al cosntructor, ahora que tenemos dos constructores unos con parametros y otro sin parametros, se puede crear la instancia llamando al constructor que no recibe parametros.

Y si damos click en el nombre de la clase depsues del `new` y vamos a la definicion este nos va a mandar directo al constructor vacio que tenemos aqui.
Si vemos este constuctor tiene dos puntos y depsues `this` para hacer referencia a la misma instancia de la clase y esta asu vez llamando al otro constructor que recibe dos parametros, si le doy click drecho ir a definicio a este this me va a mandar al constrcutor que esta recibiendo los dos parametros. Al utilizar this y llamar al otro constructor le estamos pasando valores por default para nuestros campos `_nombre` y `_apellido` y obviamente ahroa si alguien llama al metodo `ImprimirNombreCompleto` ya no vereos Nombre completo  = a vacio sino que ahora veremos los valores por default que definimos al llamar al constructor con parametros desde el constructor vacios:

>Si corremos el codigo veremos
>Nombre Completo = No se proporciono un Nombre No se proporciono un Apellido

Entonces si queremos hacer que el constructor sin parametros sea un poco mas util y asegurar que los campos de nuestra clase sean inicializados, podemos tener dos constructores y desde el constructor sin parametros llamar al otro utilizando la palabra `: this` y de este modo inicializar esos parametros a un valor por defecto, asi si alguien llama a los metodos que estan utilizando estos campos pues podran ver un resultado en pantalla y no solo valores vacios.

Y por otro lado si alguien mas quiere llamar a la clase y veamos como crear otra instancia de la misma clase:

```csharp
class Program
{
    public static void Main()
    {
        Cliente ClienteUno = new Cliente();
        ClienteUno.ImprimirNombreCompleto();

        Cliente ClientDos = new Cliente(
    }
}
```

Si vemos cuando abro los parentesis el intellisense me esta diciendo que hay dos constructores para esta clase, uno que no recibe parametros y otro que recibe dos parametros.  

Entonces hay dos constructores para esta clase y la unica diferencia es el numero de parametors que recibe cada uno Y esto es lo que llamamos Overloading o sobrecarga del constructor, esta clase tiene dos constructores uno que no recibe ningun parametro y otro que recibe un nombre y apellido, entonces basicamente podemos sobrecargar un constructor, y la sobre carga es tener dos o mas constructores los cuales reciben diferente numero o tipo de parametros.

Entonces por ejemplo si pongo "Homero","Simpson"

```csharp
class Program
{
    public static void Main()
    {
        Cliente clienteUno = new Cliente();
        clienteUno.ImprimirNombreCompleto();

        Cliente clientDos = new Cliente("Homero","Simpson");
        clienteDos.ImprimirNombreCompleto();
    }
}
```
Y si corro el programa otra vez:

>Si corremos el codigo veremos
>Nombre Completo = No se proporciono un Nombre No se proporciono un Apellido
>Nombre Completo = Homero Simpson

Vemos que tenemos el resultado de llamar al metodo `ImprimirNombreCompleto` de el objeto `ClienteDos` y le habiamos pasado `"Homero"` como nombre y `"Simpson"` como apellido.

Y esto es todo, volvamos a las dispositivas

## [Parte 19][4]
[18:27]
El proposito del constructor es inicializar los campos de la clase.  
* El contructor es llamado automoaticamente cuando se crea la instancia de la clase.  
* Los constructores no tienen valores de retorno 
* y deben ser llamados igual que la clase. (Esta es una diferencia importante entre un metodo de la clase y un constrcutor, porque a simple vista un constructor se ve como un metodo, pero si el nombre es igual que la calse y no tiene valor de retorno entonces es un constructor y no un metodo de clase)

Los constructores no son obligatorios, si no creamos un constructor para la clase, .net framework asignara el constructor por default que es un constructor sin parametros, pero una vez que nosotros proporcionemos un constructor a la clase, el constructor default ya no sera asignado por el framework.

Y los constructores pueden ser sobrecargados con difernete numero de parametros o tipo de parametroso, esto significa uqe podemos tener varios constructores cada unos recibiendo diferente numero de parametros o mismo numero de parametros pero con diferentes tipos de parametros, esto es lo que se conoce en programacion como sobrecarga o Overloading.

## [Parte 19][5]
Los destructores tiene el mismo nombre que la clase con el simbolo de tilde de la ñ al inicio y estos no reciben prametro ni tamcpo retornan algun valor.

Dentro del destructor es donde podemos poner codigo para liberar recursos de memoria, durante la ejecucion del codigo o durante el ciclo de vida de la clase, esta pudo haber esta almacenando valores en memoria, entonces estos valores pueden ser limpiados aqui en el constructor para liberar esa memoria.

Hablaremos acerca de los destructores a detalle y tambien sobre el Garbage Collector o recolector de basura en proximas lecciones

## [Parte 19][6]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.