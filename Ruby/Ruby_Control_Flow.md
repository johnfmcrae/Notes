# Control Statements

Control statements use the **`end`** keyword, like in MATLAB.

## Conditionals

Ruby uses the **`elsif`** keyword for *else if* cases.

```rb
a = 2
if a == 1
    puts "a = 1"
elsif a == 2
    puts "a = 2"
else
    puts "a is not 1 or 2"
end
```

Ruby also has the **`unless`** keyword, which is similar to a negated *if* statement.

```rb
a = 2
unless a == 4
    puts "a is not 4"
else
    puts "a is 4"
end
```

The **`unless`** keyword does not have a *elseunless* keyword, but **`else`** does work with **`unless`**.

## Loops

Ruby has two basic loops: **`while`** and **`until`**. **`while`** loops are as you'd expect,

```rb
i = 0
while i < 4
    puts i
    i += 1
end
```

The **`until`** keyword is to the **`while`** keyword what **`unless`** is to **`if`**. Meaning, **`until`** is similar to saying *while condition is not true*. The following *unless* statement produces the same output as the above *while* statement.

```rb
j = 0
until j == 4
    puts j
    j += 1
end
```

You can also implement an infinite loop using the **`do`** keyword,

```rb
loop do
  puts "foo"  
  puts "bar"  
  sleep 300
end
```

Ruby does also have a **`for`** keyword, which is used as a **`for ... in`** loop.

```rb
for i in ['fee', 'fi', 'fo', 'fum']
  print i, " "
end
```

However, under the hood, the **`for ... in`** loop is translated to using Ruby iterators.

```rb
for aSong in songList
  aSong.play
end

# same as
songList.each do |aSong|
  aSong.play
end
```

## Iterators

Ruby has many handy iterator methods which are meant to provide cleaner, less error-prone versions of the sorts of tasks you would usually do with a *for* loop. Here are some examples,

```rb
3.times do
  print "Ho! "
end
# produces: Ho! Ho! Ho!

0.upto(9) do |x|
  print x, " "
end
# produces: 0 1 2 3 4 5 6 7 8 9

0.step(12, 3) {|x| print x, " " }
# produces: 0 3 6 9 12

[ 1, 1, 2, 3, 5 ].each {|val| print val, " " }
# produces: 1 1 2 3 5
```

[main Ruby notes](Ruby_Basics.md)
