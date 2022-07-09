# JavaScript

## Visión General

Lenguaje multiparadigma, dinamicamente tipado y con objetos predefinidos.

## Tipos de datos

<details> <summary>Pulsa para ampliar</summary>

- Number
- BigInt
- String
- Boolean
- Symbol (new in ES2015)
- Object
  - `Function`
  - `Array`
  - `Date`
  - `RegExp`
- null
- undefined
- Error

### Number

<details> <summary>Pulsa para ampliar</summary>

Los datos numéricos son:
- [**Number.**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#numeric_types) Representación por defecto de un valor numérico. Número flotante de doble precisión (64 bits).
- [**BigInt.**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#bigint_type) Representan enteros. No se pueden usar en operaciones de la librería `Math` ni con valores `Number`. Se crean mediante `BigInt(value)` o añadiendo `n` al final del número.

Para obtener un número se utiliza la función `parseInt(valor, base)`. Se puede utilizar `parseInt(valor)`, pero el resultado depende del navegador. También puede utilizarse el operador `+` para transformar un string en un número:

```javascript
parseInt('123', 10); // 123
parseInt('010', 10); // 10

parseInt('010');  //  8
parseInt('0x10'); // 16

+ '42';   // 42
+ '010';  // 10
+ '0x10'; // 16
```


Los valores `NaN`, `Infinity` y `-Inifnity` se pueden obtener como resultado en operaciones matemáticas. Cualquier operación que incluya un `NaN` dará como resultado un `NaN`. Igualmente pasa con `Inifnity`:

```javascript
parseInt('hello', 10); // NaN
NaN + 5;               // NaN

 1 / 0; //  Infinity
-1 / 0; // -Infinity
```

Pueden comprobarse los `NaN` con la función `Number.isNaN(value)`. La función global `isNaN(value)` realiza una comprobación sin tener en cuenta el tipo de dato, por lo que no es recomendable si se utilizan tipos `Number`:

```javascript
Number.isNaN(NaN); // true
Number.isNaN('hello'); // false
Number.isNaN('1'); // false
Number.isNaN(undefined); // false
Number.isNaN({}); // false
Number.isNaN([1]) // false
Number.isNaN([1,2]) // false

isNaN('hello'); // true
isNaN('1'); // false
isNaN(undefined); // true
isNaN({}); // true
isNaN([1]) // false
isNaN([1,2]) // true
```

Pueden comprobarse los `Infinity` y `NaN` con la función `isFinite(value)`:

```javascript
isFinite(1 / 0);     // false
isFinite(-Infinity); // false
isFinite(NaN);       // false
```

</details>

### Strings

<details> <summary>Pulsa para ampliar</summary>

Los métodos mas comunes de un string son:

```javascript
'hello'.length; // 5

'hello'[0];        // "h"
'hello'.charAt(0); // "h"

'hello, world'.replace('world', 'mars'); // "hello, mars"

'hello'.toUpperCase(); // "HELLO"
```

</details>

### Otros tipos

<details> <summary>Pulsa para ampliar</summary>

`null` hace referencia a un valor vacío.

`undefined` representa que un valor aún no ha sido asignado.

El tipo **Boolean** representa los valores booleanos `true` y `false`:
1. `false`, `0`, strings vacías (`""`), `NaN`, `null`, y `undefined` se convierten en `false`.
2. Cualquier otro valor se vuelve `true`.

```javascript
Boolean('');  // false
Boolean(234); // true
``` 

</details>

</details>

## Variables

<details> <summary>Pulsa para ampliar</summary>

Las variables pueden declararse de las formas `let`, `const` y `var`.

`let` declara variables a nivel de bloque:

```javascript
let a;              // undefined
let name = 'Simon'; // "Simon"
```

`const` declara variables a nivel de bloque y cuyo valor es inmutable:

```javascript
const Pi = 3.14; // variable Pi
Pi = 1;          // Error
```

`var` declara variables globales. No es recomendable usarlo:

```javascript
var a;              // undefined
var name = 'Simon'; // "Simon"
```

## Operadores

Los operadores numéricos disponibles son `+`, `-`, `*`, `/` y `%`. El operador de asignación es `=`. Además se puede realizar una operación-asignación utilizando un operador matemático seguido del operador de asignación (`+=`):

```javascript
x = 0;

x = x + 5;
x += 5;
```

Exiten los operadores `++`y `--` que incrementan y decrementan en 1 en valor de la variable prefija o postfija:
```javascript
x = 0; // 0

x++;   // 1
++x;   // 2

x--;   // 1
--x;   // 0
```


El operador `+` también realiza concatenación de strings:

```javascript
'hello' + ' world'; // "hello world"
```

Cuando se realiza una operación con un string el resultado es convertido a `String`:

```javascript
'3' + 4 + 5;  // "345"
 3 + 4 + '5'; // "75"
```

Los operadores de comparación son `<`, `>`, `<=`, `>=`, `==`, `!=`, `===` y `!==`. El operador `==` compara los valores, aunque cuando los tipos de datos de los extremos son distintos fuerza la conversión de tipos (teniendo un carácter impredecible), mientras que `===` compara el valor y el tipo de dato. Es por ello que se recomienda usar siempre `===`. Ejemplos:

```javascript
123 == '123'; // true
1 == true;    // true

123 === '123'; // false
1 === true;    // false

// Ejemplos de la imprevisibilidad del operador ==:
"0" == 0 // true
[] == 0 // true
[1] == 1 // true
[1,2] == 2 // false, esto es porque la lista [] se pasa a entero, devolverá 0 al estar vacía y 1 en otro caso 
```

JavaScript también cuenta con [operadores binarios](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators).

</details>

## Estructuras de control

<details> <summary>Pulsa para ampliar</summary>

Las estructuras de control disponibles son:

- `if-else`
- `while`
- `do-while`
- [`for`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)
- [`for`...`of`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of). Itera sobre todos los elementos de un objeto iterable, devolviendo el indice como un número. Evita propiedades no indexadas. En general, itera sobre los elementos (**recomendable**).
- [`for`...`in`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in). Itera sobre todas las propiedades enumerables, devolviendo el indice como un string. En general, itera sobre los indices.
- `switch`. Las comparaciones se realizan mediante el operador `===`.

También estan disponibles los operadores binarios `&&` y `||` que permiten realizar comprobaciones en la asignación (comprobación de nulos). Otro operador disponible es el operador ternario `?:` que realiza una comprobación binaria en una linea, permitiendo la asignación:

```javascript
const name = o && o.getName();

const name = cachedName || (cachedName = getName());

const allowed = (age > 18) ? 'yes' : 'no';
```

</details>

## Objetos

<details> <summary>Pulsa para ampliar</summary>

Existen dos formas de crear un objeto vacío:

```javascript
const obj = new Object();

const obj = {};
```

Puede utilizarse para inicializar un objeto:

```javascript
const obj = {
  name: 'Carrot',
  _for: 'Max', // 'for' es una palabra reservada
  details: {
    color: 'orange',
    size: 12
  }
};
```

Para acceder a un atributo se puede utilizar la notación de punto o la notación de corchetes:

```javascript
obj.details.color;      // orange
obj['details']['size']; // 12
```

Se pueden crear prototipos de objetos, los cuales devuelven un objeto del tipo deseado:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const you = new Person('You', 24); // Nombre "You" de edad 24
```

Es posible utilizar los objetos para utilizar JavaScript con el paradigma OOP (Programación Orientada a Objetos):
```javascript
class Humanoid {
  constructor() {
    this.dna = 'human';
  }
  walk() {
    console.log("This " + this.dna + " is going for a walk");
  }
}
```

### Arrays

<details> <summary>Pulsa para ampliar</summary>

Los arrays son un tipo especifico de objeto. Pueden crearse de las siguientes formas:

```javascript
[element0, element1, /* ... ,*/ elementN]

new Array(element0, element1, /* ... ,*/ elementN)

new Array(arrayLength)
```

Cuentan con la propiedad `length` cuyo valor es uno más al valor del mayor índice utilizado:

```javascript
const a = ['dog', 'cat', 'hen'];
a.length; // 3

a[100] = 'fox';
a.length; // 101
```

Para iterar sobre un array puede utilizarse un bucle `for`, `for`...`in`, `for`...`of` (**recomendable**), o la función `.forEach(function)`:

```javascript
['dog', 'cat', 'hen'].forEach((currentValue, index, array) => {
  // CODE
});
```

Para añadir un item al final del array se utiliza el método `.push(item1, ..., itemN)`. Para una lista completa de los métodos disponibles consultar [esta página](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

</details>

### Funciones

<details> <summary>Pulsa para ampliar</summary>

Para declarar una función se utiliza la siguiente sintaxis:

```javascript
function add(x, y) {
  const total = x + y;
  return total;
}
```

Se puede llamar a una función sin el número de parametros establecido, lo cual establecerá a `undefined` aquellos parametros no especificados. Se pueden pasar más argumentos de los que espera la función, lo que implicará que todo parámetro a mayores será ignorado:

```javascript
add();        // NaN
add(2, 3, 4); // 5
```

Todas las funciones tienen acceso a una variable adicional `arguments` dentro de su cuerpo la cual es un objeto parecido a un array que contiene todos los argumentos pasados a la función:

```javascript
function add() {
  let sum = 0;
  for (const item of arguments) {
    sum += item;
  }
  return sum;
}

add(2, 3, 4, 5); // 14
```

Se puede obtener el mismo resultado con la [sintaxis de resto de parametros](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters):

```javascript
function avg(...args) {
  let sum = 0;
  for (const item of args) {
    sum += item;
  }
  return sum / args.length;
}

avg(2, 3, 4, 5); // 3.5
```

El método `.apply(obj, arr)` te permite llamar a una función dado un objeto y un array de valores que serán usados como parametros:

```javascript
avg.apply(null, [2, 3, 4, 5]); // 3.5
```

JavaScript permite la creación de funciones anónimas que pueden ser usadas como argumentos para otras funciones:

```javascript
let fnc1 = function() {
  // CODE
};

let fnc2 = () => {
  // CODE
};
```

</details>

### Objetos personalizados

<details> <summary>Pulsa para ampliar</summary>

La creación de prototipos de objetos personalizados es bastante sencilla:

```javascript
// Objeto Person
function Person(first, last) {
  this.first = first;
  this.last = last;
}
// Método de Person
Person.prototype.fullName = function() {
  return this.first + ' ' + this.last;
};
// Método de Person
Person.prototype.fullNameReversed = function() {
  return this.last + ', ' + this.first;
};

```

JavaScript permite añadir elementos al prototipo de objetos predefinidos:

```javascript
const s = 'Simon';
s.reversed(); // TypeError on line 1: s.reversed is not a function

String.prototype.reversed = function() {
  let r = '';
  for (let i = this.length - 1; i >= 0; i--) {
    r += this[i];
  }
  return r;
};

s.reversed(); // nomiS
'This can now be reversed'.reversed(); // desrever eb won nac sihT
```

Todo objeto incluye el método `.toString()` el cual se llama cuando se intenta representar el objeto en forma de string. Se puede modificar, como cualquier otro método:

```javascript
const s = new Person('Simon', 'Willison');
s.toString(); // [object Object]

Person.prototype.toString = function() {
  return '<Person: ' + this.fullName() + '>';
}

s.toString(); // "<Person: Simon Willison>"
```

Se puede utilizar el método `.apply(obj, arr)` anterior para crear un `new` trivial (en este caso no inicializa la cadena de prototipos):

```javascript
function trivialNew(constructor, ...args) {
  const o = {}; // Create an object
  constructor.apply(o, args);
  return o;
}

const bill = trivialNew(Person, 'William', 'Orange');
const bill = new Person('William', 'Orange');
```

La función `.apply()` tiene una hermana, `.call()`, la cual funciona igual pero toma los argumentos expandidos.

</details>

</details>

## Clausuras

<details> <summary>Pulsa para ampliar</summary>

Se pueden crear funciones a partir de funciones con los parámetros especificados:

```javascript
function makeAdder(a) {
  return function(b) {
    return a + b;
  };
}

const add5 = makeAdder(5);
const add20 = makeAdder(20);

add5(6);  // 11
add20(7); // 27
```

</details>
