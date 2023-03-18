# Contenido

[TOC]

# Parte 20 - Miembros de clase estaticos y de instancia en C#

## [Parte 20][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 20: Miembros de clase estaticos y de instancia en C#

## [Parte 20][2]

Em esta leccion entenderemos los conceptos de 
* Miembros estaticos de clase(static class members)
* Miembros de instancia de clase(isntance class member)
* Diferencia entre miembros estaticos y de instancia
* Y tambien Un ejemplo explicando cuando debemos crear ciertos miembros como estaticos

veamos un ejemplo

### [vs][01]
Como parte de entender a los miembros estaticos y de instancia de clase, primero creemos una clase muy simple llamada Circulo

```csharp
using System;

class Circulo{

}

class Program{
    public static void Main(){

    }
}
```

Y esta clase circulo va a tener dos campos:
* Pi
* Radio

Muy bien vamos agregar estos dos campos:
[00:44]

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;
}

class Program{
    public static void Main(){

    }
}
```

Para inicializar los campos de la clase como sabemos podemos hacer uso de un constructor, en la parte 19 - Introducccion a las clases de este tutorial hablamos sobre los constructores, entonces vamos a crear el constructor y como saben el constructor debe tener el mismo nombre que la clase, no tiene tipo de retorno y puede recibir parametros los cuales pueden ser utilziados para inicializar los campos de la clase.
  

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }
}

class Program{
    public static void Main(){

    }
}
```

Como vemos en el constructor estamos recibiendo un parametro de tipo entero llamado `radio` y este valor lo estamos utiliznado apra inicializar el campo de la clase `_radio`, entonces hemos creado un constructor que inicializar el campo `_radio` y el campo `_pi` ya esta siendo inicializado en la misma linea donde se declaro

Ahora vamos a crear un metodo que nos sirva para calcular el area del circulo y retorne el valor calculado.

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
    }
}

class Program{
    public static void Main(){

    }
}
```

Ya tenemos el metodo que va retornar un `float` y que es lo que va hacer este metodo pues clacular el area y retornar su valor.

Sabemos que para calcular el area de un cuadrado la formula es pi por radio al cuadrado asi que podemos realizar ese calculo de la siguiente manera

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return this._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){

    }
}
```

Recordemos que la palabra reservada `this` esta haciendo refernecia a la instancia de la clase, entonces al utilizarla tendremos acceso a los miembros de instancia de la clase.

Si vemos el codigo tenemos la clase  Circulo la cual al ser una clase tiene unos datos que repesentan el estado de la clase y los datos son los campos `_pi`y `_radio` y tambien tiene un comportamiento representado por que es lo que puede hacer esta clase, que puede hacer esta clase? pues calcular el area entonces podemos decir que el metodo `CalcularArea` es el comportamiento de la clase.

Para darle uso a esta clase podemos crear un objecto en en el metodo `Main`
[04:06]
¿Cómo hacemos esto?, veamoslo

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return this._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(
    }
}
```

Como vimos utilizamos el operador `new` para crear la isntancia de la clase `Circulo`, el cual nos indica que se esta creando la instancia para el objeto `c1`, entonces al estar creando un objeto de `Circulo` debemos pasarle el parametro al constructor, aqui en este punto despues de `new`y el nombre de la clase si vemos el intellisense nos estadiciendo que esta clase en su constructor requiere un campo de tipo int, el campo `radio`, entonces vamos a pasarle un valor de tipo `int`

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return this._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
    }
}
```
[04:31]

Ya esta crea la instancia y si quiero obtener el area del circulo para despues mostrarla en pantalla:

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return this._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area = c1.CalcularArea();
    }
}
```

Estoy usando la instancia de la clase para llamar al metodo `CalcularArea()` y si vemos el valor de retorno de este metodo pues es un `float` y este valor lo estamos gaurdando en al variable `area`, si quiero imprimir el area puedo hacerlo ~~con Console.Writeline~~
[04:52]

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return this._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area = c1.CalcularArea();

        Console.WriteLine($"El area del circulo es: {area}");
    }
}
```

