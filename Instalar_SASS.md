# Para instalar SASS en tu proyecto seguir los siguientes pasos

1. Abrir la terminal en la carpeta del proyecto
2. Ingresar: ``npm init`` -> Con esto se nos creara el archivo package.json, en caso de tener ya el archivo packege.json solo ingresar ``npm install``
3. Luego instalar SASS con el comando: ``npm install node-sass --save-dev`` y ``npm install nodemon --save-dev`` -> este último por posibles errores.
4. Luego instalar lo siguiente en la terminal: ``npm install concat --save-dev``, ``npm install autoprefixer --save-dev``, ``npm install postcss-cli --save-dev ``, ``npm install postcss --save-dev``, ``npm install npm-run-all --save-dev``
5. Luego poner lo siguiente en el archivo package.json: ![image_2022-02-23_185804](https://user-images.githubusercontent.com/71052601/155423631-95d8bab3-3b29-4e73-b3ef-df01ea17c278.png)
6. Para hacer correr el SASS con los cambios en vivo del proyecto ejecutar el siguiente comando: ``npm run start`` -> esto nos generara el archivo style.css en la carpeta css
7. Para generar el comprimido más el prefix ejecutar el comando: ``npm run build:css`` -> esto nos generar el comprimido y el prefix en la carpeta css
8. Eso es todo :)
