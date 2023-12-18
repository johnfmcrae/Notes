# Virtual

From Stroustrup (65),

> The word virtual means “may be redefined later in a class derived from this one."

The virtual keyword can be found inside an **abstract type.** An abstract type is one where the **interface** and the **representation** are decoupled. Stroustrup provides the example of a class called `container` which is meant as a more generic form of `vector`,

```cpp
class Container {
public:
    virtual double& operator[](int) = 0; // pure virtual function
    virtual int size() const = 0; // const member function (§3.2.1.1)
    virtual ˜Container() {} // destructor (§3.2.1.2)
};
```

You cannot use Container or its member functions on its own. The fact that Container contains virtual functions makes it an **abstract class**. You must explicitly define a new class which can inherit from Container, but this class must then define its implementation of the virtual functions given in Container. In other words, Container is acting solely as an **interface** and a class derived from it must provide its own representation.

[Contents](_main_cpp_notes.md)