Ahora si vemos este codigo, es un codigo muy simple, solo estamos creando una instancia de la clase, pasandole un valor miediante el constructor, despues llamando a un metodo que retorna calcula y retorna el area y al final mostrando el are en pantalla. 

> Si corremos esta aplicacion, veremos el resultado del area
> El area del circulo es: 78.525

Obtuvimos los resultaods esperados al correr el programa, ahora hagamos otra cosa.
[05:38]

Digamos que quiero crear otro objecto para la clase Circulo 

```csharp
using System;

class Circulo{
    float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return this._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Ok, hasta ahora lo que hemos hecho es crear dos instancias de la clase `Circulo`, una con un radio de 5 y la otra con un radio de 6, vamos a correr este codigo y veamos los resultados

> Corramos le codigo
> El area del circulo 1 es: 78.525
> El area del circulo 2 es: 113.076

Muy bien es un ejemplo simple, pero tenemos algo mal aqui en la forma como hemos diseñado esta clase, veamos esto, como sea que creemos un objecto para la clase `Circulo` la unica diferencia es que `c1` tiene un radio de 5 y `c2` tiene un radio de 6, pero el valor `_pi` es 3.1416 en la instancia `_c1` y tambien es 3.1416 en la instancia `c2`, entonces sin importar si creamos 1,2 o mil instancias de la clase `Circulo` el valor de `_pi` es una constante y no va a cambiar en ningun objeto de `Circulo` que creemos, entonces si el valor de `_pi` no cambia digamos que deberia ser un valor estaico o `static`.

Osea que cuando un valor no cambie entre instancias de clase es prudente convertir este valor en un valor `static`, antes de convertir `_pi` en un valor estatico veamos que esta pasando con este codigo, entonces  en memoria cuando creamos los objetos `c1` y `c2` si vemos la clase `Circulo` que contiene dos campos los cuales no tiene la palabra reservada `static` al inico por lo tanto son campos de instancia o campos no estaticos, y esto no solo aplica para los campos tambien aplica para los metodos, constructors y diferentes miembros de la clase, digamos que todos los diferentes miembros que una clase puede tener, pueden ser de dos tipos: estaticos o de instancia.

Para que un miembro de una clase sea estatico debe tener la palabra reservada `static` si no la tiene es entonces es de instancia.

Cuando un miembro de la clase es de instancia lo que va a pasar en memoria y veamos el diagrama en la diapositiva.

## [Parte 20][3]

Si ambos `_pi` y `_radio` son miembros de instancia, al crear varias instancias de la clase `Circulo` cada instancia va a reservar pocisiones de memoria para todos sus miembros de instancia, osea `c1` va a tener dos espacios reservados de la memoria para cada uno de sus campos de instancia y lo mismo pasara para el objeto `c2` y como vemos `_pi` vale lo mismo en ambas instancias por lo tanto digamos que estamos gastamos memoria de mas, innecesariamente creando dos objetos de `_pi`.  Entonces si tuvieramos que crear miles de circulos imaginense que la variable `_pi` va a tener el mismo valor en todas esas instancias y se va crear un espacio en memoria para esta variable en cada una de las instancia y esto terminaria consumiendo mucha memoria.  Entonces viendo este comportamiento y pensando como diseñar mejor nuestras clases tiene sentido cambiar la variable `_pi` para que sea un miembro de clase estatico porque el valor en realidad no esta cambiando, al marcar `_pi` como estatico en memoria habra solo 1 posicion reservada para esta variable sin importar cuantas instancias de la clase creemos y este valor al ser estatico sera compartido con todas las instancia que tengamos.

## [Parte 20][4]
Si `_pi` es estatico y `_radio` es un miembro de instancia, como vemos en el diagrama en este caso ambos compartiran el valor de `_pi` el cual sera creado en memoria solo una vez y este sera compartido con todos los objectos de `Circulo` sin importar si cremaos 2 o miles de objetos de la clase.

Y este comportamiento con los miembros de clase estaticos tambien aplica para metodos, por ejemplo si tenemos un metodo de instancia cada instancia tendra su porpia copia de ese metodo en memoria pero si tenemos un metodo estatico entonces ese metodo solo existira una vez en memoria y sera compartido para todas las instancias.

Si tenemos algo que no va a cambiar entre las diferentes instancias de una clase entonces es conveniente marcarlo como estatico.

### [vs][01]
Entonces volviendo a nuestro ejemplo marquemos la variables `_pi` como estatica.  Y recordemos la diferncia entre un miembro de clase estatico y uno de instancia es que al llamarlos por ejemplo para los de instancia necesitamos crear una instancia de la clase primero, pero para los estaticos tendremos que utilizar el nombre de la clase.
[10:58]

```csharp
using System;

