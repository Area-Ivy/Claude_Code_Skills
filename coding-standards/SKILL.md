---
name: coding-standards
description: 【Mandatory Priority Call】This skill must be called first to load coding standards before any code-related operations. Trigger conditions include but are not limited to: writing new code, modifying existing code, code review, refactoring, technology selection, architecture design. This is a mandatory requirement that must be called before executing code operations and cannot be skipped.
verification_code: AE-CODING-STD-V1
---

## Project Coding Standards

The following coding standards must be followed:

## Important Notice
When generating or modifying code, the following coding standards must be strictly followed. These standards are mandatory and cannot be ignored.
---

## Naming Conventions

### Variables
**Convention**: camelCase
**Description**: Variable names must use lower camelCase
**Correct Examples**: userName, isActive, totalCount
**Incorrect Examples**: user_name, is_active, TotalCount

### Constants
**Convention**: UPPER_SNAKE_CASE
**Description**: Constant names must use uppercase snake case
**Correct Examples**: MAX_SIZE, API_KEY, DEFAULT_TIMEOUT
**Incorrect Examples**: maxSize, apiKey, defaultTimeout

### Functions
**Convention**: camelCase
**Description**: Function names must use lower camelCase and should start with a verb
**Correct Examples**: getUserData, calculateTotal, isValid
**Incorrect Examples**: get_user_data, CalculateTotal, valid

### Classes
**Convention**: PascalCase
**Description**: Class names must use PascalCase (upper camelCase)
**Correct Examples**: UserService, HttpClient, DatabaseConnection
**Incorrect Examples**: userService, httpClient, database_connection

### Files
**Convention**: kebab-case
**Description**: File names should use kebab-case (hyphen-separated)
**Correct Examples**: user-service.js, http-client.ts, data-processor.py
**Incorrect Examples**: UserService.js, httpClient.ts, data_processor.py

## Formatting Standards

### Indentation
**Description**: Use 2 spaces for indentation, do not use tabs

### Quotes
**Description**: Prefer single quotes for strings, unless the string contains single quotes
**Correct Examples**: 'hello world', "it's a test"
**Incorrect Examples**: "hello world"

### Semicolons
**Description**: Semicolons are not mandatory in JavaScript/TypeScript (can be adjusted based on project requirements)

### Line Length
**Description**: Maximum 100 characters per line

## Comment Standards

### Function Comments
**Description**: Public functions and methods must have documentation comments
**Example**:
```javascript
/**
 * Get user data
 * @param {string} userId - User ID
 * @returns {Promise<User>} User object
 */
function getUserData(userId) { ... }
```

### Complex Logic Comments
**Description**: Complex business logic must have explanatory comments

### TODO Comments
**Description**: Use TODO markers for pending tasks

## Best Practices

### Error Handling
**Description**: Errors and exceptions must be handled properly, avoid empty catch blocks
**Example**:
```javascript
try {
  // code
} catch (error) {
  console.error('Error:', error)
  // appropriate error handling
}
```

### Magic Numbers
**Description**: Avoid using magic numbers, define them as constants
**Example**:
```javascript
const MAX_RETRY_COUNT = 3

for (let i = 0; i < MAX_RETRY_COUNT; i++) { ... }
```

### Function Length
**Description**: A single function should not exceed 50 lines, long functions should be split

### Single Responsibility
**Description**: Functions and classes should follow the Single Responsibility Principle, each function should do only one thing

## Security Standards

### No Hardcoded Sensitive Information
**Description**: Hardcoding passwords, API keys, and other sensitive information is prohibited
**Solution**: Use environment variables or configuration files

### Input Validation
**Description**: All external inputs must be validated to prevent injection attacks

### SQL Injection Prevention
**Description**: Use parameterized queries to prevent SQL injection

### XSS Prevention
**Description**: Escape user input to prevent XSS attacks

---

# Backend Standards (Python)

> Based on Google Python Style Guide

## Linting

### Run Linter
**Description**: Run pylint/ruff over your code before committing
**Tool**: Use ruff or pylint with appropriate configuration

### Suppressing Warnings
**Description**: Suppress warnings only when inappropriate; add explanation
**Example**:
```python
def do_PUT(self):  # pylint: disable=invalid-name
    ...  # WSGI requires this name
```

---

## Python Naming Conventions

### Naming Summary Table
| Type | Public | Internal |
|------|--------|----------|
| Packages | `lower_with_under` | |
| Modules | `lower_with_under` | `_lower_with_under` |
| Classes | `CapWords` | `_CapWords` |
| Exceptions | `CapWords` | |
| Functions | `lower_with_under()` | `_lower_with_under()` |
| Constants | `CAPS_WITH_UNDER` | `_CAPS_WITH_UNDER` |
| Variables | `lower_with_under` | `_lower_with_under` |
| Parameters | `lower_with_under` | |

### Variables and Functions
**Convention**: snake_case (lower_with_under)
**Correct Examples**: user_name, get_user_data, is_valid
**Incorrect Examples**: userName, getUserData

### Private Members
**Convention**: Single underscore prefix `_private` for internal use
**Note**: Avoid double underscore `__private` (name mangling); prefer single underscore
**Example**: `_internal_method`, `_secret_key`

### Module Names
**Convention**: All lowercase with underscores, use `.py` extension, never use dashes
**Correct Examples**: user_service.py, http_client.py
**Incorrect Examples**: user-service.py, UserService.py

### Names to Avoid
- Single character names (except: `i`, `j`, `k` for iterators, `e` for exceptions, `f` for files)
- Dashes in any package/module name
- `__double_leading_and_trailing_underscore__` names (reserved by Python)
- Names that include the type (e.g., `id_to_name_dict`)

---

## Imports

### Import Rules
- Use `import x` for importing packages and modules
- Use `from x import y` where x is the package prefix and y is the module name
- Use `from x import y as z` when there are naming conflicts or y is inconveniently long
- Use `import y as z` only for standard abbreviations (e.g., `import numpy as np`)

### Import Formatting
**Description**: Imports should be on separate lines, grouped and sorted
**Order**:
1. Python future imports (`from __future__ import annotations`)
2. Python standard library imports
3. Third-party module imports
4. Local/project imports

