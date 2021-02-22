# Types

## String

### Literal

- Single Quoted
  - Example
    ```
    'test' 
    '123\' 
    'aa''aaa'  
    ```
  - No support for interpolation
  - All literal keeps as it is, but `''` will be treated as `'`
  
- Double Quoted
  - Example
    ```
    "test"
    "123\\"
    "aa'aaa"
    ```
  - Support interpolation
    ```
    "test $VAR $(EXP)"
    ``` 
  
  - Support escaped characters
    - `\XXX`       three octal digits represet one escaped character
    - `\xXX`       two hexadecimal digits represet one escaped character
    - `\uXXXX`     four hexadecimal digits represet one unicode character
    - `\UXXXXXXXX` eight hexadecimal digits represet one unicode character
    - `\a`         is the “bell” character, equivalent to \007 or \x07.
    - `\b`         is the “backspace” character, equivalent to \010 or \x08.
    - `\f`         is the “form feed” character, equivalent to \014 or \x0c.
    - `\n`         is the “new line” character, equivalent to \012 or \x0a.
    - `\r`         is the “carriage return” character, equivalent to \015 or \x0d.
    - `\t`         is the “tab” character, equivalent to \011 or \x09.
    - `\v`         is the “vertical tab” character, equivalent to \013 or \x0b.
    - `\\`         is the “backslash” character, equivalent to \134 or \x5c.
    - `\"`         is the “double-quote” character, equivalent to \042 or \x22.
    - `\$`         is used to distinguish from interpolation

- Heredoc

  Almost the same as double quoted, but scoped by `"""`; linebreaks are recorded.
  Notice that all escaped characters will still take effect; but `"` will be a valid character itself.
  ```
  """
  heredoc
  """
  ```
### Encoding
  Force `UTF-8`.
  
## Number

### Float
- Double Precision

### Integer
- 64-bit Length

### BigInteger
- Implemented by JVM BigInteger with default configuration

### BigDecimal
- Implemented by JVM BigDecimal with default configuration

### Literal
- Integer
  - Decimal: `10000`
  - Hexadecimal: `0x123abc`
  - Octal: `0o123`
  - Binary: `0b00100`
- Floating Point
  - Normal Format: `0.0123123`
  - Scientific Format: `1.5e-10, 1.5e+1000, 1.5E10`
- Optional sign can be added (`+, -`)
- `_` can be used between digits and has no other effects: `1_000_000_000, 1_0000_0000, 1.23_123`

 ## Vector
 - Random accessible
 - Not sparse
 
 ## List
 - Not random accessible
 
 ## HashMap
 [TODO]
  
 ## Struct
 [TODO]
 
 ## Exception
 [TODO]
