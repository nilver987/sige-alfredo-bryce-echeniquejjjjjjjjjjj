# Proyecto final: calculadora web

Una calculadora con teclado en la página web, hecha con tres archivos: **HTML** (la estructura), **CSS** (el diseño) y **JavaScript** (la lógica). Todo el JavaScript usa lo visto en las sesiones: variables, tipos de datos, operadores, condicionales y `switch`.

Guarda los tres archivos en la misma carpeta, con estos nombres exactos, y abre `calculadora.html` en el navegador.

=== "calculadora.html"

    ```html
    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Calculadora básica</title>
        <link rel="stylesheet" href="calculadora.css">
    </head>
    <body>
        <main class="calculadora">
            <h1>Calculadora</h1>
            <input id="pantalla" class="pantalla" type="text" value="0" readonly>
            <div class="teclado">
                <button class="tecla tecla-funcion" data-accion="limpiar">C</button>
                <button class="tecla tecla-funcion" data-accion="borrar">DEL</button>
                <button class="tecla tecla-funcion" data-accion="porcentaje">%</button>
                <button class="tecla tecla-operacion" data-operacion="/">÷</button>

                <button class="tecla" data-numero="7">7</button>
                <button class="tecla" data-numero="8">8</button>
                <button class="tecla" data-numero="9">9</button>
                <button class="tecla tecla-operacion" data-operacion="*">×</button>

                <button class="tecla" data-numero="4">4</button>
                <button class="tecla" data-numero="5">5</button>
                <button class="tecla" data-numero="6">6</button>
                <button class="tecla tecla-operacion" data-operacion="-">−</button>

                <button class="tecla" data-numero="1">1</button>
                <button class="tecla" data-numero="2">2</button>
                <button class="tecla" data-numero="3">3</button>
                <button class="tecla tecla-operacion" data-operacion="+">+</button>

                <button class="tecla tecla-cero" data-numero="0">0</button>
                <button class="tecla" data-accion="decimal">.</button>
                <button class="tecla tecla-igual" data-accion="igual">=</button>
            </div>
        </main>
        <script src="calculadora-web.js"></script>
    </body>
    </html>
    ```

=== "calculadora.css"

    ```css
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #1e2330;
      font-family: Arial, Helvetica, sans-serif;
    }

    .calculadora {
      width: 320px;
      padding: 20px;
      background: #2b3245;
      border-radius: 16px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
    }

    h1 {
      margin: 0 0 12px;
      font-size: 20px;
      text-align: center;
      color: #e8ecf5;
    }

    .pantalla {
      width: 100%;
      height: 64px;
      margin-bottom: 16px;
      padding: 0 14px;
      font-size: 32px;
      text-align: right;
      color: #ffffff;
      background: #141824;
      border: none;
      border-radius: 10px;
    }

    .teclado {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    .tecla {
      height: 56px;
      font-size: 20px;
      color: #ffffff;
      background: #3b4460;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }

    .tecla:hover {
      filter: brightness(1.15);
    }

    .tecla:active {
      transform: scale(0.96);
    }

    .tecla:focus-visible {
      outline: 3px solid #ffffff;
      outline-offset: 2px;
    }

    .tecla-funcion {
      background: #5a6482;
    }

    .tecla-operacion {
      color: #1e2330;
      background: #f0a030;
    }

    .tecla-cero {
      grid-column: span 2;
    }

    .tecla-igual {
      background: #3cb371;
    }
    ```

