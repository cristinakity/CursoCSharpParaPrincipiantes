# Contenido

[TOC]

# Parte 27 - Propiedades en C#

## [Prerequisitos]
Copiar este codigo a C# primero

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

## [Parte 27][1]

Hola bienvenidos yo soy Cristina,
esta es la Parte 27: Propiedades en c#

## [Parte 27][2]

Em esta leccion veremos

Propiedades de lectura y escribura, de solo lectura y de solo escritura

Tambien veremos las propiedades auto implementadas que fueron introducidas a partir de la version 3.0 de c# y el descriptor de acceso init el cual existe apartir de la version 9.0 de c#

## [Parte 27][3]

En la leccion anterior hemos visto como protejer campos de la clase utilizando los metodo getter y setter, en esta leccion haremos lo mismo utilizando propieades.

Si no has visto el video anterior: Parte 26 porque usar propiedades, te sugiero que lo veas antes de continar con este video porque utilizaremos ejemplos del video anterior.

### [vs][01]

En la leccion anterior teniamos la clase Estudiante de ejemplo y encapsulamos los campos id, nombre y calificacionAprobatoria para cumplir las reglas de negocio que teniamos definidas, para esto utilizamos los metodos getter y setter correspondientes para cada campo.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

Por ejemplo para leer y escribir en este campo privado `_id`, estamos haciendo uso de los metodos `GetId` y `SetId`, ¿Como podemos hacer esto mismo utilizando propieadades?  Para hacerlo tendremos que modificar un poco el codigo, sabemos que el id es un entero entonces podemos modificiar el metodo SetId para que retorne un entero

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int SetId(int id)
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

Y no tenemos que recibir ningun parametro asi que vamos remover esta parte del metodo

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int SetId
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

