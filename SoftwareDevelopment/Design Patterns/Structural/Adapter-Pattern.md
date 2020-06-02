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

</div>

# Information Technology : Adapter Pattern

</div>

<div id="content" class="view">

## Adapter

![](https://www.oodesign.com/images/structural/adapter-pattern.png)

### Intent

**Adapter** is a structural design pattern that allows objects with
incompatible interfaces to collaborate.

![](attachments/463530012/463530256.png)

### Problem

Imagine that you’re creating a stock market monitoring app. The app
downloads the stock data from multiple sources in XML format and then
displays nice-looking charts and diagrams for the user.

At some point, you decide to improve the app by integrating a smart
3rd-party analytics library. But there’s a catch: the analytics library
only works with data in JSON format.

![](attachments/463530012/463530258.png)

You could change the library to work with XML. However, this might break
some existing code that relies on the library. And worse, you might not
have access to the library’s source code in the first place, making this
approach impossible.

### Solution

You can create an *adapter*. This is a special object that converts the
interface of one object so that another object can understand it.

An adapter wraps one of the objects to hide the complexity of conversion
happening behind the scenes. The wrapped object isn’t even aware of the
adapter. For example, you can wrap an object that operates in meters and
kilometers with an adapter that converts all of the data to imperial
units such as feet and miles.

Adapters can not only convert data into various formats but can also
help objects with different interfaces collaborate. Here’s how it works:

1.  The adapter gets an interface, compatible with one of the existing
    objects.
2.  Using this interface, the existing object can safely call the
    adapter’s methods.
3.  Upon receiving a call, the adapter passes the request to the second
    object, but in a format and order that the second object expects.

Sometimes it’s even possible to create a two-way adapter that can
convert the calls in both directions.

![](attachments/463530012/463530259.png)

Let’s get back to our stock market app. To solve the dilemma of
incompatible formats, you can create XML-to-JSON adapters for every
class of the analytics library that your code works with directly. Then
you adjust your code to communicate with the library only via these
adapters. When an adapter receives a call, it translates the incoming
XML data into a JSON structure and passes the call to the appropriate
methods of a wrapped analytics object.

When you travel from the US to Europe for the first time, you may get a
surprise when trying to charge your laptop. The power plug and sockets
standards are different in different countries. That’s why your US plug
won’t fit a German socket. The problem can be solved by using a power
plug adapter that has the American-style socket and the European-style
plug.

### Structure

#### Object adapter

This implementation uses the object composition principle: the adapter
implements the interface of one object and wraps the other one. It can
be implemented in all popular programming languages.

![](attachments/463530012/463530261.png)

#### Class adapter

This implementation uses inheritance: the adapter inherits interfaces
from both objects at the same time. Note that this approach can only be
implemented in programming languages that support multiple inheritance,
such as C++.

![](attachments/463530012/463530260.png)

### Pseudocode

This example of the **Adapter** pattern is based on the classic conflict
between square pegs and round holes.

![](attachments/463530012/463530257.png)

### Real world example

Consider that you have some pictures in your memory card and you need to
transfer them to your computer. In order to transfer them you need some
kind of adapter that is compatible with your computer ports so that you
can attach memory card to your computer. In this case card reader is an
adapter. Another example would be the famous power adapter; a three
legged plug can't be connected to a two pronged outlet, it needs to use
a power adapter that makes it compatible with the two pronged outlet.
Yet another example would be a translator translating words spoken by
one person to another

### In plain words

Adapter pattern lets you wrap an otherwise incompatible object in an
adapter to make it compatible with another class.

### Wikipedia says

In software engineering, the adapter pattern is a software design
pattern that allows the interface of an existing class to be used as
another interface. It is often used to make existing classes work with
others without modifying their source code.

### Pros and Cons

<div class="table-wrap">

<table>
<thead>
<tr class="header">
<th>Pros</th>
<th>Cons</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><em>Single Responsibility Principle</em>. You can separate the interface or data conversion code from the primary business logic of the program.</td>
<td>The overall complexity of the code increases because you need to introduce a set of new interfaces and classes. Sometimes it’s simpler just to change the service class so that it matches the rest of your code.</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em>. You can introduce new types of adapters into the program without breaking the existing client code, as long as they work with the adapters through the client interface.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

### Programmatic Example

#### C\#

<div>

Consider a game where there is a hunter and he hunts lions.

First we have an interface `Lion` that all types of lions have to
implement

> interface ILion { void Roar(); } class AfricanLion : ILion { public
> void Roar() {} } class AsiaLion : ILion { public void Roar() { } }

And hunter expects any implementation of `Lion` interface to hunt.

> 
> 
> ``` 
> class Hunter
> {
>     public void Hunt(ILion lion) { }
> }
>                     
> ```

Now let's say we have to add a `WildDog` in our game so that hunter can
hunt that also. But we can't do that directly because dog has a
different interface. To make it compatible for our hunter, we will have
to create an adapter that is compatible

> 
> 
> ``` 
>  // This needs to be added to the game
> class WildDog
> {
>     public void bark() { }
> }
> 
> // Adapter around wild dog to make it compatible with our game
> class WildDogAdapter : ILion
> {
>     private WildDog mDog;
>     public WildDogAdapter(WildDog dog) {
>         this.mDog = dog;
>     }
>     public void Roar() {
>         mDog.bark();
>     }
> }
>                     
> ```

And now the `WildDog` can be used in our game using `WildDogAdapter`.

> 
> 
> ``` 
> var wildDog = new WildDog();
> var wildDogAdapter = new WildDogAdapter(wildDog);
> 
> var hunter = new Hunter();
> hunter.Hunt(wildDogAdapter);
>                     
> ```

</div>

#### Java

<div>

First we have interfaces `RowingBoat` and `FishingBoat`

> 
> 
> ``` 
> public interface RowingBoat {
>     void row();
> }
> 
> public class FishingBoat {
>     private static final Logger LOGGER = LoggerFactory.getLogger(FishingBoat.class);
>     public void sail() {
>         LOGGER.info("The fishing boat is sailing");
>     }
> }
>                     
> ```

And captain expects an implementation of `RowingBoat` interface to be
able to move

> 
> 
> ``` 
> public class Captain implements RowingBoat {
>     private RowingBoat rowingBoat;
>     public Captain(RowingBoat rowingBoat) {
>         this.rowingBoat = rowingBoat;
>     }
> 
>     @Override
>     public void row() {
>         rowingBoat.row();
>     }
> }
>                     
> ```

Now let's say the pirates are coming and our captain needs to escape but
there is only fishing boat available. We need to create an adapter that
allows the captain to operate the fishing boat with his rowing boat
skills.

> 
> 
> ``` 
> public class FishingBoatAdapter implements RowingBoat {
>     private static final Logger LOGGER = LoggerFactory.getLogger(FishingBoatAdapter.class);
>     private FishingBoat boat;
>     public FishingBoatAdapter() {
>         boat = new FishingBoat();
>     }
> 
>     @Override
>     public void row() {
>         boat.sail();
>     }
> }
>                     
> ```

And now the `Captain` can use the `FishingBoat` to escape the pirates.

> 
> 
> ``` 
> Captain captain = new Captain(new FishingBoatAdapter());
> captain.row();
>                 
> ```

</div>

#### JavaScript

<div>

Consider a game where there is a hunter and he hunts lions.

First we have an interface `Lion` that all types of lions have to
implement

``` 
/*
Lion interface : roar()
*/

class AfricanLion  {
    roar() {}
}

class AsianLion  {
    roar() {}
}
                
```

And hunter expects any implementation of `Lion` interface to hunt.

``` 
class Hunter {
    hunt(lion) {
        // ... some code before
        lion.roar()
        //... some code after
    }
}
                
```

Now let's say we have to add a `WildDog` in our game so that hunter can
hunt that also. But we can't do that directly because dog has a
different interface. To make it compatible for our hunter, we will have
to create an adapter that is compatible

``` 
// This needs to be added to the game
class WildDog {
    bark() {
    }
}

// Adapter around wild dog to make it compatible with our game
class WildDogAdapter {

    constructor(dog) {
        this.dog = dog;
    }
    
    roar() {
        this.dog.bark();
    }
}
                
```

And now the `WildDog` can be used in our game using `WildDogAdapter`.

``` 
wildDog = new WildDog()
wildDogAdapter = new WildDogAdapter(wildDog)

hunter = new Hunter()
hunter.hunt(wildDogAdapter)
                
```

</div>

#### PHP

<div>

Consider a game where there is a hunter and he hunts lions.

First we have an interface  `Lion` that all types of lions have to
implement interface

``` 
                                                           
interface Lion {  
    public function roar(); 
} 
class AfricanLion implements Lion {  
    public function roar()  {  
    } 
} 
class AsianLion implements Lion {  
    public function roar()  {  } 
}
                
```

And hunter expects any implementation of `Lion` interface to hunt.

``` 
class Hunter
{
    public function hunt(Lion $lion)
    {
        $lion->roar();
    }
}
                
```

Now let's say we have to add a `WildDog` in our game so that hunter can
hunt that also. But we can't do that directly because dog has a
different interface. To make it compatible for our hunter, we will have
to create an adapter that is compatible

``` 
// This needs to be added to the game
class WildDog
{
    public function bark() { }
}

// Adapter around wild dog to make it compatible with our game
class WildDogAdapter implements Lion
{
    protected $dog;
    public function __construct(WildDog $dog) {
        $this->dog = $dog;
    }

    public function roar() {
        $this->dog->bark();
    }
}
                
```

And now the `WildDog` can be used in our game using `WildDogAdapter`.

``` 
$wildDog = new WildDog();
$wildDogAdapter = new WildDogAdapter($wildDog);

$hunter = new Hunter();
$hunter->hunt($wildDogAdapter);                                                 
                
```

</div>

#### Python

<div>

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?
The Adapter pattern provides a different interface for a class. We can
think about it as a cable adapter that allows you to charge a phone
somewhere that has outlets in a different shape. Following this idea,
the Adapter pattern is useful to integrate classes that couldn't be
integrated due to their incompatible interfaces.

*What does this example do?

The example has classes that represent entities (Dog, Cat, Human, Car)
that make different noises. The Adapter class provides a different
interface to the original methods that make such noises. So the
original interfaces (e.g., bark and meow) are available under a
different name: make_noise.

*Where is the pattern used practically?
The Grok framework uses adapters to make objects work with a
particular API without modifying the objects themselves:
http://grok.zope.org/doc/current/grok_overview.html#adapters

*References:
http://ginstrom.com/scribbles/2008/11/06/generic-adapter-class-in-python/
https://sourcemaking.com/design_patterns/adapter
http://python-3-patterns-idioms-test.readthedocs.io/en/latest/ChangeInterface.html#adapter

*TL;DR
Allows the interface of an existing class to be used as another interface.
"""

class Dog(object):
    def __init__(self):
        self.name = "Dog"

    def bark(self):
        return "woof!"

class Cat(object):
    def __init__(self):
        self.name = "Cat"

    def meow(self):
        return "meow!"

class Human(object):
    def __init__(self):
        self.name = "Human"

    def speak(self):
        return "'hello'"

class Car(object):
    def __init__(self):
        self.name = "Car"

    def make_noise(self, octane_level):
        return "vroom{0}".format("!" * octane_level)

class Adapter(object):
    """
    Adapts an object by replacing methods.
    Usage:
    dog = Dog()
    dog = Adapter(dog, make_noise=dog.bark)
    """

    def __init__(self, obj, **adapted_methods):
        """We set the adapted methods in the object's dict"""
        self.obj = obj
        self.__dict__.update(adapted_methods)

    def __getattr__(self, attr):
        """All non-adapted calls are passed to the object"""
        return getattr(self.obj, attr)

    def original_dict(self):
        """Print original object dict"""
        return self.obj.__dict__

def main():
    """
    >>> objects = []
    >>> dog = Dog()
    >>> print(dog.__dict__)
    {'name': 'Dog'}

    >>> objects.append(Adapter(dog, make_noise=dog.bark))

    >>> objects[0].__dict__['obj'], objects[0].__dict__['make_noise']
    (<...Dog object at 0x...>, <bound method Dog.bark of <...Dog object at 0x...>>)

    >>> print(objects[0].original_dict())
    {'name': 'Dog'}

    >>> cat = Cat()
    >>> objects.append(Adapter(cat, make_noise=cat.meow))
    >>> human = Human()
    >>> objects.append(Adapter(human, make_noise=human.speak))
    >>> car = Car()
    >>> objects.append(Adapter(car, make_noise=lambda: car.make_noise(3)))

    >>> for obj in objects:
    ...    print("A {0} goes {1}".format(obj.name, obj.make_noise()))
    A Dog goes woof!
    A Cat goes meow!
    A Human goes 'hello'
    A Car goes vroom!!!
    """

if __name__ == "__main__":
    import doctest
    doctest.testmod(optionflags=doctest.ELLIPSIS)
                
```

</div>

</div>

</div>

<div id="footer" role="contentinfo">

<div class="section footer-body">

</div>

</div>