=== "calculadora-web.js"

    ```javascript
    // ===== CONEXIÓN CON LA PÁGINA (se explica aparte) =====
    const pantalla = document.getElementById("pantalla");
    const teclado = document.querySelector(".teclado");

    // ===== VARIABLES (las "cajitas") =====
    let textoPantalla = "0";   // lo que se ve en pantalla
    let primerNumero = 0;      // el primer número de la operación
    let operacion = "";        // "+", "−", "×", "÷" o "" si no hay ninguna pendiente
    let empezarNuevo = false;  // true = el siguiente número que se escriba reemplaza lo que hay en pantalla
    let tienePunto = false;    // true = el número que se está escribiendo ya tiene punto decimal

    // Todo lo de adentro se ejecuta cada vez que se hace clic en el teclado
    teclado.addEventListener("click", function (evento) {
      const boton = evento.target;      // la tecla presionada
      const tecla = boton.textContent;  // lo que dice la tecla: "7", "+", "C", ...

      // Se ignora el clic si fue en el espacio entre teclas
      if (boton !== teclado) {

        // Si en pantalla había un error, se empieza de cero
        if (textoPantalla === "Error") {
          textoPantalla = "0";
        }

        switch (tecla) {

          // ----- Tecla C: borra todo -----
          case "C":
            textoPantalla = "0";
            primerNumero = 0;
            operacion = "";
            empezarNuevo = false;
            tienePunto = false;
            break;

          // ----- Tecla DEL: borra el número que se está escribiendo -----
          case "DEL":
            if (empezarNuevo === false) {
              textoPantalla = "0";
              tienePunto = false;
            }
            break;

          // ----- Tecla %: divide el número entre 100 -----
          case "%":
            textoPantalla = textoPantalla / 100;
            // El módulo (%) 1 da el residuo: si no es 0, el número tiene decimales
            if (textoPantalla % 1 === 0) {
              tienePunto = false;
            } else {
              tienePunto = true;
            }
            textoPantalla = "" + textoPantalla;   // "" + número lo vuelve texto
            break;

          // ----- Tecla punto decimal -----
          case ".":
            if (empezarNuevo === true) {
              textoPantalla = "0.";
              tienePunto = true;
              empezarNuevo = false;
            } else if (tienePunto === false) {
              textoPantalla = textoPantalla + ".";
              tienePunto = true;
            }
            break;

          // ----- Teclas de operación (+ − × ÷) y tecla igual (=) -----
          // Varios case seguidos comparten el mismo código
          case "+":
          case "−":
          case "×":
          case "÷":
          case "=":

            // Si hay una operación pendiente y ya se escribió el segundo número, se calcula
            if (operacion !== "" && empezarNuevo === false) {
              const segundoNumero = textoPantalla * 1;   // texto * 1 lo vuelve número
              let resultado = 0;

              switch (operacion) {
                case "+":
                  resultado = primerNumero + segundoNumero;
                  break;
                case "−":
                  resultado = primerNumero - segundoNumero;
                  break;
                case "×":
                  resultado = primerNumero * segundoNumero;
                  break;
                case "÷":
                  if (segundoNumero === 0) {
                    resultado = "Error";
                  } else {
                    resultado = primerNumero / segundoNumero;
                  }
                  break;
              }

              textoPantalla = "" + resultado;
            }

            // Lo que hay en pantalla pasa a ser el primer número
            primerNumero = textoPantalla * 1;
            if (textoPantalla === "Error") {
              primerNumero = 0;
            }

            // Se guarda la operación elegida (si fue "=", no queda ninguna pendiente)
            if (tecla === "=") {
              operacion = "";
            } else {
              operacion = tecla;
            }

            empezarNuevo = true;
            tienePunto = false;
            break;

          // ----- Cualquier otra tecla es un número (0 al 9) -----
          default:
            if (empezarNuevo === true) {
              textoPantalla = tecla;
              empezarNuevo = false;
              tienePunto = false;
            } else if (textoPantalla === "0") {
              textoPantalla = tecla;
              tienePunto = false;
            } else {
              textoPantalla = textoPantalla + tecla;
            }
            break;
        }

        // Se muestra en la pantalla de la calculadora
        pantalla.value = textoPantalla;
      }
    });
    ```

La lógica usa solo lo visto en clase: variables y constantes, tipos de datos, operadores (incluido el módulo), `if`, `else if`, condicionales anidados y `switch`. Lo único que no es de las sesiones son las líneas de "conexión con la página": `getElementById`, `querySelector`, `addEventListener` con su `function`, y `.textContent` y `.value`. Se presentan como "la oreja que escucha los clics".

## Detalles para explicar en clase

- **`case` seguidos:** `+`, `−`, `×`, `÷` y `=` comparten el mismo código.
- **Texto y números:** `texto * 1` lo vuelve número y `"" + número` lo vuelve texto. Más adelante se pueden cambiar por `Number()` y `String()`.
- **DEL:** borra el número completo que se está escribiendo, no solo el último dígito.
