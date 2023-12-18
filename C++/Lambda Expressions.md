# Lambda Expressions

**Lambda** functions (often simply, *"lambda"*) allow us to create an **anonymous function object** within another function. They are useful for creating short functions on the fly which can then be passed to subsequent algorithms or functions later on. For example, we can specify a sum in main function as,

```cpp
int main() {

    auto fsum = [](int x, int y) -> int {
        return x + y;
    };

    std::cout << fsum(3, 5) << "\n";

    return 0;
}
```

Let's note a few syntactical features of the lambda. First, the square brackets `[]` is the **lambda-introducer**, which tells the compiler to create a lambda function. Next, we have the **trailing-return-type**, `->`, which is an optional specifier which let's us choose the return type of the lambda. We don't actually need to use `->` in the above example, since the return type is not ambiguous. Finally, note that the lambda is terminated with a semicolon after the curly bracket, `};`, which is easy to forget!

You can take the anonymity of the function one step further and define it directly in the input parameter list of another function if you want. For example, let's say we want to use a function to tell if a number is odd or not,

```cpp
bool IsOdd(int n) {
    return n % 2 != 0;
}
```

and let's say we want to use the `IsOdd` function as an input to the STL function [`std::count_if( InputIt first, InputIt last, UnaryPredicate p )`](https://en.cppreference.com/w/cpp/algorithm/count)[^1],

[^1]: I believe that the "unary predicate" is a [logic element](https://en.wikipedia.org/wiki/Predicate_(mathematical_logic)), so it should return a `bool`

```cpp
int main() {
    vector<int> v { 1, 2, 3, 4, 5 };

    auto IsOdd = [] (int n) {return n % 2 != 0;};
    std::cout << std::count_if(v.begin(), v.end(), IsOdd) << "\n"; // 3

    return 0;
}
```

We could in fact simplify this code by using a lambda, without having to create a name, directly in the `count_if` function,

```cpp
int main() {
    vector<int> v { 1, 2, 3, 4, 5 };

    std::cout << std::count_if(v.begin(), v.end(), [] (int n) {return n % 2 != 0;}) << "\n";

    return 0;
}
```

Note that in the above example we didn't need to evaluate the anonymous function due to the nature of the `count_if` function. However, in most cases you do need to provide an input to an anonymous function with `()`.

[Contents](_main_cpp_notes.md)
