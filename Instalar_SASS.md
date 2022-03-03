# Para instalar SASS en tu proyecto seguir los siguientes pasos

1. Abrir la terminal en la carpeta del proyecto
2. Ingresar: ``npm init`` -> Con esto se nos creara el archivo package.json (En la consola nos pedirá llenar ciertos campos como el nombre del proyecto, versión, etc...), en caso de tener ya el archivo package.json solo ingresar ``npm install``
3. Luego instalar SASS con el comando: ``npm install node-sass --save-dev`` y ``npm install nodemon --save-dev`` -> este último por posibles errores.
4. Luego instalar lo siguiente en la terminal: ``npm install concat --save-dev``, ``npm install autoprefixer --save-dev``, ``npm install postcss-cli --save-dev ``, ``npm install postcss --save-dev``, ``npm install npm-run-all --save-dev``
5. Luego poner lo siguiente en el archivo package.json: ![image_2022-02-25_155145](https://user-images.githubusercontent.com/71052601/155785729-9e5ea25f-0536-48d5-9e2f-977fda6b2577.png)
[configJSON.txt](https://github.com/Jalgoz/Recursos/files/8144208/configJSON.txt)


7. Para hacer correr el SASS con los cambios en vivo del proyecto ejecutar el siguiente comando: ``npm run start`` -> esto nos generara el archivo style.css en la carpeta css
8. Para generar el comprimido más el prefix ejecutar el comando: ``npm run build:css`` -> esto nos generar el comprimido y el prefix en la carpeta css
9. Eso es todo :)

> P.D.: Si hay errores en ``npm run build:css``, primero fijarse que se instalaron todos los paquetes si aun asi no da eliminar el node_modules y volver a instalar todo