**Example**:
```python
from __future__ import annotations

import os
import sys
from collections.abc import Mapping, Sequence
from typing import Any, TypeVar

import numpy as np
import tensorflow as tf
from absl import app
from absl import flags

from myproject.backend import huxley
from myproject.backend.state_machine import main_loop
```

### No Relative Imports
**Description**: Do not use relative names in imports; use the full package name
```python
# Yes
from mypackage.submodule import helper

# No
from .submodule import helper
```

---

## Formatting Standards

### Line Length
**Description**: Maximum line length is 80 characters
**Exceptions**:
- Long import statements
- URLs in comments
- Long string constants (paths, URLs)
- pylint disable comments

### Line Continuation
**Description**: Use implicit line joining inside parentheses, brackets, and braces; do not use backslash
```python
# Yes
foo_bar(self, width, height, color='black', design=None, x='foo',
        emphasis=None, highlight=0)

if (width == 0 and height == 0 and
        color == 'red' and emphasis == 'strong'):
    pass

# No (backslash)
if width == 0 and height == 0 and \
        color == 'red' and emphasis == 'strong':
    pass
```

### Indentation
**Description**: Use 4 spaces for indentation; never use tabs
```python
# Yes - Aligned with opening delimiter
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# Yes - 4-space hanging indent
foo = long_function_name(
    var_one, var_two, var_three,
    var_four
)

# No - 2-space indent
foo = long_function_name(
  var_one, var_two)
```

### Trailing Commas
**Description**: Use trailing commas only when closing bracket is on a new line
```python
# Yes
golomb4 = [
    0,
    1,
    4,
    6,
]

# No
golomb4 = [
    0,
    1,
    4,
    6,]
```

### Blank Lines
- Two blank lines between top-level definitions (functions, classes)
- One blank line between method definitions
- No blank line following a `def` line

### Whitespace
```python
# Yes - No space inside brackets
spam(ham[1], {'eggs': 2}, [])

# No
spam( ham[ 1 ], { 'eggs': 2 }, [ ] )

# Yes - Space after comma, not before
if x == 4:
    print(x, y)

# No
if x == 4 :
    print(x , y)

# Yes - Space around operators
x == 1

# No
x<1

# Yes - No space around = in keyword arguments
def complex(real, imag=0.0): return Magic(r=real, i=imag)

# Yes - Space around = when type annotation present
def complex(real, imag: float = 0.0): return Magic(r=real, i=imag)
```

### Semicolons
**Description**: Do not use semicolons to terminate lines or put multiple statements on one line

### Parentheses
**Description**: Use parentheses sparingly; not required for returns or simple conditions
```python
# Yes
if foo:
    bar()
return foo
return spam, beans

# No
if (x):
    bar()
return (foo)
```

---

## Type Annotations

### General Rules
- Annotate public APIs with type hints
- Use type checking tools like pytype or mypy
- Annotating `self` or `cls` is generally not necessary

### Type Annotations Required
**Description**: All public function parameters and return values must have type annotations
**Example**:
```python
def get_user(user_id: int) -> User | None:
    """Get user information."""
    pass

def process_items(items: list[dict[str, Any]]) -> tuple[int, list[str]]:
    """Process item list."""
    pass
```

### Use TypeAlias for Complex Types
```python
from typing import TypeAlias

_LossAndGradient: TypeAlias = tuple[tf.Tensor, tf.Tensor]
ComplexTFMap: TypeAlias = Mapping[str, _LossAndGradient]
```

### NoneType
**Description**: Use explicit `X | None` instead of implicit; use `Optional` for older Python
```python
# Yes (Python 3.10+)
def func(a: str | None = None) -> str:
    ...

# Yes (older Python)
def func(a: Optional[str] = None) -> str:
    ...

# No - implicit optional
def func(a: str = None) -> str:
    ...
```

### Forward Declarations
**Description**: Use `from __future__ import annotations` or string quotes for forward references
```python
from __future__ import annotations

class MyClass:
    def __init__(self, stack: Sequence[MyClass]) -> None:
        ...
```

### Type Variables
```python
from typing import TypeVar

_T = TypeVar("_T")
AddableType = TypeVar("AddableType", int, float, str)

def next_item(items: list[_T]) -> _T:
    return items.pop()
```

---

## Docstrings

### Format
**Description**: Always use triple double-quotes `"""` for docstrings (per PEP 257)

### Module Docstrings
```python
"""A one-line summary of the module or program, terminated by a period.

Leave one blank line. The rest of this docstring should contain an
overall description of the module or program.

Typical usage example:

    foo = ClassFoo()
    bar = foo.function_bar()
"""
```

### Function/Method Docstrings
**Description**: Required for public APIs, nontrivial size, or non-obvious logic
**Sections**: Args, Returns/Yields, Raises
```python
def fetch_smalltable_rows(
    table_handle: smalltable.Table,
    keys: Sequence[bytes | str],
    require_all_keys: bool = False,
) -> Mapping[bytes, tuple[str, ...]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle. String keys will be UTF-8 encoded.

    Args:
        table_handle: An open smalltable.Table instance.
        keys: A sequence of strings representing the key of each table
            row to fetch. String keys will be UTF-8 encoded.
        require_all_keys: If True only rows with values set for all keys
            will be returned.

    Returns:
        A dict mapping keys to the corresponding table row data fetched.
        Each row is represented as a tuple of strings.

    Raises:
        IOError: An error occurred accessing the smalltable.
    """
```

### Class Docstrings
```python
class SampleClass:
    """Summary of class here.

    Longer class information...

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """

    def __init__(self, likes_spam: bool = False):
        """Initializes the instance based on spam preference.

        Args:
            likes_spam: Defines if instance exhibits this preference.
        """
        self.likes_spam = likes_spam
        self.eggs = 0
```

### Overridden Methods
**Description**: Use `@override` decorator; docstring not required if behavior unchanged
```python
from typing_extensions import override

class Child(Parent):
    @override
    def do_something(self):
        pass
```

---

## String Formatting

### Prefer f-strings
**Description**: Use f-strings, % operator, or format method; prefer f-strings for readability
```python
# Yes
x = f'name: {name}; score: {n}'
x = '%s, %s!' % (imperative, expletive)
x = 'name: {}; score: {}'.format(name, n)

# No - string concatenation for formatting
x = 'name: ' + name + '; score: ' + str(n)
```

