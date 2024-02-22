# References

Think of a reference as another name for something in C++. There are two flavours of references in C++, lvlaue references, created with the `&` operator, and rvalue references, created with the `&&` operator. In brief, lvalues are named variables and rvalues are temporary obejcts. See [lvalues and rvalues](lvalues%20and%20rvalues.md) for more details.

An important implication of the distinction between lvalue and rvalue references is that lvalue references do not allow you to create references to literals. So for example,

```cpp
void MyFunction(int& number) {
    std::cout << "The number is: " << number << "\n";
}

main int() {
    int myNumber = 1;
    MyFunction(myNumber); // OK
    MyFunction(2);        // not valid
}
```

Conversely, if we made the argument to the function an rvalue reference, we would not be able to pass in an lvalue in the calling context,

```cpp
void MyFunction(int&& number) {
    std::cout << "The number is: " << number << "\n";
}

main int() {
    int myNumber = 1;
    MyFunction(myNumber); // not valid
    MyFunction(2);        // OK
}
```
