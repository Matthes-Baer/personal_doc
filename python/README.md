# Python

## Useful Links

## Useful Functions

### Built-in Functions

- `print()` — Output to console
- `input()` — Take user input
- `len()` — Length of iterable
- `type()` — Check type of variable
- `str()`, `int()`, `float()`, `bool()` — Type conversions
- `list()`, `tuple()`, `set()`, `dict()` — Data structure conversions
- `range(start, stop, step)` — Generate sequences of numbers
- `enumerate(iterable, start=0)` — Iterate with index
- `zip(*iterables)` — Combine iterables element-wise
- `min()`, `max()` — Get smallest/largest values
- `sum()` — Sum of elements
- `sorted(iterable, key=None, reverse=False)` — Return sorted list
- `any()`, `all()` — Logical checks on iterables
- `abs()` — Absolute value
- `round(number, digits=0)` — Round numbers
- `help()` — Interactive help / docstring info
- `dir(object)` — List attributes/methods
- `id(object)` — Unique identifier of an object
- `isinstance(object, type)` — Check type

### String Methods

- `.lower()`, `.upper()` — Change case
- `.strip()`, `.rstrip()`, `.lstrip()` — Remove whitespace
- `.split(sep=None)` — Split string
- `.join(iterable)` — Join iterable into string
- `.replace(old, new)` — Replace substring
- `.find(sub)`, `.index(sub)` — Search substring

### List Methods

- `.append(x)` — Add element
- `.extend(iterable)` — Add multiple elements
- `.insert(index, x)` — Insert at position
- `.remove(x)` — Remove first occurrence
- `.pop(index=-1)` — Remove & return element
- `.sort()` — Sort in place
- `.reverse()` — Reverse in place
- `.copy()` — Shallow copy

### Dictionary Methods

- `.keys()` — Dictionary keys
- `.values()` — Dictionary values
- `.items()` — Key-value pairs
- `.get(key, default=None)` — Safe access
- `.update(dict)` — Merge dictionaries
- `.pop(key)` — Remove & return value
- `.setdefault(key, default=None)` — Set default if missing

### File Handling

- `open(filename, mode)` — Open file (`'r'`, `'w'`, `'a'`, `'rb'`, `'wb'`)
- `.read()` — Read entire file
- `.readline()` — Read one line
- `.readlines()` — Read all lines
- `.write(str)` — Write to file
- `.close()` — Close file
- Use `with open(...) as f:` to auto-close files

## General Information

- Python is **interpreted**, **dynamic**, and **strongly typed**.
- **Indentation matters** — Python uses whitespace instead of braces.
- Variables are **references to objects**, not fixed memory locations.
- Common data types: `int`, `float`, `str`, `bool`, `list`, `tuple`, `set`, `dict`.
- **Mutable types**: `list`, `dict`, `set`
- **Immutable types**: `int`, `float`, `str`, `tuple`, `bool`
- Functions are defined using `def name(parameters):`.
- Use `return` to send values back from a function.
- **Loops**:
  - `for item in iterable:`
  - `while condition:`
- **Conditionals**: `if`, `elif`, `else`
- **Boolean operators**: `and`, `or`, `not`
- **Comparisons**: `==`, `!=`, `<`, `>`, `<=`, `>=`
- **Comprehensions** provide concise syntax:
  - List: `[x for x in iterable if condition]`
  - Dict: `{k: v for k, v in iterable}`
- **Exceptions** are handled with `try`, `except`, `else`, `finally`.
- **Modules** are imported using `import module` or `from module import name`.
- **Comments** use `#`; docstrings use triple quotes.
- Python uses **zero-based indexing**.
- Negative indexes access elements from the end (`-1` is last).
- `None` represents the absence of a value.
- Strings support **slicing**: `s[start:stop:step]`.

## Code Examples
