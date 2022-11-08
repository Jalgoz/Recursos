# Arrays

## Métodos más comunes
```
.push('Valor') -> Agrega un valor nuevo al final del array  
.unshift('Valor') -> Agrega un valor nuevo al principio del array
.pop() -> Elimina el último elemento del array  
.shift() -> Elimina el primer elemento del array  
.indexOf('Valor') -> Retorna la posición del valor que le mandamos si no esta el elemento en el array retorna -1  
.includes('Valor') -> Retorna true o false dependiendo si el valor existe en el array
```

## Método Split
```
const splitArr = 'J o s e'.split(' ');
console.log(arr); // (4) ['J', 'o', 's', 'e']
```

> No muta al array original, y devuelve un array dividido por el carácter que deseemos      

## Método Slice
``` 
let arr = ['a', 'b', 'c', 'd', 'e'];

console.log(arr.slice(2)); // ['c', 'd', 'e'];   
console.log(arr.slice(2, 4)); // ['c', 'd'];    
console.log(arr.slice(-2)); // ['d', 'e'];    
console.log(arr.slice(1, -1)); // ['b', 'c', 'd'];    
console.log(arr.slice()); // ['a', 'b', 'c', 'd', 'e'];    
```
> No muta el array, pero si devuelve otro array      

## Método Splice
```
console.log(arr.splice(-1)); // ['e']   
console.log(arr); // ['a', 'b', 'c', 'd']
console.log(arr.splice(1, 2)); // ['b', 'c']
console.log(arr); // ['a', 'd']
```
> Si muta el array, el array mutará cortando la parte que se le extrajo

## Método Reverse
``` 
arr = ['a', 'b', 'c', 'd', 'e'];
const arr2 = ['j', 'i', 'h', 'g', 'f'];
console.log(arr2.reverse()); // ['f', 'g', 'h', 'i', 'j']
console.log(arr2); // ['f', 'g', 'h', 'i', 'j']
```
> Para dar la vuelta el array, si muta el array que llama la función

## Método Concat
```
const letters = arr.concat(arr2);
console.log(letters); // ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
```
> Uné 2 arrays, no muta el array que llama la función

```
console.log([...arr, ...arr2]); // ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
```
> También se puede hacer con el spread operator 

## Método Join
```
console.log(letters.join(' - ')); // a - b - c - d - e - f - g - h - i - j
```
> No devuelve una array, sino un cadena unida por ' - ', no muta el array original

## Método At
```
const arr = [23, 11, 64];
console.log(arr[0]); // 23
console.log(arr.at(0)); // 23

console.log(arr[arr.length - 1]); // 64
console.log(arr.slice(-1)[0]); // 64
console.log(arr.at(-1)); //64
console.log('Jose'.at(-1));
```
> El método at es recomendable usar cuando se busca extraer el último elemento de un array

## Método Entries
```
let arr = ['a', 'b', 'c', 'd', 'e'];

for (let a of arr.entries()) 
  console.log(`Posición ${a[0] + 1}: ${a[1]}`);
// Imprime
Posición 1: a
Posición 2: b
Posición 3: c
Posición 4: d
Posición 5: e
```
> Con el método entries podemos acceder a la posición y al valor de los datos de un array

## Método Foreach
```
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

movements.forEach(function (movement) {
  console.log(movement);
});
```
> El método foreach como se conoce

## Foreach vs Of
```
for (let [i, movement] of movements.entries()) {
  if (movement > 0) {
    console.log(`Movement ${i + 1}: You deposited ${movement}`);
  } else {
    console.log(`Movement ${i + 1}: You withdrew ${Math.abs(movement)}`);
  }
}
```
> Con el of también se puede recorrer la matriz como foreach, pero para llevar un contador se necesita llamar a la función entries() del array para que devuelva el indice y el dato
```
movements.forEach(function (mov, i, arr) {
  if (mov > 0) {
    console.log(`Movement ${i + 1}: You deposited ${mov}`);
  } else {
    console.log(`Movement ${i + 1}: You withdrew ${Math.abs(mov)}`);
  }
});
```
> Con el foreach ya se recibe el dato, indice y todo el array. **Cuando se debe usar foreach o of: En general se debe usar el foreach es mejor, pero en el foreach no se puede usar break si o si recorrerá todo el array, por lo que si se necesita usar break se debe usar el of**

