# TESTING TDD - PyTest
- The pytest framework makes it easy to write small, readable tests, and can scale to support complex functional testing for applications and libraries.

- pytest allows you to use the standard Python assert for verifying expectations and values in Python tests. For example, you can write the following:


content of test_assert1.py
>def f():
>     return 3
> 
> def test_function():
>    assert f() == 4



The Cycle
this is an example of an important thing about TDD: the cycle.

The cycle is made by three steps:

🆘 Write a unit test and make it fail (it needs to fail because the feature isn’t there, right? If this test passes, call the Ghostbusters, really)
✅ Write the feature and make the test pass! (you can dance after that)
🔵 Refactor the code — the first version doesn’t need to be the beautiful one (don’t be shy)



# Recursion
## What is Recursion? 
The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called a recursive function. Using a recursive algorithm, certain problems can be solved quite easily

## Need of Recursion
Recursion is an amazing technique with the help of which we can reduce the length of our code and make it easier to read and write. It has certain advantages over the iteration technique which will be discussed later. A task that can be defined with its similar subtask, recursion is one of the best solutions for it. For example; The Factorial of a number.

## How recursive function store in memory?
Recursion uses more memory, because the recursive function add to the stack with each recursive call, and keep the values there until the until the call is finished. Recursive function uses LIFO (LAST FILL FIRST OUT) Structure just like stack data structure.