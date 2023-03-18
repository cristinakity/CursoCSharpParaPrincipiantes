# Contenido

[TOC]

# Parte 17 - Tipos de parametros dentro de los Metodos en C#

## [Parte 17][1]

Hola bienvenidos a Pragim Technologies yo soy Cristina,
esta es la Parte 17: Diferentes tipos de parametros dentro de los metodos en C#

En la parte 16 hablamos sobre la estrucutra de los metodos, donde vimos la estructura basica de los metodos, algunos ejemplos simples de como pasarle parametros a  los metodos y como obtener el valor de retorno de un metodo.

## [Parte 17][2]

Un metodo en C# puede tener diferentes tipos de parametros:
1. Parametros de valor
2. Parametros por referencia
3. Parametros de salida
4. Parametros de entrada
5. Matrices de parametros (parameter arrays)

Em esta leccion tambien veremos los terminos Parametros de metodo y argumentos de metodos.

Veamos un ejemplo

### [vs]-01

Muy bien, digamos que tengo un metodo muy simple:

```csharp
    public static void MetodoSimple(
```

Y este metodo va a recibir un parametro:

```csharp
    public static void MetodoSimple(int j)
    {

    }
```

Y lo que va hacer este metodo es: si le pasamod un valor entero va a cambiar el valor a 101

```csharp
    public static void MetodoSimple(int j)
    {
        j = 101;
    }
```

Cualquier entero que sea pasado a este metodo va a ser cambiado al valor 101, y es todo lo que hara, muy simple no hara ningun calculo ni mostrar nada en pantalla, solo cambiar el valor del parametro recibido.

Ahora para llamar a este metodo como es un metodo estatico, tengo que hacerlo mediante el nombre de la clase, en la leccion anterior Parte 16 - Metodos en C# vimos que para los metodos estaticos debemos utilizar el nombre de la clase para invocarlos, no es necesario crear una instancia para invocarlos como en el caso de los metodos de instancia.

Y como estamos en la misma clase tambien podemos llamarlo solo con el nombre del metodo.

```csharp
    static void Main()
    {
        MetodoSimple(
    }

    public static void MetodoSimple(int j)
    {
        j = 101;
    }
```

Y tenemos que pasarle un parametro, para hacerlo vamos a crear una variable:

```csharp
    static void Main()
    {
        int i = 0;

        MetodoSimple(i);
    }

    public static void MetodoSimple(int j)
    {
        j = 101;
    }
```

Entonces cree una variable `i` de tipo `int` la cual vale cero y la estoy pasando como parametro para `MetodoSimple` y ahora voy a motrar en pantalla el valor de `i`

```csharp
    static void Main()
    {
        int i = 0;

        MetodoSimple(i);

        Console.WriteLine(i);
    }

    public static void MetodoSimple(int j)
    {
        j = 101;
    }
```

Muy bien, veamos el codigo estoy creando la variable i y la estoy pasando como parametro a este metodo y dentro del metodo estoy cambiando el valor del parametro a 101.

Ahora, la pregunta es ¿Cuando cambie el valor de `j` aqui dentro del metodo, este cambiara el valor de la variable `i` que pasamos como parametro?

Entonces cuando estamos pasando `i`, en este caso estamos pasando el valor  de `i` que es cero.  Esto porque el parametro esta siendo enviado como valor o value parameter y lo que hace es enviar una copia de ese valor el cual es cero en este caso y despues esta cambiandolo el valor pero solo a esa copia no al parametro original que pasamos.

## [Parte 17][3]-01

Para nuestro ejemplo en memoria lo que esta pasando es como en el primer diagrama al pasar parametros por valor o value parameters, en realidad ambas variables i y j estan apuntado a diferentes posiciones de memoria por lo tanto son diferentes objetos con diferentes valores y si se cambia el valor en una variable este valor no sera actualizado o no afectara a la otra variable.

Entonces primero:
* i = 0, y al pasar el valor de i 
* j = 0, j tambien vale cero que es el valor que esta recibiendo, pero este no es el mismo que i, sino que es una copia en memoria.