### String Accumulation
**Description**: Do not use `+` or `+=` to accumulate strings in a loop; use `''.join()` or `io.StringIO`
```python
# Yes
items = ['<table>']
for last_name, first_name in employee_list:
    items.append('<tr><td>%s, %s</td></tr>' % (last_name, first_name))
items.append('</table>')
employee_table = ''.join(items)

# No
employee_table = '<table>'
for last_name, first_name in employee_list:
    employee_table += '<tr><td>%s, %s</td></tr>' % (last_name, first_name)
employee_table += '</table>'
```

### Logging Strings
**Description**: Use pattern-string with %-placeholders for logging; not f-strings
```python
# Yes
logger.info('TensorFlow Version is: %s', tf.__version__)
logging.error('Cannot write to home directory, $HOME=%r', homedir)

# No
logging.info(f'TensorFlow Version is: {tf.__version__}')
```

### Quote Characters
**Description**: Be consistent within a file; pick `'` or `"` and stick with it
**Note**: Prefer `"""` for multi-line strings and docstrings

---

## Comprehensions & Generators

### List Comprehensions
**Description**: Allowed for simple cases; no multiple `for` clauses or complex filter expressions
```python
# Yes
result = [mapping_expr for value in iterable if filter_expr]

descriptive_name = [
    transform({'key': key, 'value': value}, color='black')
    for key, value in generate_iterable(some_input)
    if complicated_condition_is_met(key, value)
]

# No - multiple for clauses
result = [(x, y) for x in range(10) for y in range(5) if x * y > 10]
```

### Generators
**Description**: Use generators for large data sets; use "Yields:" in docstring
```python
def generate_items(data: list[int]) -> Iterator[int]:
    """Generates processed items.

    Yields:
        Processed integer values.
    """
    for item in data:
        yield item * 2
```

---

## Default Arguments

### Mutable Default Arguments
**Description**: Never use mutable objects as default values
```python
# Yes
def foo(a, b=None):
    if b is None:
        b = []

def foo(a, b: Sequence = ()):  # Empty tuple OK (immutable)
    ...

# No
def foo(a, b=[]):
    ...

def foo(a, b=time.time()):  # Evaluated at module load time
    ...
```

---

## Conditional Expressions

### Ternary Operator
**Description**: Okay for simple cases; each portion must fit on one line
```python
# Yes
one_line = 'yes' if predicate(value) else 'no'

the_longest_ternary_style_that_can_be_done = (
    'yes, true, affirmative, confirmed, correct'
    if predicate(value)
    else 'no, false, negative, nay'
)

# No
bad_line_breaking = ('yes' if predicate(value) else
                     'no')
```

---

## True/False Evaluations

### Implicit False
**Description**: Use implicit false for empty sequences and None checks
```python
# Yes
if not users:
    print('no users')

if foo is None:
    ...

# No
if len(users) == 0:
    print('no users')
```

### None Checks
**Description**: Always use `is None` or `is not None` to check for None
```python
# Yes
if foo is None:
    ...

# No
if foo == None:
    ...

if not foo:  # Could be False, 0, or empty
    ...
```

---

## Lambda Functions

### Usage
**Description**: Okay for one-liners; prefer named functions for complex logic
```python
# Yes - simple lambda
sorted(items, key=lambda x: x.name)

# Yes - use operator module for common operations
from operator import mul
functools.reduce(mul, numbers)

# No - complex lambda
lambda x, y: (x + y) * (x - y) / (x ** 2 + y ** 2)
```

---

## Default Iterators and Operators

### Use Built-in Iterators
```python
# Yes
for key in adict: ...
if obj in alist: ...
for line in afile: ...
for k, v in adict.items(): ...

# No
for key in adict.keys(): ...
for line in afile.readlines(): ...
```

---

## Properties

### Usage
**Description**: Use properties for trivial attribute access or computed values
```python
class Circle:
    def __init__(self, radius: float):
        self._radius = radius

    @property
    def radius(self) -> float:
        """The radius of the circle."""
        return self._radius

    @property
    def area(self) -> float:
        """The area of the circle."""
        return 3.14159 * self._radius ** 2
```

---

## Decorators

### Usage Rules
- Use decorators judiciously when there is a clear advantage
- Avoid `staticmethod`; use module-level functions instead
- Use `classmethod` only for named constructors or class-specific operations
- Write unit tests for decorators

---

## Exception Handling

### Exception Rules
- Make use of built-in exception classes when appropriate
- Do not use `assert` for validation; use `raise ValueError`
- Libraries should define their own exceptions inheriting from existing ones
- Exception names should end in `Error`

### Catch-All Exceptions
**Description**: Never use bare `except:` or catch `Exception` unless re-raising
```python
# Yes - specific exception
try:
    user = get_user(user_id)
except UserNotFoundError:
    return None

# Yes - re-raising
try:
    do_something()
except Exception:
    logger.exception('Unexpected error')
    raise

# No - bare except
try:
    do_something()
except:
    pass

# No - catching Exception without re-raising
try:
    do_something()
except Exception:
    pass
```

### Minimize try/except Block
**Description**: Keep try blocks small to avoid hiding real errors
```python
# Yes
try:
    value = collection[key]
except KeyError:
    return default

# No - too much code in try block
try:
    value = collection[key]
    result = process(value)
    save(result)
    return result
except KeyError:
    return default
```

### Use finally for Cleanup
```python
try:
    file = open('data.txt')
    process(file)
finally:
    file.close()
```

### Custom Exceptions
```python
class BusinessError(Exception):
    """Base exception for business logic errors."""

    def __init__(self, code: int, message: str):
        self.code = code
        self.message = message
        super().__init__(message)


class UserNotFoundError(BusinessError):
    """Raised when a user is not found."""

    def __init__(self, user_id: int):
        super().__init__(1001, f"User {user_id} not found")
```

---

## Files and Resources

### Use Context Managers
**Description**: Explicitly close files and sockets; use `with` statement
```python
# Yes
with open("hello.txt") as hello_file:
    for line in hello_file:
        print(line)

# Yes - for objects without context manager support
import contextlib

with contextlib.closing(urllib.urlopen("http://www.python.org/")) as page:
    for line in page:
        print(line)
```

