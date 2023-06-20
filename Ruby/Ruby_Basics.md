# Ruby Basics

Topics to cover

- control statements
- arrays
- IO
- modules
- classes

## Some Basic Info

You can interact with the Ruby like you would the Python interpreter by launching `irb`, interactive Ruby.

## [Control Statements](Ruby_Control_Flow.md)

Ruby has *if* statements and *while* loops. The *for* keyword is available, but you're often better off using Ruby's *iterator* methods.

## Containers

Ruby has an *Array* class, which is is the go-to container class.

```rb
# initialize an array
array = [2, 4, 6, 8]

array[0]    # => 2
array[-2]   # => 6
array[1,3]  # => [4, 6, 8]
array[0..2] # => [2, 4, 6]
```