Despues cuando cambiamos el valor de j:
* i = 0, i sigue valiendo cero
* j = 101  pero ahora j vale 101

> Si corremos el ejemplos veremos en pantalla cero el valor de i
> 0

Debido a que estamos pasando un value parameter, o parametro de valor, este al llegar al metodo se crea una copia en memoria del valor y de este modo cualquier cambio en `j` no afecta `i`.

Pero por otro lado, si hacemos una simple modificacion al codigo:

Voy agregar la palabra reservada `ref` lo cual indicara que este sera un parametro de referencia o reference parameter

```csharp
    static void Main()
    {
        int i = 0;

        MetodoSimple(i);

        Console.WriteLine(i);
    }

    public static void MetodoSimple(ref int j)
    {
        j = 101;
    }
```

Utilizando `ref` el parametro `j` ya no sera un parametro de valor o value parameter si no que ahora es un parametro por referencia o reference parameter.

Y ahora cuando haya que invocar el metodo debemos utilizar la palabra `ref`

```csharp
    static void Main()
    {
        int i = 0;

        MetodoSimple(ref i);

        Console.WriteLine(i);
    }

    public static void MetodoSimple(ref int j)
    {
        j = 101;
    }
```

Ahora ¿qué es lo que va a pasar en memoria?

## [Parte 17][3]-02

Ahora `i` y `j` estan haciendo referencia a la  misma posicion de memoria  por lo tanto en un principio ambos van a tener el valor de cero, pero ahora `j` no esta creando una copia de ese valor como en los parametros por valor, sino que esta apuntado a la misma posicion de memoria que `i`, entonces cuando el metodo cambia el valor de `j` tambien esta cambiaando el valor de `i`.

Entonces tenemos dos variables diferentes `i` y `j` las cuales estan apuntando a la misma posicion de la memoria.  Entonces si cambio el valor de una la otra tambien se vera afectada.

> Si corremos el ejemplos veremos en pantalla 101 el valor de i y tambiern de j porque apunta a la misma posicion de memoria, al pasar el parametros por referencia esto es lo que pasa.
> 101

Esta es la diferencia entre pasar un parametro por valor o por referencia.

## [Parte 17][3]-03

Entonces el pasar parametros por valor, se crea una copia en memorai del valor y cada variable apunta a una posicion diferente de memoria, si un valor cambia en una no afecta a la otrra.

Por otra parte al pasar valor por referencia digamos que se pasa esa referencia o posicion de memoria de una variable al parametro y ahora ambas variables a punta a la misma posicion de memoria lo cual significa que al cambiar una de las variables la otra se vera afectada, porque apunta a la misma referencia o misma posicion de la memoria.

Muy bien, esto es pasar el parametro por valor o pasar parametro por referencia.

## [Parte 17][2]-02

El proximo tipo de parametro que vamos a ver es Modificador de parametro out

### [vs]-02

¿Cuándo debemos utilizar el modificador de parametro out?, antes de responder esta pregunta creemos un metodo muy sencillo.

Quiero crear una funcion que sume dos numeros y regrese la suma y tambien quiero que me regrese la multiplicacion, como hago esto:

```csharp
publis static Main()
{

}

public static int Calcular(int primerNumero, int segundoNumero)
{
    return primerNumero + segundoNumero;
}
```

En este ejemplo Calcular solo tiene un valor de retorno el cual es int y solo puede regresar la suma, no puede regresar tambien la multiplicacion, para esto podemos hacer uso del modificador de parametro out y es muy facil de hacer.

Entonces para poder regresar tambien la multiplicacion lo que vamos hacer es crear nuevos parametros y agregarles el modificador de parametro `out`

```csharp
publis static Main()
{

}

public static int Calcular(int primerNumero, int segundoNumero, out int suma, out int multiplicacion)
{
    return primerNumero + segundoNumero;
}
```

Bien ahora qué haremos? pues calcularé la suma y la guardare en el parametro de salida suma y lo mismo para la multiplicacion.

Entonces como ya tengo mis parmetros de salida, osea los parametros que tienen el modificador de parametro out, ya no necesito que este metodo retorne un tipo de dato int, ni que retorne nada, asi que cambiare el tipo de retorno para que en lugar de `int` sea `void`.

