# Contenido

[TOC]

# Parte 1: Introducción a C#

## Recursos:
- Youtube:  
    [![Parte001](https://img.youtube.com/vi/nSMybHaYddo/mqdefault.jpg)](https://youtu.be/nSMybHaYddo) 

- [![Pdf](../../CursoCSharpParaPrincipiantes/assets/64_pdf_icon.png)](001-C%23-Introduccion.pdf)

## [Parte 01][1] Diapositiva 1
Hola bienvenidos a Pragim Technologies mi nombre es Cristina Carrasco, 
esta es la parte 1: Introducción a C#

## [Parte 01][2] Diapositiva 2
## En esta lección veremos:
- La estrucutra basica de un programa en C#
- Que es un namespace
- Proposito del metodo Main o principal

## [Parte 01][3] Diapositiva 3
... Vamos al ejemplo!

## [VS][01]

Vamos abrir Visual Studio
- Inicio y escribimos Visual Studio
- Damos click para abrirlo una vez abierto vamos a crear un proyecto nuevo:

Y recordemos que en .Net podemos crear una gran variedad de programas utilizando diferentes
1. Lenguajes de programacion
   	- `<Ejemplos y mostrar la lista>`

2. Plataformas de desarrollo: como por ejemplo
	- `<Mostrar la lista>`

3. Tipos de proyectos| tipos de applicaciones
	- `<Mostrar la lista>`

En esta leccion nos enfocaremos en:
- Lenguaje: C#
- Plataforma: Windows
- Tipo de proyecto o applicacion: Consola
	
Visual studio nos da dos opciones:

1. **.Net Core**
   - Es para desarrollar en cualquier plataforma
2. **.Net Framework**
   - Es para entornos de desarrollo de Windows

Nombraremos al proyecto: `CSharpIntroduccion`
- [Click Aceptar]

Esto creara un proyecto de consola de C#

Bien, Hablaremos de El explorador de Solucciones, ventana de propiedades, toolbox, etc en proximas lecciones asi que hay que cerrarlos por ahora.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp7
{
    internal class Program
    {
        static void Main(string[] args)
        {
        }
    }
}
```

Y voy hacer este program tan simple como sea posible asi que removeremos codigo innecesario dejando solo lo minimo requerido para que funcione.

`<Remover todo lo innecesario>`
```csharp
using System;

class Program
{
    static void Main()
    {
    }
}
```

Ok

Si miran este programa es muy simple solo 3 lineas de codigo y 2 pares de llaves.

Bien, ¿Qué queremos que haga este programa?
Quiero que este programa imprima un mensaje muy simple en la consola, la consola no es otra cosa que Command Prompt o simbolo de sistema tambien conodico como CMD, 
Podeos acceder al Comman Prompt 
- si presionamos [Windows] + [R] 
- escribimos CMD
- damos click en aceptar

Esta es la ventana de comandos, simbolo de sistema o command prompt, en una ventana como esta quiero que el progama muestre el mensaje "Bienvenidos al curso de introduccion a C#" y para hacer esto es muy simple

No tengo que crear nuevos metodos ni nada por el estilo, puedo hacer uso de clases que ya vienen incluidas en el framework de .net, si eres nuevo en el framework de .net  por favor revisa mis video tutoriales de .net framework

Dentro de framework de .net tenemos una clase llamada Console y la podemos utilziar para escribir mensajes en la Consola o leer mensajes de la consola.  Este programa tiene que escribir algo en la consola porlo que utilizare una funcion llamada `WriteLine` y con esto le pasare un mensaje que sera mostrado en la Consola 

`<Escribir "Bienvenidos al curso de introduccion a C#">`

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Bienvenidos al curso de introduccion a C#");
    }
}
```

Y ahora para correr el programa presiono [Ctrl] + [F5] y una vez que lo haga abrira una ventana de Consola con el mensaje impreso en pantalla y un mensaje presione cualquier clase para salir y si lo hago la ventan se cerrada automaticamente.

Y es asi de simple si queremos mostrar un mensaje en pantalla solo utilizamos el metodo WriteLine dentro de la clase `Console` y pasar el mensaje que queremos que imprima o muestre en pantalla.

Bien, Si vemos este programa hay varias partes envueltas en el funcionamiento de este:
- La primer linea aqui es: "La declaracion de los namespace"
	- **¿Qué es la declaracion del namespace?**
    	- Basicamente esta linea le dice al resto del programa que vamos a utilizar codigo que se entra dentro de el namespace System.
  	- **¿Qué es un namespace?**
    	- Por el momento hay que entender que es una coleccion de clases, porque si vemos esta clase `Console`, si revisamos el nombre completo es System.`Console`, lo que significa que la clase `Console` esta dentro del namespace System.
    - Si no tuviera la declaracion del namespace System ¿Qué pasaria?
		- `<removerla>`
		- Miren tenemos un error, cual es el error? La clase `Console` no existe, este subrayado rojo indica que hay un error en el codigo, si trato de "build" esta aplicacion si voy al menu Debug>build vere el error en la parte de abajo de la pantalla, un error de compilacion 
  			> "El nombre `Console` no existe en el contexto actual" 
			
			esto es porque el pograma no sabe de donde viene esta Clase `Console`, para hacer uso de clases dentro del namespace system necesitamos utilizar la declaracion de using System; Esto le dira a nuestro programa que haremos uso de esta clase que esta dentro de system namespace.
		
	- ¿Es el Namespace una coleccion de clases?, no, es una coleccion de varios objectos por ejemplo

## [Parte 01][4]

Un namespace se utiliza para organizar el codigo y ademas es una coleccion de clases, interfaces, estructuras, enumeradores y delegados.
	
Hablaremos de todos estos objetos a detalle en proximas lecciones asi que por ahora no se preocupen por estos conceptos y solo para entender que es un namespace, basicamente se utilizan para organizar el codigo y es una coleccion de estos objetos.
	
## [vs][02]

Solo para demostrales que de hecho el namespace es una coleccion de todo esto, `<escribir System.>` miren esto por ejemplo `Action`  es un delegado, un namespace puede contener delegados, 
y si vemos este `Activator` es una clase, y veremos mas objetos variados, si vemos esto `Configuration` es otro namespace lo cual significa que un namespace tambien puede contener a otros namespaces, que es un namespace es algo que sirve para organizar el codigo y puede contener clases, delegados, namespaces, etc.

¿Es obligatorio que declaremos el `namespaces` aqui? no, podemos removerlo y poner el nombre completo de la clase con todo y namespace, asi que podemos utilizar todo el nombre de la clase asi o utilizar using y agregar el namespace al programa es decision de casa programador y depende de lo que mas nos convenga.  Por lo general se utiliza la declaracion de los namespaces al principio porque si utilizamos la clase Consolo por ejemplo en muchas partes del codigo no tendriamos que repetir el namespace System en cada ocasion y esto hace la programacion mas facil, basicamente tendriamos menos codigo.
	
Otra cosa importante que entender aqui es esta clase Program, cualquier codigo que escriban estara dentro de una clase existen clases estaticas y clases de instancia de las cuales hablaremos ha detalle en proxima lecciones hasta entonces nose preocupen por este tema,  pero tengan en mente cualquier codigo que escriban estara dentro de una clase, esta funcion `Main` tiene que existir dentro de una clase y asi es, se encuentra dentro de la clase Program, ok?

Este metodo o esta funcion, funciones y metodos son en realidad los que hacen el trabajo dentro de los programas, hablaremos de funciones a detalle en proximas lecciones, una funcion puede tener algo llamdo modificadores de acceso, modificadores staticos, pueden retornar diferentes tipos de datos, tambien tiene un nombre y parametros, asi que hablaremos de esto en proximas lecciones, pero si vemos aqui esta funcion `Main()`, `Main` es el nombre dela funcion, esta funcion es muy importante en applicaciones de consola porque es donde se ejecuta este programa, cada vez que corremos el programa la ejecucion de este inicia justamente aqui en esta funcion `Main` en esta llave de apaertura y termina en la llave de cierre, asi que si corro este programa que va ha pasar? la ejecucion entrada aqui imprimira esta linea de codigo y terminara aqui. 

Hare una copia de esta funcion y llamare a esta `Main1` y solo para diferenciarla agregare un 1 aqui al final.

Si ejecuto este programa ¿Qué mensaje creen que se mostrara en la consola?, este mensaje o este otro? o los dos? Qué creen que pasara?

## [Parte 01][4]

	Si vemos la definicion del Metodo `Main`... `<Leer definicion>`
	
## [vs][03]

Entonces ¿Cuál es el metodo `Main`?..

- `<seleccionar metodo main>`
- `<seleccionar metodo main1>` Este no es el metodo main porque se llama `Main1`, el programa tratara el metodo `main1` como algo mas y no como el punto de entrada para la aplicacion de consola.
- `<Seleccionar Main>` Este es el metodo de entrada para la aplicacion asi que la ejecucion del programa iniciara aqui y terminara aqui y no mostrara en pantalla esta linea, ok?

Si nuestra clase es Program y tiene cientos de metodos dentro de ella como sabe la clase que metodo iniciara la ejecucion de este programa, eso queda determinado por el metodo Main porque es el putno de entrada de la  aplicacion, asi que vamos a correr o ejecutar esta aplicacion y vemos el mensaje `<Leer el mensaje>` el cual es este de aqui y no mostrara esta otra linea, pero que tal si quiero que esta linea tambien sea mostrada en pantalla?

y la forma de hacerlo es justo antes de que el programa termine podemos llamar a la funcion `Main1()` entonces que va ha pasar? cuando corramos el programa la ejecucion iniciara aqui mostrara este mensaje en pantalla y despues tenemos la llamda a `Main1()` asi que el programa llamara esta funcion tambien,  entrara a la funcion `Main1()` y mostrara este otro mensaje en pantalla finalizara la llamada a la funcion `Main1()`, regresara al a ejecucion de `Main()` y finalizara aqui.

Si corro el programa mostra los do mensajes en la ventan de consola.
	
Una cosa que hay que tener en cuenta es que cada aplicacion de consola debe tener un metodo `Main` que basicamente le dice a la aplicaicon que ese es el  punto de entrada al programa, o que es donde el programa debe iniciar la ejecucion.
	
## [Parte 01][3] Diapositiva 3
`<Explicar el codigo>`
```csharp
//Declaración de los Namespace
using System;

class Program
{
    static void Main()
    {
        //Escribir en la consola
        Console.WriteLine("¡Bienvenido a PRAGIM Technologies!");
    }
}
```


## [Parte 01][4] Diapositiva 4
La declaración de Namespace: “`using System`” indica el uso del namespace `System`.
Un Namespace es utilizado para organizar el código y es una colección de clases, interfaces, estructuras, enums y delegados.

El método `Main` es el punto de entrada para la aplicación.


## [Parte 01][5] Diapositiva 5

Esto es todo en esta presentacion, para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Gracias por estar aqui que  tenga un excelente dia :)