---

## TODO Comments

### Format
**Description**: Use TODO with a link to a resource (bug reference preferred)
```python
# Yes
# TODO: crbug.com/192795 - Investigate cpufreq optimizations.
# TODO: b/123456789 - Remove this workaround after API v2 release.

# No - referring to individual
# TODO(yourusername): Fix this later.
```

---

## Main Function

### Module Entry Point
**Description**: Use `if __name__ == '__main__'` guard for executable modules
```python
def main():
    ...

if __name__ == '__main__':
    main()
```

### With absl
```python
from absl import app

def main(argv: Sequence[str]):
    # process non-flag arguments
    ...

if __name__ == '__main__':
    app.run(main)
```

---

## Function Length

### Keep Functions Small
**Description**: Prefer small and focused functions; if exceeds 40 lines, consider breaking up
**Rationale**: Easier to read, test, and maintain

---

## Mutable Global State

### Avoid Global State
**Description**: Avoid mutable global state; use module-level constants instead
```python
# Yes - constants are fine
_MAX_HOLY_HANDGRENADE_COUNT = 3
SIR_LANCELOTS_FAVORITE_COLOR = "blue"

# No - mutable global
_current_user = None  # Avoid this pattern
```

---

## Nested Classes and Functions

### Usage Rules
**Description**: Avoid nested functions except when closing over a local value
```python
# Yes - closing over local variable
def make_adder(x: int) -> Callable[[int], int]:
    def adder(y: int) -> int:
        return x + y
    return adder

# No - just to hide function
def outer():
    def inner():  # Should be module-level with _ prefix
        ...
```

---

## Threading

### Thread Safety
**Description**: Do not rely on atomicity of built-in types
```python
# Yes - use Queue for thread communication
from queue import Queue

task_queue: Queue[Task] = Queue()

# Yes - use locks for shared state
import threading

lock = threading.Lock()
with lock:
    shared_resource.update()
```

---

## Power Features

### Avoid Advanced Features
**Description**: Avoid metaclasses, bytecode access, dynamic inheritance, import hacks, etc.
**Rationale**: Harder to read, understand, and debug

---

## Async Programming Standards

### async/await Usage
**Description**: Use async for I/O-intensive operations, use multiprocessing for CPU-intensive operations
```python
async def fetch_data(urls: list[str]) -> list[dict]:
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        return await asyncio.gather(*tasks)
```

### Avoid Blocking Calls
**Description**: Using time.sleep() in async functions is prohibited; use asyncio.sleep()

---

## Python Database Standards

### ORM Usage
**Description**: Prefer ORM (SQLAlchemy/Django ORM); use raw SQL only for complex queries

### Transaction Management
```python
async with session.begin():
    user = User(name=name)
    session.add(user)
    # Auto commit or rollback
```

### N+1 Query Problem
**Description**: Use joinedload/selectinload to preload related data
```python
# Correct
users = await session.execute(
    select(User).options(selectinload(User.orders))
)

# Wrong: N+1 query
for user in users:
    print(user.orders)  # Queries on each iteration
```

---

## API Design Standards

### RESTful Standards
- GET: Retrieve resource
- POST: Create resource
- PUT: Full update
- PATCH: Partial update
- DELETE: Delete resource

### Response Format
```python
# Success response
{
    "code": 0,
    "message": "success",
    "data": { ... }
}

# Error response
{
    "code": 1001,
    "message": "User not found",
    "data": null
}
```

### Pagination Format
```python
{
    "code": 0,
    "data": {
        "items": [...],
        "total": 100,
        "page": 1,
        "page_size": 20
    }
}

---

# Frontend Standards (JavaScript/TypeScript)

> Based on Airbnb JavaScript Style Guide

---

## References (Variables)

### Prefer const
**Description**: Use `const` for all references; avoid `var`. eslint: `prefer-const`, `no-const-assign`
```javascript
// bad
var a = 1;
var b = 2;

// good
const a = 1;
const b = 2;
```

### Use let for Reassignment
**Description**: If you must reassign, use `let` instead of `var`. eslint: `no-var`
```javascript
// bad
var count = 1;
if (true) {
  count += 1;
}

// good
let count = 1;
if (true) {
  count += 1;
}
```

### Block Scope
**Description**: `let` and `const` are block-scoped; `var` is function-scoped
```javascript
{
  let a = 1;
  const b = 1;
  var c = 1;
}
console.log(a); // ReferenceError
console.log(b); // ReferenceError
console.log(c); // 1
```

---

## Objects

### Literal Syntax
**Description**: Use literal syntax for object creation. eslint: `no-new-object`
```javascript
// bad
const item = new Object();

// good
const item = {};
```

### Computed Properties
**Description**: Use computed property names when creating objects with dynamic keys
```javascript
function getKey(k) {
  return `a key named ${k}`;
}

// bad
const obj = {
  id: 5,
  name: 'San Francisco',
};
obj[getKey('enabled')] = true;

// good
const obj = {
  id: 5,
  name: 'San Francisco',
  [getKey('enabled')]: true,
};
```

### Method Shorthand
**Description**: Use object method shorthand. eslint: `object-shorthand`
```javascript
// bad
const atom = {
  value: 1,
  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  value: 1,
  addValue(value) {
    return atom.value + value;
  },
};
```

### Property Shorthand
**Description**: Use property value shorthand
```javascript
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
  lukeSkywalker: lukeSkywalker,
};

// good
const obj = {
  lukeSkywalker,
};
```

### Group Shorthand Properties
**Description**: Group shorthand properties at the beginning
```javascript
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
  episodeOne: 1,
  lukeSkywalker,
  episodeThree: 3,
  anakinSkywalker,
};

// good
const obj = {
  lukeSkywalker,
  anakinSkywalker,
  episodeOne: 1,
  episodeThree: 3,
};
```

### Quote Properties
**Description**: Only quote properties that are invalid identifiers. eslint: `quote-props`
```javascript
// bad
const bad = {
  'foo': 3,
  'bar': 4,
  'data-blah': 5,
};

// good
const good = {
  foo: 3,
  bar: 4,
  'data-blah': 5,
};
```

### Spread Operator
**Description**: Prefer object spread over `Object.assign`. eslint: `prefer-object-spread`
```javascript
// bad
const original = { a: 1, b: 2 };
const copy = Object.assign({}, original, { c: 3 });

