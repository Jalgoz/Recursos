# Exportaciones e Importaciones
En react todo el rato estas exportado componentes y importándolos en otro lado para renderizarlos por eso es muy importante saber como hacer esto.

### Primera manera (normal)
```
export function App() {
	return <h1>Hola Mundo</h1>;
}
```
> Cuando exportas de esta manera se debe importar de la siguiente manera.
```
import { App } from "./NombreArchivo";
```
> Como se puede ver se importa con el nombre de la función, entre corchetes y especificando la ruta
### Segunda manera (por defecto)
```
function App() {
	return <h1>Hola Mundo</h1>;
}

export default App;
```
> Cuando exportas de esta manera se debe importar de la siguiente manera
```
import App from "./NombreArchivo";
```
> Como se puede ver se importa con el nombre de la función, sin corchetes y especificando la ruta
### Tercera manera (exportación multiple)
```
function App() {
	return <h1>Hola Mundo</h1>;
}

function App2() {
	return <h1>Hola Mundo 2</h1>;
}

export {
	App,
	App2
}
```
> Cuando exportas de esta manera se debe importar de la siguiente manera.
```
import {App, App2} from "./NombreArchivo";
```
> Como se puede ver se importa con el nombre de las funciones, con corchete separados por coma y especificando la ruta

### Tercera manera (exportación multiple con default)
```
function App() {
	return <h1>Hola Mundo</h1>;
}

function App2() {
	return <h1>Hola Mundo 2</h1>;
}

export {
	App as default,
	App2
}
```
> Cuando exportas de esta manera se debe importar de la siguiente manera.
```
import App, { App2 } from "./NombreArchivo";
```
> Como se puede ver se importa con el nombre de las funciones, el por default sin corchetes separado de una coma de los otros que estarán en corchetes.