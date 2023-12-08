## Async
El operador `async` se utiliza para indicar que una función es asíncrona, lo que significa que devuelve una promesa. Cuando se llama a una función asíncrona, se puede utilizar `await` para esperar a que la promesa se resuelva.
```
async function miFuncion() {
  return "Hola Mundo";
}

miFuncion().then((valor) => {
  console.log(valor); // Imprime: Hola Mundo
});
```

En este caso, `miFuncion` es una función asíncrona que devuelve una promesa que se resuelve con el valor `"Hola Mundo"`. Utilizamos `.then` para manejar el valor cuando la promesa se resuelve.

Ahora, veamos cómo se utiliza await:

```
async function miFuncion() {
  let promesa = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Hola Mundo"), 1000);
  });

  let resultado = await promesa; // Espera hasta que la promesa se resuelva

  console.log(resultado); // Imprime: Hola Mundo
}

miFuncion();
```

En este ejemplo, creamos una promesa que se resuelve después de 1 segundo. Luego, utilizamos `await` para esperar a que la promesa se resuelva antes de continuar. Esto significa que resultado obtiene el valor de la promesa una vez que se resuelve.

Es importante notar que `await` sólo puede ser utilizado dentro de una función async.

async es non-blocking, es decir, no bloquea la ejecución del código. Por ejemplo, si tenemos una función asíncrona que tarda 1 segundo en ejecutarse, el resto del código no se detendrá durante ese tiempo. En cambio, el código continuará ejecutándose mientras la función se está ejecutando en segundo plano.

Detrás de escenas async funciona con promesas, por lo que es importante entenderlas bien para poder utilizar async correctamente.

## Promises
Una promesa es un objeto que representa la terminación o el fracaso de una operación asíncrona. Una promesa puede estar en uno de los siguientes estados:

- pending: estado inicial, no cumplida o rechazada.
- fulfilled: significa que la operación se completó satisfactoriamente.
- rejected: significa que la operación falló.
- settled: la promesa se cumplió o rechazó, pero no está pendiente.
- resolved: se ha resuelto: se ha cumplido o rechazado.
- unresolved: no se ha resuelto: pendiente.

Una promesa se crea con el constructor `Promise`. Para crear una promesa, se debe pasar una función callback con dos parámetros: `resolve` y `reject`. Estos son métodos que se utilizan para determinar el resultado de la promesa.

```js
const promesa = new Promise((resolve, reject) => {
  // Hacer algo que tome tiempo, por ejemplo:
  setTimeout(() => {
    // Si todo sale bien, llamamos a resolve y pasamos el resultado
    resolve("¡Éxito!");
  }, 1000);

  // Si algo sale mal, llamamos a reject y pasamos el error
  reject("¡Algo salió mal!");
});
```

En este ejemplo, creamos una promesa que se resuelve después de 1 segundo. Si todo sale bien, llamamos a `resolve` y pasamos el resultado. Si algo sale mal, llamamos a `reject` y pasamos el error.

Para manejar el resultado de la promesa, utilizamos los métodos `.then` y `.catch`:

```js
promesa
  .then((resultado) => {
    console.log(resultado); // Imprime: ¡Éxito!
  })
  .catch((error) => {
    console.log(error); // Imprime: ¡Algo salió mal!
  });
```

## AJAX
AJAX es una técnica de programación que permite actualizar una página web sin necesidad de recargarla. Esto se logra utilizando JavaScript para enviar y recibir datos de un servidor web.

AJAX significa Asynchronous JavaScript And XML. Aunque el nombre incluye XML, en realidad no es necesario utilizar XML para utilizar AJAX. En su lugar, se puede utilizar JSON, que es más fácil de utilizar con JavaScript.

Para enviar una solicitud AJAX, se utiliza el objeto XMLHttpRequest. Este objeto permite enviar y recibir datos de un servidor web.

Para enviar una solicitud, se utiliza el método `open` para especificar el tipo de solicitud y la URL. Luego, se utiliza el método `send` para enviar la solicitud.

```js
const request = new XMLHttpRequest();
request.open("GET", "https://jsonplaceholder.typicode.com/users");
request.send();
```

En este ejemplo, creamos una solicitud GET para obtener los usuarios de la API JSONPlaceholder. Luego, enviamos la solicitud.
