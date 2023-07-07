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

## Sequences

Some ideas on how to implement sequences of notes in Ruby

```rb
# we want something with a syntax like,
# {g4 g4 c'2 c'4 c'8 a8 a2}
# use the string.split method to parse the input
# possibly a 2D array? maybe even an object?

tempo = 100 
quarterNote = 60/tempo

do
    play 67
    sleep quarterNote
    play 67
    sleep quarterNote
    play 72
    sleep quarterNote*2
    play 72
    quarterNote/2
end

noteArray = [[67, quarterNote], [67, quarterNote], [72, quarterNote*2], [72, quarterNote/2]]

noteArray.each do |note|
    play note[0]
    sleep note[1]
end
```
