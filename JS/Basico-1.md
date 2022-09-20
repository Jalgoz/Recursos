# JAVASCRIPT

JavaScript es una lenguaje de alto nivel, orientado a objetos y multiparadigma.

|                | var | let | const |
| -------------- | --- | --- | ----- |
| Global Scope   | Si  | No  | No    |
| Function Scope | Si  | Si  | Si    |
| Block Scope    | Si  | Si  | No    |

## Convertir datos
`De string a number -> Number()`  
`De number a string -> String()`

### valores que pueden ser convertidos a falso
`0, undefined, '', null, NaN -> Boolean()`

### valores que pueden ser convertidos a verdadero
`cualquier numero que no sea 0, 'texto', variables definidas -> Boolean()`

## Operadores ternarios
`const esMayor = 23 >= 18 ? true : false;`

## Funciones 
`// Declaración de función -> Pueden ser llamadas antes de ser declaradas.`  
`function calcAge1(birthYear) {
    return 2037 - birthYear;
}`

`// Expresión de función -> No pueden ser llamadas antes de ser declaradas.`  
`const calcAge2 = function (birthYear) {
    return 2037 - birthYear;
}`

`// Arrow Function`  
`const calcAge3 = birthYear => 2037 - birthYear;`

## Array Method's
`.push('Valor') -> Agrega un valor nuevo al final del array`  
`.unshift('Valor') -> Agrega un valor nuevo al principio del array`
`.pop() -> Elimina el último elemento del array`  
`.shift() -> Elimina el primer elemento del array`  
`.indexOf('Valor') -> Retorna la posición del valor que le mandamos si no esta el elemento en el array retorna -1`  
`.include('Valor') -> Retorna true o false dependiendo si el valor existe en el array`
