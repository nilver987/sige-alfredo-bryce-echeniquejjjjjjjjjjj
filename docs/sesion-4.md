# Sesión 4: Ciclos

Hasta ahora cada instrucción se ejecuta una sola vez. Un **ciclo** repite un bloque de código mientras se cumpla una condición. Así no hay que copiar la misma instrucción muchas veces.

## 4.1 ¿Qué son los ciclos?

Imagina que te piden escribir 100 veces "No hablaré en clase". Escribir 100 líneas de código sería muy largo; con un ciclo se escribe una vez y la computadora lo repite.

Todo ciclo tiene tres partes:

- **Inicio:** el valor con el que empieza una variable (por ejemplo, `1`).
- **Condición:** hasta cuándo se repite (por ejemplo, mientras sea menor o igual a 5). Es una comparación como las de los condicionales.
- **Cambio:** cómo avanza la variable en cada vuelta (por ejemplo, sumarle 1).

Sin ciclo, mostrar los números del 1 al 5 sería así:

```javascript
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

Imagina hacerlo hasta el 1000. Para eso se usan los ciclos: `for` y `while`.

## 4.2 Ciclo for

El `for` se usa cuando **sabemos cuántas veces** hay que repetir. Junta las tres partes del ciclo en una sola línea: `for (inicio; condición; cambio)`.

```javascript
for (let i = 1; i <= 5; i = i + 1) {
  console.log("Número:", i);
}
```

Así se lee: empieza con `i = 1`; mientras `i` sea menor o igual a 5, ejecuta el bloque; y en cada vuelta súmale 1 a `i`. Muestra los números del 1 al 5. Cada repetición se llama **iteración**.

Otro ejemplo, la tabla de multiplicar del 5:

```javascript
for (let i = 1; i <= 10; i = i + 1) {
  console.log("5 x", i, "=", 5 * i);
}
```

Muestra `5 x 1 = 5`, `5 x 2 = 10`, y así hasta `5 x 10 = 50`.

## 4.3 Ciclos while

El `while` ("mientras") se usa cuando **no sabemos cuántas veces** hay que repetir: sigue mientras la condición sea verdadera. Aquí el inicio va antes del ciclo y el cambio va dentro del bloque.

```javascript
let contador = 1;

while (contador <= 5) {
  console.log("Número:", contador);
  contador = contador + 1;
}
```

## 4.4 Ciclos infinitos

Un ciclo infinito es el que nunca termina, porque su condición siempre es verdadera. El programa se queda repitiendo y no responde. El error más común es olvidar el cambio dentro del ciclo.

```javascript
let contador = 1;

while (true) {
  console.log("Número:", contador);
  contador = contador + 1;
}
```

La condición `true` siempre es verdadera, así que este ciclo cuenta 1, 2, 3, 4… sin parar, hasta el infinito.

También pasa por error: si en el ciclo `while (contador <= 5)` se olvida la línea `contador = contador + 1`, el contador se queda en 1 y repite "Número: 1" para siempre.

!!! danger "Cuidado al probarlo"
    Este código no se detiene. En la terminal se corta con ++ctrl+c++.

A veces un ciclo infinito se hace a propósito, como en un juego que repite hasta que el jugador acierta. Para salir se usa `break`, el mismo que vimos en el `switch`:

```javascript
let intentos = 0;

while (true) {
  intentos = intentos + 1;
  console.log("Intento", intentos);

  if (intentos === 3) {
    break;   // sale del ciclo
  }
}
```

Muestra `Intento 1`, `Intento 2` e `Intento 3`, y ahí se detiene.
