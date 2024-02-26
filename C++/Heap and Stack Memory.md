# Heap and Stack Memory

**Stack** memory is what the compiler uses to allocate space for most things in C++, such as local variables. Memory blocks are allocated on a stack and popped from the stack in LIFO order. Stack memory is generally allocated in the CPU cache and is faster than heap memory. However, the cache doesn't have as much space as RAM so you have to be careful to avoid the dreaded *stack overflow*.

Stack memory is destroyed when it goes out of scope.

**Heap** memory is allocated explicitly by the programmer. Heap memory allocation and deallocation is not a feature shared by all languages. Other languages can do allocation but not every language requires the programmer to deallocate. Heap memory allocation comes into C++ from C. You can spot it by watching out for the following keywords:

- `new`
- `delete`
- `malloc`
- `free`

C programmers use heap allocation to implement dynamic memory allocation. C++ programmers may also be interested in heap memory allocation when they need to allocate memory that persists beyond its scope because stack memory is destroyed when it goes out of scope. This idea should trigger some loud alarm bells in your mind however, because forgetting to deallocate heap memory is what leads to **memory leaks**.

The heap is also referred to as *free store*.