```csharp
publis static Main()
{

}

public static void Calcular(int primerNumero, int segundoNumero, out int suma, out int multiplicacion)
{
    return primerNumero + segundoNumero;
}
```

Ahora asignare los valores a suma y multiplicacion

```csharp
publis static Main()
{

}

public static void Calcular(int primerNumero, int segundoNumero, out int suma, out int multiplicacion)
{
    suma = primerNumero + segundoNumero;
    multiplicacion = primerNumero * segundoNumero;
}
```

Ahora podemos llamar este metodo `Calcular`

```csharp
publis static Main()
{
    Calcular(10,20
}
```

Entonces 10 y 20 son los numeros que quiero sumar y multiplicar.
Una vez realizados los calculos el resultado sera almacenado en estos dos parametros de salida suma y multiplicacion.
Asi que necesitamos dos variables para recibir eseos parametros de salida, antes de llamar a la funcion creemos esas variables:

```csharp
publis static Main()
{
    int totalSumado = 0;
    int totalMultiplicado = 0;
    Calcular(10,20
}
```

Ahora lo que vamos hacer es pasar esos parametros y al ser parametros de salida con el modificador out, es necesario agregar la palabra reservada `out` no solo cuando se define el metodo sino tambien cuando se pasan los parametros.

```csharp
publis static Main()
{
    int totalSumado = 0;
    int totalMultiplicado = 0;
    Calcular(10, 20, out totalSumado, out totalMultiplicado);
}
```

Entonces debemos incluir la palabra reservada `out` no solo en la declaracion del metodo sino que tambien cuando lo llamamos o cuando pasamos los parametros.

Bien, si quiero mostrar la suma y la multiplicacion en pantalla, puedo hacerlo agregando la instruccion para mostrar los datos en pantalla despues de llamar al metodo `Calcular`

```csharp
publis static Main()
{
    int totalSumado = 0;
    int totalMultiplicado = 0;
    Calcular(10, 20, out totalSumado, out totalMultiplicado);

    Console.WriteLine($"Suma = {totalSumado}, Multiplicacion = {totalMultiplicado}");
}
```

>Si corremos este programa veremos Suma es igual a 30 y la multiplicaciones  = 200
>Suma = 30, Multiplicacion = 200

Y asi es como se utiliza el modificador de parametro out.

## [Parte 17][5]-01

Cuando queramos que un metodo retorne mas de un valor podemos hacer uso del modificador de parametros out.


Me gustaria añadir una nota importante aqui porque como mencione no es posible regresar mas de un valor como return value.

Pero hay una forma de hacerlo.
1. La forma de regresar mas de un tipo de dato al crear metodos es regresando un tupla o tuple(tah-pl) en ingles.
   * Un tupla basicamente lo que hace es agrupar varios elementos en una estructura de datos ligera, osea tecnicamente solo ponemos entre parentesis un grupo de variables y con esto todo ese conjunto se convierte en un tupla; Esta nueva funcionalidad que se incluyó en c# apartir de la version 7.0 nos permite que un metodo pueda tener de tipo de retorno un tupla y asi regresar mas de un valor al mismo tiempo.

Veamos el mismo ejemplo utilziando tuplas:

```csharp
public static (int, int) Calcular2(int primerNumero, int segundoNumero)
{
    int suma = primerNumero + segundoNumero;
    int multiplicacion = primerNumero * segundoNumero;

    return (suma, multiplicacion);
}
```

Esta seria la forma de crear el tupla.
Bien ahora veamo como llamar a este metodo y obtener la suma y multiplicacion.


```csharp
publis static Main()
{
    int totalSumado = 0;
    int totalMultiplicado = 0;
    var resultados = Calcular2(10, 20);

    totalSumado = resultados.item1;
    totalSumado = resultados.item2;

    //Calcular(10, 20, out totalSumado, out totalMultiplicado);

    Console.WriteLine($"Suma = {totalSumado}, Multiplicacion = {totalMultiplicado}");
}
```

