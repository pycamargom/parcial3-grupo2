# Cheatsheet de JavaScript

Resumen rápido del contenido del curso: fundamentos, operadores, estructuras de control, entrada y salida, conversión de tipos y funciones.

---

## 1. Primera línea de código

```javascript
console.log("¡Hola mundo!");   // salida en la consola
alert("¡Hola mundo!");         // ventana emergente

let numero = 24;
console.log(`numero = "${numero}"`);   // interpolación con backticks
```

---

## 2. Comentarios

```javascript
// Comentario de una línea
let numero = 7; // Comentario al final de una línea

/*
  Comentario
  de varias líneas
*/
```

---

## 3. Variables

Son contenedores para almacenar, manipular y mostrar información. Cada variable tiene un **nombre único** y un **valor** que puede ser de distintos tipos.

```javascript
variable_type variable_name = value;
let numero = 4;
```

### Reglas de nombramiento

```javascript
// Válido
let horasTurno = 10;
let _nombre = "Juan";
let $hora = 5;

// Inválido
let 19Porciento = "IVA";   // empieza con número
let horas-turno = 10;      // guion medio
let if = true;             // palabra reservada
```

| Regla | Detalle |
|---|---|
| Caracteres permitidos | Letras (a-z, A-Z), números (0-9), guion bajo (`_`) y signo de dólar (`$`) |
| No pueden | Comenzar con un número |
| Sensibilidad | `myVariable` y `myvariable` son diferentes |
| Convención | **camelCase**: cada palabra después de la primera comienza con mayúscula (`horasExtraNoche`) |

---

## 4. Tipos de dato primitivo

| Tipo | Descripción | Ejemplo |
|---|---|---|
| `Number` | Enteros y decimales | `42`, `3.14` |
| `String` | Secuencia de caracteres / texto | `"Hola"`, `'JS'` |
| `Boolean` | Valor lógico | `true`, `false` |
| `BigInt` | Enteros de precisión arbitraria (muy grandes) | `9007n` |
| `Undefined` | Variable declarada sin valor asignado | `let a;` |
| `Null` | Ausencia intencional de valor | `let a = null;` |
| `NaN` | Indeterminación matemática | `'a' - 7` → `NaN` |
| `Symbol` | Identificador único e inmutable | `Symbol('id')` |

**`typeof`**: devuelve el tipo de dato de una variable u operando sin evaluarlo.

```javascript
typeof 42;        // "number"
typeof "Hola";    // "string"
```

---

## 5. Objeto Math

Objeto interno con constantes, funciones y métodos para trabajar matemáticamente.

| Método | Descripción | Ejemplo |
|---|---|---|
| `Math.round(x)` | Redondea al entero más cercano | `Math.round(4.7)` → `5` |
| `Math.floor(x)` | Redondea hacia abajo | `Math.floor(4.7)` → `4` |
| `Math.ceil(x)` | Redondea hacia arriba | `Math.ceil(4.1)` → `5` |
| `Math.random()` | Número aleatorio entre 0 y 1 | `Math.random()` → `0.123...` |
| `Math.max(a, b)` | Valor máximo | `Math.max(10, 20)` → `20` |
| `Math.min(a, b)` | Valor mínimo | `Math.min(10, 20)` → `10` |
| `Math.pow(base, exp)` | Potencia | `Math.pow(2, 3)` → `8` |
| `Math.sqrt(x)` | Raíz cuadrada | `Math.sqrt(16)` → `4` |
| `Math.abs(x)` | Valor absoluto | `Math.abs(-5)` → `5` |

---

## 6. Strings

### Tipos de comillas

