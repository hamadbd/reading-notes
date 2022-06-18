## List Comprehensions

List comprehensions are a unique way to create lists in Python. A list comprehension consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses. The expressions can be any kind of Python object. List comprehensions will commonly take the form of [<value> for <vars> in <iter>].

A simple case: Say we want to turn a list of strings into a list of string lengths. We could do this with a for loop:
```
>>> names = ["Nina", "Max", "Rose", "Jimmy"]
>>> my_list = [] # empty list
>>> for name in names:
...     my_list.append(len(name))
...
>>> print(my_list)
[4, 3, 4, 5]
```
We can do this much easier with a list comprehension:
```
>>> names = ["Nina", "Max", "Rose", "Jimmy"]
>>> my_list = [len(name) for name in names]
>>> print(my_list)
[4, 3, 4, 5]
```
We can also use comprehensions to perform operations, and the lists we assemble can be composed of any type of Python object. For example:
```
>>> names = ["Nina", "Max", "Rose", "Jimmy"]
>>> my_list = [("length", len(name) * 2) for name in names]
>>> print(my_list)
[('length', 8), ('length', 6), ('length', 8), ('length', 10)]
```

In the above example, we assemble a list of tuples - each tuple contains the element “length” as well as each number from the len() function multiplied by two.

## Conditionals
You can also use conditionals (if statements) in your list comprehensions. For example, to quickly make a list of only the even lengths, you could do:
```
>>> names = ["Nina", "Max", "Rose", "Jimmy"]
>>> my_list = [len(name) for name in names if len(name) % 2 == 0]
>>> print(my_list)
[4, 4]
```

Here, we check divide every string length by 2, and check to see if the remainder is 0 (using the modulo operator).

## String Joining with a List Comprehension
Back in our exercise on converting between types, we introduced the string.join() function. You can call this function on any string, pass it a list, and it will spit out a string with every element from the list “joined” by the string. For example, to get a comma-delimited list of numbers, you might be tempted to do:
```
>>> my_string = ",".join([0, 1, 2, 3, 4])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sequence item 0: expected str instance, int found
```

Unfortunately, you can’t join a list of numbers without first converting them to strings. But you can do this easily with a list comprehension:

```
>>> my_list = [0, 1, 2, 3, 4]
>>> my_string = ",".join([str(num) for num in my_list])
>>> print(my_string)
0,1,2,3,4
```