Si vemos la variable resultado contiene los dos valores int que estamos regreando en el metodo Calcular2, pero digamos que es algo confuso porque en realidad no sabemos a que se refiere cada valor, entonces como buena practica podemos ponerle un nombre o alias a esos valores de retorno. 

Veamos el ejemplo de como hacerlo

```csharp
public static (int Suma, int Multiplicacion) Calcular2(int primerNumero, int segundoNumero)
{
    int suma = primerNumero + segundoNumero;
    int multiplicacion = primerNumero * segundoNumero;

    return (suma, multiplicacion);
}
```

Ahora que le asignamos nombres a las variables dentro del tupla, tendremos un error al momento de intentar utilizar las variable, porque obviamente el nombre cambio.

```csharp
publis static Main()
{
    int totalSumado = 0;
    int totalMultiplicado = 0;
    var resultados = Calcular2(10, 20);

    totalSumado = resultados.Suma;
    totalSumado = resultados.Multiplicacion;

    //Calcular(10, 20, out totalSumado, out totalMultiplicado);

    Console.WriteLine($"Suma = {totalSumado}, Multiplicacion = {totalMultiplicado}");
}
```

Hay varias formas de declarar y obtener el resulatdo de un tupla, podemos crear una variable de tipo tupla desde un comienzo, o simplemente utilizar var, ultilizando var el tipo de dato se infiere automaticamente, entonces veamos como hacer lo mismo pero jugando un poquito con el codigo.

```csharp
publis static Main()
{
    int totalSumado = 0;
    int totalMultiplicado = 0;
    (totalSumado, totalMultiplicado) = Calcular2(10, 20);

    //totalSumado = resultados.Suma;
    //totalSumado = resultados.Multiplicacion;

    //Calcular(10, 20, out totalSumado, out totalMultiplicado);

    Console.WriteLine($"Suma = {totalSumado}, Multiplicacion = {totalMultiplicado}");
}
```

Y puedo simplificar aun mas el codigo

```csharp
publis static Main()
{
    //int totalSumado = 0;
    //int totalMultiplicado = 0;
    (int totalSumado,int totalMultiplicado) = Calcular2(10, 20);

    //totalSumado = resultados.Suma;
    //totalSumado = resultados.Multiplicacion;

    //Calcular(10, 20, out totalSumado, out totalMultiplicado);

    Console.WriteLine($"Suma = {totalSumado}, Multiplicacion = {totalMultiplicado}");
}
```

Bueno entonces estaria seria una explicacion muy basica de como retornar varios valores para un metodo y recordemos que podemos hacer esto de dos maneras utilizando el modificador de parametro out y la otra forma es regresando un tupla.


El siguiente Modificador de parametro es in.  Vamos a ver un ejemplo para entenderlo.

### [vs]-02

Muy bien, el modificador in manda el parametro por referencia, pero tiene la diferencia de que el parametro no puede ser cambiando en el metodo, entonces en que escearios podria ser util usar le modificador de parametro in, se me ocurre un ejemplo con valores fijos que no queremos que cambien, podriamos tener un metodo para convertir de pesos a dolares y enviarle como parametro el tipo de cambio, si enviamos un tipo de cambio no queremos que dentro del metodo se pueda modificar ese tipo de cambio en este caso podemos enviar el parametro como in.

```csharp
public static int ConvertirAPesos(int dolares, in int tipoDeCambio){
    return dolares * tipoDeCambio;
}
```

Para llamar a este metodo tengo que agregar in al pasar el parametro y antes crear las varaibles necesarias para almacenar los parametros y el valor de retorno.

```csharp
static Main(){
    int tipoDeCambioOriginal = 19;
    int totalDolares = 100;
    int totalPesos = Program.ConvertirAPesos(totalDolares, in tipoDeCambioOriginal);

    Console.WriteLine($"Tipo de cambio = {tipoDecambioOriginal}, Dolares = {dolares}, Pesos= {totalPesos}");
}

public static int ConvertirAPesos(int dolares, in int tipoDeCambio){
    return dolares * tipoDeCambio;
}
```

Si vemos el ejemplo se ve casi igual que el modificador de parametro out, pero la diferencia es que si intento cambiar el valor de la variable tipoDeCambio tendre un error de compilacion, intentemoslo:


