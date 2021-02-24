# Basic Defintions

## Normal Identifier

A normal identifier refers to the sequence starting with one of the following:

- ASCII Alphabet `[a-zA-Z]`
- Non-ASCII Unicode Printables
- ASCII Symbols `_`

And then followed by:
- ASCII Digit `[0-9]`
- ASCII Alphabet `[a-zA-Z]`
- Non-ASCII Unicode Printables
- ASCII Symbols `_`

## Variable

A variable can be any sequence starting with a `$`, and then followed by one or more variable chars

### Variable Char

- ASCII Digit `[0-9]`
- ASCII Alphabet `[a-zA-Z]`
- ASCII Symbols `_`
- Non-ASCII Unicode Printables

### Examples:
```
$abc
$1
$13a
$11_11
$你好
```

## Function Name

### Special

The following symbols can be function names when used alone:

- '+'
- '-'
- '*'
- '/'
- '%'

This kind of function names are not allowed to be assigned as member field.

### General 

A function name is either a special function name or a normal identifier

## Namespace

Variables and functions can be decorated with namespaces. A namespace itself need to follow the rule of normal identifier.
In all the decorated variable follows:
```
decorated variable <- '$' (<normal identifier> ':')* <variable> 
decorated function <- (<normal identifier> ':')* <function name> 
```
For example, in `$a:b:c`, the space model is
```
a {
  b {
    $c
  }
}
```

## Member field

The following lexical components are allowed for member fields:

- General Function Name
- Normal Identifier

### Access

Member field access follows `<variable>.<member>`


## Bareword

A bareword contains the characters from the following set:

- ASCII letters (a-z and A-Z) and numbers (0-9)

- The symbols `!%+,-./:@\_`

- Non-ASCII Unicode Printables

## Whitespace

The following and their klein closures are whitespaces:

- Line swiches including
  - carriage new line
  - new line

- space character ' '

- '\t'

- comment: a text section starts with `#` and ends before (not including) a line switch

## Crossline

A crossline is defined as
```
'\' [whitespace] <line switch>
```

## Basic Expression

The expressions in Selfish take the following forms:

- Single Quoted String is an expression
- Double Quoted String is an expression (including interpolation)
- Bareword is an expression
- Variable is an expression
- Member Access is an expression

Given `S` is an expression:
- `(S)` is also an expression

Given `X, Y` are expressions:

- `X <whitespace/crossline>+ Y` is also an expression

Given `X, Y` are expressions:
- `X <whitespace/crossline>+ | <whitespace/crossline>+ Y` is also an expression called pipeline

The above rule terminates until it reaches a line switch.

Pipeline has a lower precedence.

### Examples

```
print 1 2 3

print (+ 1 2)

(first function-array) 1 2 3

(1)

obj | func | func

(obj | func) xyz
```

### Issues

 - Barewords include numerical literals and the problem will be handled as runtime coercion. More precisely, strings are coerced into numbers
 - The head node of an expression should be checked
   - if it is a string explicitly (not a bareword), the expression must be understand as finding the executable to run
   - variable or member access should be determined in parse phase
   - if it is lexically impossible to be a function or variable or member access, the expression must be understand as finding the executable to run
   - otherwise, the real thing to do is determined in runtime by the following order:
     - if alias exists, execute alias
     - if function exists, execute function
     - if the executable can be found, run executable
     - throw expression

## Tilde Expansion Rule

## Wildcard Expansion Rule

