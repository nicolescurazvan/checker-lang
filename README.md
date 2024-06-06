# CheckerLanguage

This is an esoteric programming language that, together with the interpreter
can be used for testing programs.
It can create input and output files, check programs and measure the time of
execution. It can also do basic mathematical calculations and generate random
numbers. The source code files can be identified by the extension `*.cklg`.

## Data types

- `int`, representing 64-bit integers.
- `float`, representing 64-bit floating-point numbers.
- `string`, representing ASCII strings.
- `bool`, representing boolean data ('true' or 'false').
- `array`, representing fixed length arrays.
- `[T]`, for variable length arrays (lists) of type `T`.
- `file`, representing a file object.

## Operations

On `int` values:

- `a + b`, for addition
- `a - b`, for subtraction
- `a * b`, for multiplication
- `a / b`, for division
- `a % b`, for remainder
- `a ** b`, for power
- `a & b`, for bitwise AND
- `a | b`, for bitwise OR
- `~a`, for bitwise NOT
- `a ^ b`, for bitwise XOR

On `float` values:

- `a + b`, for addition
- `a - b`, for subtraction
- `a * b`, for multiplication
- `a / b`, for division
- `a ** b`, for power

The `float` operations support combinations of `float` and `int` values, returning
`float` values.

On `string` values:

- `a + b`, for concatenation (one of the terms can be `int` or `float`)
- `a * b`, where `b` is an `int` value, for repeating the string

On `bool` values:

- `a && b`, for AND
- `a || b`, for OR
- `~a`, for NOT
- `a ^ b`, for XOR

## Syntax

The language is statically typed and the instructions end with `;`.
Comments are like in C (`//` for single-line comments, `/*` for multiline comments).

### Variables

Variables are declared as:
`int x = 50;`

### If statements

`if` statements are declared like this:
```
if (x % 2 == 0) {
    // Code
} elif (x % 3 == 2) {
    // Code
} else {
    // Code
}
```

### For loops

`for` loops can be C-style or have ranges. They are declared like this:
```
for (i = 0; i != 10; i++) {
    // Code
}
```

or

```
for (int x: vector) {
    // Code
}
```

### While loops

`while` loops are declared like in C:
```
while (i > 10) {
    // Code
}
```

### Functions

Functions are declared like in C:
```
int foo(int x, int y, string s) {
    // Code
}
```

Every program must have a `main` function, of type `void`. It takes
an integer (`argc`) and a list of strings (`argv`) as arguments. They
are optional.

## Keywords

- Variable types, like `int`, `float` or `string`
- `void`
- `true` and `false`
- `main`
- `return`
- `import`
- The names of the basic functions mentioned below

## Basic functions

- `read`, for reading variables from the console or from a file
- `readline`, for reading an entire line from the console or from a file
- `write`, for writing variables to the console or to a file
- `writeline`, for writing an entire line from the console or from a file
- `open`, for opening a file
- `close`, for closing a file

## Examples

### Swap two numbers read from the console

```
void main() {
    int a, b;
    read(stdin, a);
    read(stdin, b);
    int c = b;
    b = a;
    a = c;
    write(stdout, a + " " + b);
}
```

### Merge two text files given as arguments and display the result

```
void main(int argc, [string] argv) {
    file f = open(argv[1], "t");
    file g = open(argv[2], "t");
    string str;
    while (readline(f, str)) {
        writeline(stdout, str);
    }
    while (readline(g, str)) {
        writeline(stdout, str);
    }
    close(f);
    close(g);
}
```