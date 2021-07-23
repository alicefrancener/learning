# 🐍 Python

## Concepts

### Underscores in Python
[The Meaning of Underscores in Python](https://dbader.org/blog/meaning-of-underscores-in-python)
[PEP* Naming Conventions](https://pep8.org/#descriptive-naming-styles)
[Understanding the underscore( _ ) of Python](https://hackernoon.com/understanding-the-underscore-of-python-309d1a029edc)

- Single Leading Underscore: `_var`
  - convention
  - weak "internal use" indicator
  - impact how names get imported from modules (`from M import *` does not import objects whose name starts with an underscore)
- Single Trailing Underscore: `var_`
  - used by convention to avoid conflicts with Python keyword (`class_`)
- Double Leading Underscore: `__var`
  - when naming a class attribute, invokes name mangling (inside class `FooBar`, `__boo` becomes `_FooBar__boo`)
- Double Leading and Trailing Underscore: `__var__`
  - “magic” objects or attributes that live in user-controlled namespaces
  - name mangling is not applied if a name starts and ends with double underscores
  - called "dunders" (double underscore)
- Single Underscore: _
  - used as a name for temporary or insignificant variable
  - the resulto of the last expression in a Python REPL 


## Bookmarks

- [Real Python](https://realpython.com/)
- [Full Stack Python](https://www.fullstackpython.com/)
- [Python Tips](https://book.pythontips.com/en/latest/)
