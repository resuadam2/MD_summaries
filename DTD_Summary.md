¡Hola! Un DTD (Document Type Definition) define la estructura y las reglas de un documento XML. Sirve para validar que un documento XML sigue un formato específico. Un DTD puede estar incrustado en el propio documento XML o en un archivo separado. A continuación, te explicaré cómo elaborar documentos DTD con ejemplos.

### 1. Tipos de DTD

#### Interno
El DTD se define dentro del documento XML.

#### Externo
El DTD se define en un archivo separado.

### Ejemplo de DTD Interno

#### Documento XML con DTD Interno

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE biblioteca [
  <!ELEMENT biblioteca (libro+)>
  <!ELEMENT libro (titulo, autor, año, precio)>
  <!ELEMENT titulo (#PCDATA)>
  <!ELEMENT autor (#PCDATA)>
  <!ELEMENT año (#PCDATA)>
  <!ELEMENT precio (#PCDATA)>
]>
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

### Ejemplo de DTD Externo

#### Archivo DTD (`biblioteca.dtd`)

```dtd
<!ELEMENT biblioteca (libro+)>
<!ELEMENT libro (titulo, autor, año, precio)>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT autor (#PCDATA)>
<!ELEMENT año (#PCDATA)>
<!ELEMENT precio (#PCDATA)>
```

#### Documento XML que referencia el DTD Externo

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE biblioteca SYSTEM "biblioteca.dtd">
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

### Explicación de los Elementos del DTD

- `<!ELEMENT nombre-de-elemento (contenido)>`: Define un elemento. El contenido puede ser otros elementos o `#PCDATA` (Parsed Character Data, es decir, texto).

- `#PCDATA`: Indica que el contenido del elemento es texto.

- `+`: Indica que el elemento debe aparecer una o más veces.

- `*`: Indica que el elemento puede aparecer cero o más veces.

- `?`: Indica que el elemento puede aparecer cero o una vez.

### Ejemplo con Atributos

#### Archivo DTD con Atributos (`biblioteca.dtd`)

```dtd
<!ELEMENT biblioteca (libro+)>
<!ELEMENT libro (titulo, autor, año, precio)>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT autor (#PCDATA)>
<!ELEMENT año (#PCDATA)>
<!ELEMENT precio (#PCDATA)>
<!ATTLIST libro
          id ID #REQUIRED>
```

#### Documento XML que referencia el DTD con Atributos

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE biblioteca SYSTEM "biblioteca.dtd">
<biblioteca>
  <libro id="L1">
    <titulo>Don Quijote de la Mancha</titulo>
    <autor>Miguel de Cervantes</autor>
    <año>1605</año>
    <precio>25.00</precio>
  </libro>
  <libro id="L2">
    <titulo>Cien años de soledad</titulo>
    <autor>Gabriel García Márquez</autor>
    <año>1967</año>
    <precio>20.00</precio>
  </libro>
</biblioteca>
```

En este ejemplo, el elemento `libro` tiene un atributo `id` que es de tipo `ID` y es obligatorio (`#REQUIRED`).

### Resumen de Tipos de Datos de Atributos

- `CDATA`: Caracteres de texto.
- `ID`: Identificador único dentro del documento.
- `IDREF`: Referencia a un `ID`.
- `IDREFS`: Referencias múltiples a `ID`.
- `NMTOKEN`: Token de nombre.
- `NMTOKENS`: Múltiples tokens de nombre.
- `ENTITY`: Referencia a una entidad.
- `ENTITIES`: Referencias múltiples a entidades.
- `NOTATION`: Referencia a una notación predefinida.
- `ENUMERATION`: Lista de valores posibles.

Con estos ejemplos y explicaciones, tienes una base sólida para empezar a elaborar y entender documentos DTD.
