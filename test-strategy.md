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