class Circulo{
    static float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return this._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Muy bien si vemos el codigo ahora que `_pi` es un miembro de clase estatico tenemos un error esto es porque la palabra reservada `this` hace referencia a la instancia de la clase y los miembros estaticos no son parte de la instancia de la clase, no  pueden ser llamados utilizando una instancia de la clase, en su lugar podemos llamar al campo utilizando el nombre de la clase.

```csharp
using System;

class Circulo{
    static float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Y esto de llamar a los miembros  estaticos utilizando el nombre de la clase directamente no solo aplica para campos por ejemplo si creamos otro metodo:

```csharp
using System;

class Circulo{
    static float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public static void Imprimir(){
        // Codigo para imprimir informacion del Circulo
    } 

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Si vemos el metodo estatico que acabamos de crear y lo comparamos con el metodo de instancia `CalcularArea()`, estamos creando instancias de la clase para las variables `c1` y `c2`, mediante estas instancias estamos llamando al metodo `CancularArea()` al ser de instancia podemos hacer esta llamada, pero para llamar al metodo `Imprimir()` el cual es estatico tendriamos que poner el nombre de la clase `Circulo.Imprimir()`, entonces si quisiera utilizar `c1` y si escribimos el punto vemos que el intelisense solo nos sugiere al metodo `CancularArea()` y no al metodo `Imprimir()`, pero por otro lado si pongo el nombre de la clase `Circulo`, pongo el punto y vemos el intellisense nos esta sugiriendo el motodo `Imprimir()`

Los miembros estaticos son llamados medientes el nombre de la clase, esto tiene mucho sentido porque los miembros estaticos no cambian entre las diferentes instancias, y los miembros de instancia son llamados mediante una instancia de la clase, esta es una de las diferencias entre los miembros estaticos y de instancia, la otra diferencia es como son almacenados en memoria, entonces sabemos que los estaticos solo son credos una vez en memoria sin importar cuantas instancias creemos y que los de instancia se crean en memoria cada vez para cada instancia.

Muy bien entonces removamos el metodo `Imprimir()`

```csharp
using System;

class Circulo{
    static float _pi = 3.1416f;
    int _radio;

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```
[14:45]

Hicimos al campo `_pi` estatico y en el metodo `CalcularArea()` cambiamos la llamada en lugar de usar `this` usamos el nombre de la clase.  Y con estos cambios ahora este programa es un poco mas esficiente porque si vemos en la dispositiva

## [Parte 20][4]

la variable `_pi` solo sera creada en memoria 1 vez y esta referencia sera utilizada por todas las instancias de la clase, osea si creamos miles de instancias solo existira un `_pi` en memoria compartodo por todas las instancias, haciendo el programa un poco mas esficiente al no desperdiciar tanta memoria para el mismo campo y asi es como funcionan los miembros de clase estaticos.

## [vs][01]
[15:24]

Muy bien, otra cosa dentro de las clases y sus miembros estaticos es que un constructor puede ser estatico.

Si vemos este codigo el campo `_radio` es un campo de instancia y para inicializar los campos de instancia se necesita un constructor de instancia como que tenemos aqui el cual recibe un parametro `int radio` y este parametro esta inicializando el campo de instancia `_radio`, de igual manera para inicializar un campo estatico podemos crear un constructor estatico, y para hacer a un constructor estatico si vemos el constructro de instancia tiene el modificador de acceso `public` (hablaremos de modificadores de acceso en proxima lecciones) entonces como decia el constructor de instancia tiene un modificador de acceso, mientras que un constructor estatico no tiene un modificador de acceso.

```csharp
using System;

class Circulo{
    static float _pi = 3.1416f;
    int _radio;

    public static Circulo(){

    }

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Bien acabo de agreagr un constructor `static` con el modificador de acceso `public`, pero si intento compilar este codigo voy a tener un mensaje de error,  y el mensaje dice que los modificadores de acceso no estan permitidos en los constructores estaticos.  Y esto tiene sentido porque si por ejemplo no ponemos modificadores de acceso en la clase, removamos el modificador de acceso del constructor de instancia

```csharp
using System;

class Circulo{
    static float _pi = 3.1416f;
    int _radio;

