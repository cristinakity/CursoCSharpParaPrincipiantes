# Contenido

[TOC]

# Parte 16 – Metodos en C#

## [Parte 16][1]

Hola bienvenidos a Pragim Technologies yo soy Cristina,
esta es la parte 16: Metodos en C#

## [Parte 16][2]

En esa leccion aprenderemos,
- La estructura basica de un metodo en c#.
- Y La diferencia entre los metodos staticos y los metodos de instancia.

## [Parte 16][3]-01

La primer pregunta que nos vamos hacer es ¿Por que metodos?,
Por qué necesitamos utilizar los metodos?
Metodos en realidad son muy utiles porque nos permiten definir nuestra logica sola una vez y utilizarla en muchos lugares, debido a esto es que los metodos hacen que el mantenimientos de nuestras aplicaciones sea mucho mas facil.

Y los metodos tambien son conocidos alguna veces como funciones, asi que digamos que si escuchan la palabra este metodo o esta funcion, seguramente se esta hablando de lo mismo.
En C# un metodo o una funcion se refiere a lo mismo osea son conceptos intercambiables o sinonimos.

## [Parte 16][4]-01

Si vemos la estructura de un metodos, este tiene varias partes:
* Atributos
* Modificadores de acceso
* Tipo de retorno
* Nombre del metodo
* Parametros
* Y el cuerpo del metodo

Hablaremos a detalle sobre los atributos y los modificadores de acceso en proximas lecciones.

Sobre el tipo de retorno de un metodo, este tipo puede ser cualquier tipo de dato en C#, 
Si no queremos que el motod regrese ningun tipo de dato, entonces tenemos que indicarlo con la palabra void.

El nombre del meotod puede ser cualquier nombre valido lo cual significa que no podemos utilziar ninguna palabra reservada de c# como nombre de un metodo,
y de preferencia utilizar algun nombre que sea significativo para la accion que el metodo realiza, por ejemplo si el metodo calcual el are de un cuadrado un buen nombre para este podria ser CalcularAreaCuadrado, un mal nombre podria ser Metodo1 o Calcular,
y porqué son malos nombres? pues porque no son de mucha ayuda al momento de hacer una llamada a ese metodo.  La idea de nombrar metodos es que al utilizarlos sin ver el codigo del metood ya sepas cual es la tarea que va a realizar, de alli la importancia de ponerles un nombre significativo.

Podemos pasarle parametros a un metodo si asi lo queremos o pueden quedar vacios, los parametros son opcionales.

Y obviamente el cuerpo del metodo contendra todo el codigo de c# de nuestro metodo o mejor dicho todas las instrucciones de c# que el metodo realizara.

Veamos un ejemplo.

### [vs]-01

En todo este tiempo hemos estamos escribiendo nuestro codigo dentro del metodo Main(), pero tambien podemos crear nuestros propios metodos y despues llamarlos.

Por ejemplo digamos que quiero crear una funcion que muestre en pantalla los numeros pares.  Es muy facil de hacer.

Escribamos la funcion:

## [Parte 16][4]-02

Como vimos antes una funcion puede tener, atributos de los cuales hablaremos en proximas lecciones, tambien peude tener modificador de acceso del cual hablaremos mas adelante, pero por ahora hagamos uso del modificador de acceso `public`

### [vs]-02

```csharp
public 
```
Cuando agreagmos el modificador acceso publico esto quiere decir que nuestro metodo podra ser utilizado en cualquier parte.

Hay otro tipo de modificadores de acceso como privado, protected, internal de los cuales hablaremos a detalle en proximas lecciones.

Bien, podemos especificar el tipo de retorno despues del modificador de acceso, si no queremos definir un valor de retorno podemos especificarlo con void, nuestro valor de retorno sera  void osea ningun valor.

```csharp
public void
```

Y despues pondremos el nombre de la funcion, esta funcion va a mostrar los numeros pares entonces podemos llamarla NumerosPares();

```csharp
public void NumerosPares()
```

Como esta funcion no va a recibir ningun parametro entonces solo abro y cierro los parentesis depsues del nombre. 

Y para definir el cuepro de la funcion solo abro y cierro las llaves

