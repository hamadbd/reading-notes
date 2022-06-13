# Python Variable Scope 
You might have come across in situations where you’re trying to access a variable but the value is either different or doesn’t even exist. This might be due to the fact that you didn’t know about variables scope.

So don’t worry, we have got you covered in this article where we will discuss the scope of variables, types of scope, and keywords associated with Python variable scope.

## What is Variable Scope in Python?
In programming languages, variables need to be defined before using them. These variables can only be accessed in the area where they are defined, this is called scope. You can think of this as a block where you can access variables.

## Types of Python Variable Scope
There are four types of variable scope in Python, let’s go through each of them.

1. Local Scope
Local scope variables can only be accessed within its block.

Let’s see it with an example."
```
a = 10
def function():
  print(“Hello”)
  b = 20
function()
print(a)
print(b)
```

Output:
```
Hello
10
Traceback (most recent call last):
  File “main.py”, line 7, in <module>
    print(b)
NameError: name ‘b’ is not defined
```
In the above example, we see that Python prints the value of variable a but it cannot find variable b. This is because b was defined as a local scope in the function so, we cannot access the variable outside the function. This is the nature of the local scope.

2. Global Scope
The variables that are declared in the global scope can be accessed from anywhere in the program. Global variables can be used inside any functions. We can also change the global variable value.
```
Msg = “This is declared globally”

def function():
  #local scope of function
  print(Msg)

function()
```
Output:
```
This is declared globally
```

But, what would happen if you declare a local variable with the same name as a global variable inside a function?
```
 msg = “global variable”
def function():
  #local scope of function
  msg = “local variable”
  print(msg)
function()
print(msg)
```
Output:
```
local variable
global variable
```

As you can see, if we declare a local variable with the same name as a global variable then the local scope will use the local variable.

If you want to use the global variable inside local scope then you will need to use the “global” keyword which we will discuss later in this article.

3. Enclosing Scope
A scope that isn’t local or global comes under enclosing scope. This will be better understood with an example.
```
def vehicle():
  fun= “Start”
  def car():
    model= “Toyota”
    print(fun)
    print(model)
  car()
vehicle()
```

Output:
```
Start
Toyota
```

In the example code, the variable fun is used inside the car() function. In that case, it is neither a local scope nor a global scope. This is called the enclosing scope.

4. Built-in Scope
This is the widest scope in Python. All the reserved names in Python built-in modules have a built-in scope.

When the Python doesn’t find an identifier in it’s local, enclosing or global scope, it then looks in the built-in scope to see if it’s defined there.
```
a = 5.5
int(a)
print(a)
print(type(a))
```

Python would see in the local scope first to see which of the variables are defined in the local scope, then it will look in the enclosing scope and then global scope.

If the identifier is not found anywhere then, at last, it will check the built-in scope.

Here the functions int(), print(), type() does not need to be defined because they are already defined in the built-in scope of Python.

## Global and Nonlocal keyword
Remember we talked about the problem “What would happen if we declare variables with the same name in different scopes?” For these type of situations, we have “global” and “nonlocal” keywords.

Let’s see how we can use them.

1. Global Keyword
Let’s consider the example, in which we first see the problem
```
a = 100
def method():
  a = 50
  print(a)
method()
print(a)
```
Output:
```
50
100
```
The above code will print the values 50 and 100 because in the local scope variable, a is referenced to 50 and outside the method() function, it is being referenced to the global variable.

But, what if we wanted to access the global variable inside the method() function. 
```
a = 100
def method():
  global a
  a = 50
  print(a)
method()
print(a)
```
Output:
```
50
50
```
Now we see that by using the global keyword, we can declare that we want to use the variable a which is defined in the global scope.

So, when assigning the 50 to the variable, we also changed the value outside the function.

2. Nonlocal Keyword
Like the global keyword, we have a “nonlocal” keyword for times when we need to change a nonlocal variable.

We will see the examples with and without a nonlocal keyword.
```
a = "global variable"
def method():
        a = "nonlocal variable"
        def function():
                a = "local variable"
                print(a)
        function()
        print(a)
method()
print(a)
```
Output:
```
local variable
nonlocal variable
global variable
```
In the function(), a is referring to “local variable”, in method(), a is referring to “nonlocal variable” and outside these functions, a refers to “global variable”.

Now we use the nonlocal variable.
```
a = "global variable"
def method():
        a = "nonlocal variable"
        def function():
                nonlocal a
                a = "local variable"
                print(a)
        function()
        print(a)
method()
print(a)
```
Output:
```
local variable
local variable
global variable
```
We used the nonlocal keyword on “a” variable inside the function().

This is why when we changed the nonlocal variable value it also changed the value of “a” variable that is defined in method() function.

## Summary
This was everything about the Python variable scope.

We understood the variable scope and its multiple types where we saw how the same name can have different values in different scope.

In the later part, we saw how you can use global and nonlocal keywords to solve the problem of having different values under the same variable name.