```csharp
static Main(){
    int tipoDeCambioOriginal = 19;
    int totalDolares = 100;
    int totalPesos = Program.ConvertirAPesos(totalDolares, in tipoDeCambioOriginal);

    Console.WriteLine($"Tipo de cambio = {tipoDecambioOriginal}, Dolares = {dolares}, Pesos= {totalPesos}");
}

public static int ConvertirAPesos(int dolares, in int tipoDeCambio){
    tipoDeCambio = 25;// explicar el error
    return dolares * tipoDeCambio;
}
```

## [Parte 17][5]-02

Entonces `in` lo que hace es crear un parametro por referencia de solo lectura, este ejemplo es uno muy basico y simple, pero en realidad `in` fue creado con la intencion de optimizar performance cuando se trabaja con strucs o estructuras muy grandes.  Si quieren saber mas sobre `in` y estructuras de datos les recomiendo revisar la documentacion oficial de microsoft en docs.microsoft.com

El ultimo tipo de parametro que tenemos es las matrices de parametros o parameter arrays, veamos un ejemplo:

### [vs]-03

Basicamente las matrices de parametros son declaras con la palabra reservada `params`, creemos un metodo para ver un ejemplo

```csharp
public static void main()
{

}

public static void MetodoConParams(params int[] numeros)
{

}
```

Bien entonces para crear una matriz de parametros como parametro para un metodo, tenemos que utilizar la palabra reservada `params`, entonces vamos hacer que este metodo nos muestre en pantalla el total de elementos que existen en el arreglo `numeros` y tambien los valores dentro del este.

```csharp
public static void main()
{

}

public static void MetodoConParams(params int[] numeros)
{
    Console.WriteLine($"Total de elementos en el arreglo: {numeros.Length}");

    foreach(int num in numeros)
    {
        Console.WriteLine(num);
    }
}
```

Listo, este es un metodo muy simple lo que hace es recibir un arreglo de parametros y primero muestra el total de elementos en el arreglo, depsues con un ciclo `foreach` itera cada elemento y muestra su valor en pantalla.

Antes de continuar con el ejemplo utilizando la palabra reservada `params`  veamos el ejemplo si la removemos.

```csharp
public static void main()
{

}

public static void MetodoConParams(int[] numeros)
{
    Console.WriteLine($"Total de elementos en el arreglo: {numeros.Length}");

    foreach(int num in numeros)
    {
        Console.WriteLine(num);
    }
}
```

Ahora voy a crear un arreglo

```csharp
public static void main()
{
    int[] arregloDeNumeros = int[3] {101, 102, 103};

}

public static void MetodoConParams(int[] numeros)
{
    Console.WriteLine($"Total de elementos en el arreglo: {numeros.Length}");

    foreach(int num in numeros)
    {
        Console.WriteLine(num);
    }
}
```

Ya tengo el arreglo con 3 elementos, si llamo al metodo

```csharp
public static void main()
{
    int[] arregloDeNumeros = int[3] {101, 102, 103};

    MetodoConParams();
}

public static void MetodoConParams(int[] numeros)
{
    Console.WriteLine($"Total de elementos en el arreglo: {numeros.Length}");

    foreach(int num in numeros)
    {
        Console.WriteLine(num);
    }
}
```

Este metodo esta esperando que le pasemos un arreglo de enteros y si no lo pasamos va a marcar un error, no tiene ninguna otra opciones que enviarle.

Pero si quisieramos hacer ese parametro opcional podemos agregar la palabra reservada `params` 

```csharp
public static void main()
{
    int[] arregloDeNumeros = int[3] {101, 102, 103};

    MetodoConParams();
}

public static void MetodoConParams(params int[] numeros)
{
    Console.WriteLine($"Total de elementos en el arreglo: {numeros.Length}");

    foreach(int num in numeros)
    {
        Console.WriteLine(num);
    }
}
```
Si vemos ahora ya no marca error, porque al utilizar `params` aunque no le pasemos nada el metodo va a seguir funcionando esto es porque `params` tambien hace al parametro opcional.