```csharp
public void NumerosPares()
{

}
```

Muy bien, entonces como quiero mostrar en pantalla los numeros pareces digamos desde el 0 hasta el 20, ¿Cómo puedo hacer esto?, pues escribamos el codigo

```csharp
public void NumerosPares()
{
    int inicio = 0;

    while(inicio <=20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Si vemos esta funcion, es una funcion muy simple la cual impreme en pantalla un numero y le va aumentando de dos en dos hasta que el numero sea mayor que 20.

Muy bien definimos esta logica para los numeros pares solo 1 vez y podemos llamar a esta funcion de donde sea que queramos.

Por ejemplo si quiero llamar a la funcion aqui en el metodo Main, 

¿cómo hago esto?

Si vemos a la funcion `NumerosPares` y a la funcion `Main` existen algunas pequeñas diferencias entre estos dos metodos la primera es que `Main` no tiene un modificador de acceso y la otra diferencia es que el metodo `NumerosPares` no tiene la palabra reservada `static` en su declaracion y el metodo `Main` si la tiene.  esta es una de las diferencias entre los metodos estaticos y los metodos de instancia:
* El metodo `Main` esta siendo llamado como un metodo estatico
* Y el mtodo `NumerosPares` debe ser llamado como un metodo de instancia

Si tengo que invocar al metodo `NumerosPares`, invocar es lo mismo que llamar o hacer uso del metodo.  Entonces si quiero invocar al metodo `NumerosPares` tengo que usar una instancia de la clase donde se encuentra el metodo.
Si vemos este metodo se encuentra dentro de la clase es `Program` y la clase programa no es static ni tampoco el metodo `NumerosPares`, en este caso el metodo `Main` al tener la palabra reservada `static`este puede ser llamado de forma estatica, si necesidad de una isntancia de la clase `Program`, pero el metodo `NumerosPares` al ser un metodo de instancia, porque no tiene la palabra `static` es un metodo de instancia y no estatico. Al ser un metodo de instancia necesitaremos una instancia de la clase `Program` para poderlo invocar.

Una instancia  no es otra cosa que un objeto de la clase, en C# para crear los objetos y darles vida a la instancia de la clase se hace uso de la palabra reservada `new`, entonces veamos el ejemplo:

```csharp
static void Main()
{
    //Primero declaro una variable de la clase Program
    Program claseProgram = 
}

