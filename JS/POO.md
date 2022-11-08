# Programación Orientada a Objetos en JS
POO es un paradigma (estilo de código) de programación basado en los conceptos de objetos.
Se usan los objetos para modelar (describir) o abstraer aspecto del mundo real. POO fue desarrollada con el principal objetivo de organizar código para hacerlo mas flexible y fácil de mantener. POO no existe como tal en JS pero si se puede implementar de otras formas.

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

## Object.create()
```
const PersonProto = {
  calcAge() {
    console.log(2037 - this.birthday);
  },

  // Función común que hará de función constructora
  init(firstName, birthday) {
    this.firstName = firstName;
    this.birthday = birthday;
  },
};

const steven = Object.create(PersonProto);
// Inicializamos el objeto steven
steven.init('Steven', 1998);
console.log(steven); // {firstName: 'Steven', birthday: 1998}
steven.calcAge(); // 39
```
> Esta es la última forma de implementar POO en JS, en este caso se crea un objeto con las funciones que se tendrán luego se instancia con el `Object.create(Objeto)` de esta manera se esta vinculando el objeto intanciado con el prototipo al no contar con una función constructora se le debe agregar una. Esta el la manera menos común de POO en JS.

## Herencia con Función constructora
```
const Person = function (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
};

Person.prototype.calcAge = function () {
  console.log(2037 - this.birthYear);
};

const Student = function (firstName, birthYear, course) {
  Person.call(this, firstName, birthYear);
  this.course = course;
};

Student.prototype = Object.create(Person.prototype);

Student.prototype.introduce = function () {
  console.log(`My name is ${this.firstName} and I study ${this.course}`);
};

const mike = new Student('Mike', 2000, 'Computer Science');
mike.introduce(); // My name is Mike and I study Computer Science
mike.calcAge(); // 37

console.log(mike instanceof Student); // True
console.log(mike instanceof Person); // True
```
> De esta forma se puede heredar un clase de otra, se tiene que llamar al constructor de la otra clase padre y asignar la palabra 'this' con el método call al objeto creado(this). Para poder heredar los métodos se tiene que hacer otro paso en el cual asignamos el prototipo del hijo a un objeto creado del prototipo del padre, este paso se tiene que hacer antes de crear cualquier otro método del hijo sino se eliminaran lo métodos previos a esta asignación.

### Sobreescritura de métodos
Cuando se heredan métodos de un padre a su hijo, el hijo puedo sobrescribir el método sin problema y al final el método usado será el del hijo.

## Herencia con Clases ES6
```
class PersonCl {
  constructor(fullName, birthYear) {
    this._fullName = fullName;
    this._birthYear = birthYear;
  }

  get fullName() {
    return this._fullName;
  }

  set fullName(name) {
    this._fullName = name;
  }

  introduce() {
    console.log(`My name is ${this._fullName}`);
  }
}

class StudentCl extends PersonCl {
  constructor(fullName, birthYear, course) {
    // Siempre debe suceder primero (super)
    super(fullName, birthYear);
    this._course = course;
  }

  introduce() {
    console.log(`My name is ${this._fullName} and I study ${this._course}`);
  }
}

const seth = new StudentCl('Seth Lozada', 2022, 'Computer Science');
seth.introduce(); // My name is Seth Lozada and I study Computer Science
console.log(seth.fullName); // Seth Lozada
```

## Campos y Métodos privados
```
class Account {
  // Public fields
  locale;

  // Private fields
  #movements;
  #pin;

  constructor(owner, pin) {
    this.owner = owner;
    this.#pin = pin;
    this.#movements = [];
    this.locale = navigator.language;
  }

  // Private methods
  #approveLoan(val) {
    return true;
  }

  // Public methods
  requestLoan(val) {
    if (this.#approveLoan(val)) {
      this.deposit(val);
    }
  }
}
```
> Para declara los campos y métodos públicos simplemente se declara sin nada por delante. Para declararlos privados se agrega '#' de este modo ya no se podrá acceder a estos atributos desde fuera de la clase. Lo métodos declarados privados no estarán en el prototype del objeto sino en la instancia como una variable más.

## Encadenar métodos
```
class Account {
  // Private fields
  #movements;

  constructor(owner, currency, pin) {
    this.owner = owner;
    this.#movements = [];
  }

  getMovements() {
    return this.#movements;
  }

  deposit(val) {
    this.#movements.push(val);
    return this;
  }

  withdraw(val) {
    this.deposit(-val);
    return this;
  }
}

const acc1 = new Account('Jose', 'EUR', 1111);
acc1.deposit(250).withdraw(130).deposit(500).deposit(150);
console.log(acc1.getMovements()); // (4) [250, -130, 500, 150]
```
> Para encadenar métodos de un objeto simplemente en el método se debe retornar el objeto en si osea 'this'.