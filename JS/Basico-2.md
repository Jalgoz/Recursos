# Manipulación del DOM
### Document Object Model (DOM), es una representación estructurada de los documentos HTML, y permite a JS acceder a estos elementos, estilos y poder manipularlos.
#### Es importante aclarar que muchos piensan que el DOM y todos los métodos y propiedades que nos permiten manipular el DOM son parte de JavaScript, pero esto no es cierto, JS es solo un lenguaje de programación que no contiene el DOM y sus métodos, sino que el DOM con sus métodos y propiedades son en realidad una API WEB, estas son librerías que los navegadores implementan y que podemos acceder desde JS.

### Para seleccionar un elemento del DOM
`document.querySelector('p').textContent;`
>Siempre se debe empezar con document y luego un punto y la propiedad que se desee.    
Si se quiere seleccionar una clase se empieza con -> .clase   
Si se quiere seleccionar una id se empieza con -> #id   
Si se quiere seleccionar una elemento se empieza con -> div, este último caso selecciona solo el primer div que encuentre.
### Métodos para seleccionar un elemento del DOM
`document.querySelector();`   
>Selecciona un solo elemento del DOM  

`document.querySelectorAll();`    
>Devuelve un array con todos los elementos con el nombre de parámetro que se le paso   

`document.getElementById();`    
>Este método selecciona por el ID por lo que no es necesario poner '#' delante del ID que deseamos buscar

`document.getElementsByClassName();`    
>Este método selecciona todos los elementos con el nombre de la clase que le pasemos por lo que no es necesario poner '.' delante de la clase que deseamos buscar. Retorna un array con todos los objetos encontrados aún que sea solo 1. Estos 2 métodos últimos el getElementById y getElementsByClassName son ligeramente más óptimos que querySelector y querySelectorAll 

### Métodos manipular las clases de un elemento seleccionado
`document.querySelector().classList.add('clase');`   
>Añadimos una clase al elemento seleccionado importante recalcar que aquí no se pone un '.' antes de la clase

`document.querySelector().classList.remove('clase');`     
>Removemos una clase al elemento seleccionado importante recalcar que aquí no se pone un '.' antes de la clase 

`document.querySelector().classList.contains('clase');`     
>Preguntamos si el elemento seleccionado contiene esa clase 

`document.querySelector().classList.toggle('clase');`     
>Si tiene esa clase lo quita, y si no lo tiene la añade

#### En ambos casos se puede remover o agregar más de una clase a la vez
`add('clase1', 'clase2');`   
`remove('clase1', 'clase2');`  

### Para cambiar el estilo de un elemento
document.querySelector('.clase').style.width='15px';
>Las propiedades de los estilos son los mismos que en css pero con la diferencia que si no tienen '-' para separar las palabras sino que se utiliza camel case background-color = backgroundColor, una cosa mas para aclarar es que en JS para darle un valor al estilo siempre se pasa un string aun que sea para el ancho

### Métodos para manejar el click en un elemento
`document.querySelector('.clase').addEventListener`       `('evento', () => {`        
  `  console.log(document.querySelector('.guess').value`         
`});`    
> Se puede hacer con un arrow function o con una función normal   

### Para que el método maneje el click también se le puede enviar con una expresión de función o una arrow function con la diferencia que no se pone el paréntesis al final de llamar la función
`const close = () => return console.log('Click')`
`.addEventListener('evento', close )`

### Los eventos pueden ser
>click -> cuando se hace click en el elemento      
>keydown -> detecta cuando presionamos una tecla   
>keypress -> detecta si mantenemos presionando una tecla   
>keyup -> detecta cuando terminamos de presionar una tecla

### Para manejar eventos en el que necesitamos saber que tecla se presiono
`document.addEventListener('keydown', function (e) {`   
  `if (e.key === 'Escape') closeModal();`   
`});`    
>'e' es la tecla que se presiono y e.key es en nombre exacto de esa tecla

### Para insertar HTML desde JS se utiliza el siguiente método

```
const html = '<div>Hola mundo</div>';
document.querySelector('.clase').insertAdjacentHTML('afterbegin', html);
```
Como primer parámetro recibe uno de estos 4: 
* 'beforebegin': Antes que el propio elemento.
* 'afterbegin': Justo dentro del elemento, antes de su primer elemento hijo.
 * 'beforeend': Justo dentro del elemento, después de su último elemento hijo.
* 'afterend': Después del propio elemento.

También esta el método que nos devuelve todo el contenido de un elemento del DOM.

`document.querySelector('.clase').innerHTML = '';`
> Con esta propiedad se puede obtener el contenido de ese elemento e incluso settearlo a vació

