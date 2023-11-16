# Pointers

**Pointers** are a feature inherited from C and in C++ we sometimes refer to them as **raw pointers**. A pointer is simply a variable which holds a memory address. To define a pointer in C and C++, use the asterisk operator, `*`. The asterisk operator also works as the dereference operator, so

```cpp
int *ptr; // defines a pointer
*ptr = 3; // the value at the address stored in ptr is 3
```

We can also use the address operator, `&` if we want to access the addresses of non-pointer variables. Hence,

```cpp
int val = 2;
ptr = &val; // ptr holds the address of val, or is "pointing to val"
ptr = &ptr; // ptr holds its own address
```

It is good practice to initialize a pointer to the **`nullptr`** as,

```cpp
int *p1 {nullptr};
```

This is because in C and C++, when a pointer is created it points to what is called a *bad value* by default. Dereferencing a bad value can lead to crashes and other issues in the program, so it si best to avoid making these at all by initializing a pointer to null.

## Pass by Pointer and Pass by Reference

What do you do when you have a massive array that you don't want to copy and paste around every time you need to pass it into a function? Pass by reference.

```cpp
void addConstantToVector(vector<int>& returnVector, int constant) {
    for (auto it = returnVector.begin(); it < returnVector.end(); it++) {
        *it += constant;
    }
}
```

Pass by reference is nice because you get the benefit of moving data around by a reference without having to worry about dereferencing. However, you can always go old-school and pass by pointer, which will do the same thing.

```cpp
using namespace std;

void tripleValueByReference(int& value) {
    value *= 3;
}

void tripleValueByPointer(int* value) {
    *value *= 3;
}

int main()
{
    auto testValue = 4;
    cout << "auto testValue = 4;" << endl;
    tripleValueByReference(testValue);
    cout << "tripleValueByReference(testValue); testValue =  " << testValue << endl;
    tripleValueByPointer(&testValue);
    cout << "tripleValueByPointer(&testValue); testValue =  " << testValue << endl;
}
```

Output:

```text
auto testValue = 4;
tripleValueByReference(testValue); testValue =  12
tripleValueByPointer(&testValue); testValue =  36
```

But beware that when you pass by pointer, you are allowed to pass a NULL pointer. When you pass by reference, the value must be initialized. Furthermore, if you are passing by a raw pointer, there is a chance that the value being pointed to could have been changed elsewhere.

## Arrays and Pointers

As in C, we can use pointers to access arrays. For example if we create an array of integers, we can access its contents using a pointer,

```cpp
int a[] = {1, 2, 3, 4};
int* p  = a; // points to a[0]
```

Increasing the pointer value allows us to iterate through the array.

```cpp
std::cout << *p << "\n"; // 1
p++;
std::cout << *p << "\n"; // 2
```

If we exceed the bounds of the array using the pointer, we will end up pointing to garbage. Remember that we can use the C function `sizeof()` to get the size of the array.

## Smart Pointers

Raw pointers, like many low-level features from C, are very powerful and therefore very dangerous. With great power comes great responsibility, which is best delegated to smarter people, like the writers of the C++ STL. The STL has some pointer classes which we can use like our classical C pointers but take care of some of the messy and dangerous bits like memory de-allocation.

There are three types of smart pointers in C++, they are,

- **Shared pointers**
- **Weak pointers**
- **Unique pointers**

There also used to be another smart pointer called the **auto pointer**, but this was removed in C++17.

All smart pointers are *classes* which manage raw pointers. You create them but you do not delete them, as the deletion is managed by the class. The usage for smart pointers is similar to that of raw pointers, meaning you use the `*` and `->` operators as you would with raw pointers.

To use smart pointers, make sure to include them with,

```cpp
#include <memory>
```

### Unique Pointers

The term **unique** in **unique pointer** refers to the fact that these pointers allow only *one* owner for the data which it points to. In other words, you cannot create a second pointer and point to what is already being pointed to by a unique pointer. Therefore, the pointer cannot be assigned or copied.

The unique pointer is implemented very efficiently and is the go-to pointer in most cases.

To initialize a unique pointer, you need to define it directly using `{}` declaration (see [Declarations](Declarations.md)),

```cpp
std::unique_ptr<int> p1 { new int { 20 } }; // pointer of type integer pointing to a value of 20
```

You *can* use `p1` as a raw pointer by changing the value it points to,

```cpp
*p1 = 50; // okay
```

However, you *cannot* change its address directly

```cpp
p1 = new int {50}; // ERROR, can't assign values to pointer
```

The second case would have you making a new address for the new value, which the unique pointer won't allow. If you need to reset the pointer, then you need to use the reset function,

```cpp
p1.reset(new int { 50 }); // okay
```

Similarly, you cannot use the copy constructor for a unique pointer,

```cpp
std::unique_ptr<int> p2 {p1}; // ERROR, attempting to copy p1 into p2 would result in a duplicate
```

You can, however, *move* the contents of `p1` into a second pointer,

```cpp
std::unique_ptr<int> p2 { std::move(p1) }; // okay
```

Now, `p1` will point to the **`nullptr`**, so be careful not to use it after having moved its contents, or better yet, delete `p1`.

---

You can pass pointers to function by value or by reference, just like raw pointers. However, it is a good idea, when passing by reference, to use **`const`** in order to prevent the user from modifying the pointer within the function.

The helper function `std::make_unique<type>(val)` is useful for making unique pointers. You can even use it with `auto`,

```cpp
std::unique_ptr<int> p1 { new int { 20 } };          // classic instantiation
std::unique_ptr<int> p2 = std::make_unique<int>(20); // helper function 
auto p3 = std::make_unique<int>(20);                 // unique pointer with auto
```

---

To make a unique pointer to an array, use the following syntax,

```cpp
std::unique_ptr<int[]> p1 = std::make_unique<int[]>(4); // array of length 4
```

### Shared Pointers

**Shared pointers** are similar to unique pointers except that they allow multiple references to an object. As a result, shared pointes can make use of the copy constructor. Hence, unlike for unique pointers, the following code is valid,

```cpp
shared_ptr<int> p1 {new int {20}};
shared_ptr<int> p2 {p1}; // copying p1 to p2 is okays
p3 = p2; // assignment is also fine
```

Like unique pointer, there is also a make function which can be used with **`auto`**,

```cpp
auto p4 = make_shared<int>(20); // preferred style
```