// good
const original = { a: 1, b: 2 };
const copy = { ...original, c: 3 };

const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
```

---

## Arrays

### Literal Syntax
**Description**: Use literal syntax for array creation. eslint: `no-array-constructor`
```javascript
// bad
const items = new Array();

// good
const items = [];
```

### Use push()
**Description**: Use Array#push instead of direct assignment
```javascript
const someStack = [];

// bad
someStack[someStack.length] = 'abracadabra';

// good
someStack.push('abracadabra');
```

### Spread for Copy
**Description**: Use array spreads `...` to copy arrays
```javascript
// bad
const itemsCopy = [];
for (let i = 0; i < items.length; i += 1) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```

### Array.from for Array-like
**Description**: Use `Array.from` for converting array-like objects
```javascript
const arrLike = { 0: 'foo', 1: 'bar', length: 2 };

// bad
const arr = Array.prototype.slice.call(arrLike);

// good
const arr = Array.from(arrLike);
```

### Callback Return
**Description**: Use return statements in array method callbacks. eslint: `array-callback-return`
```javascript
// bad - no returned value
[[0, 1], [2, 3]].reduce((acc, item) => {
  const flatten = acc.concat(item);
});

// good
[[0, 1], [2, 3]].reduce((acc, item) => {
  const flatten = acc.concat(item);
  return flatten;
}, []);

// good - implicit return
[1, 2, 3].map((x) => x + 1);
```

---

## Destructuring

### Object Destructuring
**Description**: Use object destructuring when accessing multiple properties. eslint: `prefer-destructuring`
```javascript
// bad
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;
  return `${firstName} ${lastName}`;
}

// good
function getFullName(user) {
  const { firstName, lastName } = user;
  return `${firstName} ${lastName}`;
}

// best
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}
```

### Array Destructuring
```javascript
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```

### Object for Multiple Returns
**Description**: Use object destructuring for multiple return values
```javascript
// bad
function processInput(input) {
  return [left, right, top, bottom];
}
const [left, __, top] = processInput(input);

// good
function processInput(input) {
  return { left, right, top, bottom };
}
const { left, top } = processInput(input);
```

---

## Strings

### Single Quotes
**Description**: Use single quotes `''` for strings. eslint: `quotes`
```javascript
// bad
const name = "Capt. Janeway";
const name = `Capt. Janeway`; // template literals should contain interpolation

// good
const name = 'Capt. Janeway';
```

### Template Literals
**Description**: Use template strings for string building. eslint: `prefer-template`
```javascript
// bad
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// good
function sayHi(name) {
  return `How are you, ${name}?`;
}
```

### No eval()
**Description**: Never use `eval()` on a string. eslint: `no-eval`

### No Unnecessary Escapes
**Description**: Do not unnecessarily escape characters. eslint: `no-useless-escape`
```javascript
// bad
const foo = '\'this\' \i\s \"quoted\"';

// good
const foo = '\'this\' is "quoted"';
const foo = `my name is '${name}'`;
```

---

## Functions

### Named Function Expressions
**Description**: Use named function expressions instead of declarations. eslint: `func-style`
```javascript
// bad
function foo() {
  // ...
}

// good
const foo = function longUniqueMoreDescriptiveName() {
  // ...
};
```

### No Function in Non-function Block
**Description**: Never declare a function in a non-function block (`if`, `while`, etc.). eslint: `no-loop-func`
```javascript
// bad
if (currentUser) {
  function test() {
    console.log('Nope.');
  }
}

// good
let test;
if (currentUser) {
  test = () => {
    console.log('Yup.');
  };
}
```

### Rest Parameters
**Description**: Never use `arguments`; use rest syntax `...` instead. eslint: `prefer-rest-params`
```javascript
// bad
function concatenateAll() {
  const args = Array.prototype.slice.call(arguments);
  return args.join('');
}

// good
function concatenateAll(...args) {
  return args.join('');
}
```

### Default Parameters
**Description**: Use default parameter syntax rather than mutating arguments
```javascript
// bad
function handleThings(opts) {
  opts = opts || {};
}

// good
function handleThings(opts = {}) {
  // ...
}
```

### Defaults Last
**Description**: Always put default parameters last. eslint: `default-param-last`
```javascript
// bad
function handleThings(opts = {}, name) {
  // ...
}

// good
function handleThings(name, opts = {}) {
  // ...
}
```

### No Parameter Mutation
**Description**: Never mutate or reassign parameters. eslint: `no-param-reassign`
```javascript
// bad
function f1(obj) {
  obj.key = 1;
}

function f2(a) {
  a = 1;
}

// good
function f1(obj) {
  const key = Object.hasOwn(obj, 'key') ? obj.key : 1;
}

function f2(a) {
  const b = a || 1;
}
```

### Spread for Variadic
**Description**: Prefer spread syntax to call variadic functions. eslint: `prefer-spread`
```javascript
// bad
const x = [1, 2, 3, 4, 5];
console.log.apply(console, x);

// good
const x = [1, 2, 3, 4, 5];
console.log(...x);

// bad
new (Function.prototype.bind.apply(Date, [null, 2016, 8, 5]));

// good
new Date(...[2016, 8, 5]);
```

---

## Arrow Functions

### Use for Callbacks
**Description**: Use arrow functions for inline callbacks. eslint: `prefer-arrow-callback`
```javascript
// bad
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

// good
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

### Implicit Return
**Description**: Omit braces and use implicit return for single expressions. eslint: `arrow-body-style`
```javascript
// bad
[1, 2, 3].map((number) => {
  const nextNumber = number + 1;
  `A string containing the ${nextNumber}.`;
});

// good
[1, 2, 3].map((number) => `A string containing the ${number + 1}.`);

// good - with side effects, use braces
[1, 2, 3].map((number) => {
  const nextNumber = number + 1;
  return `A string containing the ${nextNumber}.`;
});
```

### Always Use Parentheses
**Description**: Always include parentheses around arguments. eslint: `arrow-parens`
```javascript
// bad
[1, 2, 3].map(x => x * x);

// good
[1, 2, 3].map((x) => x * x);
```

