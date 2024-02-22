# lvalues and rvalues

Loosely speaking, *lvalues* and *rvalues* refer to the left and right side of an expression. In practice, there are different types of lvalues and rvalues and there is also something called an *xvalue*. The types of values have to do with how the compiler works and what is and what is not available to the program.

The [following definitions](https://learn.microsoft.com/en-us/cpp/cpp/lvalues-and-rvalues-visual-cpp?view=msvc-170) are from Microsoft. The link also includes a handy diagram which clarifies the relationship between the different types.

> * A glvalue is an expression whose evaluation determines the identity of an object, bit-field, or function.
> * A prvalue is an expression whose evaluation initializes an object or a bit-field, or computes the value of the operand of an operator, as specified by the context in which it appears.
> * An xvalue is a glvalue that denotes an object or bit-field whose resources can be reused (usually because it is near the end of its lifetime). Example: Certain kinds of expressions involving rvalue references (8.3.2) yield xvalues, such as a call to a function whose return type is an rvalue reference or a cast to an rvalue reference type.
> * An lvalue is a glvalue that isn't an xvalue.
> * An rvalue is a prvalue or an xvalue.

[Contents](_main_cpp_notes.md)