| Comilla | Símbolo | Atajo (Windows) | Uso |
|---|---|---|---|
| Simples | `'` | `Alt + 39` | Texto normal |
| Dobles | `"` | `Shift + 2` o `Alt + 34` | Texto normal |
| Backticks | `` ` `` | `Alt + 96` | Interpolación de variables |

```javascript
let nombre = "Ana";
let saludo = `Hola, ${nombre}`;   // "Hola, Ana"
```

### Métodos y propiedades

Ejemplos con `let cadena = "Hola Mundo"`:

| Método / Propiedad | Descripción | Ejemplo |
|---|---|---|
| `length` | Longitud de la cadena | `cadena.length` → `10` |
| `slice(start, end)` | Extrae una parte y devuelve una nueva | `cadena.slice(0, 4)` → `"Hola"` |
| `substring(start, end)` | Similar a `slice()`, no acepta índices negativos | `cadena.substring(0, 4)` → `"Hola"` |
| `replace(old, new)` | Reemplaza la primera ocurrencia | `cadena.replace("Mundo", "JS")` → `"Hola JS"` |
| `replaceAll(o, n)` | Reemplaza todas las ocurrencias | `cadena.replaceAll("o", "a")` → `"Hala Manda"` |
| `toUpperCase()` | Convierte a mayúsculas | `"HOLA MUNDO"` |
| `toLowerCase()` | Convierte a minúsculas | `"hola mundo"` |
| `trim()` | Elimina espacios en ambos extremos | `"  Hola ".trim()` → `"Hola"` |
| `charAt(index)` | Carácter en el índice | `cadena.charAt(0)` → `"H"` |
| `indexOf(char)` | Índice de la primera ocurrencia | `cadena.indexOf("M")` → `5` |
| `includes(sub)` | Verifica si contiene una subcadena | `cadena.includes("Mundo")` → `true` |
| `split(separator)` | Divide la cadena en partes | `cadena.split(" ")` → `["Hola", "Mundo"]` |

---

## 7. Operadores

### Aritméticos

Ejemplos con `let a = 10, b = 3`:

| Operador | Descripción | Ejemplo | Resultado |
|---|---|---|---|
| `+` | Suma / Concatenación | `a + b` | `13` |
| `-` | Resta | `a - b` | `7` |
| `*` | Multiplicación | `a * b` | `30` |
| `/` | División | `a / b` | `3.333...` |
| `%` | Módulo (resto) | `a % b` | `1` |
| `**` | Exponenciación | `a ** b` | `1000` |

### De comparación

Comparan dos valores y devuelven un booleano. Ejemplos con `x = 5`:

| Operador | Descripción | Ejemplo | Resultado |
|---|---|---|---|
| `==` | Igualdad (solo valor) | `x == "5"` | `true` |
| `===` | Igualdad estricta (valor y tipo) | `x === "5"` | `false` |
| `!=` | Desigualdad | `x != 8` | `true` |
| `>` | Mayor que | `x > 8` | `false` |
| `<` | Menor que | `x < 8` | `true` |
| `>=` | Mayor o igual que | `x >= 5` | `true` |
| `<=` | Menor o igual que | `x <= 5` | `true` |

### Lógicos

Ejemplos con `let a = true, b = false`:

| Operador | Descripción | Ejemplo | Resultado |
|---|---|---|---|
| `&&` | AND lógico (Y) | `a && b` | `false` |
| `\|\|` | OR lógico (O) | `a \|\| b` | `true` |
| `!` | NOT lógico (negación) | `!a` | `false` |

### Unarios

Tienen un solo operando. Ejemplos con `let x = 5`:

| Operador | Nombre | Ejemplo | Resultado | Valor de `x` después |
|---|---|---|---|---|
| `++` | Incremento (prefijo) | `++x` | `6` | `6` |
| `++` | Incremento (sufijo) | `x++` | `5` | `6` |
| `--` | Decremento (prefijo) | `--x` | `4` | `4` |
| `--` | Decremento (sufijo) | `x--` | `5` | `4` |
| `-` | Negación unaria | `-x` | `-5` | `5` |
| `+` | Más unario (conversión a número) | `+"5"` | `5` | `5` |

> **Prefijo vs sufijo:** el prefijo (`++x`) incrementa y luego devuelve el valor; el sufijo (`x++`) devuelve el valor y luego incrementa.

---

## 8. Estructuras de control

Gestionan el flujo de ejecución: permiten tomar decisiones y repetir tareas según se cumpla o no una condición.

| Tipo | Función |
|---|---|
| **Condicionales** | Ejecutan bloques de código según una condición verdadera o falsa |
| **Ciclos o bucles** | Repiten un bloque mientras se cumpla la condición de permanencia |
| **Control de ciclos** (`break`, `continue`) | Modifican el comportamiento normal de los bucles |

### if, else, else if

Toma un camino solo si se cumple la condición.

```javascript
if (condicion) {
    // Se ejecuta si la condición es verdadera
} else if (otraCondicion) {
    // Se ejecuta si la primera es falsa y esta es verdadera
} else {
    // Se ejecuta si ninguna condición se cumple
}
```

### Operador ternario

Forma abreviada de `if-else` para asignaciones rápidas.

```javascript
condicion ? expresion1 : expresion2;

let mensaje = edad >= 18 ? "Mayor de edad" : "Menor de edad";
```

- `expresion1`: se devuelve si la condición es verdadera.
- `expresion2`: se devuelve si la condición es falsa.

### switch

Evalúa una expresión y la compara con varios `case`.

```javascript
switch (expresion) {
    case x:
        // Se ejecuta si la expresión es igual a x
        break;
    case y:
        // Se ejecuta si la expresión es igual a y
        break;
    default:
        // Se ejecuta si no coincide ningún case
        break;
}
```

> Sin `break`, la ejecución continúa en el siguiente `case`.

---

## 9. Ciclos (bucles)

**Iteración:** cada ejecución del bloque de código que indica el ciclo (cada repetición).

Flujo: se evalúa la condición → si se cumple, se ejecuta el bloque y el iterador cambia → se vuelve a evaluar → si no se cumple, el ciclo termina.

### while

Ejecuta el bloque **mientras** la condición sea verdadera.

```javascript
while (condicion) {
    // Bloque de código
}
```

> **Ojo:** pueden crearse bucles infinitos sin querer. Asegúrate de que la condición llegue a ser falsa.

### do… while

Similar a `while`, pero **garantiza que el bloque se ejecute al menos una vez**.

```javascript
do {
    // Bloque de código
} while (condicion);
```

### for

Repite un bloque un número específico de veces; ideal para iterar sobre arrays u objetos.

```javascript
for (iterador; condicion; incremento) {
    // Bloque de código
}

