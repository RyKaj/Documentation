<div id="main" class="aui-page-panel">

<div id="main-header">

<div id="breadcrumb-section">

1.  [Information Technology](index.html)
2.  [3.0 Sofware Development
    Lifecycle](3.0-Sofware-Development-Lifecycle_380470491.html)
3.  [Design Patterns](Design-Patterns_451820045.html)
4.  [1.0 Design Pattern - Programming
    Language](1.0-Design-Pattern---Programming-Language_451820065.html)
5.  [Creational Design
    Patterns](Creational-Design-Patterns_451820114.html)



# Information Technology : Singleton Pattern

## Singleton

![](https://www.oodesign.com/images/creational/singleton-pattern.gif)

### Intent

**Singleton** is a creational design pattern that lets you ensure that a
class has only one instance, while providing a global access point to
this instance.

![](attachments/463530003/463530331.png)

### Problem

The Singleton pattern solves two problems at the same time, violating
the *Single Responsibility Principle*:

1.  **Ensure that a class has just a single instance**. Why would anyone
    want to control how many instances a class has? The most common
    reason for this is to control access to some shared resource—for
    example, a database or a file.
    
    Here’s how it works: imagine that you created an object, but after a
    while decided to create a new one. Instead of receiving a fresh
    object, you’ll get the one you already created.
    
    Note that this behavior is impossible to implement with a regular
    constructor since a constructor call **must** always return a new
    object by design.
    
    ![](attachments/463530003/463530332.png)

2.  **Provide a global access point to that instance**. Remember those
    global variables that you (all right, me) used to store some
    essential objects? While they’re very handy, they’re also very
    unsafe since any code can potentially overwrite the contents of
    those variables and crash the app.
    
    Just like a global variable, the Singleton pattern lets you access
    some object from anywhere in the program. However, it also protects
    that instance from being overwritten by other code.
    
    There’s another side to this problem: you don’t want the code that
    solves problem \#1 to be scattered all over your program. It’s much
    better to have it within one class, especially if the rest of your
    code already depends on it.

Nowadays, the Singleton pattern has become so popular that people may
call something a *singleton* even if it solves just one of the listed
problems.

### Solution

All implementations of the Singleton have these two steps in common:

  - Make the default constructor private, to prevent other objects from
    using the `new` operator with the Singleton class.
  - Create a static creation method that acts as a constructor. Under
    the hood, this method calls the private constructor to create an
    object and saves it in a static field. All following calls to this
    method return the cached object.

If your code has access to the Singleton class, then it’s able to call
the Singleton’s static method. So whenever that method is called, the
same object is always returned.

### Structure

![](attachments/463530003/463530333.png)

### Pseudocode

### Real world example

There can only be one president of a country at a time. The same
president has to be brought to action, whenever duty calls. President
here is singleton.

### In plain words

Ensures that only one object of a particular class is ever created.

### Wikipedia says

In software engineering, the singleton pattern is a software design
pattern that restricts the instantiation of a class to one object. This
is useful when exactly one object is needed to coordinate actions across
the system.

Singleton pattern is actually considered an anti-pattern and overuse of
it should be avoided. It is not necessarily bad and could have some
valid use-cases but should be used with caution because it introduces a
global state in your application and change to it in one place could
affect in the other areas and it could become pretty difficult to debug.
The other bad thing about them is it makes your code tightly coupled
plus mocking the singleton could be difficult.

### Pros and Cons



<table>
<thead>
<tr class="header">
<th>Pros</th>
<th>Cons</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>You can be sure that a class has only a single instance.</td>
<td>Violates the <em>Single Responsibility Principle</em> . The pattern solves two problems at the time.</td>
</tr>
<tr class="even">
<td>You gain a global access point to that instance.</td>
<td>The Singleton pattern can mask bad design, for instance, when the components of the program know too much about each other.</td>
</tr>
<tr class="odd">
<td>The singleton object is initialized only when it’s requested for the first time.</td>
<td>The pattern requires special treatment in a multithreaded environment so that multiple threads won’t create a singleton object several times.</td>
</tr>
<tr class="even">
<td><br />
</td>
<td>It may be difficult to unit test the client code of the Singleton because many test frameworks rely on inheritance when producing mock objects. Since the constructor of the singleton class is private and overriding static methods is impossible in most languages, you will need to think of a creative way to mock the singleton. Or just don’t write the tests. Or don’t use the Singleton pattern.</td>
</tr>
</tbody>
</table>



### Programmatic Example

To create a singleton, make the constructor private, disable cloning,
disable extension and create a static variable to house the instance

#### C\#



> 
> 
> ``` 
> public class President
> {
>     static President instance;
>     // Private constructor
>     private President()
>     {
>         //Hiding the Constructor
>     }
> 
>     // Public constructor
>     public static President GetInstance()
>     {
>         if (instance == null) {
>             instance = new President();
>         }
>         return instance;
>     }
> }
>                     
> ```

Then in order to use

> 
> 
> ``` 
> President a = President.GetInstance();
> President b = President.GetInstance();
> 
> Console.WriteLine(a == b); //Output : true
>                     
> ```



#### Java



``` 
public enum EnumIvoryTower {
  INSTANCE;
}
                
```

Then in order to use

``` 
EnumIvoryTower enumIvoryTower1 = EnumIvoryTower.INSTANCE;
EnumIvoryTower enumIvoryTower2 = EnumIvoryTower.INSTANCE;
assertEquals(enumIvoryTower1, enumIvoryTower2); // true
                
```



#### PHP



``` 
final class President
{
    private static $instance;

    private function __construct()
    {
    // Hide the constructor
    }

    public static function getInstance(): President
    {
        if (!self::$instance) {
        self::$instance = new self();
    }

    return self::$instance;
    }

    private function __clone()
    {
    // Disable cloning
    }

    private function __wakeup()
    {
    // Disable unserialize
    }
}
                
```

Then in order to use

``` 
$president1 = President::getInstance();
$president2 = President::getInstance();

var_dump($president1 === $president2); // true

                
```



#### Python



``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?
The Borg pattern (also known as the Monostate pattern) is a way to
implement singleton behavior, but instead of having only one instance
of a class, there are multiple instances that share the same state. In
other words, the focus is on sharing state instead of sharing instance
identity.

*What does this example do?
To understand the implementation of this pattern in Python, it is
important to know that, in Python, instance attributes are stored in a
attribute dictionary called __dict__. Usually, each instance will have
its own dictionary, but the Borg pattern modifies this so that all
instances have the same dictionary.
In this example, the __shared_state attribute will be the dictionary
shared between all instances, and this is ensured by assigining
__shared_state to the __dict__ variable when initializing a new
instance (i.e., in the __init__ method). Other attributes are usually
added to the instance's attribute dictionary, but, since the attribute
dictionary itself is shared (which is __shared_state), all other
attributes will also be shared.
For this reason, when the attribute self.state is modified using
instance rm2, the value of self.state in instance rm1 also changes. The
same happens if self.state is modified using rm3, which is an
instance from a subclass.
Notice that even though they share attributes, the instances are not
the same, as seen by their ids.

*Where is the pattern used practically?
Sharing state is useful in applications like managing database connections:
https://github.com/onetwopunch/pythonDbTemplate/blob/master/database.py

*References:
https://fkromer.github.io/python-pattern-references/design/#singleton

*TL;DR
Provides singleton-like behavior sharing state between instances.
"""


class Borg(object):
    __shared_state = {}

    def __init__(self):
        self.__dict__ = self.__shared_state
        self.state = 'Init'

    def __str__(self):
        return self.state

class YourBorg(Borg):
    pass

if __name__ == '__main__':
    rm1 = Borg()
    rm2 = Borg()

    rm1.state = 'Idle'
    rm2.state = 'Running'

    print('rm1: {0}'.format(rm1))
    print('rm2: {0}'.format(rm2))

    rm2.state = 'Zombie'

    print('rm1: {0}'.format(rm1))
    print('rm2: {0}'.format(rm2))

    print('rm1 id: {0}'.format(id(rm1)))
    print('rm2 id: {0}'.format(id(rm2)))

    rm3 = YourBorg()

    print('rm1: {0}'.format(rm1))
    print('rm2: {0}'.format(rm2))
    print('rm3: {0}'.format(rm3))

### OUTPUT ###
# rm1: Running
# rm2: Running
# rm1: Zombie
# rm2: Zombie
# rm1 id: 140732837899224
# rm2 id: 140732837899296
# rm1: Init
# rm2: Init
# rm3: Init
                
```














