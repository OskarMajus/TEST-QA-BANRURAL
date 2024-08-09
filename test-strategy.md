# Plan de ataque: Correción de Errores en el Juego "Adivina tú Número"

## Introducción
Este documento describe los errores identificados en el código del juego "Adivina tú Número" y la soluciones para corregirlos, asegurando que el código cumpla con los requisitos especificados en el enunciado del proyecto.

## Errores Identificados y Soluciones

### Error 1: Generación del Número aleatorio fuera del rango
- **Descripción del Error:**
El número aleatorio generado en la versión original del código estaba utilizando un rago incorrecto (`Math.random()*10`)

- **Análisis:**
La expresión (`Math.random()*10`) genera números entre 0 y 9. Para cumplir con el requisito de generar un número entre 1 y 100 la expresión debe ser modificada.

- **Solución:**
**Cambiar la fórmula para generar los números**
```javascript
let randomNumber = Math.floor(Math.random()*100)+1;
```

### Error 2: Falta de validación para Números Enteros:
- **Descripción del Error:**
El código original no validaba si el número ingresado por el jugador era un entero. Esto podría permitir que se ingreseran valores reales y valores mayores a 100 o menores a 1.

- **Solución:**
- **Agregar Validación:"** Implementar una validación que verifique si el número ingresado es un entero entre 1 y 100. Si no lo es, mostrar una alerta y no incrementar el contador de intentos:
```javascript
let userGuess = Number(guessField.value);
 if (!Number.isInteger(userGuess) || userGuess < 1 || userGuess > 100) {
       alert('Por favor, ingresa un número entero entre 1 y 100.');
       guessField.value = '';
       guessField.focus();
       return;
     }
 ```

 ### Error 3: La variable ATTEMPS estaba definida en 5
 -**Descripción del error:**
 La variable ATTEMP estaba asignada con el valor = 5 lo cual solo permitia 5 intententos al jugador y no cumplia con lo descrito en los requisitos que eran 10 intentos para adivinar el número.

 -**Solución:**
 - **Asignar la variable correctamente:** Se asigna a la variable el valor de 10.
 ```javascript
 const ATTEMPS = 10;
 ```

 ### Error 4: Colores Incorrectos en Mensajes
 -**Descripción del Error:**
 Los mensajes "Incorrecto El número es mayor o menor" también el de "Felicitaciones" y "Perdiste" tenian los colores incorrectos según los requisitos. Por ejemplo en incorrecto  estaba el color verde en lugar del negro

 **Solución:**

 **Modificar los Colores:** Cambiar los colores para que cumplan con los requsisitos:
- **Mensaje de error:** 
       ```javascript
       lastResult.style.backgroundColor = 'black';
       ```
     - **Mensaje de victoria:** 
       ```javascript
       lastResult.style.backgroundColor = 'green';
       ```
     - **Mensaje de derrota:**
       ```javascript
       lastResult.style.backgroundColor = 'red';
       ```

### Error 5: Evento click del boton de Ingresar el número estaba mal escrito así como el del limpiar
-**Descripción del Error:**
El evento click del botón estaba mal escrito, por tal motivo al ingresar un número a la caja de texto, este no era leido y no realizaba ninguna función

**Solución:**
- **Reescribir nuevamente la propiedad addeventListener** Se reescribio el evento del botón guessSummit y resetButton addeventListener a addEventListener
```javascript
guessSubmit.addEventListener('click', checkGuess);

resetButton.addEventListener('click', resetGame);
```

### Error 6: Conversión de entrada 'userGuess'
-**Descripción del Error:**
El valor de entrada estaba definido como un string y no había sido convertido a número.

**Solución:**
- **Se convierte a valor numerico la cadena** el valor de entrada  userGuess se convierte a un valor numerico 
```javascript
let userGuess = Number(guessField.value);
```

### Error 7: `TypeError: Cannot set properties of null (Setting 'textContent')`
-**Descripción del Error:**
Este error ocurre cuando el código intenta acceder a una propiedad (`textContent`) de un elemento del DOM  que es `null`. El error se produce cuando se intenta asignar un valor a `lowOrHi.textContent`.

-**Análisis:**
El error indica que el elemento `lowOrHi` no está seleccionado correctamente en el DOM

**Solución:**
 1. **Verificar la Clase:** Asegurarse de que el elemento `<p>` que se intenta seleccionar tenga correctamente la clase `lowOrHi`.
  2. **Corrección en el HTML:** Asegurarse de que el elemento esté definido correctamente en el HTML:
     ```html
     <p class="lowOrHi"></p>
     ```
  3. **Verificación de Selección:** Confirmar que el selector es correcto y no contiene errores tipográficos:
     ```javascript
     const lowOrHi = document.querySelector('.lowOrHi');
     ```


