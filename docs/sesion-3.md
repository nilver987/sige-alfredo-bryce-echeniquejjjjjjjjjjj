# Sesión 3: Condicionales

Hasta ahora el programa ejecuta todas las instrucciones en orden, sin elegir nada. Los condicionales le permiten tomar decisiones: "si pasa esto, haz aquello; si no, haz otra cosa". Es lo mismo que hacemos todos los días: si llueve, llevo paraguas; si no llueve, no.

Con los condicionales la calculadora del taller anterior podrá hacer solo la operación que el usuario elija, en lugar de mostrar las cuatro.

## 3.2 Condicionales

Un condicional revisa una **condición**, que es una comparación con resultado verdadero o falso (los operadores de comparación de la sesión anterior: `>`, `<`, `===`, `!==`). Según el resultado, el programa ejecuta un bloque de código u otro.

!!! note
    En JavaScript, `===` es el "igual" que se recomienda usar.

## 3.3 Condicional simple

Es el más básico: si la condición es verdadera, se ejecuta el bloque; si es falsa, no pasa nada. Se escribe con `if` ("si").

```javascript
let edad = 18;

if (edad >= 18) {
  console.log("Eres mayor de edad");
}
```

## 3.4 Condicional doble

Agrega qué hacer cuando la condición es falsa, con `else` ("si no"). Siempre se ejecuta uno de los dos bloques.

```javascript
let edad = 15;

if (edad >= 18) {
  console.log("Eres mayor de edad");
} else {
  console.log("Eres menor de edad");
}
```

## 3.5 Condicional anidada

Es un condicional dentro de otro, para decidir en varios niveles. También se puede encadenar con `else if` ("si no, y si…").

```javascript
let nota = 14;

if (nota >= 18) {
  console.log("Excelente");
} else if (nota >= 11) {
  console.log("Aprobado");
} else {
  console.log("Desaprobado");
}
```

!!! warning "El orden importa"
    El programa revisa las condiciones de arriba hacia abajo y se detiene en la primera que sea verdadera.

## 3.6 Validar enteros y tipos de datos

En la lógica de mayor o menor de edad, la variable `edad` debe ser un número entero (15, 18, 20). Si llega un valor como `15.3`, el programa igual diría "menor de edad". Para que solo acepte enteros se valida con `Number.isInteger()`, que da verdadero solo si el valor es un entero.

```javascript
let edad = 15.3;

if (Number.isInteger(edad)) {
  if (edad >= 18) {
    console.log("Eres mayor de edad");
  } else {
    console.log("Eres menor de edad");
  }
} else {
  console.log("La edad debe ser un número entero");
}
```

Con `15.3` muestra "La edad debe ser un número entero". Con `15` muestra "Eres menor de edad" y con `20`, "Eres mayor de edad". Es un condicional anidado (3.5): el `if` de afuera revisa que sea entero y el de adentro decide si es mayor o menor de edad.

## 3.8 Condicional switch

Cuando hay muchas opciones para una misma variable, encadenar `else if` se vuelve largo. El `switch` ("según") revisa el valor de una variable y ejecuta el caso que coincida. Cada caso termina con `break`, y `default` es lo que pasa si ningún caso coincide.

Con esto la calculadora ya puede hacer solo la operación elegida, que era lo que faltaba en el taller:

```javascript
let primerNumero = 10;    // ingrese el primer número
let segundoNumero = 5;    // ingrese el segundo número
let operacion = "+";      // ingrese la operación: "+", "-", "*" o "/"

switch (operacion) {
  case "+":
    console.log("Suma:", primerNumero + segundoNumero);
    break;
  case "-":
    console.log("Resta:", primerNumero - segundoNumero);
    break;
  case "*":
    console.log("Multiplicación:", primerNumero * segundoNumero);
    break;
  case "/":
    if (segundoNumero === 0) {
      console.log("No se puede dividir entre cero");
    } else {
      console.log("División:", primerNumero / segundoNumero);
    }
    break;
  default:
    console.log("Operación no válida");
}
```

Con los valores de arriba la consola muestra `Suma: 15`. Dentro del caso de la división hay un condicional anidado (3.5) que evita dividir entre cero.
