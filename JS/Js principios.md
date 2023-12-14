# JS Principios

## JS imperativa vs declarativa

- Imperativa: Escribir código que le diga a la computadora exactamente qué hacer paso a paso.
- Declarativa: Escribir código que le diga a la computadora qué hacer, pero no cómo hacerlo.
- Ejemplo imperativo:

```js
const numeros = [1, 2, 3, 4, 5];
const numerosDobles = [];

for (let i = 0; i < numeros.length; i++) {
  numerosDobles.push(numeros[i] * 2);
}

console.log(numerosDobles); // Imprime: [2, 4, 6, 8, 10]
```

- Ejemplo declarativo:

```js
const numeros = [1, 2, 3, 4, 5];
const numerosDobles = numeros.map((numero) => numero * 2);

console.log(numerosDobles); // Imprime: [2, 4, 6, 8, 10]
```

## JS dinámico vs estático
- Dinámico: El tipo de una variable puede cambiar en tiempo de ejecución.
- Estático: El tipo de una variable no puede cambiar en tiempo de ejecución.

## JS programación funcional
- La programación funcional es un paradigma de programación que trata a las funciones como objetos de primera clase. Esto significa que las funciones se pueden asignar a variables, devolver desde otras funciones y pasar como argumentos a otras funciones.
- La programación funcional se basa en los siguientes principios:
  - Inmutabilidad: Los datos no cambian después de ser creados.
  - Funciones puras: Las funciones no tienen efectos secundarios, es decir, no modifican los datos fuera de la función.
  - Composición: Las funciones se pueden combinar para crear otras funciones más complejas.

## JS orientado a objetos
- La programación orientada a objetos es un paradigma de programación que utiliza objetos y sus interacciones para diseñar aplicaciones y programas de computadora.
- La programación orientada a objetos se basa en los siguientes principios:
  - Abstracción: Los objetos se utilizan para modelar entidades del mundo real que tienen propiedades y comportamientos.
  - Encapsulación: Los objetos encapsulan los datos (propiedades) y el código (comportamiento) en un solo bloque.
  - Herencia: Los objetos pueden heredar propiedades y comportamientos de otros objetos.
  - Polimorfismo: Los objetos pueden tomar diferentes formas según el contexto.