### Avoid Confusion with Comparisons
**Description**: Wrap expressions with comparisons in parentheses. eslint: `no-confusing-arrow`
```javascript
// bad
const itemHeight = (item) => item.height <= 256 ? item.largeSize : item.smallSize;

// good
const itemHeight = (item) => (item.height <= 256 ? item.largeSize : item.smallSize);
```

---

## Classes & Constructors

### Use class Syntax
**Description**: Always use `class`. Avoid manipulating `prototype` directly.
```javascript
// bad
function Queue(contents = []) {
  this.queue = [...contents];
}
Queue.prototype.pop = function () {
  const value = this.queue[0];
  this.queue.splice(0, 1);
  return value;
};

// good
class Queue {
  constructor(contents = []) {
    this.queue = [...contents];
  }
  pop() {
    const value = this.queue[0];
    this.queue.splice(0, 1);
    return value;
  }
}
```

### Use extends
**Description**: Use `extends` for inheritance
```javascript
// bad
const inherits = require('inherits');
function PeekableQueue(contents) {
  Queue.apply(this, contents);
}
inherits(PeekableQueue, Queue);

// good
class PeekableQueue extends Queue {
  peek() {
    return this.queue[0];
  }
}
```

### Method Chaining
**Description**: Methods can return `this` to help with method chaining
```javascript
// good
class Jedi {
  jump() {
    this.jumping = true;
    return this;
  }

  setHeight(height) {
    this.height = height;
    return this;
  }
}

const luke = new Jedi();
luke.jump().setHeight(20);
```

### No Useless Constructor
**Description**: Empty constructors or those that just delegate are unnecessary. eslint: `no-useless-constructor`
```javascript
// bad
class Jedi {
  constructor() {}
}

class Rey extends Jedi {
  constructor(...args) {
    super(...args);
  }
}

// good
class Rey extends Jedi {
  constructor(...args) {
    super(...args);
    this.name = 'Rey';
  }
}
```

### Methods Should Use this
**Description**: Class methods should use `this` or be made static. eslint: `class-methods-use-this`

---

## Modules

### Use ES6 Modules
**Description**: Always use modules (`import`/`export`) over non-standard systems
```javascript
// bad
const AirbnbStyleGuide = require('./AirbnbStyleGuide');
module.exports = AirbnbStyleGuide.es6;

// good
import { es6 } from './AirbnbStyleGuide';
export default es6;
```

### No Wildcard Imports
**Description**: Do not use wildcard imports
```javascript
// bad
import * as AirbnbStyleGuide from './AirbnbStyleGuide';

// good
import AirbnbStyleGuide from './AirbnbStyleGuide';
```

### No Duplicate Imports
**Description**: Only import from a path in one place. eslint: `no-duplicate-imports`
```javascript
// bad
import foo from 'foo';
import { named1, named2 } from 'foo';

// good
import foo, { named1, named2 } from 'foo';
```

### No Mutable Exports
**Description**: Do not export mutable bindings. eslint: `import/no-mutable-exports`
```javascript
// bad
let foo = 3;
export { foo };

// good
const foo = 3;
export { foo };
```

### Imports First
**Description**: Put all `import`s above non-import statements. eslint: `import/first`
```javascript
// bad
import foo from 'foo';
foo.init();
import bar from 'bar';

// good
import foo from 'foo';
import bar from 'bar';

foo.init();
```

### No Filename Extensions
**Description**: Do not include JavaScript filename extensions. eslint: `import/extensions`
```javascript
// bad
import foo from './foo.js';
import bar from './bar.jsx';

// good
import foo from './foo';
import bar from './bar';
```

---

## Iterators and Generators

### Prefer Higher-Order Functions
**Description**: Use higher-order functions instead of loops. eslint: `no-iterator`
```javascript
const numbers = [1, 2, 3, 4, 5];

// bad
let sum = 0;
for (let num of numbers) {
  sum += num;
}

// good
const sum = numbers.reduce((total, num) => total + num, 0);

// bad
const increasedByOne = [];
for (let i = 0; i < numbers.length; i++) {
  increasedByOne.push(numbers[i] + 1);
}

// good
const increasedByOne = numbers.map((num) => num + 1);
```

---

## Variables

### One Declaration Per Variable
**Description**: Use one `const` or `let` declaration per variable. eslint: `one-var`
```javascript
// bad
const items = getItems(),
    goSportsTeam = true,
    dragonball = 'z';

// good
const items = getItems();
const goSportsTeam = true;
const dragonball = 'z';
```

### Group const and let
**Description**: Group all `const`s and then group all `let`s
```javascript
// bad
let i;
const items = getItems();
let dragonball;
const goSportsTeam = true;

// good
const goSportsTeam = true;
const items = getItems();
let dragonball;
let i;
```

### No Chain Assignment
**Description**: Don't chain variable assignments. eslint: `no-multi-assign`
```javascript
// bad - creates implicit globals
let a = b = c = 1;

// good
let a = 1;
let b = a;
let c = a;
```

### Avoid ++ and --
**Description**: Avoid unary increments and decrements. eslint: `no-plusplus`
```javascript
// bad
let num = 1;
num++;

// good
let num = 1;
num += 1;
```

### No Unused Variables
**Description**: Disallow unused variables. eslint: `no-unused-vars`

---

## Comparison Operators & Equality

### Use === and !==
**Description**: Use `===` and `!==` over `==` and `!=`. eslint: `eqeqeq`

### Shortcuts for Booleans
**Description**: Use shortcuts for booleans, but explicit comparisons for strings and numbers
```javascript
// bad
if (isValid === true) { }
if (name) { }
if (collection.length) { }

// good
if (isValid) { }
if (name !== '') { }
if (collection.length > 0) { }
```

### Braces in Switch Cases
**Description**: Use braces for `case` clauses with lexical declarations. eslint: `no-case-declarations`
```javascript
// bad
switch (foo) {
  case 1:
    let x = 1;
    break;
  default:
    class C {}
}

// good
switch (foo) {
  case 1: {
    let x = 1;
    break;
  }
  default: {
    class C {}
  }
}
```

### No Nested Ternaries
**Description**: Ternaries should not be nested. eslint: `no-nested-ternary`
```javascript
// bad
const foo = maybe1 > maybe2
  ? 'bar'
  : value1 > value2 ? 'baz' : null;

// good
const maybeNull = value1 > value2 ? 'baz' : null;
const foo = maybe1 > maybe2 ? 'bar' : maybeNull;
```

