# Programación Orientada a Objetos en JS
POO es un paradigma (estilo de código) de programación basado en los conceptos de objetos.
Se usan los objetos para modelar (describir) o abstraer aspecto del mundo real. POO fue desarrollada con el principal objetivo de organizar código para hacerlo mas flexible y fácil de mantener.

## Abstracción
Ignora o oculta los detalles que no importan, permitiéndonos tener una vista general de lo que estamos implementando. Nos ayuda a simplificar los aspectos del mundo real que pueden llegar a ser muy complejos abstraiéndolos para una mejor comprensión. 

## Encapsulamiento
Restringir el acceso de las propiedades y métodos de una clase, así estos no podrán ser accedidos fuera de esta. Esto para prevenir que cualquier código externo pueda manipular el estado interno de la clase.

## Herencia
Hace que las propiedades y métodos de una cierta clase estén disponibles para las clases hijas, formando una herencia entre clases. Esto nos permite reutilizar lógica que es común en ambas clases.

## Polimorfismo
Permite a las clases hijas poder sobre escribir métodos heredados de una clase padre. Esto nos da la capacidad de que diferentes objetos tengan una respuesta distinta e independiente a una misma acción.

_______________________________________________________
## Como funciona POO en JS ?
A diferencia de la POO clásica donde instanciamos objetos de una clase. En JS tenemos un objeto que tenemos que vincularlo a un Prototype (serian como clases), los Prototype contienen los métodos, propiedades y al enlazarlos al objeto estos también pueden acceder a estos métodos y propiedades a esto se le llama la herencia de prototipo. Una diferencia muy importante de la POO clásica y la de JS es que en la primera los objetos instanciados copian los métodos de la clase a todas las instancias y en la segunda los objetos delegan su comportamiento (métodos) al prototype.

### Como implementar la POO en JS ?
Existen 3 diferentes formas para implementar:  
1.- **Función constructora**  
* Técnica de crear objetos desde una función.
* Esta es la forma en que Arrays, Maps y Sets están implementados.
* Es una forma de crear objetos mediante programación.  
* Esta forma es la más antigua y es como se implementaba antes clases.

2.- **Clases de ES6**  
* Esta es la alternativa más moderna.
* Detrás de escenas las clases de ES6 trabajan igual que la función constructora. Es más como una capa de obstrucción de esta.  
  
3.- **Object.create()** 
* Es la forma más fácil y directa de vincular un objeto a un prototipo de objeto, pero a su vez es la menos común que se utiliza.

## Función constructora
```
const Person = function (firstName, birthYear) {
  // Es convención que sea la primera letra en mayúscula del nombre de la clase
  this.firstName = firstName;
  this.birthYear = birthYear;
};

const jose = new Person('Jose', 1995);
console.log(jose); // Person {firstName: 'Jose', birthYear: 1995}

// 1. Un nuevo objeto es creado
// 2. La función es llamada, this = objeto nuevo creado
// 3. Este nuevo objeto se vincula al prototipo Persona
// 4. La función automáticamente retorna el objeto
```
> Para crear un objeto se de usar la palabra reservada new

### Prototype
Para crear los métodos no se recomienda hacerlo en la función constructora Person por un tema de rendimiento. En cambio se hace lo siguiente: 
```
Person.prototype.calcAge = function () {
  console.log(2037 - this.birthYear);
};

jose.calcAge(); // 42
```
> Creándolo asi la variable 'jose' tiene acceso al método calcAge. Es así como hereda ese método del objeto Person. Cabe recalcar que el prototype creado pertenece a todos los objetos vinculados a Person y no así a Person mismo

```
console.log(Person.prototype.isPrototypeOf(jose)); // True
console.log(Person.prototype.isPrototypeOf(Person)); // False
```
También se puede declarar propiedades con prototype
```
Person.prototype.species = 'Homo Sapiens';
console.log(jose.__proto__); // {species: 'Homo Sapiens', calcAge: ƒ, constructor: ƒ}
```
> Esta será como una propiedad heredad que compartirá con los demás objetos vinculados al Person.

## Clases en ES6
```
// Class declaration
class PersonCl {
  constructor(firstName, birthYear) {
    this._firstName = firstName;
    this._birthYear = birthYear;
  }

  // Todo lo que este fuera del constructor estará en el prototipo y no el objeto en sí
  calcAge() {
    console.log(2037 - this._birthYear);
  }
}

// Instanciamos un objeto con la clase Persona
const esmeralda = new PersonCl('Esmeralda', 2000);
esmeralda.calcAge(); // 37

// También se puede crear los métodos de esta forma
PersonCl.prototype.greet = function () {
  console.log(`Hey ${this.firstName}`);
};

esmeralda.greet(); // Hey Esmeralda

// 1. Classes are NOT hoisted
// 2. Classes are first-class citizes // Osea pueden pasarlas a la s funciones y también devolverlas de las funciones
// 3. Classes are executed in strict mode
```
> Es muy similar a la funciones constructoras, con la diferencia de que se crea con la palabra 'class' y que las métodos si se pueden agregar en el cuerpo de la clase.

### Getter & Setter
```
class PersonCl {
  constructor(firstName, birthYear) {
    this._firstName = firstName;
    this._birthYear = birthYear;
  }

  get firstName() {
    return this._firstName;
  }

  set firstName(name) {
    this._firstName = name;
  }
}

const jose = new PersonCl('Jose', 1995);
console.log(jose.firstName); // Jose

jose.setFirstName = 'Adolfo'; // Adolfo
console.log(jose.firstName);
```
> Como se ve se debe declarar con la palabra get y set. Se los llama sin usar el '()'. Por convención es recomendado poner _ antes de las variables de la clase, debido a que puede crear conflicto con el nombre del set y get.

### Método estático
```
class PersonCl {
  constructor(firstName, birthYear) {
    this._firstName = firstName;
    this._birthYear = birthYear;
  }

  static hey() {
    console.log('Hello');
  }
}

const jose = new PersonCl('Jose', 1995);

PersonCl.hey(); // Hello
jose.hey(); // Uncaught TypeError: jose.hey is not a function
```
> Para crear métodos estáticos se debe crear con la palabra reservada static. Solo la clase puede acceder a este método NO los objetos instanciados de esta clase.