## SET
```
const ordersSet = new Set([
  'Pasta',
  'Pizza',
  'Pizza',
  'Risotto',
  'Pasta',
  'Pizza',
]);
```

`console.log(ordersSet); // Set(3) {'Pasta', 'Pizza', 'Risotto'}`
> En un SET todos los valores repetidos son eliminados

`console.log(ordersSet.size); // 3`
> Para ver la longitud del SET

`console.log(ordersSet.has('Pizza')); // true`
> Para verificar si se tiene un elemento en particular

`ordersSet.add('Garlic Bread');`
> Para añadir un nuevo elemento

`ordersSet.delete('Risotto');`
> Para eliminar un elemento del SET

`ordersSet.clear();`
> Para eliminar todos los elementos del SET

`console.log(ordersSet[0]);`
> No se puede acceder por el indice, por que básicamente los SET no tienen indice

`for (const order of ordersSet) console.log(order);`
> Es posible iterar los SETs

## Para convertir de SET a ARRAY y viceversa
```
const staff = ['Waiter', 'Chef', 'Waiter', 'Manager', 'Chef', 'Waiter'];

// const staffUnique = new Set(staff); // Para convertir un array a SET

const staffUnique = [...new Set(staff)]; // Para eliminar los elementos duplicados pero conservarlos en un array
```

## Cuando usar Set o Array
**Arrays:**   
* Usar cuando necesitamos listas ordenadas
* Cuando necesitamos manipular la data
  
**Sets:**   
* Usar cuando necesitamos trabajar con valores únicos
* Necesitamos eliminar los datos duplicados de un array
   

## Método Map
```
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

const eurToUsd = 1.1;

const movementsUSD = movements.map(mov => mov * eurToUsd);
console.log(movementsUSD);
```
> Map devuelve un array con las modificaciones que hicimos al array en la función, el método map puede acceder al valor, indice y al array completo en si. El map no muta al array original.

## Método Filter
```
const deposits = movements.filter(mov => mov > 0); 
console.log(deposits); // (5) [200, 450, 3000, 70, 1300]
```
> Filter devuelve un array con los datos que pasen el filtro, el truco es que pasan solo los que son true por eso siempre devolver en el arrow function del filter un boolean.

## Método Reduce
```
const balance = movements.reduce((acc, cur, i, arr) => acc + cur, 0);

console.log(balance); // 3840
```
> El método reduce nos ayuda acumular en las iteraciones, al final devolverá solo el acumulado, los parámetros que recibe son acc = el acumulado, cur = el dato actual de la iteración, i = el indice, arr = el array en si. También se le puede especificar en que posición queremos que empiece el acumulado en este caso empezará en 0.

## Método Find
```
const firstWithdrawal = movements.find(mov => mov < 0);

console.log(firstWithdrawal); // -400
```

> Busca en todo el array, y devuelve la primera ocurrencia si se busca que devuelve más de una usar mejor el filter.

## Método findIndex
```
const index = movements.findIndex(
      mov => mov === -400);
console.log(index); // 2
```
> Devuelve la posición en la que se encuentra el dato a buscar.

## Método Some 
```
console.log(movements); // (8) [200, 450, -400, 3000, -650, -130, 70, 1300]
console.log(movements.some(mov => mov > 1500)); // True
console.log(movements.some(mov => mov > 5000)); // False
```
> Devuelve true si un elemento del arreglo cumple la condición. Solo es necesario que uno lo cumpla y devolverá true en caso de que ninguno cumpla retornará false.

## Método Every 
```
console.log(movements.every(mov => mov > 0)); // False
const movements2 = [430, 1000, 700, 50, 90];
console.log(movements2.every(mov => mov > 0)); // True
```
> Every retorna true si todos los elementos cumplen con la condición en caso contrario devolverá false.