    static Circulo(){

    }

    Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Si remeuvo  el modificador de acceso de un miembro de la clase por default este miembro sera privado or `private` y que significa que sea privado, pues que solo podra ser accedido dentro de la misma clase, fuera de la clase no se podra acceder a este miembro de clase.

En el momento que removi el modificador de acceso `public` del constructor de instancia, este se convirto en un constructor privado y ya no podra ser accesido fuera de la clase y como vemos hay errores de compilacion aca en donde estamos creando las instancias, el error dice que la clase `Circulo` no contiene un constructor que reciba un parametro y esto es porque el constructor no es visible aqui fuera de la clase, solo sera visible dentro de la clase porque removimos el modifciador de acceso `public` y por default ahora se ha convertido en un constructor `private` y solo estara disponible dentro de la misma clase.

Entonces el constructro que inicializa los campos de instancia debe ser publico para poder pasarle el valor al campo de instancia y este sera llamando al momento de crear la instancia de la clase.

```csharp
using System;

class Circulo{
    static float _pi = 3.1416f;
    int _radio;

    static Circulo(){

    }

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Por otro lado el constructor `static` sera llamado automaticamente cada vez que utilicemos el campo estatico, no es necesario llamar a los constructores estaticos, sino que son llamados automaticamente (o explicitamente) cuando se accede o se hace uno de los miembros estaticos de la clase.

Entonces un constructor estatico no puede ser publico porque no necesita ser llamado desde fuera de la clase, ni ser invocado, si no que este se invoca automaticamente al momento de hacer uso por ejemplo del capmo `_pi` que es estatico y los construres estaticos son utilizados para inicializar a los campos estaticos de la clase.

Si quiero inicializar el campo estatico `_pi` en lugar de hacerlo aqui mismo donde se esta declarando puedo hacerlo en el constructor statico.

```csharp
using System;

class Circulo{
    static float _pi;
    int _radio;

    static Circulo(){
        Circulo._pi = 3.1416f;
    }