Y lo que debemos tener en su lugar son los descriptores de acceso de propiedad get y set

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int SetId
    {
        set 
        {
            if(id <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = id;
        }
        get
        {

        }
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

Y el `get` lo unico que hara es retornar el `id`:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int SetId
    {
        set 
        {
            if(id <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = id;
        }
        get
        {
            return this._id;
        }
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

Otro cambio es en lugar de que se llame `SetId`, le pondremos simplemente `Id`

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int Id
    {
        set 
        {
            if(id <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = id;
        }
        get
        {
            return this._id;
        }
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

Con esto ya tenemos la propiedad Id y como le asignamos valor:


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int Id
    {
        set 
        {
            if(id <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = id;
        }
        get
        {
            return this._id;
        }
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
      //est.SetId(101);
      est.Id
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

Como vemos podemos acceder a esta propiedad como si fuera un campo,el intellisense nos esta mostrando la propiedad igual como cualquier campo publico de la clase. Entonces le peudo asignar el valor directamente como los campos publicos de clase.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int Id
    {
        set 
        {
            if(id <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = id;
        }
        get
        {
            return this._id;
        }
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
      //est.SetId(101);
      est.Id = 101;
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

Entonces como funciona esta propieada: cuando le asignamos un valor a la propiedad este sera pasado aqui y el descriptor de acceso `set` sera llamado y dentro de este descriptor existe una palabra reservada llamada `value`, entonces vamos a cambiar un poco el codigo para hacer uso de `value`:


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
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
      //est.SetId(101);
      est.Id = 101;
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.GetId()}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

Esta palabra reservada `value` dentro de `set`, contiene el valor que se le asigna a la propiedad.  Entonces al asignar valor a una propiedad se llama al set dentro de la propiedad y este descriptor de acceso `set` recibira el valor dentro de la palabra reservada `value`.

Muy similar si queremos obtener el valor solo tendremos que usar la propiedad como si fuera un campo publico de la clase, pero en este caso se llamara al descriptor de acceso `get` que existe dentro de la propieadad.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
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
      //est.SetId(101);
      est.Id = 101;
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

Por ultimo vamos a remover el metodo `GetId()` porque ya no es necesario.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

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

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

Si vemos la diferencia entre utilizar una propiedad en este caso Id es una propiedad y utilizar los getter y setter, pues la diferencia es que la propiedad se ve como si fuera un campo mas de la clase y con getter y setter estamos llamando a metodos.  En ambos casos tenemos un campo privado, osea protejido y mediante encapsulamiento estamos accediendo a los campos.  La ventaja de las propieades que es trabajamso con ellas como si estuvieramos trabajando directo con los campos, y al asignarle valor a una propiedad se hace mediante el descriptor de acceso `set` y al obtener el valor mediante el descriptor de acceso `get`.

[04:36]

Ahora vamos a cambiar el campo `_nombre` para utiliza una propiedad en lugar de los metodos `GetNombre()` y `SetNombre()`

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

    public int GetCalificacionAprobatoria()
    {
        return _calificacionAprobatoria;
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(nombre)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = nombre;
        }
        get
        {

        }
    }

    public string GetNombre(){
        return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

Cambiamos el metodo por `public string Nombre`, en lugar de `public void SetNombre(string nombre)` y agregamos los descriptores de acceso `get` y `set`, el set hara lo mismo que ya hacia el metodo, solo que debemos utilizar la palabra reservada `value`  para obtener el valor recibido y el descriptor de acceso `get` hara lo mismo que estamos haciendo en el meotodo `GetNombre()`, entonces vamos aplicar estos cambios:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

    public int GetCalificacionAprobatoria()
    {
        return _calificacionAprobatoria;
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

[06:18]

Si vemos el codigo esta propiedad Nombre tiene los descriptores de acceso `get` y `set`, lo cual significa que esta propiedad es de lectura y escritura, osea que podemos asignarle valor y tambien podemos leer el valor, entonces a travez de esta propiedad podemos asignarle un valor al campo privado `_nombre` y tambien podemos leer el valor de este.

Pero si recordamos del ejemplo anterior una de las reglas de negocio es que el campo _calificacionAprobatoria fuera de solo lectura, si queremos que una propiedad sea de solo lectura lo que demos hacer es definir solo el descriptor de acceso `get`.  Una propiedad con solo el descriptor de acceso `get` es una propiedad de solo lectura.

Veamos como hacer esto:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.SetNombre("Homero");

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.GetNombre()}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.GetCalificacionAprobatoria()}");
    }
}
``` 

Lo que hemos hecho hasta ahora es remover todos los metodos get y set, y en su lugar crear las propiedades correspondientes para cada metodo.

Si vemos el ejemplo tenemos dos propiedades de lectura y escritura,  y como sabemos que son de lectura y escritura pues porque contiene ambos descritores de acceso `get` y `set`, y tambien tenemos una propiedad de solo lectura: `CalificacionAprobatoria`, entonces `CalificacionAprobatoria` sabemos que es de solo lecutra porque solo tiene el descriptor de acceso `get` el cual sirve para obtener el valor.

Veamos como hacer uso de estas propiedades:


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.Nombre = "Homero";

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.Nombre}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.CalificacionAprobatoria}");
    }
}
``` 

Para la propiedad `CalificacionAprobatoria` no podremos asignarle un valor porque es de solo lectura asi que vamos a instentar asignarle un valor:


```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.Nombre = "Homero";
      est.CalificacionAprobatoria = 30;

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.Nombre}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.CalificacionAprobatoria}");
    }
}
```

Como vemos al intentar asignarle un valor a la propiedad de solo lectura el compilador nos esta marcando el error: _No se puede asignar a la propiedad o el indizador 'Estudiante.CalificacionAprobatoria' porque es de solo lectura_

Vemos ese error porque esta propiedad solo tiene el descriptor de acceso `get` y esto la convierte en una propiedad de solo lectura, no podemos asignarle valor solo podemos obtener su valor.

Para hacer que una propiedad sea de solo lectura en lugar de tener ambos descriptores de acceso `get` y `set`, debemos de crear solamente el descriptor de acceso `get`.

[08:56]

Y de igual manera si queremos crear una propiedad de solo escritura tendriamos que dejarle solo el descriptor de acceso `set` y remover el descriptor de acceso `get`, esto hara que la propiedad sea de solo escritura.

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;

    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.Nombre = "Homero";

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.Nombre}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.CalificacionAprobatoria}");
    }
}
```

Como vemos en el ejemplo al momento de mostrar en pantalla las propiedades estamos accediendo a ellas como si fueran campos publicos de la clase.

> Se corro el programa, como vemos esta funcionando igual que antes, solo que ahora estamos utilizando propiedades en lugar de metodos getter y setter
> El id del estudiante es 101
> El nombre del estudiante es Homero
> La calificacion aprobatoria para el estudiante es 65

## [Parte 27][3]

En C# para encapsular y proteger campos utilizamos las propiedades en lugar de los metodos getter y setter.

1. Usamos los descriptores de acceso de propiedades get y set para implementar las propiedades.
1. get y set = lectura y escritura.
1. get = solo lectura.
1. set = solo escritura.

La ventaja de las propiedades sobre los métodos Get() y Set() es que puedes acceder a estas como si fueran campos públicos de la clase.

[10:51]

## [Parte 27][4]
Otro concepto importante que se agrego apartir de C# 3.0  son las propiedades auto implementadas.

### [vs][01]

Muchas veces quizas no tengamos tantas reglas de negocio para los campos, como en el ejemplo que validabamos si el nombre era nulo o vacio, tambien que el id no sea negativo.

Digamos por ejemplo que tengo mas campos en esta clase:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;
    private string _ciudad;
    private string _email;


    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.Nombre = "Homero";

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.Nombre}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.CalificacionAprobatoria}");
    }
}
```

Si tuviera que crear propiedades para estos campos:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;
    private string _ciudad;
    private string _email;
    
    public string Email{
        get
        { 
            return this._email;
        }
        set
        {
            this._email = value;
        }
    }

    public string Ciudad{
        get
        { 
            return this._ciudad;
        }
        set
        {
            this._ciudad = value;
        }
    }

    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.Nombre = "Homero";

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.Nombre}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.CalificacionAprobatoria}");
    }
}
```

Para cualquier propiedad que no requiera ninguna logica o regla de negocio dentro de los descriptores de acceso vamos a tener codigo similar.

Y hablando del tipo de clases que se crean en el mundo laboral probablemente tengamos clases con muchos campos y la mayoria de los campos no necesitaran una logica especifica ni validar nada, en esos casos es mucho codigo el que tenemos que escribir y es por esto que se crearon las propiedades auto implementadas.

Veamos el ejemplo de como crear las propiedades auto implementadas:

```csharp
public class Estudiante
{
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;
    
