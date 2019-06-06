# Objects
-	Every object has identity, type and value
-	Identity never changes, id() is used to get identity
-	type determines behaviour and state of the object, type() is used to get type
-	Object's type can't be changed, it can but not advised
-	Depending on value changes or not objects can be of two types
	-	Mutable - whose value can be changed
	-	Immutable - whose value cannot be changed, and immutable object can have mutable objects whose value can be changed
	-	Mutability is determined by the type of object
-	Objects can become unreachable but not destroyed they are garbage-collected

## Containers
- They contain links/references to other objects, e.g. tuples, lists, dictionaries.
- An immutable container like tuple can have mutable objects like lists.
- The id() of values of tuples will not chage but the value of values of tuple may change.

## Type Hierarchy
### None
- Used to signify the absence of any value.
- Accessed through built-in name `None`.
- It's truth value is False.
### NotImplemented
- Used to signify that a particular function is not doing what they were meant to do.
- Accessed through built-in name `NotImplemented`.
- It's truth value is True.
### Ellipsis
- Accessed through `...` or built-in name `Ellipsis`.
- It's truth value is True.
### numbers.Number
- Created by numeric literals
- Immutable
- numbers.Integral
  - Set of integers
  - Two types
    - Integers(`int`)
      - It's value is subject to memory.
      - Binary representation.
      - Negatives are in 2's complement.
    - Booleans(`bool`)
      - Either `True` or `False`.
      - Subtype of Integers, `False = 0`, and `True = 1`.
- numbers.Real(`float`)
  - Double precision floating point numbers
- numbers.Complex(`complex`)
  - A pair of double precision floating point numbers.
  - Real and imaginary part of `z` can be accessed using `z.real` and `z.imag` respectively.
### Sequences
- Finite ordered sets indexed by non-negative numbers.
- `len()` represents number of items of a sequence.
- Index start from `0 to len()-1`.
- Item *i* of sequence *a* is selected by `a[i]`.
- Slicing is done using `a[i:j]` meaining for all k satisfying `i<=k<j`. It generates a new sequence.
- **Immutable Sequences**
  - Object of an immutable sequence cannot change. Further referenced objects may be mutable.
  - **String**
    - Represented by `str`.
    - Sequence of Unicode code points which fall in range `U+0000 - U+10FFFF`.
    - `ord()` converts string to its integer range `0 - 10FFFF`
    - `chr()` converts integer in range `0 - 10FFFF` to string.
    - `str.encode()` is used to convert `str` to `bytes`, provided the text_encoding.
    - `bytes.decode()` is used to convert `bytes` to `str`.
  - **Tuples**
    - Represnted by `tuple`.
    - Comma seperated arbitrary objects enclosed in paranteses `(a, b, c)`. It can be empty.
  - **Bytes**
    - Represented by `bytes`.
    - Array of 8-bit numbers in the range `0<=x<256`.
    - `b'234'` or `bytes()` can be used to create bytes objects.
    - `decode()` is used to create `str` from `bytes`.
- **Mutable Sequences**
  - Can be changed
  - **Lists**
    - Represented by `list`.
    - Created by comma seperated arbitrary objects in square brackets `[a, b, c]`. It can be empty.
  - **Byet Arrays**
    - Represented by `bytearray`.
    - Created by `bytearray()` constructor.
