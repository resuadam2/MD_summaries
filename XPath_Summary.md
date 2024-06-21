XPath (XML Path Language) es un lenguaje utilizado para navegar por los elementos y atributos de un documento XML. La versión más reciente es XPath 3.1, que introduce varias mejoras y características avanzadas. A continuación, te proporcionaré un resumen de la sintaxis de XPath 3.1 junto con ejemplos.

### Sintaxis Básica de XPath

#### Selección de Nodos

- `/`: Selecciona el nodo raíz.
- `//`: Selecciona nodos en el documento desde el nodo actual que coinciden con la selección, sin importar dónde se encuentren.
- `.`: Selecciona el nodo actual.
- `..`: Selecciona el nodo padre del nodo actual.
- `@`: Selecciona atributos.

#### Ejemplos de Selección de Nodos

```xml
<biblioteca>
  <libro>
    <titulo>Don Quijote de la Mancha</titulo>
    <autor>Miguel de Cervantes</autor>
    <año>1605</año>
  </libro>
  <libro>
    <titulo>Cien años de soledad</titulo>
    <autor>Gabriel García Márquez</autor>
    <año>1967</año>
  </libro>
</biblioteca>
```

- `//libro`: Selecciona todos los elementos `<libro>` en el documento.
- `/biblioteca/libro/titulo`: Selecciona todos los elementos `<titulo>` que son hijos de `<libro>` en el elemento `<biblioteca>`.
- `//libro[@año="1967"]`: Selecciona todos los elementos `<libro>` con el atributo `año` igual a "1967".

### Predicados

Los predicados se utilizan para filtrar nodos seleccionados por una expresión XPath.

#### Ejemplos de Predicados

```xml
//libro[autor="Miguel de Cervantes"]
```

Selecciona todos los elementos `<libro>` donde el hijo `<autor>` tiene el valor "Miguel de Cervantes".

```xml
//libro[2]
```

Selecciona el segundo elemento `<libro>`.

### Funciones en XPath

XPath incluye muchas funciones incorporadas para manipular y evaluar datos.

#### Ejemplos de Funciones

```xml
count(//libro)
```

Devuelve el número de elementos `<libro>`.

```xml
string-length(//titulo)
```

Devuelve la longitud del contenido del primer `<titulo>`.

```xml
concat(//titulo[1], " - ", //autor[1])
```

Concatena el contenido del primer `<titulo>` y el primer `<autor>` con un guion en medio.

### Operadores en XPath

#### Operadores de Comparación

- `=`: Igual.
- `!=`: Diferente.
- `<`: Menor que.
- `<=`: Menor o igual que.
- `>`: Mayor que.
- `>=`: Mayor o igual que.

#### Ejemplo de Operadores de Comparación

```xml
//libro[año > 1900]
```

Selecciona todos los elementos `<libro>` donde el año es mayor que 1900.

#### Operadores Lógicos

- `and`: Y lógico.
- `or`: O lógico.
- `not()`: Negación lógica.

#### Ejemplo de Operadores Lógicos

```xml
//libro[año > 1900 and autor="Gabriel García Márquez"]
```

Selecciona todos los elementos `<libro>` donde el año es mayor que 1900 y el autor es "Gabriel García Márquez".

### XPath 3.1: Características Avanzadas

#### Expresiones Lambda

XPath 3.1 introduce funciones lambda (anónimas).

```xml
let $increment := function($x) { $x + 1 }
return $increment(5)
```

Define una función lambda que incrementa un número y la aplica al valor 5, devolviendo 6.

#### Arrays y Maps

XPath 3.1 introduce arrays y maps.

##### Arrays

```xml
[1, 2, 3, 4]
```

Define un array de números.

##### Maps

```xml
map { "name": "John", "age": 30 }
```

Define un mapa con claves "name" y "age".

#### Ejemplo Completo de XPath 3.1

```xml
<biblioteca>
  <libro>
    <titulo>Don Quijote de la Mancha</titulo>
    <autor>Miguel de Cervantes</autor>
    <año>1605</año>
    <precio>25.00</precio>
  </libro>
  <libro>
    <titulo>Cien años de soledad</titulo>
    <autor>Gabriel García Márquez</autor>
    <año>1967</año>
    <precio>20.00</precio>
  </libro>
</biblioteca>
```

Consulta XPath para seleccionar títulos de libros con un precio mayor a 20:

```xml
//libro[precio > 20]/titulo
```

Esta consulta devuelve:

```xml
<titulo>Don Quijote de la Mancha</titulo>
<titulo>Cien años de soledad</titulo>
```

### Resumen

XPath 3.1 ofrece una sintaxis robusta para navegar y manipular datos XML, con funciones avanzadas como arrays, maps y expresiones lambda. Esta guía proporciona una base sólida para trabajar con XPath en la última versión.