    public string Email{ get; set; }
    public string Ciudad{ get; set; }

    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.Nombre = "Homero";

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.Nombre}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.CalificacionAprobatoria}");
    }
}
```

En este caso lo que esta pasando en el codigo es que el compilador esta creando los campos privados para estas propiedades automaticamente, y seta propiedades estaran leyendo y escribiendo en esos campos que estan siendo creados automaticamente por el compilador.

Enontonces si tenemos 30 campos que no tienen ninguna regla de negocio podemos hacer uso de las propiedades auto implementadas para crearlos como si estuvieramos simplemente creando los campos, pero al agregar los descriptores de accesos get y set se crearan como campos public y detras de escena el compilador creara los campos privados.  Con esto se reduce notablemente la cantidad de codigo que tenemos que escribir.

## [Parte 27][4]
Si no hay lógica adicional para los descriptores de acceso de propiedades podemos hacer uso de las propiedades auto implementadas las cuales fueron introducidas a partir de la versión de C# 3.0.

Las propiedades auto implementadas reducen la cantidad de código que tenemos que escribir.

Cuando utilizamos propiedades auto implementadas, el compilador crea un campo privado el cual puede ser accedido a través del get y set de la propiedad.

## [Parte 27][5]
Otro concepto dentro de las propiedades es el descriptor de acceso `init`, ya hemos visto los descriptores de acceso get y set, y como vimos en los ejemplos get esa para obtener el valor y set para asignarle valor, entonces ¿para que sirve `init`?, veamos un ejemplo:

### [vs][01]

En el caso del descriptor de acceso `init`, no lo podemos utilizar en este proyecto porque a la fecha no podemos utilziar todas las funcionalidades de C# 9.0 dentro de proyectos de .net framework, solo para que no hay confunsion alguna en c# tenemos diferentes versiones del lenguaje c# y tambien diferentes versiones de .net, algunas son compatibles otras no, para mas informacion a cerca de la compatibilidad les sugiero revisar la pagina oficial de visual studio.

En este caso y solo para ver el ejemplo de como utilziar el descriptor de acceso `init` voy abrir otro poryecto que ya tengo listo donde estoy utilizando la version .net 5, pero antes de eso les voy a mostrar que `init` no funciona en este proyecto:

```csharp
public class Estudiante
{    
    private int     _id;
    private string  _nombre;
    private int     _calificacionAprobatoria = 65;
    
