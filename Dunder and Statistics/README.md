# Dunder 
1- init
This is a method you must have already used if you have worked with classes. The init method is used to create an instance of the class.
```
def __init__(self,names):
    if names:
        self.names = names.copy()
        for name in names:
            self.versions[name] = 1
    else:
        raise Exception("Please Enter the names")
```
The init method defined above accepts a list of names as parameters and stores it in the class’ names list. Additionally, it also populates the versions dictionary. We have also put a check on the names list.

If the list is empty, an exception is raised. Below is how we would use the init method.
```
p = softwares(['S1','S2','S3'])
p1 = softwares([])
```
The first statement would work fine but the second line would raise an exception since an empty list was passed in as a parameter.

2- str
The str method is useful when we want to use instances of our class in a print statement. As discussed earlier, it usually returns a memory object. But we can override the str method to meet our requirements.
```
def __str__(self):
    s ="The current softwares and their versions are listed below: \n"
    for key,value in self.versions.items():
        s+= f"{key} : v{value} \n"
    return s
    ```
The above str method returns the software and their versions. Ensure that the function returns a string. Below is how we would call the method.
```
print(p)
```

3- setitem
When assigning values in a dictionary, the setitem method is invoked.
```
d = {}
d['key'] = value
```
We can give instances of our class a similar feature with the help of the setitem method.
```
def __setitem__(self,name,version):
    if name in self.versions:
        self.versions[name] = version
    else:
        raise Exception("Software Name doesn't exist")
```
The method above is going to update the version number of the software. If the software is not found, it will raise an error.

In the 3rd line, we use the built-in setitem method of a dictionary.

We can invoke the setitem method in the following way:
```
p['S1'] = 2
p['2'] = 2
```
The first line would update the version of software S1 to 2. But the second line would raise an exception since software 2 doesn’t exist.

4- getitem
The getitem method is like the setitem method, the major difference being that the getitem method is called when we use the [] operator of a dictionary.
```
d = {'val':key}
print(d['val'])
```
Instances of our class can also be given a similar feature.
```
def __getitem__(self,name):
    if name in self.versions:
        return self.versions[name]
    else:
        raise Exception("Software Name doesn't exist")
```
The above method essentially returns the version of the software. If the software is not found, it raises an exception. To invoke the getitem method, we can write the following line of code.
```
print(p['S1'])
print(p['1'])
```
The first line would print the version of S1. But, the second line would raise an Exception since 1 doesn’t exist.

5- delitem
The delitem is like the setitem and getitem method. To avoid repetition, we will move on to the implementation and use case.
```
def __delitem__(self,name):
    if name in self.versions:
        del self.versions[name]
        self.names.remove(name)
    else:
        raise Exception("Software Name doesn't exist")
```
The delitem method deletes the software from the dictionary as well as the list.

It can be used as follows.
```
del p['S1']
```

6- len
In a dictionary, the len method returns the number of elements in a list or the number of key-value pairs in a dictionary.

We can define a len method for our class as well.
```
def __len__(self):
    return len(self.names)
```
The len method for our class returns the number of softwares. As you might have noticed, we are using the built-in len method of a list to return the number of software.

The len method of our class can be used in the following way.
```
print(len(p))
```

7- contains
The contains method is used when using the in operator. The return value has to be a boolean.
```
def __contains__(self,name):
    if name in self.versions:
        return True
    else:
        return False
```
The method checks if the name is found in the dictionary. We will be using the dictionary’s built-in contains method for that.
```
if 'S2' in p:
    print("Software Exists")
else:
    print("Software DOESN'T exist")
```
The code above prints the statement inside the if blocks since software S2 is present inside the versions dictionary.

## COMPLETE CODE 
 Complete code
```
class softwares:
    names = []
    versions = {}
    
    def __init__(self,names):
        if names:
            self.names = names.copy()
            for name in names:
                self.versions[name] = 1
        else:
            raise Exception("Please Enter the names")
    
    def __str__(self):
        s ="The current softwares and their versions are listed below: \n"
        for key,value in self.versions.items():
            s+= f"{key} : v{value} \n"
        return s
    
    def __setitem__(self,name,version):
        if name in self.versions:
            self.versions[name] = version
        else:
            raise Exception("Software Name doesn't exist")
    
    def __getitem__(self,name):
        if name in self.versions:
            return self.versions[name]
        else:
            raise Exception("Software Name doesn't exist")
    
    def __delitem__(self,name):
        if name in self.versions:
            del self.versions[name]
            self.names.remove(name)
        else:
            raise Exception("Software Name doesn't exist")
    
    def __len__(self):
        return len(self.names)
    
    def __contains__(self,name):
        if name in self.versions:
            return True
        else:
            return False
```
