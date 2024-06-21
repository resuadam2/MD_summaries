¡Claro! Un XSD (XML Schema Definition) define la estructura, contenido y tipos de datos de un documento XML de manera más potente y precisa que un DTD. A continuación, te proporcionaré un resumen de la sintaxis de XSD con ejemplos.

### 1. Tipos de Definición en XSD

#### Definición Interna
El esquema se define dentro del documento XML.

#### Definición Externa
El esquema se define en un archivo separado.

### Ejemplo de XSD Interno

#### Documento XML con XSD Interno

```xml
<?xml version="1.0" encoding="UTF-8"?>
<biblioteca xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:noNamespaceSchemaLocation="biblioteca.xsd">
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

### Ejemplo de XSD Externo

#### Archivo XSD (`biblioteca.xsd`)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="biblioteca">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="libro" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="titulo" type="xs:string"/>
              <xs:element name="autor" type="xs:string"/>
              <xs:element name="año" type="xs:integer"/>
              <xs:element name="precio" type="xs:decimal"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

#### Documento XML que referencia el XSD Externo

```xml
<?xml version="1.0" encoding="UTF-8"?>
<biblioteca xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:noNamespaceSchemaLocation="biblioteca.xsd">
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

### Explicación de los Elementos del XSD

- `<xs:schema>`: El elemento raíz que define el esquema.
- `<xs:element>`: Define un elemento.
- `<xs:complexType>`: Define un tipo de datos complejo que puede contener otros elementos o atributos.
- `<xs:sequence>`: Define que los elementos hijos deben aparecer en un orden específico.
- `type`: Define el tipo de datos de un elemento.

### Ejemplo con Atributos

#### Archivo XSD con Atributos (`biblioteca.xsd`)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="biblioteca">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="libro" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="titulo" type="xs:string"/>
              <xs:element name="autor" type="xs:string"/>
              <xs:element name="año" type="xs:integer"/>
              <xs:element name="precio" type="xs:decimal"/>
            </xs:sequence>
            <xs:attribute name="id" type="xs:ID" use="required"/>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

#### Documento XML que referencia el XSD con Atributos

```xml
<?xml version="1.0" encoding="UTF-8"?>
<biblioteca xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:noNamespaceSchemaLocation="biblioteca.xsd">
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

### Resumen de Tipos de Datos Comunes en XSD

- `xs:string`: Cadena de texto.
- `xs:integer`: Número entero.
- `xs:decimal`: Número decimal.
- `xs:boolean`: Valor booleano (`true` o `false`).
- `xs:date`: Fecha en el formato `YYYY-MM-DD`.
- `xs:time`: Hora en el formato `HH:MM:SS`.
- `xs:dateTime`: Fecha y hora combinadas en el formato `YYYY-MM-DDTHH:MM:SS`.

### Validación de Datos

#### Restricciones de Longitud y Valor

```xml
<xs:element name="titulo">
  <xs:simpleType>
    <xs:restriction base="xs:string">
      <xs:minLength value="1"/>
      <xs:maxLength value="100"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```

#### Valores Predeterminados y Fijos

```xml
<xs:element name="moneda" type="xs:string" default="USD"/>
<xs:element name="pais" type="xs:string" fixed="España"/>
```

Con estos ejemplos y explicaciones, deberías tener una comprensión básica de cómo elaborar y entender documentos XSD para definir la estructura y los tipos de datos de documentos XML.
