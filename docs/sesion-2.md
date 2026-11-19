# Sesión 2: Fundamentos de la programación

Entre el ser humano y la máquina hay una parte intermedia: los lenguajes de programación (JavaScript, Python, PHP, Java y muchos más). Todos se basan en unos fundamentos que son los mismos en cualquier lenguaje. Si los aprendes una vez, los puedes usar en el lenguaje que elijas después.

En esta sesión se ven esos fundamentos: sintaxis, variables y constantes, tipos de datos y operadores. Al final se aplican todos en una calculadora de consola.

## 2.1 Sintaxis

La **sintaxis** es la forma en que se "habla" en un lenguaje de programación. Aprender un lenguaje de programación es como aprender inglés, francés o portugués: hay reglas que seguir.

En español entendemos "yo como manzanas" y hasta "manzanas como yo", aunque suene raro. Pero con "@#* manzanas" no se entiende nada. Los lenguajes de programación son muy estrictos: no se puede saltar una regla ni olvidar una coma.

Cada lenguaje tiene su propia sintaxis, pero no hay que confundirse: la **lógica** (la serie de pasos) es la misma en todos. Solo cambia la forma de escribirla.

```javascript
console.log("Hola");   // correcto
console.log("Hola;     // error: falta cerrar la comilla
```

## 2.2 Variables y constantes

Una **variable** es una cajita con una etiqueta donde guardamos un valor que el programa va a usar. Por ejemplo, para registrar a un alumno necesitamos su correo: creamos una cajita con la etiqueta "correo" y dentro ponemos el correo. Como su nombre lo indica, una variable puede variar: si mañana el alumno cambia de correo, cambiamos el valor de la cajita.

Una **constante** también es una cajita con etiqueta, pero su valor no puede cambiar nunca. El ejemplo clásico es pi: siempre vale 3,1416, sin importar qué tan grande sea el círculo. Si intentas cambiarla, el lenguaje muestra un error.

```javascript
let correo = "ana@colegio.pe";         // variable
correo = "ana.lopez@colegio.pe";       // el valor cambió
const PI = 3.1416;                     // constante
```

¿Cuántas cajitas puedo tener? Todas las que quepan en la memoria RAM de la computadora. Por eso una computadora con muchas aplicaciones abiertas se pone lenta: cada programa usa variables y constantes, y cada una necesita un pedacito de RAM.

## 2.3 ¿Qué son los tipos de datos?

Los tipos de datos sirven para categorizar las variables: en una cajita solo se guarda cierto tipo de dato. Piensa en tu closet: un cajón para las medias, otro para las camisas y otro para los zapatos. ¿Podrías guardar zapatos en el cajón de las camisas? Se puede, pero luego al abrirlo habría problemas.

Con los lenguajes pasa igual. Unos son estrictos: "en esta cajita solo caben camisas". Otros son flexibles y permiten cambiar el tipo de dato de una variable mientras el programa corre. Se puede, pero no es recomendable.

## 2.4 ¿Cuáles son los tipos de datos?

Estos son los que más se usan:

- **Entero:** números sin decimales, positivos o negativos (`15`, `-3`).
- **Decimal:** números con decimales, como la estatura de una persona (`1.70`).
- **Texto:** letras, palabras y frases. Hoy hasta se pueden guardar emojis (`"Lucía"`).
- **Booleano:** solo verdadero o falso (`true`, `false`).
- **Fecha:** sirve para comparar fechas, por ejemplo cuántos días pasaron desde el 1 de julio de 2020 hasta hoy.
- **Lista (arreglo):** muchos valores dentro de una sola variable.

La lista evita crear una variable por cada dato. Para guardar la edad de toda la clase no hace falta `edad1`, `edad2`, `edad3`… y así hasta 100: se crea una variable `edades` que guarda todos los valores.

```javascript
let nombre = "Lucía";          // texto
let edad = 15;                 // entero
let estatura = 1.65;           // decimal
let esEstudiante = true;       // booleano
let edades = [15, 16, 14, 15]; // lista
```

## 2.5 Operadores

Con las variables hacemos operaciones, y los símbolos que las indican se llaman **operadores**.

- **Aritméticos:** suma (`+`), resta (`-`), multiplicación (`*`), división (`/`) y módulo (`%`), que es el residuo de una división. Son los que más se usan.
- **De comparación:** comparan dos valores y dan verdadero o falso: igual (`==`), mayor que (`>`), menor que (`<`) y diferente (`!=`). Se usan después en los condicionales.

### Orden de las operaciones

Primero se resuelve lo que esté entre paréntesis. Luego la multiplicación, la división y el módulo, de izquierda a derecha. Al final, la suma y la resta.

!!! question "Pregunta para la clase"
    ¿Cuánto es `5 + 5 * 5 - 5`?

    ??? success "Respuesta"
        Primero 5 × 5 = 25, luego 5 + 25 = 30 y al final 30 − 5 = **25**.

Aunque haya reglas, conviene escribir paréntesis para que el código se lea fácil: el código se escribe para que lo lean otras personas, no solo uno mismo.

```javascript
console.log(5 + 5 * 5 - 5);      // 25
console.log((5 + 5) * 5 - 5);    // 45 (el paréntesis va primero)
console.log(10 % 3);             // 1 (el residuo de 10 ÷ 3)
console.log(10 > 7);             // true
```

## 2.7 Taller: Crea una calculadora

El taller aplica todo lo anterior: una calculadora muy sencilla que se ejecuta en la **consola** (sin página web ni interfaz gráfica) y que suma, resta, multiplica y divide dos números. Usa sintaxis, variables, tipos de datos y operadores aritméticos.

**Herramientas.** Se usa JavaScript, que tiene una sintaxis sencilla y no obliga a declarar el tipo de cada dato. Para escribir el código se usa un editor de código, como Visual Studio Code: pone colores y marca los errores de sintaxis.

```javascript
let primerNumero = 10;
let segundoNumero = 5;

console.log("Primer número:", primerNumero);
console.log("Segundo número:", segundoNumero);

console.log("Suma:", primerNumero + segundoNumero);
console.log("Resta:", primerNumero - segundoNumero);
console.log("Multiplicación:", primerNumero * segundoNumero);
console.log("División:", primerNumero / segundoNumero);
```

Al ejecutarlo en la consola se muestra: suma 15, resta 5, multiplicación 50 y división 2.

Las variables no se ven por sí solas: hay que mostrarlas al usuario con `console.log`. Todavía no se pueden usar condicionales, así que la calculadora muestra las cuatro operaciones en vez de elegir una. Eso se ve en el siguiente módulo, [Condicionales](sesion-3.md).
