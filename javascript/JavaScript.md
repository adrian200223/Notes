# JavaScript

## Visión General

Lenguaje multiparadigma, dinamicamente tipado y con objetos predefinidos.

## Tipos de datos

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

<details> <summary> ### Number </summary>

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