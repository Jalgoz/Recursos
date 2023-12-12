# HOW JS WORKS
## JS Simple Thread
JavaScript es un lenguaje de programación asíncrono, no bloqueante y concurrente. Esto significa que JavaScript puede ejecutar varias tareas al mismo tiempo sin bloquear el hilo principal.

## JS Engine
El motor de JavaScript es un programa que interpreta y ejecuta código JavaScript. Los navegadores web tienen sus propios motores de JavaScript, pero también existen otros motores de JavaScript como Node.js.

El motor de JavaScript consta de dos partes principales:

- Memory Heap: es donde se almacenan las variables y el alcance.
- Call Stack: es donde se almacenan las funciones y las llamadas a esas funciones.

## Memory Heap
El Memory Heap es donde se almacenan las variables y el alcance. Cuando se declara una variable, se almacena en el Memory Heap. Cuando se crea una función, se almacena en el Memory Heap. Cuando se crea un objeto, se almacena en el Memory Heap.

## Call Stack
El Call Stack es donde se almacenan las funciones y las llamadas a esas funciones. Cuando se llama a una función, se agrega al Call Stack. Cuando se devuelve un valor de una función, se elimina del Call Stack.

## Event Loop
El Event Loop es un bucle que se ejecuta continuamente y comprueba si hay tareas que se deben ejecutar. Si hay tareas que se deben ejecutar, las agrega al Call Stack.

## JS Runtime
El tiempo de ejecución de JavaScript es el entorno en el que se ejecuta el código JavaScript. Por ejemplo, el tiempo de ejecución de JavaScript de un navegador web es el entorno en el que se ejecuta el código JavaScript de una página web.

El tiempo de ejecución de JavaScript consta de dos partes principales:

- Web APIs: son las APIs que proporciona el navegador web. Por ejemplo, el DOM API, el XMLHttpRequest API y el Fetch API.
- JS Engine: es el motor de JavaScript que interpreta y ejecuta el código JavaScript.

## Donde se ejecuta el código Asíncrono
El código asíncrono se ejecuta en el Event Loop. Cuando se llama a una función asíncrona, se agrega al Call Stack. Cuando la función se completa, se elimina del Call Stack. Cuando se completa la función, se agrega al Event Loop. Cuando el Event Loop detecta que la función está completa, la agrega al Call Stack.

### Microtask Queue
El Microtask Queue es donde se almacenan las tareas asíncronas (Promises). Cuando se completa una tarea asíncrona, se agrega al Microtask Queue. Cuando el Call Stack está vacío, se agrega la tarea asíncrona al Call Stack.

### Callback Queue
El Callback Queue es donde se almacenan las tareas asíncronas (Callbacks). Cuando se completa una tarea asíncrona, se agrega al Callback Queue. Cuando el Call Stack está vacío, se agrega la tarea asíncrona al Call Stack.

### Diferencia entre Microtask Queue y Callback Queue
La diferencia entre el Microtask Queue y el Callback Queue es que el Microtask Queue tiene prioridad sobre el Callback Queue. Esto significa que cuando el Call Stack está vacío, se agrega una tarea asíncrona del Microtask Queue al Call Stack antes que una tarea asíncrona del Callback Queue.

- Microtask Queue: Promises
- Callback Queue: Callbacks

### Ejemplo
```js
console.log('Primero'); // 1

setTimeout(() => {
  console.log('Segundo') // 4
}, 0);

Promise.resolve().then(() => console.log('Tercero')); // 3

console.log('Cuarto'); // 2
```
El orden de ejecución de este código es el siguiente:

1. Primero
2. Cuarto
3. Tercero
4. Segundo

En este ejemplo, "Primero" y "Cuarto" serán agregados al Call Stack y se imprimirán en la consola. Luego, "Segundo" será agregado al Callback Queue y "Tercero" será agregado al Microtask Queue. Cuando el Call Stack esté vacío, "Tercero" será agregado al Call Stack y se imprimirá en la consola. Luego, "Segundo" será agregado al Call Stack y se imprimirá en la consola.