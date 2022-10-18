# Arrays

## Métodos más comunes
```
.push('Valor') -> Agrega un valor nuevo al final del array  
.unshift('Valor') -> Agrega un valor nuevo al principio del array
.pop() -> Elimina el último elemento del array  
.shift() -> Elimina el primer elemento del array  
.indexOf('Valor') -> Retorna la posición del valor que le mandamos si no esta el elemento en el array retorna -1  
.include('Valor') -> Retorna true o false dependiendo si el valor existe en el array
```

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

for (let a of arr.entries()) console.log(`Posición ${a[0] + 1}: ${a[1]}`);
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

## Método Map

```
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

const eurToUsd = 1.1;

const movementsUSD = movements.map(mov => mov * eurToUsd);
console.log(movementsUSD);
```
> Map devuelve un array con las modificaciones que hicimos al array en la función, el método map puede acceder al valor, indice y al array completo en si. El map no muta al array original.

