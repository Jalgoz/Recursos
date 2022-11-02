# JavaScript

## Destructuring Arrays
Sirve para poder copiar valores de un array o objeto a otro ya sea que se quiere solo una variable o el array dentro de otro array

### Ejemplo sin usar el Destructuring
`const arr = [2, 3, 4];`  
`const a = arr[0];`  
`const b = arr[1];`  
`const c = arr[2];`


### Ejemplo usando Destructuring
`const [x, y, z] = arr;`

#### Tambien se puede saltar un elemento si se desea 
`[x, , z] = arr; // Dejando un espacio en blanco`

______________________________________________
## Tambien se puede con una estructura de datos mas compleja

`const restaurant = {`     
  `name: 'Classico Italiano',`  
  `location: 'Via Angelo Tavanti 23, Firenze, Italy',`  
  `categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],`  
  `starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread',`   `'Caprese`   `Salad'],`    
  `mainMenu: ['Pizza', 'Pasta', 'Risotto'],`
  `openingHours: {`   
    `thu: {`   
      `open: 12,`   
      `close: 22,`    
   `},`  
    `fri: {`    
      `open: 11,`     
      `close: 23,`    
   `},`   
    `sat: {`   
      `open: 0, // Open 24 hours`     
      `close: 24,`    
    `},`         
  `},`  

#### Obtendremos el primer y el tercer dato de categories
  `let [principal, , secondary] = restaurant.categories;`  
#### Si queremos cambiar los valores también se puede de manera más fácil y sin el uso de una variable temporal
`[principal, secondary] = [secondary, principal];`  
### Matriz anidada
`const nested = [2, 4, [5, 6]];`   
`let [i, , j] = nested;`
#### El problema acá es que j será un vector con 2 posiciones[5, 6], si queremos obtener directamente los valores de ese vector se debe hacer lo siguiente  
`[i, , [j, k]] = nested; // j = 5 y k = 6`    

### Destructuring array también nos ayuda en caso de que no sepamos el tamaño del array
#### Ademas se le puede asignar valores por defecto, escribiendo la variable = valorPorDefecto
`const [p = 1, q = 1, r = 1] = [8, 9]; // r será igual a 1 por que así lo especificamos en caso de no especificar será undefined`
________________________________________________
## Destructuring Objects
### Cuando hacemos destructuring con corchetes, nos los busca por el nombre que tiene dentro del objeto, sin importar el orden en el que le mandemos, restaurant esta definido más arriba
`let { name, openingHours, categories } = restaurant; // El resultado será name = restaurant.name, openingHours = restaurant.openingHours, categories = restaurant.categories`

### También se les puede asignar un nombre aparte para acceder a esa variable
`{ name: n, openingHours: o, categories: c } = restaurant;`

### Los valores por defecto también son permitidos
`const { menu = [], starterMenu: starters = [] } = restaurant; // En este caso 'menu' será un array vació debido a que no existe ese campo en restaurante`

### Cambiando variables en este caso se debe tener cuidado

`let a = 111;`  
`let c = 999;`  
`const obj = { a: 23, b: 7, c: 14 };`  
`{a, c} = obj; // Dará error se tiene que encerrar en paréntesis`  
`({ a, c } = obj); // a = 23, c = 14`

### También se puede acceder a las variables anidadas de los objetos
#### Como mostramos antes openingHours = restaurant.openingHours
`const {`  
  `fri: { open, close },`  
`} = openingHours;`   
### // open = 11, close = 23 
_____________________________________
## Spread operator
### Lo que hace es desempaquetar un array para pasarlo a otro o hacer otras acciones, la característica principal es que al usar el spread operator en un array nos quedamos con cada valor individual de este

`const arr = [7, 8, 9];`  

`console.log(arr); // resultado=(3) [7, 8, 9] `   
`console.log(...arr); // resultado=7 8 9`

### Se puede copiar array a otro mas fácilmente
`const newArr = [1, 2, ...arr] // El resultado será un nuevo array con 5 posiciones con los valores de 1, 2, 7, 8, 9` 

### Spread operator siempre desglosara el elemento
#### Ejemplo
`const name = 'Jose';` 
`console.log(...name); // resultado=(4) ['J', 'o', 's', 'e']` 

### También nos ayuda a copiar objetos
`const restaurant = {`     
  `name: 'Classico Italiano',`  
  `location: 'Via Angelo Tavanti 23, Firenze, Italy',`  
  `categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],`  
  `starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread',`   `'Caprese`   `Salad'],`    
  `mainMenu: ['Pizza', 'Pasta', 'Risotto'],`
  `openingHours: {`   
    `thu: {`   
      `open: 12,`   
      `close: 22,`    
   `},`  
    `fri: {`    
      `open: 11,`     
      `close: 23,`    
   `},`   
    `sat: {`   
      `open: 0, // Open 24 hours`     
      `close: 24,`    
    `},`         
  `},`  

  `const newRestaurant = {...restaurant};`   

________________________________________________
## Diferencia Spread operator y Destructuring
### Ambos nos ayudan a copiar array's la diferencia principal esta en que Destructuring no permite copiar un array a otras variables ya se para almacenar un valor único o otro array, en cambio Spread operator no nos permite guardar un valor individual sino lo copia como array pero separado por comas

________________________________________________
## Rest Pattern

### Rest y Spread son lo opuesto el uno del otro mientras Spread nos permite separar los valores para asignarlos a una variable, Rest junta los valores para asignar a una variable, Spread desempaqueta y Rest Empaqueta 

### Spread, porque esta a la derecha de '='
### Rest, porque esta a la izquierda de '='
`const [a, b, ...others] = [1, 2, 3, 4, 5]; // El resultado será que others será un array con 3 posiciones mientras a y b tendrán un solo valor`

### El elemento Rest siempre debe ser el ultimo elemento
`const [x, y, ...othersZ, z] = [1, 2, 3, 4, 5]; // Esto esta mal saldrá error`

### Rest en objetos
### Rest busca el nombre sat y los demás se van con weekDays, pero para poder buscar así por nombre se debe hacer con corchetes
`const { sat, ...weekDays } = restaurant.openingHours;`  

_____________________________

## Short Circuiting (&& , || and ??)

### Se puede comparar cualquier tipo de dato y en este caso retornara 3 porque es un valor verdadero, en caso de que sea el valor falso, no declarado, vació, undefined, null o '0' retornara 'Jose'
`const a = 3;`  
`console.log(a || 'Jose'); // Retornara 3`

### Evalúa las variables de izquierda a derecha hasta que encuentre un tipo de dato verdadero o que si exista en este caso Hello, en caso de que todos sean falsos retorna el último elemento falso
`console.log(undefined || 0 || '' || null || false || 'Hello' || 5); // Retornara Hello`


### Incluso es mas corto que el operador ternario
`let noExist;`
`const guest1 = noExist ? noExist : 10; // guest1 = 10`      
`const guest2 = noExist || 10; //  guest2 = 10`

### El operador && trabaja al contrario, retornara el valor que es falso, igual evaluando las variables de izquierda a derecha, si todos los valores son verdaderos devolverá el último
`console.log(true && 0 && 'Jose'); // Devolverá 0` 

### El número 0 en ambos casos es tomado como un dato falso

### Existe otro operador que el el ?? que es el operador nulo en este caso solo evalúa si son null o undefined y toma como valores verdaderos a 0 y ''
`const guestCorrect = 0 ?? 10;`    
`console.log(guestCorrect); // Retornará 0`    