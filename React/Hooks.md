# Hooks
Estos nos permiten usar el estado y otras características de React sin escribir una clase.

## UseState
```
import React, { useState } from 'react';

export const CounterApp = ({ value }) => {
	const [counter, setCounter] = useState(value); // Valor inicial

	const handleAdd = () => {
		setCounter(counter + 1);
		// setCounter(c => c + 1);
	};

	return (
		<>
			<h1>CounterApp</h1>
			<h2> {counter} </h2>

			<button onClick={handleAdd}>+1</button>
		</>
	);
};
```
> El useState retorna una pareja de valores: el estado actual y una función que lo actualiza, es como un get y set. El useState recibe un parámetro que es el valor inicial que tomará la variable (estado). El useState se utiliza para decirle a React que cuando detecte el cambio en esa variable se vuelva a cargar mostrando el nuevo valor o estado. En otras palabras de debe usar este Hook cuando queremos decirle a React que el componente tiene que tener un estado. También queda aclarar que el useState guarda el estado aún cuando ya se salio de la función hasta que se recargue la página.
>

## UseEffect
```
  useEffect(() => {
    getGifs(category);
  }, []);
```
> Hace que solo se ejecute una vez el callback, y no puede ser un async daria error.