    public string Email{ get; set; }
    public string Ciudad{ get; set; }
    public int EscuelaId {get; init;}

    public int CalificacionAprobatoria
    {
        get
        {            
            return _calificacionAprobatoria;
        }
    }

    public string Nombre
    {
        set {            
            if(string.IsNullOrEmpty(value)){
                throw new Exception("El nombre no puede ser nulo o vacio");
            }
            this._nombre = value;
        }
        get
        {
            return string.IsNullOrEmpty(this._nombre) ? "Sin nombre" : this._nombre;
        }
    }

    public int Id
    {
        set 
        {
            if(value <= 0){
                throw new Exception("El id del estudiante no puede ser un numero negativo");
            }
            this._id = value;
        }
        get
        {
            return this._id;
        }
    }

}
public class Program
{
    static void Main(string[] args)
    {
      Estudiante est = new Estudiante();
      //est.SetId(101);
      est.Id = 101;
      est.Nombre = "Homero";

      Console.WriteLine($"El id del estudiante es {est.Id}");
      Console.WriteLine($"El nombre del estudiante es {est.Nombre}");
      Console.WriteLine($"La calificacion aprobatoria para el estudiante es {est.CalificacionAprobatoria}");
    }
}
```

Si vemos los errores hay varios:
1. Utilice la version 9.0 del lenguaje, actualmente estamos en la version 7.3
   * Pero en este caso ya probe cambiando la version del lenguaje en el archivo del proyecto y no funciona, sigue mostrando el otro error
1. El otro error dice que el tipo predefinido IsExternalInit no esta definido ni importado

Entonces init no va a funcionar en proyectos de .net framework 4.8 y si quieren hacer uso de init y otras caracteristicas mas introducidas apartir de c# 9.0 tendran que crear proyectos a partir de .net 5

Dicho esto vamos abrir el proyecto que tenemos de .net 5

```csharp
public partial class Program
{
    public static void Main()
    {
    }
}
```

Voy a crear la clase estudiante con una propiedad Id la cual tendra los descriptores de acceso init y set:

```csharp
public class Estudiante
{
    public int Id { get; init; }
}

public partial class Program
{
    public static void Main()
    {
    }
}
```

Haremos uso de la propiedad en el metodo `Main`:

```csharp
public class Estudiante
{
    public int Id { get; init; }
}

public partial class Program
{
    public static void Main()
    {
        Estudiante est = new Estudiante();

        Console.WriteLine($"El id del estudiante es: {est.Id}");
    }
}
```

Estoy creando uns instancia o un objeto de la clase estudiante y despues estoy mostrando el pantalla el valor de la propiedad Id, vamos a intentar asignarle un valor y veremos lo que pasa:

```csharp
public class Estudiante
{
    public int Id { get; init; }
}