## Método Flat
```
const arr = [[1, 2, 3], [4, 5, 6], 7, 8];
console.log(arr); // (4) [Array(3), Array(3), 7, 8]
console.log(arr.flat()); // 8) [1, 2, 3, 4, 5, 6, 7, 8]

const arrDeep = [[[1, 2], 3], [4, [5, 6]], 7, 8];
console.log(arrDeep.flat()); // (6) [Array(2), 3, 4, Array(2), 7, 8]
console.log(arrDeep.flat(2)); // (8) [1, 2, 3, 4, 5, 6, 7, 8]
```
> EL método Flat desanida array's anidados volviéndola un array de un solo nivel. Si se tiene varios niveles de anidación de array se le tiene que pasar como parámetro hasta que nivel se quiere desanidar.

## Método Flat
```
const arr = [[1, 2, 3], [4, 5, 6], 7, 8];
console.log(arr); // (4) [Array(3), Array(3), 7, 8]
console.log(arr.flat()); // 8) [1, 2, 3, 4, 5, 6, 7, 8]

const arrDeep = [[[1, 2], 3], [4, [5, 6]], 7, 8];
console.log(arrDeep.flat()); // (6) [Array(2), 3, 4, Array(2), 7, 8]
console.log(arrDeep.flat(2)); // (8) [1, 2, 3, 4, 5, 6, 7, 8]
```
> EL método Flat desanida array's anidados volviéndola un array de un solo nivel. Si se tiene varios niveles de anidación de array se le tiene que pasar como parámetro hasta que nivel se quiere desanidar.

## Método FlatMap
```
const balance = accounts.flatMap(acc => acc.movements);
console.log(balance);
```
> Flatmap te permite iterar sobre un objeto ya creado, luego tal como flat desanidará los array's. Con flatmap solo se puede desanidar un nivel.

## Método Sort
```
// Strings
console.log(owners); // ['Jonas Schmedtmann', 'Jessica Davis', 'Steven Thomas Williams', 'Sarah Smith']

console.log(owners.sort()); // ['Jessica Davis', 'Jonas Schmedtmann', 'Sarah Smith', 'Steven Thomas Williams']
```
> El método sort muta el array original
```
// Numbers
console.log(movements); // [200, 450, -400, 3000, -650, -130, 70, 1300]

// return > 0 = B , A (Switch order)
// return < 0 = A , B (Keep order)

const sortNumberAsc = (a, b) => a - b;
const sortNumberDes = (a, b) => b - a;

console.log(movements.sort(sortNumberAsc)); //[-650, -400, -130, 70, 200, 450, 1300, 3000]
console.log(movements.sort(sortNumberDes)); // [3000, 1300, 450, 200, 70, -130, -400, -650]
```
>Para ordenar números se debe mandar una callback function al sort ya que sino lo ordenara como si fuera una cadena de strings. La lógica es que si se retorna un número mayor a 0 entonces se cambiará de posición de (A, B) a (B, A) y si es menor a 0 no mantendrá la posición.

## Método Fill
```
const x = new Array(7);
console.log(x); // (7) [vacío × 7]

x.fill(1, 3, 6); 
console.log(x); // (7) [vacío × 3, 1, 1, 1, vacío]
```
> Con el método fill podemos llenar una matriz vacía, ya que no se podrá hacerlo con map. El primer parámetro que recibe es el dato con el que se desea rellenar el array, el segundo es desde que indice se quiere empezar y el último es hasta donde se quiere llenar, si se quiere llenar todo el array solo mandar `x.fill(1)`. Se pueden llenar también arrays con datos ya existentes.

## Array.From
```
const y = Array.from({ length: 7 }, () => 1);
console.log(y); // (7) [1, 1, 1, 1, 1, 1, 1]

const z = Array.from({ length: 7 }, (_, i) => i + 1);
console.log(z); // (7) [1, 2, 3, 4, 5, 6, 7]
```
> Nos ayuda a crear arrays programaticamente pudiendo controlar que datos queremos que sean los que contenga el array.

## Pasar arrow functions
```
const deposit = mov => mov > 0;
console.log(movements.some(deposit)); // True
console.log(movements.every(deposit)); // False
console.log(movements.filter(deposit)); // (5) [200, 450, 3000, 70, 1300]
```
> A estos métodos se les puede pasar una variable que contenga un función, es más optimo y más funcional