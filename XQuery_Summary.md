XQuery (XML Query Language) es un lenguaje diseñado para consultar y manipular datos almacenados en formato XML. Es muy poderoso y permite realizar consultas complejas, transformación de datos y generación de nuevos documentos XML. La versión más reciente es XQuery 3.1. A continuación, te proporciono un resumen de la sintaxis de XQuery 3.1 con ejemplos.

### Estructura Básica de una Consulta XQuery

Una consulta XQuery generalmente tiene la forma:

```xquery
xquery version "3.1";
(: Comentarios :)
<result>
  {
    expresión
  }
</result>
```

### Ejemplos Básicos

#### Selección Simple

Dado el siguiente documento XML:

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

Consulta XQuery para seleccionar todos los títulos de los libros:

```xquery
xquery version "3.1";
for $libro in doc("biblioteca.xml")//libro
return $libro/titulo
```

#### Selección con Filtrado

Consulta XQuery para seleccionar títulos de libros cuyo precio sea mayor a 20:

```xquery
xquery version "3.1";
for $libro in doc("biblioteca.xml")//libro
where $libro/precio > 20
return $libro/titulo
```

#### Construcción de Nuevo XML

Consulta XQuery para crear un nuevo documento XML con los títulos y autores:

```xquery
xquery version "3.1";
<libros>
  {
    for $libro in doc("biblioteca.xml")//libro
    return
      <libro>
        <titulo>{ $libro/titulo }</titulo>
        <autor>{ $libro/autor }</autor>
      </libro>
  }
</libros>
```

### Funciones y Variables

#### Declaración de Variables

```xquery
xquery version "3.1";
let $precioMinimo := 20
for $libro in doc("biblioteca.xml")//libro
where $libro/precio > $precioMinimo
return $libro/titulo
```

#### Uso de Funciones

```xquery
xquery version "3.1";
declare function local:esBarato($precio as xs:decimal) as xs:boolean {
  $precio < 20
};
for $libro in doc("biblioteca.xml")//libro
where local:esBarato($libro/precio)
return $libro/titulo
```

### Operadores y Expresiones

#### Operadores de Comparación

- `=`: Igual.
- `!=`: Diferente.
- `<`: Menor que.
- `<=`: Menor o igual que.
- `>`: Mayor que.
- `>=`: Mayor o igual que.

#### Ejemplo de Comparación

```xquery
xquery version "3.1";
for $libro in doc("biblioteca.xml")//libro
where $libro/año > 1900
return $libro/titulo
```

#### Operadores Lógicos

- `and`: Y lógico.
- `or`: O lógico.

#### Ejemplo de Operadores Lógicos

```xquery
xquery version "3.1";
for $libro in doc("biblioteca.xml")//libro
where $libro/año > 1900 and $libro/precio < 30
return $libro/titulo
```

### Características Avanzadas de XQuery 3.1

#### Arrays

```xquery
xquery version "3.1";
let $array := [1, 2, 3, 4]
return $array[2]  (: Devuelve 2 :)
```

#### Maps

```xquery
xquery version "3.1";
let $map := map { "nombre": "Juan", "edad": 30 }
return $map("nombre")  (: Devuelve "Juan" :)
```

#### Funciones Lambda

```xquery
xquery version "3.1";
let $incrementar := function($x) { $x + 1 }
return $incrementar(5)  (: Devuelve 6 :)
```

### Ejemplo Completo de XQuery

#### Dado el documento XML:

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

#### Consulta XQuery para crear un nuevo documento XML con libros de Gabriel García Márquez cuyo precio sea mayor a 20:

```xquery
xquery version "3.1";
<libros>
  {
    for $libro in doc("biblioteca.xml")//libro
    where $libro/autor = "Gabriel García Márquez" and $libro/precio > 20
    return
      <libro>
        <titulo>{ $libro/titulo }</titulo>
        <autor>{ $libro/autor }</autor>
        <precio>{ $libro/precio }</precio>
      </libro>
  }
</libros>
```

Este resumen proporciona una base sólida para trabajar con XQuery 3.1, cubriendo la selección de nodos, filtrado, construcción de nuevos XML, uso de variables y funciones, así como características avanzadas como arrays, maps y funciones lambda.