public void NumerosPares()
{
    int inicio = 0;

    while(inicio <=20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Y ahora con la palabra reservada `new` le doy vida al objeto creando su instancia.

```csharp
static void Main()
{
    //Primero declaro una variable de la clase Program
    Program claseProgram = new Program()
}

public void NumerosPares()
{
    int inicio = 0;

    while(inicio <=20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Entonces `claseProgram` es una instancia de la clase `Program` y esta instancia representa un objeto de la clase `Program`, digamos que instancia y objeto podrian ser sinonimos.

Y algo que hay que tener en cuenta es que en C# cada vez que se usa la palabra `new` para crear un objeto de una clase, en ese momento se esta dando vida a una instancia de esa clase.

Muh bien entonces ahora que `claseProgram` representa una instancia de `Program` puedo hacer uso de esta variable `casleProgram` para llamar al metodo de instancia `NumerosPares()`.

```csharp
static void Main()
{
    Program claseProgram = new Program()
    claseProgram.NumerosPares();
}

public void NumerosPares()
{
    int inicio = 0;

    while(inicio <=20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Entonces la diferencia entre metodos estaticos y metodos de instancia es que para llamar a un metood de instancia es necesario crear una instancia de la clase que contiene al metodo y para crear la instancia hay que hacer uso de la palabra reservada `new`, una vez creada la instancia de la clase podemos poner la variable despues escribir punto y tendremos acceso a todos sus metodos de instancia.

### [Run]-01

> Si corro este programa, lo que hara es motrar en pantalla los numeors pares desde el 0 hasta el 20
> 0
> 2
> .
> .
> 20

### [vs]-03

Este es un metodo de instancia, pero ahora hagamoslo statico.
¿Cómo cambio el meotod para que sea statico?, solo hay que agregarle la palabra `static`

```csharp
static void Main()
{
    Program claseProgram = new Program()
    claseProgram.NumerosPares();
}

public static void NumerosPares()
{
    int inicio = 0;

    while(inicio <=20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Ahora este metodo es estatico, y veamos que ahora que el metodo es estatico tenemos un error de compilacion:
>  NumeroPares() no puede ser accedido por una referencia de instancia. En su lugar utilice el nombre del tipo.

¿En qué tipo existe este metodo?, pues en la clase `Program`, la clase `Program` es el tipo para este metodo.  

Si nos pide utilizar el nombre del tipo en lugar de la instancia lo que tenemos que hacer es  poner `Program.` directamente, veamos el ejemplo:

```csharp
static void Main()
{
    Program.NumerosPares();
}

public static void NumerosPares()
{
    int inicio = 0;

    while(inicio <=20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Entonces si el metodo es statico entonces para invocar este metodo no lo podemos hacer  creando una instancia de la clase, sino que debemos hacer uso del nombre de la clase nadamas, seguida de punto y el nombre del metodo estatico.

### [Run]-02

> Si corro este programa, el resultado sera el mismo que antes solo que ahora estamos llamando a un metodo estatico y no a uno de instancia
> 0
> 2
> .
> .
> 20


### [vs]-04

Ahora si vemos este metodo tenemos:
* El modificador de acceso
* El modificador estatico
* Tenemos void que indica que no tendra un tipo de retorno
* Despues el nombre del metodo 
* Tambien abrimos y cerramos parantensis lo cual indica que este metodo no recibira ningun parametro

Como no tenemos ningun parametro definido en el metodo, en culaquier lado donde llamemos a este metodo, solo podra imprimir los numeros pares hatas el 20.

Pero digamos que quiero hacerlo mas dinamico y poder especificar el numero limite, para darle esa flexibilidad al usuario podemos hacer uso de los parametros.

Digamos por ejemplo que quiero mostrar en pantalla los numeros pares hasta el 30, quisiera pasar ese parametro de la siguietne manera:

```csharp
static void Main()
{
    Program.NumerosPares(30);
}

public static void NumerosPares()
{
    int inicio = 0;

    while(inicio <=20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Y de esta forma el metodo `NumerosPares` deberia ser capaz de imprimir los numeros hasta el 30, y tal vez en otro programa quiero imprimir los numeros hasta el 50 y en esa otra parte del sistema le voy a pasar 50 en lugar de 30 como numero limite, pero la logica deberia ser la misma, solo que esta ves queremos habilitar la opcion de pasarle un parametro al metodo.

Bien veamos como pasar parametros a los metodos.

```csharp
static void Main()
{
    Program.NumerosPares(30);
}

public static void NumerosPares(int numeroLimite)
{
    int inicio = 0;

    while(inicio <= 20 ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Con esto el motodo ya va a recibir el numero limite como parametro y en lugar de tener este codigo duro aqui o codigo harcodeado, recuerden que codigo harcodeado es cuando tenemos valores fijos en el codigo, ya sea numeros o texto, entonces en lugar de tener 20 aqui fijo vamos a utilizar el paremetro recibido `numerolimite`

```csharp
static void Main()
{
    Program.NumerosPares(30);
}

public static void NumerosPares(int numeroLimite)
{
    int inicio = 0;

    while(inicio <= numeroLimite ){
        Console.WriteLine(inicio);
        inicio = inicio + 2;
    }
}
```

Bien ahora estamos pasando el valor de 30 al pamaretro numeroLimite el cual sera utilizado para saber hasta que numero mostrar en pantalla.

> Si corro este programa, vemos que este funciona como esperamos
> 0
> 2
> .
> .
> 30

Y si quiero que le programa muestre los valores hasta el 50, solo tengo que llamar al metodo y pasarle como parametro del numero 50.

Si vemos este metodo no estamos regresando ningun valor, tenemos void como tipo de retorno asi que no regresamos nada.

Digamos por ejemplo que quiero crear otro metodo que tenga un valor de retorno:

```csharp
public int Sumar(int primerNumero, int segundoNumero)
{

}
```
Y que hara este metodo, pues va a sumar esos dos numeros y retornar la suma.

```csharp
public int Sumar(int primerNumero, int segundoNumero)
{
    return primerNumero + segundoNumero;
}
```

Si vemos este metodo, esta recibiendo 2 parametros, sumandolos y retornando esa suma a donde se este llamando el metodo.

Aqui el tipo de retorno del metodo es entero y en este otro meotodo el tipo de retorno es void.

Como no tengo la palabra `static` en este metodo pues esto significa que es un metodo de instancia y para invocarlo no lo podemos hacer directo con el nombre de la clase, asi que tendremos que crear la instancia de la clase `Program`.


```csharp
static void Main()
{
    Program.NumerosPares(30);
    
    Program claseProgram = new Program();
    claseProgram.Sumar(
}

public int Sumar(int primerNumero, int segundoNumero)
{
    return primerNumero + segundoNumero;
}
```

Si vemos el intellisence el tipo de retorno es `int` y el metodo recibe dos parametros de tipo `int`, `primerNumero` y `segundoNumero`

```csharp
static void Main()
{
    Program.NumerosPares(30);
    
    Program claseProgram = new Program();
    claseProgram.Sumar(10 , 20);
}

public int Sumar(int primerNumero, int segundoNumero)
{
    return primerNumero + segundoNumero;
}
```

Si le paso 10 como primerNumero y 20 como segundoNumero, tendra que regresarme la suma 30, como ya se que el valor de retorno es un `int`, puedo crear una variable de tipo `int` para recibir ese valor de retorno.

```csharp
static void Main()
{
    Program.NumerosPares(30);
    
    Program claseProgram = new Program();
    int suma = claseProgram.Sumar(10 , 20);
}

public int Sumar(int primerNumero, int segundoNumero)
{
    return primerNumero + segundoNumero;
}
```

Entonces en la variable suma setoy aguardando el valor de retorno del metodo Sumar y puedo ahora hacer suo de esa variable, por ejepmlo mostrar ese resultado en pantalla:

```csharp
static void Main()
{
    Program.NumerosPares(30);
    
    Program claseProgram = new Program();
    int suma = claseProgram.Sumar(10 , 20);

    Console.WriteLine($"Suma = {suma}");
}

public int Sumar(int primerNumero, int segundoNumero)
{
    return primerNumero + segundoNumero;
}
```

> Bien si corremos el progrmaa vemos que se muestran los numeros pares hasta 30 y despues la suma de 10 + 20, suma igual a 30
> 0
> 2
> .
> .
> 30
> Suma = 30


## [Parte 16][4]-03

Hemos visto la estrutua de un metodo o funcion la cual consiste de:
* Atributos
* Modificadores de acceso
* Tipo de retorno, el cual puede ser void
* Nombre del metodo: el cual puede ser cualquier nombre valido
* Los Parametros que pueden ser opcionales
* Y el cuerpo del metodo

## [Parte 16][5]

Tambien hemos visto la diferencia entre los metodos estaticos y los de instancia.

Cuando un metodo tiene la palabra reservada static entonces este es un metodo estatico, si no la tiene es un metodo de instancia.

Si queremos invocar un metodo estatico tenemos que hacerlo usando el nombre de la clase, en cambio si queremos invocar un metodo de isntancia tenemos que hacerlo a traves de una instancia de la clase, osea tenemos que crear la isntancia de la clase haciendo uso de la palabra reservada `new`.

Hay una razon por la cual quisieramos que un metodo sea estatico en lugar que de instancia, ok, pero hablaremos en detalle de esto en proximas lecciones, para ahora solo debemos entender la diferencia basica entre un metodo estatico y uno de instancia:
* Un metodo es estatico si tiene la palabra static si no es un metodo de instancia
* Un metodo estatico se debe invocar con el nombre de la calse
* Un metodo de instancia se debe invocar con una instancia de la clase

Y mas adelante veremos porque creamos metodos estaticos o de instancia, cuando hablemos de clases veremos la logica detras de cuando utilizar statics y cuando no.

## [Parte 16][6]

Para recursos adicionales pueden vistar el sitio web PragimTech.com.

Esto es todo por hoy gracias por ver este video, te deseo quee tengas un excelente dia.