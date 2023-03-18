
# Contenido

[TOC]

# Parte 2: Leer y escribir en la consola


## Recursos:
- Youtube:  
    [![Parte001](https://img.youtube.com/vi/-NGto7710Qk/mqdefault.jpg)](https://youtu.be/-NGto7710Qk) 

- [![Pdf](../../CursoCSharpParaPrincipiantes/assets/64_pdf_icon.png)](002-C%23-Leer%20y%20escribir%20en%20la%20consola.pdf)

## [Parte 2][1]

Hola bienvenidos a Pragim Technologies mi nombre es Cristina Carrasco, 
esta es la parte 2: Leer y escribir en la consola

## [Parte 2][1]

En la parte 1: Introduccion a C#
Vimos <next>

## [Parte 2][2]

La estructura basica de un programa en C#
¿Qué es un Namespace?
y el Proposito del metodo Main

<next>

## [Parte 2][3]
Vimos un programa de C# muy sencillo, si vemos la diapositiva lo que el programa hace es mostrar este mensaje en la pantalla
<Change to Parte 2>

## [Parte 2][1]

Pero en esta leccion Parte 2 haremos este programa un poco mas interactivo, 

por ejemplo al ejectuar el programa este preguntar por le nombre del usuario y podemos escribir el nombre en la consola y el programa debera mostrar como resultado Hola y el nombre escrito, 

si escribo Pragim com nombre el programa debera mostrar Hola Pragim, o si escribo Cristina el programa demera mostra en la consola Hola Cristina

Con esto el programa deberia ser un poco interactivo; Tomara el valor introducido por el usuario y el programa regresara un mensaje con ese valor...
Esto es leer desde la consola y escribir en la consola.

<next>

## [Parte 2][2]

Asi que en esta leccion veremos:
- Leer desde la consola	
- Escribir en la consola
- 3 formas de escribir en la consola
	- a) Concatenando
	- b) Sintaxis de marcadores de posicion (Place holder)
	- c) Interpolacion de cadenas (String interpolation)		
		>  Una cadena interpolada es un literal de cadena que puede contener expresiones de interpolación

Vamos al ejemplo!

## [vs]
Qué debe hacer nuestro programa?
Debe mostrarle un mensaje al usuario, pidiendole que escriba su nombre
El usuario escribira su nombre
y el programa retornara otro mensaje mostrando el nombre del usuario

- Para escribir un mensaje en la consola podemos utilizar el metodo WriteLine dentro de la clase Console:
  
`<escribir Console.WriteLine();>`

- Le diremos al usuario que escriba su nombre:
`<"Por favor escriba su nombre: ">`

Una vez que el usuario escriba su nombre y presione [Enter]
deberiamos recibir ese nombre desde la consola, 
por ejemplo si corro este programa se mostrara el mensaje "Por favor escriba su nombre"
Asi que el usuario tendra que escribir su nombre y nosotros deberiamos obtener ese nombre desde la consola 
Y para hacer eso, para leer datos desde la consola tenemos que hacer uso del metodo `ReadLine()`

**Qué hace la funcion ReadLine?**

Esta funcion leeara una linea de texto que hayamos escrito en la consola, todo lo escrito antes de presionar Enter.
Si vemos el intellisense podemos notar que esta function retorna un string
al escribir por ejmpleo Pragim, pragim es un string, y este valor necesita ser almacenado en una variable

`<escribir String NombreDeUsuario =>`
Asi que esta variable almacenara el nombre del usuario
[Video-03:37]
La variable guardara el valor y que queremos ahcer con este valor? mostralo en la consola.

Y para hacer esto, es igual escribimos algo en la consola utilizando el metodo WriteLine
`<Escribir>`
Escribo la palabra que queiro imprimir y agrego o concateno el valor de la variable nombreDeUsuario

Vamos a correr el programa [ctrl] + [F55]

Cuando lo corro nos muestra el primer mensaje y el curso se queda aqui en al consola esperando que escriba el nombre:
`<escribir> `y presionar [enter] 
al momento de presionar enter lo que va ha pasar es que esta parte del codigo sera ejecutada y el resultado sera almacenado en la variable 

Y en la isguiente linea mostraremos en pantalla el mensaje Hola junto con el nombre escrito.

Es asi de simple:

Esto es Escribir en la consola 
y esta linea es leer desde la consola

Para escribir en la consola existen mas formas, esto es concatener

Para hacer lo mismo pero con Place holder sintax, o sintaxys de marcador de posicion, y como lo haces es muy facil:

<escribir "Hola {0}"> {0} <-- este es el placeholder o marcador de posicion...
Va tomar la variable y reemplazar esta parte por la variable

Si corro el programa el resultado sera el mismo.

Hay una mejor manera de hacerlo es mi preferisa, simplemente utilziar String interpolation, o interpolacion de cadena.

Para hacer esto igual se utilizan las llave como tipo placeholder, pero en lugar de poner un numero ponemos la variable, y hay que utilizar el signo de pesos $ al inicio de la cadena.

## [Parte 2][3]
	C# es case sensitive, distingue entre mayusculas y minusculas, por lo cual <regresar al ejemplo>
	Si por error escribo nombredeusuario este se pondra seleccionado en rojo indicando que tenemos un error
	el compilar de C# trata estos dos nombres de variable como si fueran variables diferentes
	por esto hay que tenerlo en cuenta siempre, errores que podriamos tener en el codigo pueden ser causados por este detalle.
	
## [vs]

	Demostrar porque es mejor string interpolation en el caso de recibir muchos datos en la pantalla
	--agregar nombre, apellido edad
	
Un ejemplo muy simple de como escribir y leer en la consola, si ven el ejemplo en verdad es muy sencillo y facil.

## [Parte 2][2]
	-- Leer otra vez la slide 
	En esta leccion vimos...
	* String interpolation es mas convenientey facil de usar.

## [Parte 2][3]
	C# es case sensitive
	
	
## [Parte 2][4] 

Esto es todo en esta presentacion, para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Gracias que tenga un excelente dia :)