### Nullish Coalescing
**Description**: Use `??` for null/undefined checks
```javascript
// good
const value = null ?? 'default'; // returns 'default'
const age = user.age ?? 18;
```

---

## Blocks

### Braces for Multiline
**Description**: Use braces with all multiline blocks. eslint: `nonblock-statement-body-position`
```javascript
// bad
if (test)
  return false;

// good
if (test) return false;

// good
if (test) {
  return false;
}
```

### Cuddled Elses
**Description**: Put `else` on the same line as `if` block's closing brace. eslint: `brace-style`
```javascript
// bad
if (test) {
  thing1();
}
else {
  thing3();
}

// good
if (test) {
  thing1();
} else {
  thing3();
}
```

### No Unnecessary Else
**Description**: If `if` always returns, subsequent `else` is unnecessary. eslint: `no-else-return`
```javascript
// bad
function foo() {
  if (x) {
    return x;
  } else {
    return y;
  }
}

// good
function foo() {
  if (x) {
    return x;
  }
  return y;
}
```

---

## Comments

### Multiline Comments
**Description**: Use `/** ... */` for multiline comments
```javascript
// bad
// make() returns a new element
// based on the passed in tag name
function make(tag) { }

// good
/**
 * make() returns a new element
 * based on the passed-in tag name
 */
function make(tag) { }
```

### Single Line Comments
**Description**: Use `//` for single line comments; place above the subject with empty line before
```javascript
// bad
const active = true;  // is current tab

// good
// is current tab
const active = true;
```

### FIXME and TODO
**Description**: Use `// FIXME:` for problems and `// TODO:` for solutions
```javascript
// FIXME: shouldn't use a global here
total = 0;

// TODO: total should be configurable by an options param
this.total = 0;
```

---

## Whitespace

### Soft Tabs
**Description**: Use soft tabs (2 spaces). eslint: `indent`
```javascript
// bad
function foo() {
∙∙∙∙let name;
}

// good
function baz() {
∙∙let name;
}
```

### Space Before Blocks
**Description**: Place 1 space before the leading brace. eslint: `space-before-blocks`
```javascript
// bad
function test(){
  console.log('test');
}

// good
function test() {
  console.log('test');
}
```

### Space Around Keywords
**Description**: Place 1 space before `(` in control statements, no space in function calls. eslint: `keyword-spacing`
```javascript
// bad
if(isJedi) {
  fight ();
}

// good
if (isJedi) {
  fight();
}
```

### Infix Operators
**Description**: Set off operators with spaces. eslint: `space-infix-ops`
```javascript
// bad
const x=y+5;

// good
const x = y + 5;
```

### Newline at End
**Description**: End files with a single newline character. eslint: `eol-last`

### Method Chaining Indentation
**Description**: Use indentation for long method chains (>2)
```javascript
// bad
$('#items').find('.selected').highlight().end().find('.open').updateCount();

// good
$('#items')
  .find('.selected')
    .highlight()
    .end()
  .find('.open')
    .updateCount();
```

### Max Line Length
**Description**: Avoid lines longer than 100 characters. eslint: `max-len`

### No Space Inside Parens/Brackets
```javascript
// bad
function bar( foo ) { }
const foo = [ 1, 2, 3 ];

// good
function bar(foo) { }
const foo = [1, 2, 3];
```

### Space Inside Braces
**Description**: Add spaces inside curly braces. eslint: `object-curly-spacing`
```javascript
// bad
const foo = {clark: 'kent'};

// good
const foo = { clark: 'kent' };
```

---

## Commas

### Trailing Commas
**Description**: Use trailing commas for cleaner git diffs. eslint: `comma-dangle`
```javascript
// bad
const hero = {
  firstName: 'Dana',
  lastName: 'Scully'
};

// good
const hero = {
  firstName: 'Dana',
  lastName: 'Scully',
};
```

### No Leading Commas
**Description**: Leading commas: **Nope.** eslint: `comma-style`
```javascript
// bad
const story = [
    once
  , upon
  , aTime
];

// good
const story = [
  once,
  upon,
  aTime,
];
```

---

## Semicolons

### Required
**Description**: **Yup.** eslint: `semi`
```javascript
// bad
const luke = {}
const leia = {}
[luke, leia].forEach((jedi) => jedi.father = 'vader')

// good
const luke = {};
const leia = {};
[luke, leia].forEach((jedi) => {
  jedi.father = 'vader';
});
```

---

## Type Casting & Coercion

### Strings
**Description**: Use `String()` for type coercion. eslint: `no-new-wrappers`
```javascript
// bad
const totalScore = new String(this.reviewScore);
const totalScore = this.reviewScore + '';

// good
const totalScore = String(this.reviewScore);
```

### Numbers
**Description**: Use `Number()` or `parseInt()` with radix. eslint: `radix`
```javascript
const inputValue = '4';

// bad
const val = new Number(inputValue);
const val = +inputValue;
const val = parseInt(inputValue);

// good
const val = Number(inputValue);
const val = parseInt(inputValue, 10);
```

### Booleans
```javascript
const age = 0;

// bad
const hasAge = new Boolean(age);

// good
const hasAge = Boolean(age);

// best
const hasAge = !!age;
```

---

## Naming Conventions

### Be Descriptive
**Description**: Avoid single letter names. Be descriptive. eslint: `id-length`
```javascript
// bad
function q() { }

// good
function query() { }
```

### camelCase
**Description**: Use camelCase for objects, functions, instances. eslint: `camelcase`
```javascript
// bad
const OBJEcttsssss = {};
const this_is_my_object = {};

// good
const thisIsMyObject = {};
function thisIsMyFunction() {}
```

### PascalCase
**Description**: Use PascalCase for constructors and classes. eslint: `new-cap`
```javascript
// bad
function user(options) {
  this.name = options.name;
}
const bad = new user({ name: 'nope' });

// good
class User {
  constructor(options) {
    this.name = options.name;
  }
}
const good = new User({ name: 'yup' });
```

