<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:tns="http://www.baeldung.com/springsoap/gen"
           targetNamespace="http://www.baeldung.com/springsoap/gen" elementFormDefault="qualified">

    <xs:element name="getCountryRequest">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="name" type="xs:string"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

    <xs:element name="getCountryResponse">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="country" type="tns:country"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

    <xs:complexType name="country">
        <xs:sequence>
            <xs:element name="name" type="xs:string"/>
            <xs:element name="population" type="xs:int"/>
            <xs:element name="capital" type="xs:string"/>
            <xs:element name="currency" type="tns:currency"/>
        </xs:sequence>
    </xs:complexType>

    <xs:simpleType name="currency">
        <xs:restriction base="xs:string">
            <xs:enumeration value="GBP"/>
            <xs:enumeration value="EUR"/>
            <xs:enumeration value="PLN"/>
        </xs:restriction>
    </xs:simpleType>
</xs:schema>



### Explain this code 



Certainly! Let's go through the XML Schema (XSD) step by step.

```xml
<?xml version="1.0" encoding="UTF-8"?>
```
- This declares the XML version and the character encoding used in the document. It's standard to specify the XML version as `1.0` and the encoding as `UTF-8`.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:tns="http://www.baeldung.com/springsoap/gen"
           targetNamespace="http://www.baeldung.com/springsoap/gen" elementFormDefault="qualified">
```
- `<xs:schema>`: This is the root element that defines the XML Schema.
- `xmlns:xs="http://www.w3.org/2001/XMLSchema"`: Declares the XML Schema namespace (prefix `xs`) that is used throughout the document.
- `xmlns:tns="http://www.baeldung.com/springsoap/gen"`: Declares a custom namespace (`tns` for target namespace). It associates a URI (`http://www.baeldung.com/springsoap/gen`) with the schema for elements like `country` and `currency`.
- `targetNamespace="http://www.baeldung.com/springsoap/gen"`: Specifies the namespace that this schema defines. This ensures that all elements defined in the schema belong to this namespace.
- `elementFormDefault="qualified"`: This means all elements within this schema must be qualified by a namespace prefix, ensuring that all elements use the `tns` namespace.

### First Element: `getCountryRequest`
```xml
<xs:element name="getCountryRequest">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="name" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```
- `<xs:element name="getCountryRequest">`: Defines an element named `getCountryRequest`. This would be the root element of a request message in your XML.
- `<xs:complexType>`: This element has a complex structure (not just a simple value like a string or integer).
- `<xs:sequence>`: Indicates that the elements inside should appear in a specific order (sequence).
- `<xs:element name="name" type="xs:string"/>`: Declares an element named `name` within the sequence, with a data type of `xs:string`. This means the request should contain a `name` element that accepts a string.

### Second Element: `getCountryResponse`
```xml
<xs:element name="getCountryResponse">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="country" type="tns:country"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```
- `<xs:element name="getCountryResponse">`: Defines an element named `getCountryResponse`. This is likely the root element of the response message.
- `<xs:complexType>`: Indicates the response is complex.
- `<xs:sequence>`: Elements must appear in sequence.
- `<xs:element name="country" type="tns:country"/>`: Declares an element named `country` that uses the `country` complex type (defined later). The type is prefixed by `tns`, meaning it refers to the `country` type defined in this schema's namespace.

### `country` Complex Type
```xml
<xs:complexType name="country">
    <xs:sequence>
        <xs:element name="name" type="xs:string"/>
        <xs:element name="population" type="xs:int"/>
        <xs:element name="capital" type="xs:string"/>
        <xs:element name="currency" type="tns:currency"/>
    </xs:sequence>
</xs:complexType>
```
- `<xs:complexType name="country">`: Defines a complex type named `country`. This will be used to structure information about a country.
- `<xs:sequence>`: The elements inside must appear in a specific order.
- `<xs:element name="name" type="xs:string"/>`: Defines a `name` element of type string.
- `<xs:element name="population" type="xs:int"/>`: Defines a `population` element of type integer.
- `<xs:element name="capital" type="xs:string"/>`: Defines a `capital` element of type string.
- `<xs:element name="currency" type="tns:currency"/>`: Defines a `currency` element which refers to the `currency` type (defined later in the schema).

### `currency` Simple Type
```xml
<xs:simpleType name="currency">
    <xs:restriction base="xs:string">
        <xs:enumeration value="GBP"/>
        <xs:enumeration value="EUR"/>
        <xs:enumeration value="PLN"/>
    </xs:restriction>
</xs:simpleType>
```
- `<xs:simpleType name="currency">`: Defines a simple type named `currency`. A simple type can only have text content, not nested elements.
- `<xs:restriction base="xs:string">`: This restricts the `currency` type to certain allowed string values.
- `<xs:enumeration value="GBP"/>`, `<xs:enumeration value="EUR"/>`, `<xs:enumeration value="PLN"/>`: Defines three valid values for the currency type: GBP (British Pound), EUR (Euro), and PLN (Polish Zloty).

### Conclusion
This schema defines two main elements:
1. `getCountryRequest`: A request containing the name of a country (a string).
2. `getCountryResponse`: A response containing a `country` element that describes the country’s name, population, capital, and currency.

The `country` complex type structures the information about the country, and the `currency` type restricts its values to one of three currencies (GBP, EUR, PLN). This structure is typically used in SOAP web services to validate requests and responses for country information.
