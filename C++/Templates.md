# Templates

Templates help us to avoid duplicate code. We can use templates when writing generic code

Example:

```cpp
template<typename Type>
Type MyMax(Type a, Type b) {
    if (a > b)
        return a;
    return b;
}

int main () {
    cout << MyMax(2, 5) << "\n" // 5, compiler guessed that the input is int
    cout << MyMax<int>(2, 5) << "\n" // 5, specify int as type
    cout << MyMax(2, 5.4) << "\n" // ERROR, compiler doesn't know what type to use
    cout << MyMax<double>(2, 5.4) << "\n" // 5.4, specify double as type

    return 0;
}
```

The compiler is essentially pasting in the appropriate variable type into the template function at compilation time.

We can also specify multiple types, e.g.

```cpp
template<class Type1, class Type2>
// note that the output is of Type1
Type1 sum (Type1 a, Type2 b) { 
    Type1 r = a + b;
    return r;
}

int main () {
    cout << sum('A', 1) << "\n" // B
    cout << sum(1, 'A') << "\n" // 66
    cout << sum<int, int>(1.2, 10) << "\n" // 11

    return 0;
}
```

You can also specify behaviour for a specific data type. In the below multiply example, we choose to print a string x number of times as out interpretation of multiplying a string.

```cpp
template<class T> // generic version
T multiply(T a, int factor) {
    return a * factor;
}

template<> // string-specific specialization
string multiply(string str, int factor) {
    string res = "";
    while (factor--)
        res += str;
    return res;
}
```

It is also possible to overload templates, *e.g.*

```cpp
template<typename T1, typename T2>
Type1 func(T1 a) {
    return a;
}

Type2 func(T1 a, T2 b) {
    return (a + b);
}
```

## Class Templates

We can also use templates to create generic classes. Here is the example from the Udemy course,

```cpp
template<typename T, int SIZE>
struct MyQueue {
    T arr[SIZE];
    int pos;
    
    MyQueue() {pos = 0;}
    MyQueue(T param_arr[], int len) {
        for (int i = 0; i < len; ++i)
            arr[i] = param_arr[i];
        pos = len;
    }

    // template within a class 
    template<typename Type>
    void sum_and_add(Type a, Type b) {
        arr[pos++] = a + b;
    }

    void print() {
        for (int i = 0; i < pos; ++i)
            cout << arr[i] << " ";
        cout<<"\n";
        }
};
```

Notice that we are passing in a non-type parameter. Beware that this parameter **must be constant** (question, so why didn't they use the `const` keyword in the template definition?).

## Variadic Templates

(See Udemy vid, Stroustrup p. 82, [Microsoft Docs](https://docs.microsoft.com/en-us/cpp/cpp/ellipses-and-variadic-templates?view=msvc-170))

A variadic template can accept an *arbitrary number of inputs* as well as an *arbitrary number of types*. This is typically accomplished using recursion, such that there is a head that is passed into the template then a tail which is called recursively. From Stroustrup (82),

```cpp
template<typename T, typename ... Tail>
void f(T head, Tail... tail) {
    g(head); // do something to head
    f(tail...); // try again with tail
}
```

We also need some way to deal with the end of the tail, in other words the base case for our recursion. To take a more concrete example from the Udemy course, let's do a sum.

```cpp
template<typename T>
// overloaded function for end-case
T Sum() {
    return 0;
}

template<typename T, typename ... Args>
T Sum(T a, Args ... args) {
    // a is first number, and remaining in args
    return a + Sum<T>(args...);
}
```

The sum is recursively calling shorter tails of the args until we get to Sum() and simply add 0 to our sum. Beware of this example though. Since Sum has an output type, whatever the first type passed into Sum is will be the final output type. For example, a few different calls will give,

```cpp
int main() {
	cout << Sum(1, 2, 3, 4) << "\n";
	cout << Sum(1.2, 2.3, 3.1, 4) << "\n";          // 10.6
	cout << Sum(1, 2.3, 3.1, 4.2) << "\n";          // 10, first value an int
	cout << Sum<double>(1, 2.3, 3.1, 4.2) << "\n";  // 10.6, specify output as double
	return 0;
}
```