### No Underscores
**Description**: Do not use trailing or leading underscores. eslint: `no-underscore-dangle`
```javascript
// bad
this.__firstName__ = 'Panda';
this.firstName_ = 'Panda';
this._firstName = 'Panda';

// good
this.firstName = 'Panda';
```

### No this References
**Description**: Don't save references to `this`. Use arrow functions or bind.
```javascript
// bad
function foo() {
  const self = this;
  return function () {
    console.log(self);
  };
}

// good
function foo() {
  return () => {
    console.log(this);
  };
}
```

### Filename Matches Export
**Description**: A base filename should match its default export
```javascript
// file: CheckBox.js
class CheckBox { }
export default CheckBox;

// in another file
import CheckBox from './CheckBox'; // ✓
import CheckBox from './checkBox'; // ✗
```

### UPPERCASE for Exported Constants
**Description**: Uppercase constants only if exported and truly constant
```javascript
// bad
const PRIVATE_VARIABLE = 'should not be uppercased';

// good
export const API_KEY = 'SOMEKEY';

// good
export const MAPPING = {
  key: 'value',
};
```

---

## Component Standards

### Component Naming
**Convention**: PascalCase, file name should match component name
**Correct**: UserProfile.tsx, OrderList.vue
**Incorrect**: userProfile.tsx, order-list.vue

### Component Size
**Description**: Single component should not exceed 300 lines; split if exceeded

### Props Definition
**Description**: Must define Props types with documentation comments
**Example (React)**:
```typescript
interface UserCardProps {
  /** User ID */
  userId: number;
  /** Whether to show avatar */
  showAvatar?: boolean;
  /** Click callback */
  onClick?: (userId: number) => void;
}

const UserCard: React.FC<UserCardProps> = ({ userId, showAvatar = true, onClick }) => {
  // ...
};
```

**Example (Vue)**:
```typescript
defineProps<{
  /** User ID */
  userId: number;
  /** Whether to show avatar */
  showAvatar?: boolean;
}>();
```

---

## React Standards

### Hooks Usage Rules
- Only call Hooks at the top level
- Only call Hooks from function components or custom Hooks

### Dependency Arrays
**Description**: useEffect/useMemo/useCallback must correctly declare dependencies
```typescript
// Correct
useEffect(() => {
  fetchUser(userId);
}, [userId]);

// Wrong: Missing dependency
useEffect(() => {
  fetchUser(userId);
}, []);
```

### State Management
- Component-level state: useState
- Cross-component sharing: Context / Zustand / Redux
- Server state: React Query / SWR

### Avoid Unnecessary Renders
```typescript
// Use memo to avoid unnecessary renders
const UserCard = memo(({ user }: { user: User }) => {
  return <div>{user.name}</div>;
});

// Use useMemo to cache computed results
const sortedItems = useMemo(
  () => items.sort((a, b) => a.name.localeCompare(b.name)),
  [items]
);
```

---

## Vue Standards

### Composition API First
**Description**: Use Composition API for new projects; avoid Options API

### Reactivity Declaration
```typescript
// Use ref for primitive types
const count = ref(0);

// Use reactive for objects
const state = reactive({
  user: null,
  loading: false,
});
```

### Component Communication
- Props: Parent to child
- Emit: Child to parent
- Provide/Inject: Cross-level
- Pinia: Global state

---

## CSS/Styling Standards

### Naming Conventions
**Convention**: BEM methodology or CSS Modules
**BEM Example**: .user-card__avatar--large

### Avoid Global Styles
**Description**: Use scoped/CSS Modules/CSS-in-JS

### CSS Variables
```css
:root {
  --color-primary: #1890ff;
  --color-error: #ff4d4f;
  --spacing-sm: 8px;
  --spacing-md: 16px;
}

.button {
  background: var(--color-primary);
  padding: var(--spacing-sm) var(--spacing-md);
}
```

### Responsive Design
**Description**: Use mobile-first strategy
```css
.container {
  padding: 16px;
}

@media (min-width: 768px) {
  .container {
    padding: 24px;
  }
}
```

---

## TypeScript Standards

### Strict Mode
**Description**: tsconfig must enable strict mode

### Type Definitions
**Description**: Avoid using `any`; use `unknown` or specific types
```typescript
// Correct
function parseJSON(text: string): unknown {
  return JSON.parse(text);
}

// Wrong
function parseJSON(text: string): any {
  return JSON.parse(text);
}
```

### Interface vs Type
**Description**: Prefer interface for object types; use type for union types
```typescript
// Object types
interface User {
  id: number;
  name: string;
}

// Union types
type Status = 'pending' | 'success' | 'error';
type Result<T> = { success: true; data: T } | { success: false; error: string };
```

### Enum Usage
**Description**: Prefer const objects or union types; avoid numeric enums
```typescript
// Recommended
const Status = {
  Pending: 'pending',
  Success: 'success',
  Error: 'error',
} as const;

type Status = typeof Status[keyof typeof Status];

// Or use union types
type Status = 'pending' | 'success' | 'error';
```

---

## Frontend Performance Standards

### Image Optimization
- Use WebP format
- Implement lazy loading
- Provide multi-resolution images

### Code Splitting
**Description**: Route-level code splitting
```typescript
// React
const UserPage = lazy(() => import('./pages/UserPage'));

// Vue
const UserPage = () => import('./pages/UserPage.vue');
```

### Request Optimization
- Merge API calls to reduce request count
- Use caching strategies
- Implement request cancellation (prevent race conditions)

### List Optimization
**Description**: Use virtual scrolling for long lists
**Example**: Use react-virtualized or vue-virtual-scroller

---

## Frontend Security Standards

### XSS Protection
**Description**: Do not use dangerouslySetInnerHTML/v-html; sanitize when necessary
```typescript
import DOMPurify from 'dompurify';

const safeHTML = DOMPurify.sanitize(userInput);
```

### CSRF Protection
**Description**: Include CSRF Token with requests

### Sensitive Information
**Description**: Do not store sensitive information in frontend; use httpOnly Cookie for tokens

---

## Testing Standards

### Write Tests
- Use Jest, Mocha, or Vitest for testing
- Strive to write many small pure functions
- Be cautious about stubs and mocks

### Test Coverage
**Description**: 100% test coverage is a good goal
**Rule**: Whenever you fix a bug, write a regression test

---

Please strictly follow the above coding standards in all code writing and modification work.
