# Contenido

[TOC]

# Parte 2: Leer y escribir en la consola

## Youtube:
### [Parte 003 - C# Tipos de datos integrados](https://www.youtube.com/watch?v=wIhXJTQ1b_w&list=PLc-yEcA6C6vnuUpisYeg47UoNJ4fg2QMg&index=3&ab_channel=KudvenkatSpanish)

## [Parte 3][1]

Hola bienvenidos a Pragim Technologies mi nombre es Cristina Carrasco, 
esta es la parte 3: Tipos de datos integrados o Built-in types
<next>

## [Parte 3][2]
En esta leccion veremos:
Los diferentes tipos de datos integrados en C#
Secuencias de escape en C#
y Verbatim Literal

- Entonces empecemos con los tipos de datos integrados en C#
[x]
<abrir visual studio con un ejemplo>
El primer tipo de dato en la lista, 
por ejemplo en nuestra aplicacion necesitamos almacenar una valor que sea verdadero o falso
En este caso necesitariamos una variable booleana para alamacenarlo
Por ejemplo una pregunta, ¿Eres mayor de edad? la respuesta seria si o no, verdadero o falso

Para crear una variable booleana usaremos
<escribir bool> la palabra reservada bool
y el nombre b = true;

este tipo de dato booleano solo puede alamacer verdadero  o falso, si o no, 1 y 0 

Si tratamos de asinarle cualquier otro valor aparte de falso o verdadero tendremos un error, por ejemplo si le trato de asignar un numero,
veremos un error y el erro es el valor  123 no puede ser convertido a tipo booleano

En otros lenguajes como C++ podemos asignarle numeros a variables boolean, en este 0 es falso y cualquier otro numero es verdadero, pero aqui en C# los valores posibles son true o false

## [Parte 3][2]
El siguiente tipo de dato que veremos son los valores enteros, o integer,
Existe una variedad de tipos de datos enteros: mensionarlos
https://msdn.microsoft.com/es-mx/library/exx3b86w.aspx
Todos estos pueden almaacenar numeros

Si vemos como los tamaños son calculados hay una formula detras de esto, por ejemplo 1 bit puede representar 2 valores diferentes
1 y 0, pero 8 bits juntos pueden representar 2 elevado a la 8ctava potencia que serian 256 valores diferentes, osea desde el  0 hasta el 255 es igual a  256 valores diferentes
asi que un solo byte que son 8bits, puede almacenar 256 valores,

Tambien tenemos sbyte, s significa sign, o el signo negativo y esto quiere decir que tambien puede almacenar valores negativos 

lo mismo pasa para los demas valores integer, short, long, tienen su contra parte Unsing = sin simbolo, una variable unsing solo puede almacenar valores positivos en este casi serian desde 0 hasta la longitud maxima 

Cual es la diferencia entre todos estos tipos de datos, pues 
byte es 1 byte,
integer es 32bits que equivalen a 4bytes
long es 64 bits, 8bytes 

Asi que es nuestra aplicacion por ejemplo si vamos almacenar la edad de una persona... el valor maximo podria ser 130 años, entonces la edad de una persona es una valor relativamente pequeño asi que para almacenar un valor como este el tipo de dato byte es mas que suficiente.
Por otro lado si quisieramos almancenar el numero de habitantes de un pais el tipo de dato Integer seria el mas adecuado porque es mas grande,  y tambien como debe ser un valor mayor que cero en este caso convendria mas usar uint y si la poblacion es mayor que maximo para int podriamos usar ulong,

Asi que dependiendo del requerimiento tenemos varias opciones de tipos de datos para usar en nuestra aplicacion.

Bueno, entonces es obligatorio recordar todos los rangos de valores posibles para cada tipo?, la verdad no creo que sea algo practico, aun si no lo recuerdas, o si no puedes acceder a internet
Visual Studio sabes cuales son los rangos, podemos obtener el numero menor y mayor para cada tipo utilizando visual studio
<ejemplo>
int i = 0;

Si queremos saber este dato para una variable int, 
El tipo de dato integer tiene propiedades <-- hablaremos de propiedades en lecciones mas avanzadas, 
pero de momento tengan en mente que int tiene una propiedad llamada MinValue y si vemos la propiedad <leer intellisent>


Console.WriteLine($"Min = {int.MinValue}");
<Correr ejemplo comprar valor con la pagina de microsoft>
<Hacer mismo ejemplo pero para Max>

Bien estos son los diferentes tipos de datos para enteros en C#

El siguiente tipo de dato son los valores de punto flotante,
enteros puedes almacenar el numero completo o "entero"
Pero los float almacenan numeros incompletos, osea con decimales,
https://msdn.microsoft.com/es-mx/library/9ahet949.aspx
Estoy serian numero grandes de 34 y  64 bits 

<ir al ejemplo>
por ejemplo 

double d = 123.2242433
Console.WriteLine(d);

Si quisiera hacer eso mismo con un entero, no podriamos almancenar la parte decimal.

int d = 123.2242433
Console.WriteLine(d);

Si lo cambiamos tendremos un error automaticamente.
<Regresar a pagina msdn>
Igual para float, si necesitamos menos precision podemos elegir float, esa seria la diferencia entre double y float.

El siguiente tipo de dato es Decimal
El tipo de dato decimal tiene mucha mas precision
tiene de 28-29 digitos y el tipo de dato es enorme 128 bits

<Regresar al ejemplo>
Igual para usar decimal solo cambiamos el tipo de dato y ya, estos son los tipos de datos presentes en C#

## [Parte 3][2]
Hablaremos de tipos de datos decimal, Esccape Sequences y Verbatim Literal en nuestro proximo video en Parte 4

Gracias por estar aqui, que tengan un dia genial!!



