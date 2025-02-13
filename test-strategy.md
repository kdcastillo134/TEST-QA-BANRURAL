error: let randomNumber = Math.random() * 10; // Segun las reglas del juego, se requiere que el numero sea del 1 al 100, por lo que hay que cambiar el 10 por un 100 y sumarle 1, para que se generen los numeros en ese rango. Ademas, debemos asegurarnos de que el numero generado sea entero, asi que lo incluimos dentro de un Math.floor para redondear los decimales.
error: const ATTEMPS = 5; // Segun las reglas del juego, el usuario tiene 10 intentos para adivinar el numero
error: const lowOrHi = document.querySelector('lowOrHi'); // Se necesitaba el punto para nombrar a la clase lowOrHi
error: if(userGuess === randomNumber)  // En esta linea se comparaba un dato string con un dato number, por lo que se convirtio userGuess a number cuando se ingresa del campo guessField a la variable: let userGuess = Number(guessField.value);
Ademas, habia un problema con la condicion porque indicaba que si el numero ingresado por el usuario y el numero generado automaticamente coincidian el usuario perdia un intento, lo cual no es correcto. Tambien se cambio el color de los mensajes de ganar a verde y de incorrecto a rojo para no confundir al usuario en el mensaje.:
    if(userGuess === randomNumber) { 
      lastResult.textContent = 'Felicitaciones! adivinaste el número!';
      lastResult.style.backgroundColor = 'green';
      setGameOver();
    } else if(guessCount === ATTEMPS) {
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'black';
      lowOrHi.textContent = '';
      setGameOver();
      ...}
error: guessSubmit.addeventListener('click', checkGuess); // Error de sintaxis en el metodo addEventListener
error: resetButton.addeventListener('click', resetGame); // Error de sintaxis en el metodo addEventListener
error: randomNumber = Math.floor(Math.random()) + 1; // Falta agregar el numero 100 para que el rango vaya del 1 al 100
correccion: El usuario podia ingresar numeros decimales y que salian del rango permitido (1 - 100), por lo que se creo una validacion para que el usuario no pierda intentos con numeros no permitidos:
    if ((!Number.isInteger(userGuess)) || (userGuess < 1 || userGuess > 100)) {
        alert("Por favor, ingresa un número entero entre 1 y 100.");
        guessField.value = '';
        guessField.focus();
        return;
    }

