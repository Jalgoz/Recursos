# REACT ⚛️
React es una biblioteca Javascript de código abierto diseñada para crear interfaces de usuario con el objetivo de facilitar el desarrollo de aplicaciones en una sola página. 

## Crear una aplicación React
`npx create-react-app my-app`  
`npm start`
> Para crear la aplicación y luego crearla

## Componentes
Pequeña pieza de código encapsulada re-utilizable que puede tener estado o no

### Estado
Es como se encuentra la información del componente en un punto determinado del tiempo.

## Recomendaciones 
Si un archivo retorna JS y HTML (JSX) se recomienda que la extensión sea jsx y no js

## Creación de componentes
Para la creación de componentes por buenas practicas se debe utilizar la primera letra mayúscula ej(App.jsx).
Una vez en el archivo se puede usar el atajo de teclados (rafc -> exportaciones normales, rfc -> exportación por defecto).

```
import React from 'react';

export const App = () => {
	return <h1>Hola Mundo</h1>;
};
```
> Se tiene la siguiente estructura. El nombre del componente funcional debe ser el mismo que del archivo. El componente debe retornar solo un elemento.

>Si se quiere crear variables lo recomendado es crearlas a fuera del componente excepto si el valor estará en constante cambio o tenga alguna relación con los hooks.

## Fragment
Los componente funcionales solo pueden retornar un solo elemento por que si deseamos devolver multiples elementos tenemos que agregar un elemento padre, esto puede romper el estilo que estamos llevando o llenarnos de elementos basura. Por eso existe los fragments que nos ayudan a agrupar elementos sin añadir nodos extra al DOM

```
export const FirstApp = () => {
	return (
		<div>
			<h1 className="black">Hola mundo</h1>
			<p>Soy un subtitulo</p>
		</div>
	);
};
```
> Sin fragment: se puede ver que estamos agregando un div extra.

```
export const FirstApp = () => {
	return (
		<>
			<h1 className="black">Hola mundo</h1>
			<p>Soy un subtitulo</p>
		</>
	);
};
```
> Aquí si estamos agregando un fragmentos que agrupe esos dos elementos y al renderizar no añadirá ningún elemento extra al DOM.

## Comunicación entre componentes (props)
```
export const FirstApp = ({ title, number }) => {
	return (
		<>
			<h1>{title}</h1>
			<p>{number}</p>
		</>
	);
};
```
> Para comunicarte entre componentes primero se tiene que declarar parámetros de entrada. Si no fijamos bien los parámetros los obtenemos de una destructuración.

```
export const App = () => {
	return <FirstApp title="Soy titulo" number={1225} />;
};
```
> Desde el componente que deseamos llamarlos debemos mandarle los parámetros. Si es un string se envía entre comillas dobles, si es número entre corchetes

## Tipos de prototipos (propTypes)
```
import React from 'react';
import PropTypes from 'prop-types'; // Importar para usar los PropTypes

export const FirstApp = ({ title }) => {
	return (
		<>
			<h1>{title}</h1>
			<p>Soy un subtitulo</p>
		</>
	);
};

// Se declaran como objetos
FirstApp.propTypes = {
	title: PropTypes.string.isRequired, // Le decimos que el prop que se tiene que enviar tiene que ser string y es required
};
```
> Los propTypes son útiles para las pruebas y controlar que tipo de dato se tiene que enviar. Siempre se declara esto al final del código.

## Prototipos por defecto (Default props)
```
// Se declaran como objetos
FirstApp.defaultProps = {
	title: 'Titulo por defecto',
};
```
> No se necesita importar nada. Si no se envía el prop al llamar el componente entonces tendrá en valor por defecto. Se puede agregar props que no estén declarados en el componente. Siempre se declara esto al final del código.
