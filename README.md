# Ibex Specification

### General Code Structure

Ibex is an indentation-based language, such as Python.
A block is defined as a continuous group of lines sharing
an indentation level greater than or equal to the first
line's indentation level.

```
A                         |1
B                         |1
    C                 |2  |1
    D                 |2  |1
        E         |3  |2  |1
    F                 |2  |1
G                         |1
    H                 |4  |1
    I                 |4  |1
```
<small>`E` belongs to block #3, `C` through `F` belong
to block #2, `A` through `I` belong to block #1.</small>

A line with indentation level _x_ must be preceded by
a line with an indentation level greater than or equal
to _x-1_.

### Functions

A function is a callable group of code which may accept
input arguments and return one or more values.

**Declaration:**
```
fn function_name
    # no arguments, no return value

fn function_name param:type
    # one argument, no return value

fn function_name param:type -> type
    # one argument, one return value

fn function_name (param1:type, param2:type) -> (type, type)
    # two arguments, two return values
```

**Invocation:**
```
# calls function with no arguments
function_name

# calls function with one argument
param -> function_name

# calls function with two arguments
(param1, param2) -> function_name
```

**Type Signature:**
```
# no arguments, no return value
fn

# one argument, no return value
fn type

# two arguments, two return values
fn (type1, type2) -> (ret1, ret2)
```

In Ibex, functions with two or more arguments are
higher-order functions. E.g. if _f_ is defined as
`fn (a, b) -> ret`, then `a -> f` = `fn b -> ret`

### Tuples
A tuple is an unresizable list of elements, which
can be composed of different element types. A tuple
can have at most 10 elements.

**Declaration:** `(val1, val2)`

**Type Signature:** `(type1, type2)`

A tuple's elements are accessed with `tuple.0`,
`tuple.1`, and so on.

### Named Tuples
A named tuple is similar to a normal tuple, but
each element is tagged with an identifier (unique
within the named tuple).

**Declaration:** `(tag1: val1, tag2: val2)`

**Type Signature:** `(tag1: type1, tag2: type2)`

A named tuple's elements are accessed with a dot
followed by the element's tag: `tuple.tag1`,
`tuple.tag2`, etc.

### Arrays

An array is a resizable collection of elements with
the same type. Arrays have a logical length and capacity.

**Declaration:**
```
# creates a one-dimensional int array with
# length 10 and capacity 10
new [10]int

# creates a one-dimensional int array with
# length 10 and capacity 20
new [10, 20]int

# creates a two-dimensional int array with
# dimensions 10x10
new [10][10]int
```

**Type Signature:**
```
# one-dimensional int array
[]int

# two-dimensional int array
[][]int
```
