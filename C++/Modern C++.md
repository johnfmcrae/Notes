# Modern C++

## Auto Almost Always

Whenever possible, use the `**auto**` keyword to initialize data. Benefits include:

- Requires value initialization (cannot write `auto i;`)
- Ensures correct type
- Makes code cleaner when long types are required
- Promotes programming to interfaces over implementations

## Uniform Initialization

```cpp
std::string s1("test");   // direct initialization 
std::string s2 = "test";  // copy initialization

T object {other};   // direct list initialization 
T object = {other}; // copy list initialization
```
