# Classes and Object-Oriented Programming in C++

## Constructors

A constructor is a special **member function** which is automatically called when an instance of a class is created. A **default constructor** generally has no arguments, as opposed to a **parameterized constuctor** which does have arguments.

You can write a constructor as you would a normal function, for example,

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle(double w, double h) {
        width = w;
        height = h;
    }
};
```

However, a better way to write a constructor is by using an **initializer list**. An initializer list allows you to initialize class member prior ro execution of the constructor body. It is also the only way to initialize `const` member data and references. An initializer list for the `Rectangle` class could look like this,

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle(double w, double h) : width(w), height(h) {
        // constructor body
    }
};
```

Note that when using an initializer list, you can use the same name for input parameters, *e.g.* you could do `width(width)` instead of `width(w)`. We can also overload the constructor as you would with other functions,

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle(double width, double height) : width(width), height(height) {
        // constructor body
    }

    // overloaded constructor
    Rectangle(double width) : width(width), height(0) {}
};
```

### Default Constructor

As mentioned above, the **default constructor** is generally a constructor which has no inputs, such as,

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle() : width(0.0), hieght(0.0) {}

    Rectangle(double width, double height) : width(width), height(height) {}
};
```

However, we can also create a default constructor by specifying *all* of the parameters, *e.g.*

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle(double width = 0.0, double height = 0.0) : width(width), height(height) {}
};
```

If you do not specify a default constructor, for example if you have a constructor with parameters but no defaults,

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle(double width, double height) : width(width), height(height) {}
};
```

Then your code will run as long as you provide inputs when initializing your class. However, if you try and initialize your class without inputs, so `Rectangle r` in this case, you will get a compilation error. The safest way to avoid this is to *always include a default constructor*.

### Delegating Constructors

We can sometimes simplify our code by using a **delegating constructor**. A delegating constructor calls another constructor of the same class. For example, we can make our default constructor a delegating constructor,

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle() : Rectangle(0.0, 0.0) {}

    Rectangle(double width, double height) : width(width), height(height) {
        // constructor body
    }
};
```

Here, the delegating constructor uses the constructor defined below to pass the arguments `(0.0, 0.0)` into the function. Another example from [Microsoft docs](https://docs.microsoft.com/en-us/cpp/cpp/delegating-constructors?view=msvc-170) shows how we can use a delegating constructor to simplify our code. Say we have the following

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

We can reduce the repeated code by delegating constructors. Now, our code becomes,

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
```

Now, `class_c(int, int, int)` calls `class_c(int, int)` which calls `class_c(int)`.

## Destructors

When an object goes out of scope, it is automatically **destructed**. A destructor is specified with the tilde symbol, `~` and does not return any parameters. For example,

```cpp
class Rectangle {
private:
    double width;
    double height;

public:
    Rectangle() : width(0), height(0) {}
    
    ~Rectangle() {cout << "Destructor\n";}
};
```

You can also specify a constructor outside of the class by scoping it appropriately, `Rectangle::~Rectangle() {...}`. Destructors are important for freeing up memory when we are done with an object.

The C++ compiler will generate a default destructor if you do not provide one. Therefore, for the most part, you do not need to worry about destructors, since objects will be destroyed as soon as they go out of scope. Sometimes, you will need to define a custom destructor, but only in cases where your class ["stores handles to system resources that need to be released, or pointers that own the memory they point to."](https://docs.microsoft.com/en-us/cpp/cpp/destructors-cpp?view=msvc-170) For the most part, you can simplify your code, improve readability and omit custom destructors by [making use of specific classes in the STL.](https://stackoverflow.com/questions/22491174/when-do-we-need-to-define-destructors) Classes like `std::vector`, `std::string` and `std::unique_ptr` have resource management built-in that will prevent unwanted issues such as memory leaks.

### Memory Leaks

**Memory leaks** tend to come up as the ultimate evil which can arise by not properly deleting objects or cleaning up memory. As mentioned above, using the STL is a good way to avoid this in C++. Memory leaks are more of an issue in C where you need to handle memory access yourself. In particular, dynamically allocated memory, which makes use of the **heap** is where you can run into trouble. For example, if in some C code, in main we specify a dynamically allocated array,

```C
int main(int argc, char *argv[]) {
    int* a  = malloc(sizeof(int));
    *a = 5;
    return 0;
}
```

Then we *should* de-allocate the array by using `free`,

```C
int main(int argc, char *argv[]) {
    int* a  = malloc(sizeof(int));
    *a = 5;
    free(a);
    return 0;
}
```

If we do not, then we will have created a memory leak because we did not free up the memory on the heap that claimed for the array. Though this may be fairly easy to spot when our memory allocation and freeing is all in the same function, it can be easier to miss when split accross multiple functions. For more info, see [this video.](https://www.youtube.com/watch?v=jx9MiCC3RJ4)

## Deleted Functions

You can use the keyword `delete` to explicitly stop the use of certain functions. For example, say you have a constructor which takes an integer as an input,

```cpp
class Employee {
private:
    int *salary {nullptr};
    string name;
public:
    Employee() = default;

    Employee(int salary, string name) : 
        salary(new int {salary}), name(name) {}
    
    ~Employee() {
        if (salary != nullptr) {
            delete salary;
            salary = nullptr;
        }
    }
};
```

You can add a line to prevent other types being passed into the Employee constructor function,

```cpp
class Employee {
private:
    int *salary {nullptr};
    string name;
public:
    Employee() = default;

    Employee(double salary, string name) = delete;

    Employee(int salary, string name) : 
        salary(new int {salary}), name(name) {}
    
    ~Employee() {
        if (salary != nullptr) {
            delete salary;
            salary = nullptr;
        }
    }
};

int main() {
    Employee e1(10, "Jim"); // okay

    // Employee e2(10.5, "Jim"); // prevented by the deleted function
}
```
