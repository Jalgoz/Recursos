# MAP
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
> Para eliminar un elemento del MAP, buscara por la llave

`console.log(rest.has('categories'));`
> Para verificar si existe la clave en el MAP

`console.log(rest.size);`
> Para obtener el tamaño del MAP

`console.log([...rest]);`
> Para convertir un map a array

`const newMap = new Map(Object.entries(object));`
> Para convertir un objet a map

```
console.log(rest.entries());
console.log(rest.keys());
console.log(rest.values());
```
> También se puede obtener las llaves y valores del mapa

### El foreach también sirve para recorrer MAP y SET
```
const currencies = new Map([
  ['USD', 'United States dollar'],
  ['EUR', 'Euro'],
  ['GBP', 'Pound sterling'],
]);

currencies.forEach(function (value, key, map) {
  console.log(`${key}: ${value}`);
});
```
> Como se pude ver el primer valor que recibe la función foreach es el valor, luego viene la llave y por último el mapa en sí.

## Cuando usar Object o Map
**Objects:**   
* Usar cuando necesitamos incluir funciones
* Cuando trabajamos con JSON (Se puede convertir a map)
  
**Maps:**   
* Usar cuando necesitamos que las llaves no sean solo strings
* Cuando solo necesitamos llave / valor