    public Circulo(int radio){
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```
[19:21]

El constructor estatico no permite modificadores de acceso, debe tener la palabra reservada `static`, son utilizados para inicializar a los campos estaticos de la clase y los constructores estaticos son llamados antes de que los constructores de instancia sean llamados y aun antes que se acceda a un miembro de clase statico, probaremos esto un poco mas adelante primero analizemos que esta pasando en este codigo, si corremos el codigo no habra ninguna diferencia entre lo que estabamos haciendo anteriormente, cuando `_pi` era un miembro de instancia.

>corremos el programa y vemos el mismo resultado que antes.
> El area del circulo 1 es: 78.525
> El area del circulo 2 es: 113.076

pero ahora tenemos que `_pi` es en realidad un miembro estatico de clase haciendo este progama un poco mas esficiente porque ahora solo tendremos esta variable 1 ves registrada en memoria como miembro estatico de la clase.
[20:13]

## [Parte 20][5]
[20:25]
Cuando un miembro de clase tiene el modificador static, este será llamado como un miembro estático (utilizando el nombre de la clase).
Cuando un miembro de clase NO tiene el modificador static, este será llamado como un miembro no estático o un miembro de instancia(debemos crear una instancia de la clase para llamarlo).

Los miembros estáticos son invocados usando el nombre de la clase, mientras que los miembros de instancia son invocados usando instancias(objectos) de la clase.

Un miembro de instancia pertenece a una instancia especifica de la clase.  Si creo 3 objectos de una clase tendré a todos los miembros de instancia de esa clase 3 veces en memoria, y solo tendré en memoria a los miembros estáticos una vez.

Hemos visto esto en el ejemplo de codigo donde teniamos los campos `_pi` y `_radio`, `_pi` era un campo estatico y etaba declarado en memoria solo una vez para las dos instancias de la clase `Circulo` que teniamos, mientras que el campo `_radio` al ser un miembor de clase de instancia estaba siendo declarado en memoria cada vez por cada instancia de la clase.

Cuando nos referimos a miembros de clase estamos hablando de todos los campos, métodos, propiedades, eventos, índices, constructores dentro de una clase.

## [Parte 20][6]

El constructor estático es utilizado para inicializar los campos estáticos de la clase.

Para declara un constructor estático solo hay que agregar la palabra reservada static al inicio.

El constructor estático es llamado solo una vez, sin importar cuantas instancias de la clase se creen, mientras que un constructor de instancia es llamado cada vez que se cree la instancia de la clase.

Los constructores estáticos son llamados antes que los constructores de instancia.  Veamos un ejemplo de esto:


```csharp
using System;

class Circulo{
    static float _pi;
    int _radio;

    static Circulo(){
        Console.WriteLine("Llamada al constructor estatico.");
        Circulo._pi = 3.1416f;
    }

    public Circulo(int radio){
        Console.WriteLine("Llamada al constructor de isntancia.");
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
    }
}
```

Si corremoes este programa, como estaos creando dos objetos de la clase, el construrctor de instancia debera ser llamados dos veces, una vez para cada instancia creada y el constructor statico sera llamado solo una vez.

> Corramos el programa.
> Llamada al constructor estatico.
> Llamada al constructor de isntancia.
> El area del circulo 1 es: 78.525
> Llamada al constructor de isntancia.
> El area del circulo 2 es: 113.076

Como vemos el constructor estatico es llamado incluso antes de que creemos el object he incluso antes de que intentemos acceder al campo estatico, por ejemplo vamos a comentar todo del metodo `Main`

```csharp
using System;

class Circulo{
    static float _pi;
    int _radio;

    static Circulo(){
        Console.WriteLine("Llamada al constructor estatico.");
        Circulo._pi = 3.1416f;
    }

    public Circulo(int radio){
        Console.WriteLine("Llamada al constructor de isntancia.");
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        /*
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
        */
    }
}
```

Ahora lo que voy hacer es mostrar en pantalla el valor de la variable estatica ` _pi`, para esto primero tengo que convertir a la variable `static flat _pi`  en `public`  para que pueda ser accedida desde afuera de la clase `Criculo` y despues ya podre llamarla directo en el metodo `Main` 


```csharp
using System;

class Circulo{
    public static float _pi;
    int _radio;

    static Circulo(){
        Console.WriteLine("Llamada al constructor estatico.");
        Circulo._pi = 3.1416f;
    }

    public Circulo(int radio){
        Console.WriteLine("Llamada al constructor de isntancia.");
        this._radio = radio;
    }

    public float CalcularArea(){
        return Circulo._pi * this._radio * this._radio;
    }
}

class Program{
    public static void Main(){
        Console.WriteLine(Circulo._pi);
        /*
        Circulo c1 = new Circulo(5);
        float area1 = c1.CalcularArea();
        Console.WriteLine($"El area del circulo 1 es: {area1}");
        
        Circulo c2 = new Circulo(6);
        float area2 = c2.CalcularArea();
        Console.WriteLine($"El area del circulo 2 es: {area2}");
        */
    }
}
```

Ahora no estoy creando una instancia de la clase, si no que estoy accediendo directo a una variable estatica de la clase utilizanod el nombre de la clase.

Entonces vamos a obtener el valor de `_pi`  el cual sera inicializado en el constructor estatico

> Corramos el programa.
> Llamada al constructor estatico.
> 3.1416

Los constructores estaticos son llamados antes que los de instancia y aun antes que los miembros estaticos de la clase tambien recordemos que solo son llamados una vez.

## [Parte 20][6]

Esto es todo por hoy, muchas gracias por escucharme

te deseo quee tengas un excelente dia.