>Si correo el codigo nos va amostrar que hay cero elementos en el arreglo, porque no le pasamos nada.
>Total de elementos en el arreglo: 0

Otra forma de llamar este metodo es pasarle el arreglo que creamos:

```csharp
public static void main()
{
    int[] arregloDeNumeros = int[3] {101, 102, 103};

    //MetodoConParams();
    MetodoConParams(arregloDeNumero);
}

public static void MetodoConParams(params int[] numeros)
{
    Console.WriteLine($"Total de elementos en el arreglo: {numeros.Length}");

    foreach(int num in numeros)
    {
        Console.WriteLine(num);
    }
}
```

> Si correo el programa nos mostrare que hay 3 elementos y los 3 elementos del arreglo
> Total de elementos en el arreglo: 3
> 101
> 102
> 103

Esta es otra manera de llamar a este metodo.

Pero en verdad la ventaja de utilizar `params` es que podemos agregar n elementos separados por coma, veamos como enviarle los valores de esta manera.

```csharp
public static void main()
{
    int[] arregloDeNumeros = int[3] {101, 102, 103};

    //MetodoConParams();
    //MetodoConParams(arregloDeNumero);
    MetodoConParams(1,2,3,4,5,6,7,8,9,10);
}

public static void MetodoConParams(params int[] numeros)
{
    Console.WriteLine($"Total de elementos en el arreglo: {numeros.Length}");

    foreach(int num in numeros)
    {
        Console.WriteLine(num);
    }
}
```

Entonces agrege los numeros del 1 al 10 pero basicamente se pueden pasar la cantidad de elementos que queramos.

>Al correr el ejemplo vemos que el total son 10 y vemos listados los numeros del 1 al 10 que fueron los valores que le pase al metodo separados por comas.
> Total de elementos en el arreglo: 10
> 1
> 2
> .
> .
> 10

Una cosa a tomar en cuenta al crear parametro de tipo matrices de parametros es que este debe ser el ultimo parametro declarado en el metodo, por ejemplo si el metodo recibe varios parametros el que tenga la palabra reservada `params` debera ser el ultimo.

Por ejemplo si quiero pasarle otro parametro:

```csharp
public static void MetodoConParams(int x, params int[] numeros)
```
Esto esta bien es posible, pero no podemos pasar int x al final despues de params

```csharp
public static void MetodoConParams(params int[] numeros, int x)
```

Entonces `params` debe ser el ultimo parametro del metodo, y solo podemos tener un parametro con la palabra reservada `params`, no podemos agregar otro parametro con la palabra reservada `params` 

```csharp
public static void MetodoConParams(params int[] numeros, params string[] nombres)
```

Esto es todo relacionado con las matrices de parametros o parameter arrays.

## [Parte 17][5]-03

Entonces la palabra reservada `params` nos permite definir un parametro el cual puede recibir n numero de datos seperados por una coma, un arreglo o ningun parametro, osea este parametro se vuleve opcional.  El parametro `params` debe ser el ultimo en la declaracion del metodo y un metodo solo puede contener un `params`

Y con esto vamos a ver a que nos referimos cuando decimos parametros de metodo y cuando decimos argumetnos de metodo.

### [vs]-04

Estos terminos los argumentos y los parametros son utilizados algunas veces en articulos y cuando buscamos al referente a programacion y pueden llegar a ser confusos, en ingles seria parameter y argument.

Entonces los parametros ocmo hemos visto son los que se crean en la declaracion del metodo, los que estan entre parentesis despues del nombre del metodo, estos serian los parametros, que basicamente son las variables que usamos en el metodo.

Y los argumentos son los que estamos pasando al llamar o invocar al metodo, entonces estos valores 1, 2, 3, etc son los argumentos del parametro numeros.

## [Parte 17][4]

Muy bien entonces hemos visto como enviar parametros por referencia y por valor.
Tambien vimos el modificador de parametro out y el modificador de parametro in, las matrices de parametros o parameter arrays y la diferencia entre parametro y argumento.

## [Parte 17][6]

Esto es todo por hoy,

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

muchas gracias por estar aqui y te deseo quee tengas un excelente dia.