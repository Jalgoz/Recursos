# JavaScript
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

## Métodos CALL y APPLY
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

Tambien funciona con el método APPLY, con la diferencia que como segundo parámetro se debe recibir un array y en call method puede ser todos los argumentos necesarios, pero apply quedo un poco obsoleto debido a que ahora existe spread operator.   
`book.apply(lufthansa, [23, 'Joe Doe'])`   
