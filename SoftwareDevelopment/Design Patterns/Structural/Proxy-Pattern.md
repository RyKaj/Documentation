<div id="main" class="aui-page-panel">

<div id="main-header">

<div id="breadcrumb-section">

1.  [Information Technology](index.html)
2.  [3.0 Sofware Development
    Lifecycle](3.0-Sofware-Development-Lifecycle_380470491.html)
3.  [Design Patterns](Design-Patterns_451820045.html)
4.  [1.0 Design Pattern - Programming
    Language](1.0-Design-Pattern---Programming-Language_451820065.html)
5.  [Structural Design
    Patterns](Structural-Design-Patterns_451820122.html)



# Information Technology : Proxy Pattern





## Proxy

![](https://www.oodesign.com/images/structural/proxy-pattern.png)

### Intent

**Proxy** is a structural design pattern that lets you provide a
substitute or placeholder for another object. A proxy controls access to
the original object, allowing you to perform something either before or
after the request gets through to the original object.

![](attachments/463530019/463530208.png)

### Problem

Why would you want to control access to an object? Here is an example:
you have a massive object that consumes a vast amount of system
resources. You need it from time to time, but not always.

![](attachments/463530019/463530210.png)

You could implement lazy initialization: create this object only when
it’s actually needed. All of the object’s clients would need to
execute some deferred initialization code. Unfortunately, this would
probably cause a lot of code duplication.

In an ideal world, we’d want to put this code directly into our object’s
class, but that isn’t always possible. For instance, the class may be
part of a closed 3rd-party library.

### Solution

The Proxy pattern suggests that you create a new proxy class with the
same interface as an original service object. Then you update your app
so that it passes the proxy object to all of the original object’s
clients. Upon receiving a request from a client, the proxy creates a
real service object and delegates all the work to it.

![](attachments/463530019/463530211.png)

But what’s the benefit? If you need to execute something either before
or after the primary logic of the class, the proxy lets you do this
without changing that class. Since the proxy implements the same
interface as the original class, it can be passed to any client that
expects a real service object.

### Structure

![](attachments/463530019/463530212.png)

### Pseudocode

This example illustrates how the **Proxy** pattern can help to introduce
lazy initialization and caching to a 3rd-party YouTube integration
library.

![](attachments/463530019/463530209.png)

The library provides us with the video downloading class. However, it’s
very inefficient. If the client application requests the same video
multiple times, the library just downloads it over and over, instead of
caching and reusing the first downloaded file.

The proxy class implements the same interface as the original downloader
and delegates it all the work. However, it keeps track of the downloaded
files and returns the cached result when the app requests the same video
multiple times.

### Real world example

Have you ever used an access card to go through a door? There are
multiple options to open that door i.e. it can be opened either using
access card or by pressing a button that bypasses the security. The
door's main functionality is to open but there is a proxy added on top
of it to add some functionality. Let me better explain it using the code
example below.

### In plain words

Using the proxy pattern, a class represents the functionality of another
class.

### Wikipedia says

A proxy, in its most general form, is a class functioning as an
interface to something else. A proxy is a wrapper or agent object that
is being called by the client to access the real serving object behind
the scenes. Use of the proxy can simply be forwarding to the real
object, or can provide additional logic. In the proxy extra
functionality can be provided, for example caching when operations on
the real object are resource intensive, or checking preconditions before
operations on the real object are invoked.

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
<td>You can control the service object without clients knowing about it.</td>
<td>The code may become more complicated since you need to introduce a lot of new classes.</td>
</tr>
<tr class="even">
<td>You can manage the lifecycle of the service object when clients don’t care about it.</td>
<td>The response from the service might get delayed</td>
</tr>
<tr class="odd">
<td>The proxy works even if the service object isn’t ready or is not available.</td>
<td><br />
</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em>. You can introduce new proxies without changing the service or clients.</td>
<td><br />
</td>
</tr>
</tbody>
</table>



### Programmatic Example

Taking our security door example from above. Firstly we have the door
interface and an implementation of door

#### C\#



> 
> 
> ``` 
> interface IDoor
> {
>     void Open();
>     void Close();
> }
> 
> class LabDoor : IDoor
> {
>     public void Close()
>     {
>         Console.WriteLine("Closing lab door");
>     }
> 
>     public void Open()
>     {
>         Console.WriteLine("Opening lab door");
>     }
> }
>                     
> ```

Then we have a proxy to secure any doors that we want

> 
> 
> ``` 
> class SecuredDoor
> {
>     private IDoor mDoor;
> 
>     public SecuredDoor(IDoor door)
>     {
>         mDoor = door ?? throw new ArgumentNullException("door", "door can not be null");
>     }
> 
>     public void Open(string password)
>     {
>         if (Authenticate(password))
>         {
>             mDoor.Open();
>         }
>         else
>         {
>             Console.WriteLine("Big no! It ain't possible.");
>         }
>     }
> 
>     private bool Authenticate(string password)
>     {
>         return password == "$ecr@t";
>     }
> 
>     public void Close()
>     {
>         mDoor.Close();
>     }
> }
>                     
> ```

And here is how it can be used

> 
> 
> ``` 
> var door = new SecuredDoor(new LabDoor());
> door.Open("invalid"); // Big no! It ain't possible.
> 
> door.Open("$ecr@t"); // Opening lab door
> door.Close(); // Closing lab door
>                     
> ```



#### Java

Taking our wizard tower example from above. Firstly we have the wizard
tower interface and the ivory tower class

``` 
public interface WizardTower {
    void enter(Wizard wizard);
}

public class IvoryTower implements WizardTower {
    private static final Logger LOGGER = LoggerFactory.getLogger(IvoryTower.class);
    public void enter(Wizard wizard) {
        LOGGER.info("{} enters the tower.", wizard);
    }
}
            
```

Then a simple wizard class

``` 
public class Wizard {

    private final String name;

    public Wizard(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return name;
    }
}
            
```

Then we have the proxy to add access control to wizard tower

``` 
public class WizardTowerProxy implements WizardTower {
    private static final Logger LOGGER = LoggerFactory.getLogger(WizardTowerProxy.class);
    private static final int NUM_WIZARDS_ALLOWED = 3;
    private int numWizards;
    private final WizardTower tower;

    public WizardTowerProxy(WizardTower tower) {
        this.tower = tower;
    }

    @Override
    public void enter(Wizard wizard) {
        if (numWizards < NUM_WIZARDS_ALLOWED) {
            tower.enter(wizard);
            numWizards++;
        } else {
            LOGGER.info("{} is not allowed to enter!", wizard);
        }
    }
}
            
```

And here is tower entering scenario

``` 
WizardTowerProxy proxy = new WizardTowerProxy(new IvoryTower());
proxy.enter(new Wizard("Red wizard")); // Red wizard enters the tower.
proxy.enter(new Wizard("White wizard")); // White wizard enters the tower.
proxy.enter(new Wizard("Black wizard")); // Black wizard enters the tower.
proxy.enter(new Wizard("Green wizard")); // Green wizard is not allowed to enter!
proxy.enter(new Wizard("Brown wizard")); // Brown wizard is not allowed to enter!
            
```



#### JavaScript



Taking our security door example from above. Firstly we have the door
interface and an implementation of door

``` 
/*
Door interface :
    open()
    close()
*/

class LabDoor {
    open() {
        console.log('Opening lab door')
    }

    close() {
        console.log('Closing the lab door')
    }
}
            
```

Then we have a proxy to secure any doors that we want

``` 
class Security {
    constructor(door) {
        this.door = door
    }

    open(password) {
        if (this.authenticate(password)) {
            this.door.open()
        } else {
            console.log('Big no! It ain\'t possible.')
        }
    }

    authenticate(password) {
        return password === 'ecr@t'
    }

    close() {
        this.door.close()
    }
}
            
```

And here is how it can be used

``` 
const door = new Security(new LabDoor())
door.open('invalid') // Big no! It ain't possible.

door.open('ecr@t') // Opening lab door
door.close() // Closing lab door

            
```



#### PHP



``` 
interface Door {
    public function open();
    public function close();
}

class LabDoor implements Door {
    public function open() {
        echo "Opening lab door";
    }

    public function close() {
        echo "Closing the lab door";
    }
}
            
```

Then we have a proxy to secure any doors that we want

``` 
class SecuredDoor
{
    protected $door;

    public function __construct(Door $door)
    {
        $this->door = $door;
    }

    public function open($password)
    {
        if ($this->authenticate($password)) {
            $this->door->open();
        } else {
            echo "Big no! It ain't possible.";
        }
    }

    public function authenticate($password)
    {
        return $password === '$ecr@t';
    }

    public function close()
    {
        $this->door->close();
    }
}
            
```

And here is how it can be used

``` 
$door = new SecuredDoor(new LabDoor());
$door->open('invalid'); // Big no! It ain't possible.

$door->open('$ecr@t'); // Opening lab door
$door->close(); // Closing lab door
            
```



Yet another example would be some sort of data-mapper implementation.
For example, I recently made an ODM (Object Data Mapper) for MongoDB
using this pattern where I wrote a proxy around mongo classes while
utilizing the magic method `  __call()  `. All the method calls were
proxied to the original mongo class and result retrieved was returned as
it is but in case of  `find` or `findOne` data was mapped to the
required class objects and the object was returned instead of `Cursor`.

#### Python



``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*TL;DR
Provides an interface to resource that is expensive to duplicate.
"""

from __future__ import print_function
import time

class SalesManager:
    def talk(self):
        print("Sales Manager ready to talk")

class Proxy:
    def __init__(self):
        self.busy = 'No'
        self.sales = None

    def talk(self):
        print("Proxy checking for Sales Manager availability")
        if self.busy == 'No':
            self.sales = SalesManager()
            time.sleep(0.1)
            self.sales.talk()
        else:
            time.sleep(0.1)
            print("Sales Manager is busy")

class NoTalkProxy(Proxy):
    def talk(self):
        print("Proxy checking for Sales Manager availability")
        time.sleep(0.1)
        print("This Sales Manager will not talk to you", "whether he/she is busy or not")

if __name__ == '__main__':
    p = Proxy()
    p.talk()
    p.busy = 'Yes'
    p.talk()
    p = NoTalkProxy()
    p.talk()
    p.busy = 'Yes'
    p.talk()

### OUTPUT ###
# Proxy checking for Sales Manager availability
# Sales Manager ready to talk
# Proxy checking for Sales Manager availability
# Sales Manager is busy
# Proxy checking for Sales Manager availability
# This Sales Manager will not talk to you whether he/she is busy or not
# Proxy checking for Sales Manager availability
# This Sales Manager will not talk to you whether he/she is busy or not
                
```












