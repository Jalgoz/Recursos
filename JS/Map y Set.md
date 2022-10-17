# MAP y SET
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

## MAP

`const rest = new Map();`  
> Los MAPs son como array pero tienen un llave y un valor

`rest.set('name', 'Classico Italiano');`
> Así agrega un nuevo elemento al MAP el primer parámetro es la llave y el segundo el valor
```
rest.set(1, 'Firenze, Italy');
rest.set(2, 'Lisbon, Portugal');
rest
  .set('categories', ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'])
  .set('open', 11)
  .set('close', 23)
  .set(true, 'We are open :D')
  .set(false, 'We are closed :(');
  ```
> Se puede agregar como llave o como valor varios tipos de datos incluyendo arrays o otros mapas

`console.log(rest.get(true));`
> get se utiliza para traer un elemento del MAP. Debe ser una clave existente sino el resultado será undefined

`console.log(rest.has('categories'));`
> Para verificar si existe la clave en el MAP

`console.log(rest.size);`
> Para obtener el tamaño del MAP

`rest.delete(1);`
> Para eliminar un elemento del MAP