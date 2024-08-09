# Plan de ataque: Correción de Errores en el Juego "Adivina tú Número"

## Introducción
Este documento describe los errores identificados en el código del juego "Adivina tú Número" y la soluciones para corregirlos, asegurando que el código cumpla con los requisitos especificados en el enunciado del proyecto.

## Errores Identificados y Soluciones

### Error 1: Generación del Número aleatorio fuera del rango
- **Descripción del Error:**
El número aleatorio generado en la versión original del código estaba utilizando un rago incorrecto (`Math.random()*10`)

- **Análisis:**
La expresión (`Math.random()*10`) genera números entre 0 y 9. Para cumplir con el requisito de generar un número entre 1 y 100 la expresión debe ser modificada.

- **Solución**
**Cambiar la fórmula para generar los números**
```javascript
let randomNumber = Math.floor(Math.random()*100)+1;
```