public partial class Program
{
    public static void Main()
    {
        Estudiante est = new Estudiante();
        est.Id = 101;  
        Console.WriteLine($"El id del estudiante es: {est.Id}");
    }
}
```

Como vemos tenemos un error de compilacion: _Solo se puede asignar la propiedad  de solo inicialización "Estudiante.Id" en un inicializador de objeto o en "this" o "base" en un constructor de instancia o un descriptor de acceso "init"._

Esto significa que solo podemos asignarle valor cuando creamos el objeto, entonces solo le podemos asignar valor dentro del constructor, en la misma propiedad o al crear el objeto vamos a ver primero al crear el objeto:


```csharp
public class Estudiante
{
    public int Id { get; init; }
}

public partial class Program
{
    public static void Main()
    {
        Estudiante est = new Estudiante(){
            Id = 101;
        } 
        Console.WriteLine($"El id del estudiante es: {est.Id}");
    }
}
```

Como vemos a una propiedad con descriptor de acceso `init` se le puede asignar valor al crear el objeto.

> Si corremos el codigo deberiamos ver el valor de id impreso
> El id del estudiante es: 101

Otra form de asiglarle valor a una propiedad con descriptor de acceso `init` es mediante el constructor.

Entonces vamos a crear un constructor para la clase y pasarle el valor del id.  Si tienes dudas a cerca de los constructores te recomiendo que veas la parte 019 - Instroduccion a las clases en c# de este tutorial.

```csharp
public class Estudiante
{
    public int Id { get; init; }

    public Estudiante(int id) {
        Id = id;
    }
}

public partial class Program
{
    public static void Main()
    {
        Estudiante est = new Estudiante(101);
        Console.WriteLine($"El id del estudiante es: {est.Id}");
    }
}
```

Entonces el constructor se llama cuando se crea la instancia de la clase o el objeto, al ser asi esto signfiica que le estamos asignando valor al Id al crear la clase, y como es una propiedad con el desciprtor de acceso `init` por lo tanto podemos asignarle valor de este modo, para probar esto voy a crear otro metodo para asignarle valor a esta propiedad:


```csharp
public class Estudiante
{
    public int Id { get; init; }

    public Estudiante(int id) {
        Id = id;
    }
    
    public void AsignarValorAlId(int id)
    {
        Id = id;
    }
}

public partial class Program
{
    public static void Main()
    {
        Estudiante est = new Estudiante(101);
        Console.WriteLine($"El id del estudiante es: {est.Id}");
    }
}
```

> Si corremos el codigo deberiamos tendremos el mismo resultado que antes
> El id del estudiante es: 101

Como vemos no podemos asignarle valor desde otro metodo, pero si desde el constructor.

Y por ultimo vamos a ver como asignarle valor directamente al crear la propiedad.

```csharp
public class Estudiante
{
    public int Id { get; init; } = 101;

    public Estudiante(int id) {
        Id = id;
    }
    
    public void AsignarValorAlId(int id)
    {
        Id = id;
    }
}

public partial class Program
{
    public static void Main()
    {
        Estudiante est = new Estudiante(101);
        Console.WriteLine($"El id del estudiante es: {est.Id}");
    }
}
```

> Si corremos el codigo deberiamos tendremos el mismo resultado que antes
> El id del estudiante es: 101

## [Parte 27][5]

El descriptor de acceso `init` fue introducido a partir de la versión C# 9.0.
`Init` se utiliza en lugar de `set` y esto indica que solo se le puede asignar valor a la propiedad durante la construcción del objeto.


Algo importante es que el `init` es como un `set` pero que solo se puede asignar valor una vez, no se pueden crear propiedades que contengan ambos descriptores de acceso `init` y `set` porque son basicamente lo mismo, con la unica diferencia que `init` solo se le puede asignar valor al crear el objeto osea, en la misma linea donde se define la propiedad, en el constructor o abriendo llaves despues crear la instancia y asignandole valor a la propiedad directamente.

## [Parte 27][6]

Esto es todo por hoy, muchas gracias por escucharme

Para recursos adicionales recuerden vistar el sitio web PragimTech.com.

te deseo quee tengas un excelente dia.