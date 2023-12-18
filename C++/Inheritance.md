# Inheritance in C++

Specify class inheritance in C++ using the colon operator, **`:`**.

```cpp
class Dog : Animal
{
    int age;
public:
    Dog(int age) : age(age) {}
};
```

## Inheritance Access Modes

The inheritance access mode of a derived class determines the access scope of the members that the derived class inherits from the base class. Specifically, a derived class can have **public**, **protected**, or **private** inheritance. The access modes behave as follows,

- **Public inheritance** maintains the access scope of the base class. Public members remain public and protected members remain protected.
- **Protected inheritance** changes the access scope of the public members to protected. Public members become *protected* and protected members remain protected.
- **Private inheritance** changes the access scope of all of the members to private. Public members as  become private and the private members become private.

Don't forget that the derived class can never access the base class' private members.

The access modes change the access of the members relative to the derived class. So a derived class with private inheritance makes all of the inherited members private. So in this example, the calling context of the derived class will not have access to any of the base class' members, because the derived class is using private inheritance.

[Contents](_main_cpp_notes.md)
