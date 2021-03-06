# Variables and types in Lua

In this chapter we'll dig into the variables in Lua and the datatypes they can
contain.

## Variable names (Identifiers)

Lua follows the convention setup by most other languages for variable naming.
Variables start with a letter or underscore, and after the initial character
can contain numbers as well.

### Variable scope

When first setting a variable in Lua, you can control whether that variable is
in a global or local context. By default, variable assignments to undefined
variables will declare the said variable as a global variable unless the
keyword `local` is used.

```lua
this_is_a_global = true
local this_is_not_global = true
```

## Lua variable types

Lua is a simple language. It is dynamically typed and there are only a few
types.

The `nil` type is the simplest type and represents an unset value. Setting a
variable to `nil` effectively removes that variable from this plane of
existence. In Lua, you can use an undeclared variable, all undeclared variables
share the initial value `nil`.

For boolean operations the values `true` and `false` are defined, representing
their expected meanings.

Functions are a type in Lua as well, they can be assigned to variables like
anything else.

```lua
local write = print
write("Hello!")
```

There is also a `userdata` type in Lua, which usually represents arbitrary C
data. Lua is designed as an embedded language and `userdata` could be used to
refer to things like C structures.

### Numbers in Lua

In Lua, there are no separate types for integers or floating point numbers. All
numbers are real numbers usually represented as a `double` type under the hood.

Even though this means all numbers are floating point numbers, arithmetic
operations are still fast and you can rely on the number type for increment and
decrement operations.

### Strings in Lua

Strings in Lua are a sequence of bytes as in many other languages. They are
binary safe so you may even include zero values into a string in Lua.

Strings can be delimited by single quotes, double quotes, or double square
brackets. You can choose which ever feels most appropriate to you, there is no
syntactic difference between single and double quotes. Double square brackets
are commonly used for multi-line strings, and as some syntactic sugar if the
first character within the string is a newline it will be ignored.

```lua
local my_string_singles = 'Hello!'
local my_string_doubles = "What's up?"
local my_multiline_string = [[
I replied, "I'm learning this Lua thing."
]]
```

### Tables in Lua

Tables are THE data structuring type in Lua. They can be used like an array or
list, like a dictionary, hash map, or associative array, and they provide a
nice means to make objects for object oriented styles of programming. Table's
are used fairly similarly to other languages, using square brackets for
accessing elements of the table, but can accept any data type as the index
(except `nil`)

A table can be created in a few different formats, here's an array-like table.
Keep in mind these types of tables start at 1, not 0. This example outputs
`two`.
```lua
local my_table = {"one", "two", "three"}
print(my_table[2])
```

To create a table with strings for indexes, this format may be used
```lua
local ages = {joe=20, stephanie=23, john=34}
print(ages["john"])
```

As mentioned before anything that is not `nil` can be used as the index for a
table, to use non-string values wrap the key in square brackets as shown here.
```lua
local empty_table = {}
local mixed_key_types = {[42]="numbas!", [false]="booleans!",
                         ["string_key"]="strings!", [empty_table]="tables!"}
```

You can also create an array-like table starting on any value you'd like, each
successive value will be iterated by 1, somewhat like an enum in C. This example will print out `others`.
```lua
local zero_indexed = {[0]="like", "those", "others", "do"}
print(zero_indexed[2])
```

[Previous Chapter: The strange bits of Lua](https://github.com/KennethWilke/learn-to-luvit/tree/master/chapter2)

[Next Chapter: Writing Lua](https://github.com/KennethWilke/learn-to-luvit/tree/master/chapter4)
