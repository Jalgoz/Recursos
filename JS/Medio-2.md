# JavaScript
## Encadenamiento opcional (?.)
Muchas veces cuando queremos llamar a un método que no existe o iterar sobre una posición del array que no existe nos da error. Pero esto ahora puede ser controlado con el encadenamiento opcional ya que nos permite evitar el error
```
let users = [{name: 'Jose', email: 'jalgoz95@gmail.com'}];
users = [];

console.log(users[0].name); // Esto dará error
console.log(users[0]?.name); // Esto mostrará undefined

const metodo = {

}

console.log(metodo?.noExiste?.tampocoExiste); // Esto mostrará undefined
```

## Funciones de Orden-Superior
En JS se pueden pasar como argumentos a una función otra función a esto se llama funciones de Orden-Superior, siendo la que recibe la función la de Orden-Superior, siempre que se pasa una función a otra, solo se debe pasar el nombre sin los paréntesis.

`const oneWord = function (str) {`    
  `return str.replace(/ /g, '').toLowerCase();`  
`};`  

`const upperFirstWord = function (str) {`   
  `const [first, ...others] = str.split(' ');`   
  `return [first.toUpperCase(), ...others].join(' ');`   
`};`  

`// High-order function`   
`const transformer = function (str, fn) {`   
  `console.log("Original string: " + str);`  
  `console.log("Transformed string: " + fn(str));`   

  `console.log("Transformed by: " + fn.name);`    
`};` 

`transformer('JavaScript is the very best!', upperFirstWord);`
> Retornará = JAVASCRIPT is the very best!

`transformer('JavaScript is the very best!', oneWord);`  
> Retornará = javascriptistheverybest!

## Métodos CALL, APPLY y BIND
Estos métodos se usan para poder de cierta manera decir donde debe apuntar la palabra this al llamar un método

`const lufthansa = {`    
  `airline: 'Lufthansa',`      
  `iataCode: 'LH',`    
 ` bookings: [],`     
  `book(flightNum, name) {`    
    `console.log(this.iataCode + flightNum + " " + name);`     
  `},`    
`};`    

`const book = lufthansa.book;`   
> Aquí asignamos la función a la constante book

`book(23, 'Joe Doe');`   
> Esta no funcionará ya que la palabra this será undefined, debido a que se esta llamando como una función regular

Para que esto funcione y se pueda incluso reutilizar el código se hace el método CALL
`book.call(lufthansa, 23, 'Joe Doe');`   
> Ahora si funcionara correctamente

También funciona con el método APPLY, con la diferencia que como segundo parámetro se debe recibir un array y en call method puede ser todos los argumentos necesarios, pero apply quedo un poco obsoleto debido a que ahora existe spread operator.   
`book.apply(lufthansa, [23, 'Joe Doe'])`  

También se usa el método bind que es muy similar a call
`const bookLW = book.bind(lufthansa);`  
> Así podemos unir el método con la función para que funcione 

Con un ejemplo más practico:
`lufthansa.planes = 300;`  
`lufthansa.buyPlane = function () {`   
  `console.log(this);`   
  `this.planes++;`   
  `console.log(this.planes);`   
`};`    

`document`   
  `.querySelector('.buy')`  
  `.addEventListener('click', lufthansa.buyPlane.bind`     
  `(lufthansa));`  
> Aquí podemos ver como unir el método buyPlane a lufthansa, porque sino de otro modo la palabra this seria del método de que se llama en este caso .queryselector('.buy').

## Immediately Invoked Function Express (IIFE)
Estas son funciones que solo se pueden ejecutar una vez:  
`(function () {`  
  `console.log('This will never run again');`   
`})();`    

` (() => {`  
  `console.log('This will never run again');`    
`})();`  
>Como se puede ver no tienen nombre y estan encerradas en paréntesis y al final tienen la llamada con ();. Estas funciones ya no podran ser llamadas nunca más

## Closures (Cierres)

`const secureBooking = function () {`   
  `let passengerCount = 0;`    

  `return function () {`   
    `passengerCount++;`    
    `console.log(passengerCount + " passenger");`    
  `};`   
`};`  

`const booker = secureBooking(); // Ahora booker es la función que retorna secureBooking();`  
`booker(); // passenger 1`  
`booker(); // passenger 2`    
> Como podemos ver arriba el alcance de la variable passengerCount esta en la función secureBooking por lo que al terminar de ejecutarse esta función también debería dejar de existir. Pero más abajo se ve que se esta asignando a booker la función que accede a la variable passengerCount, a simple vista uno podría decir que cuando llamemos a booker() dará error pero noo, de hecho si podrá acceder y aumentar el valor de passengerCount. A esto se la llama Closure, esto permite que no se pierda la conexión con las variables que existen en el lugar donde nace la función booker. En otras palabra cuando booker es creado se crea una conexión con secureBooking por la cual puede acceder a la variable passengerCount. Programaticamente no hay forma de acceder a la variable passengerCount desde booker. 
