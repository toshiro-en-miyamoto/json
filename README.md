# json
JSON - JavaScript Object Notation

- [Introducing JSON](https://www.json.org/json-en.html)
- [JSON-Java - package org.json](https://github.com/stleary/JSON-java)
- [Introduction to JSON-Java](https://www.baeldung.com/java-org-json)

## Introducing JSON

### Grammar

- **overall**
  - json
    - element
  - element
    - ws value ws
  - elements
    - element
    - element `,` elements
  - ws
    - `""`
    - `\0020` ws
    - `\000A` ws
    - `\000D` ws
    - `\0009` ws
  - value
    - object
    - array
    - string
    - number
    - `true`
    - `false`
    - `null`
- **objects and arrays**
  - object
    - `{` ws `}`
    - `{` members `}`
  - members
    - member
    - member `,` members
  - member
    - ws string ws `:` element
  - array
    - `[` ws `]`
    - `[` elements `]`
- **character strings**
  - string
    - `"` characters `"`
  - characters
    - `""`
    - character characters
  - character
    - '0020' . '10FFFF' - `"` - `\`
    - `\`escape
  - escape
    - `"`
    - `\`
    - `/`
    - `b`
    - `f`
    - `n`
    - `r`
    - `t`
    - `u` hex hex hex hex
- **numbers**
  - hex
    - digit
    - `A` . `F`
    - `a` . `f`
  - digit
    - `0`
    - onenine
  - onenine
    - `1` . `9`
  - digits
    - digit
    - digit digits
  - number
    - integer fraction exponent
  - integer
    - digit
    - onenine digits
    - `-` digit
    - `-` onenine digits
  - fraction
    - `""`
    - `.` digits
  - exponent
    - `"`
    - `E` sign digits
    - `e` sign digits
  - sign
    - `""`
    - `+`
    - `-`

### Examples

#### Example 1

```JSON
{"menu": {
  "id": "file",
  "value": "File",
  "popup": {
    "menuitem": [
      {"value": "New", "onclick": "CreateNewDoc()"},
      {"value": "Open", "onclick": "OpenDoc()"},
      {"value": "Close", "onclick": "CloseDoc()"}
    ]
  }
}}
```

The same text expressed as XML:

```XML
<menu id="file" value="File">
  <popup>
    <menuitem value="New" onclick="CreateNewDoc()" />
    <menuitem value="Open" onclick="OpenDoc()" />
    <menuitem value="Close" onclick="CloseDoc()" />
  </popup>
</menu>
```

#### Example 2

```JSON
{"widget": {
    "debug": "on",
    "window": {
        "title": "Sample Konfabulator Widget",
        "name": "main_window",
        "width": 500,
        "height": 500
    },
    "image": { 
        "src": "Images/Sun.png",
        "name": "sun1",
        "hOffset": 250,
        "vOffset": 250,
        "alignment": "center"
    },
    "text": {
        "data": "Click Here",
        "size": 36,
        "style": "bold",
        "name": "text1",
        "hOffset": 250,
        "vOffset": 100,
        "alignment": "center",
        "onMouseUp": "sun1.opacity = (sun1.opacity / 100) * 90;"
    }
}}
```

The same text expressed as XML:

```XML
<widget>
    <debug>on</debug>
    <window title="Sample Konfabulator Widget">
        <name>main_window</name>
        <width>500</width>
        <height>500</height>
    </window>
    <image src="Images/Sun.png" name="sun1">
        <hOffset>250</hOffset>
        <vOffset>250</vOffset>
        <alignment>center</alignment>
    </image>
    <text data="Click Here" size="36" style="bold">
        <name>text1</name>
        <hOffset>250</hOffset>
        <vOffset>100</vOffset>
        <alignment>center</alignment>
        <onMouseUp>
            sun1.opacity = (sun1.opacity / 100) * 90;
        </onMouseUp>
    </text>
</widget>
```
