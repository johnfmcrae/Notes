# Optional

Use for returns that may or may not be present. Include with `<optional>` Example:

```cpp
#include <iostream>
#include <optional>
#include <string>
 
// optional can be used as the return type of a factory that may fail
std::optional<std::string> create(bool b)
{
    if (b)
        return "Godzilla";
    return {};
}

// std::nullopt can be used to create any (empty) std::optional
auto create2(bool b)
{
    return b ? std::optional<std::string>{"Godzilla"} : std::nullopt;
}

int main()
{
    std::cout << "create(false) returned "
              << create(false).value_or("empty") << '\n';
    
    // optional-returning factory functions are usable as conditions of while and if
    if (auto str = create2(true))
        std::cout << "create2(true) returned " << *str << '\n';
}
```

Output:

```no-lang
create(false) returned empty
create2(true) returned Godzilla
```

`value_or` is a method of the `optional` class, defined as: *returns the contained value if available, another value otherwise*.
