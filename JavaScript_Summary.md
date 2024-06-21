Claro, aquí tienes un resumen básico de la sintaxis de JavaScript que cubre variables, constantes, funciones, procedimientos, estructuras condicionales e iterativas, estructuras de datos comunes y clases:

### Sintaxis Básica de JavaScript

#### Variables y Constantes

En JavaScript, las variables se definen usando `var`, `let` o `const`:

```javascript
// Variables
var x = 5;
let nombre = "Juan";
const PI = 3.14159;

// Constantes (se asigna una vez y no puede cambiar)
const LIMITE_INTENTOS = 3;
```

#### Funciones y Procedimientos

Las funciones en JavaScript se definen con la palabra clave `function`:

```javascript
// Función
function suma(a, b) {
    return a + b;
}

// Procedimiento (función sin retorno explícito)
function imprimirSaludo(nombre) {
    console.log("Hola, " + nombre);
}

// Uso de función y procedimiento
let resultado = suma(3, 4);
imprimirSaludo("Ana");
```

#### Estructuras Condicionales

Las estructuras condicionales en JavaScript se definen con `if`, `else if` (opcional) y `else`:

```javascript
// Ejemplo de estructura condicional
let edad = 18;

if (edad >= 18) {
    console.log("Eres mayor de edad.");
} else {
    console.log("Eres menor de edad.");
}
```

#### Estructuras Iterativas

JavaScript admite bucles `for`, `while` y `do-while` para la iteración:

```javascript
// Ejemplo de bucle for
for (let i = 0; i < 5; i++) {
    console.log(i);
}

// Ejemplo de bucle while
let contador = 0;
while (contador < 5) {
    console.log(contador);
    contador++;
}
```

#### Estructuras de Datos Más Comunes

JavaScript proporciona varias estructuras de datos integradas:

- **Arrays**: Colección ordenada y mutable de elementos.

  ```javascript
  let miArray = [1, 2, 3, 4, 5];
  ```

- **Objetos**: Colección de pares clave-valor.

  ```javascript
  let miObjeto = { nombre: "Juan", edad: 30 };
  ```

- **Sets**: Colección de valores únicos de cualquier tipo.

  ```javascript
  let miSet = new Set([1, 2, 3, 4]);
  ```

- **Mapas**: Colección de pares clave-valor donde las claves pueden ser de cualquier tipo.

  ```javascript
  let miMapa = new Map();
  miMapa.set("nombre", "Ana");
  ```

#### Clases

En JavaScript, las clases se definen usando la palabra clave `class`. Las clases pueden tener métodos (funciones) y propiedades.

```javascript
// Definición de una clase
class Persona {
    // Constructor
    constructor(nombre, edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // Método de instancia
    saludar() {
        console.log(`Hola, mi nombre es ${this.nombre} y tengo ${this.edad} años.`);
    }
}

// Creación de un objeto (instancia)
let persona1 = new Persona("Ana", 25);

// Uso de método de instancia
persona1.saludar();
```

### Consideraciones Adicionales

- **Tipado Dinámico**: JavaScript es un lenguaje de tipado dinámico, lo que significa que las variables pueden contener diferentes tipos de datos en diferentes momentos de la ejecución.
  
- **Eventos y Asincronía**: JavaScript es fundamentalmente asincrónico y es comúnmente utilizado para manejar eventos en páginas web.

Este resumen proporciona una introducción básica y completa a la sintaxis de JavaScript, cubriendo variables, constantes, funciones, procedimientos, estructuras condicionales e iterativas, estructuras de datos comunes y clases. JavaScript es el lenguaje principal para la programación del lado del cliente en aplicaciones web modernas y también es ampliamente utilizado en el desarrollo del lado del servidor y en aplicaciones móviles.