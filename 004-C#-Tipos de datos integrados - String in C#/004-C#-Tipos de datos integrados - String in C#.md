[Part4][1]
Hola bienvenidos a Pragim Technologies mi nombre es Cristina Carrasco, 
esta es la parte 4: Tipos de datons integrados: String en C#
[Part4][2]
Ya vimos los demas tipos de datos integrados en Parte 3 de estos videos.

En esta leccion veremos los tipos de datos String
Desde la parte 1 ya estuvimos trabajando con valores string cuando mostramos mensajes en pantalla y tambien leimos strings desde la consola y lo concatenamos con Hola y el nombre ingresado.

En esta leccion veremos los tipos strings  y varios otros detalles que debemos tener en mente al trabajar con strings, como las secuencias de escape por ejemplo.

Bien, vamos al ejemplo:
<visual studio>
En C# los strings se representan dentro de comillas dobles, asi que en C# estas se usan para indicar el inicio y el fin de una cadena de caracteres  o de un string.
Por ejemplo si queremos almacenar el nombre de una persona:

	string name = "Pragim";
	<explicar esto indica el inicio, esto indica el final>
	
	Si queiro mostrar le nombre en pantalla:
	Console.WriteLine(Name);
	
	<correr y explicar>
	
	Digamos que quiero mostrar Pragim junto con las comillas, 
	¿Cómo hago eso?
	
	""Pragin"<--Si pongo otra comilla doble aqui, 
	Miren eseto, aqui estoy indicando que el estring inicia aqui y finaliza aqui, por lo tanto lo demas no es parte del string y tengo un error en el codigo.
	
	Y como se muestra las comillas dobles para C# tienen un significado especial, no puedo simplemente ir y ponerlas dentro de un string espernao que se muestren en pantalla porque para C# esto significa otra cosa.
	Si quiero imprimir la comilla doble, hay una forma especial de hacerlo y es utilizando las secuencias de escape o scane sequence.
	
	En C# el caracter para indicar la secuencia de escape es la diagonal invertida \ 
	por ejemplo: comillas dobles tienen un significado especial pero puedo utilizar el caracter especial para la secuencia de escapa he indicarle a C# que quiero mosrar esas comillas dobles como parte de mi string
	"\"Pragim"
	Esta diagonal invertida lo que hace es decirle a C# que lo que sea que siga de mi sera tratado como cualquier caracter y sera mostrado en caso que queramos mostrarlo en consola sin importar que tenga un significado especial, 
	
	Hay algunos caracteres que tiene un sifnificado especial para C# y para esto necesitamos el caracter de secuencia de escape.
	
	Vamos a completar este ejemplo queiro que la palabra Pragim se muestre en pantalla entre comillas dobles..|
	<terminar el ejemplo y correrlo>
	
	Hay diferentes carascteres de secuencia de escape en C# y si quieren hecharles un vistazo pueden visitar este articulo de msdn:
	https://docs.microsoft.com/es-mx/cpp/c-language/escape-sequences
	
	Hay diferente por ejemplo siquiero mostrar la comilla simple: \' o si quiero mostrar un salto de linea \n
	
	Vamos hacer un ejemplo con \n Nueva linea
	<hacer el ejemplo> 
	
	Uno\nDos\nTres
	
	si utilizo esto, las palabras seran mostradas en nuevas lineas.
	
	\n tiene un significado especial, no vamos a ver \n en la pantalla si no que hara un salto de linea o mostrara el texto en una nueva linea.
	
	<volver a la pagina msdn>
	Entonces las secuencias de escape dependiendo la que usemos tendremos el resultado esperado, por ejemplo si quiero mostrar la diagonal invertida en el mensaje pues utilizare \\
	
	Por ejemplo en una ruta de windows, si quiero imprimir una ruta valida:
	c:\\pragim\\dotnet\\Curso\\CSharp
	
	Si corremos el programa..<run>
	
	Vemos que tengo \\ aqui pero en la consola solo estamos mostrando \ porque es el caracter de escape y lo definimos utilizando  \\ el compilador sabe que \\ es el caracter de escape para \
	
	Aun asi si vemos este codigo, no es tan facil de leer, esto no se ve como una ruta de windows valida, digamos se ve bien aqui y  esat simple entre comillas, pero imaginemos que tenemos una lista de directorios de windows y para poderlos mostrar correctamente tendremos que agregarle las diagonales nosotros a toda la lista.
	
	Por suerte para solucionar esto en C# tenemos lago llamado Verbatim Literal
	¿Qué es Verbatim Literal?
	
	Veamos un ejemplo 
	Si vemos este string en particular no se ve "bien", como una ruta normal de windows no es tan facilmente lejible, para hacerlo mas simple:
	Agregamos @ y vamos a correr el programa
	Si ven aqui ahora tenemos\\ doble diagonal invertida, 
	entonces cuando agregamos la @ al inicio del string todos nuestras secuencias de escape ya no seran tratadas como secuencias de escape ahora seran como caracteres imprimibleds justo como cualqueir otro caracter letra o numero, 
	Entonces si quieres tratar a las secuencias de escape como cualquier otro caracter que se puede mostrar en al consola solo hay que agregar la @ al inicio lo cual convertira le  estring en Vebatim Literal
	
	Cuando realmente se utilzia Verbatim string, este ejemplo que acabamos de ver es una de esas ocaciones al trabajar con rutas de archivos, porque si queremos que el programa se vea mas legible pues solo hacemos eso y ya.
	<remover doble \ digonal invertida >
	Si corremos esto y comparamos se ve mas bonito mas simple tal cual.
	
	[Part 4][2]
	
	En esta leccion hemos visto.
	El tipo de dato incluido en C# String, que inicia con comilla doble y termian en comilla doble, osea en C# los string se definen dentro de comillas dobles.
	Vimos que existen diferentes secuencias de escape, para saltar linea, o moestrar caracteres especiales, y este caractere de secuencia de escape es la diagonal invertida en C#, si quieres imprimir la comilla simple o doble o la diagonal invertida tendremos que hacer uso del caracter de secuencia de escape \
	<next>
	Tambien vimos Verbam Literal, ¿Que es verbatim literal?
	[Part 4][3]
	<leer la diapositiva>
	
	Tabmien vimos que si queremmos mostrar estos caracteres en la consola podemos utilziar Verbatim Literal, que esto se indica agregando una @ al inicio del string
	
	[Part 4][4] 
Esto es todo en esta presentacion, para recursos adicionales porfavor revisen la pagina web en Pragimtech.com,

Gracias que tenga un excelente dia :)
	