for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

| Parte | Descripción |
|---|---|
| Iterador | Valor inicial (`let i = 0`) |
| Condición | Condición de permanencia (`i < 5`) |
| Incremento | Modificación del iterador (`i++`) |

---

## 10. Interactividad: entrada y salida

```javascript
// Entrada
let nombre = prompt("¿Cuál es tu nombre?");

// Salida
console.log("Hola mundo");
alert("Hola mundo");
```

| Función | Tipo | Descripción |
|---|---|---|
| `prompt()` | Entrada (navegador) | Ventana emergente que pide un dato. **Siempre devuelve un string** (o `null` si el usuario cancela) |
| `console.log()` | Salida | Muestra información en la consola de depuración; herramienta principal del desarrollador |
| `alert()` | Salida | Ventana emergente de alerta con un mensaje |

---

## 11. Conversión de tipos de datos

Transforma datos de un tipo a otro, de forma **explícita** o **implícita** (coerción automática).

| Conversión | Funciones |
|---|---|
| A número | `Number(valor)`, `parseInt(valor)`, `parseFloat(valor)` |
| A string | `String(valor)`, `variable.toString()` |
| A booleano | `Boolean(valor)` |

```javascript
let edad = Number(prompt("¿Cuántos años tienes?"));
let precio = parseFloat("19.99");
let entero = parseInt("42");
```

**Valores que se convierten a `false`:** `0`, `null`, `undefined`, `NaN` y `""` (cadena vacía). Todo lo demás es `true`.

---

## 12. Insertar JavaScript en HTML

### JavaScript externo (recomendado)

Crea un archivo `.js` y enlázalo en el HTML. Mantiene el código organizado y reutilizable.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Ejemplo JS</title>
</head>
<body>
    <h1>Hola Mundo</h1>
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript interno (inline)

Se escribe directamente dentro del HTML con la etiqueta `<script>`.

```html
<script>
    // Código de JavaScript
</script>
```

---

## 13. Funciones

Bloques de código reutilizables para tareas específicas. Se ejecutan cuando se las **llama o invoca**.

| Elemento | Descripción |
|---|---|
| `function` | Palabra reservada que inicia la declaración |
| Nombre | Identificador de la función |
| Parámetros | Variables entre paréntesis (opcionales) |
| Cuerpo | Instrucciones entre llaves `{...}` |
| `return` | Devuelve un valor y finaliza la ejecución. Sin `return`, retorna `undefined` |

```javascript
function sumar(a, b) {
    return a + b;
}
console.log(sumar(5, 3));   // 8
```

### Formas de declarar funciones

**Declaración:** la forma más popular; la función existe en todo el código.

```javascript
function saludo() {
    return "¡Hola!";
}
saludo();
```

**Expresión:** guarda la función dentro de una variable y se ejecuta con ella.

```javascript
const saludo = function saludar() {
    return "¡Hola!";
};
saludo();
```

**Como objeto (constructor `Function`):** posible, pero poco usada en el mundo real por ser incómoda y poco práctica.

```javascript
const saludo = new Function("return 'Hola';");
saludo();
```

### Funciones flecha (Arrow Functions)

Forma corta de escribir funciones, disponible desde ECMAScript 6 (ES6).

```javascript
const saludo = () => console.log("¡Hola!");
saludo();
```

| Regla | Ejemplo |
|---|---|
| Sin parámetros se indica `()` | `() => ...` |
| Con un solo parámetro se puede omitir el paréntesis | `x => x * 2` |
| Con dos o más parámetros van entre paréntesis | `(a, b) => a + b` |
| Si el cuerpo es de una sola línea, se omiten las llaves `{}` | `(a, b) => a + b` |
| En ese caso también se omite el `return` | El valor se devuelve implícitamente |

---

## Resumen rápido

| Necesito... | Uso |
|---|---|
| Mostrar un mensaje al usuario | `alert()` / `console.log()` |
| Pedir un dato | `prompt()` (devuelve string) |
| Convertir texto a número | `Number()`, `parseInt()`, `parseFloat()` |
| Tomar una decisión | `if / else if / else`, ternario, `switch` |
| Repetir un número conocido de veces | `for` |
| Repetir mientras se cumpla algo | `while` |
| Repetir al menos una vez | `do… while` |
| Redondear | `Math.round()`, `Math.floor()`, `Math.ceil()` |
| Reutilizar código | `function` o función flecha |
