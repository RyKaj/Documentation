###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------


# Information Technology : Decorator Pattern


## Decorator

<kbd>![](https://www.oodesign.com/images/structural/decorator-pattern.png)</kbd>

### Intent

**Decorator** is a structural design pattern that lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors.

<img src"./attachments/decorator/463530229.png" />

### Problem

Imagine that you’re working on a notification library which lets other programs notify their users about important events.

The initial version of the library was based on the `Notifier` class that had only a few fields, a constructor and a single `send` method. The method could accept a message argument from a client and send the message to a list of emails that were passed to the notifier via its constructor. A third-party app which acted as a client was supposed to create and configure the notifier object once, and then use it each time something important happened.

<img src"./attachments/decorator/463530231.png" />

At some point, you realize that users of the library expect more than just email notifications. Many of them would like to receive an SMS about critical issues. Others would like to be notified on Facebook and, of course, the corporate users would love to get Slack notifications.

<img src"./attachments/decorator/463530235.png" />

How hard can that be? You extended the `Notifier` class and put the additional notification methods into new subclasses. Now the client was supposed to instantiate the desired notification class and use it for all further notifications.

But then someone reasonably asked you, “Why can’t you use several notification types at once? If your house is on fire, you’d probably want to be informed through every channel.”

You tried to address that problem by creating special subclasses which combined several notification methods within one class. However, it quickly became apparent that this approach would bloat the code immensely, not only the library code but the client code as well.

<img src"./attachments/decorator/463530233.png" />

You have to find some other way to structure notifications classes so that their number won’t accidentally break some Guinness record.

### Solution

Extending a class is the first thing that comes to mind when you need to alter an object’s behavior. However, inheritance has several serious caveats that you need to be aware of.

  - Inheritance is static. You can’t alter the behavior of an existing object at runtime. You can only replace the whole object with another one that’s created from a different subclass.
  - Subclasses can have just one parent class. In most languages, inheritance doesn’t let a class inherit behaviors of multiple classes at the same time.

One of the ways to overcome these caveats is by using *Aggregation* or *Composition* instead of *Inheritance*. Both of the alternatives work almost the same way: one object *has a* reference to another and delegates it some work, whereas with inheritance, the object itself *is* able to do that work, inheriting the behavior from its superclass.

With this new approach you can easily substitute the linked “helper” object with another, changing the behavior of the container at runtime. An object can use the behavior of various classes, having references to multiple objects and delegating them all kinds of work. Aggregation/composition is the key principle behind many design patterns, including Decorator. On that note, let’s return to the pattern discussion.

<img src"./attachments/decorator/463530234.png" />

*Wrapper* is the alternative nickname for the Decorator pattern that clearly expresses the main idea of the pattern. A “wrapper” is an object that can be linked with some “target” object. The wrapper contains the same set of methods as the target and delegates to it all requests it receives. However, the wrapper may alter the result by doing something either before or after it passes the request to the target.

When does a simple wrapper become the real decorator? As I mentioned, the wrapper implements the same interface as the wrapped object. That’s why from the client’s perspective these objects are identical. Make the wrapper’s reference field accept any object that follows that interface. This will let you cover an object in multiple wrappers, adding the combined behavior of all the wrappers to it.

In our notifications example, let’s leave the simple email notification behavior inside the base `Notifier` class, but turn all other notification methods into decorators.

<img src"./attachments/decorator/463530232.png" />

The client code would need to wrap a basic notifier object into a set of decorators that match the client’s preferences. The resulting objects will be structured as a stack.

<img src"./attachments/decorator/463530236.png" />

The last decorator in the stack would be the object that the client actually works with. Since all decorators implement the same interface as the base notifier, the rest of the client code won’t care whether it works with the “pure” notifier object or the decorated one.

We could apply the same approach to other behaviors such as formatting messages or composing the recipient list. The client can decorate the object with any custom decorators, as long as they follow the same interface as the others.

### Structure

<img src"./attachments/decorator/463530237.png" />

### Pseudocode

In this example, the **Decorator** pattern lets you compress and encrypt sensitive data independently from the code that actually uses this data.

<img src"./attachments/decorator/463530230.png" />

The application wraps the data source object with a pair of decorators. Both wrappers change the way the data is written to and read from the disk:

  - Just before the data is **written to disk**, the decorators encrypt and compress it. The original class writes the encrypted and protected data to the file without knowing about the change.

  - Right after the data is **read from disk**, it goes through the same     decorators, which decompress and decode it.

The decorators and the data source class implement the same interface, which makes them all interchangeable in the client code.

### Real world example

Imagine you run a car service shop offering multiple services. Now how do you calculate the bill to be charged? You pick one service and dynamically keep adding to it the prices for the provided services till you get the final cost. Here each type of service is a decorator.

### In plain words

Decorator pattern lets you dynamically change the behavior of an object at run time by wrapping them in an object of a decorator class.

### Wikipedia says

In object-oriented programming, the decorator pattern is a design pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class. The decorator pattern is often useful for adhering to the Single Responsibility Principle, as it allows functionality to be divided between classes with unique areas of concern.

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
            <td>You can extend an object’s behavior without making a new subclass.</td>
            <td>It’s hard to remove a specific wrapper from the wrappers stack.</td>
        </tr>
        <tr class="even">
            <td>You can add or remove responsibilities from an object at runtime.</td>
            <td>It’s hard to implement a decorator in such a way that its behavior doesn’t depend on the order in the decorators stack.</td>
        </tr>
        <tr class="odd">
            <td>You can combine several behaviors by wrapping an object into multiple decorators.</td>
            <td>The initial configuration code of layers might look pretty ugly.</td>
        </tr>
        <tr class="even">
            <td><em>Single Responsibility Principle</em>. You can divide a monolithic class that implements many possible variants of behavior into several smaller classes.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

Lets take coffee for example. First of all we have a simple coffee implementing the coffee interface

#### C\#



> 
> 
> ``` 
> interface ICoffee
> {
>     int GetCost();
>     string GetDescription();
> }
> 
> class SimpleCoffee : ICoffee
> {
>     public int GetCost() {
>         return 5;
>     }
> 
>     public string GetDescription() {
>         return "Simple Coffee";
>     }
> }
>                     
> ```

We want to make the code extensible to allow options to modify it if required. Lets make some add-ons (decorators)

> 
> 
> ``` 
> class MilkCoffee : ICoffee
> {
>     private readonly ICoffee mCoffee;
> 
>     public MilkCoffee(ICoffee coffee)
>     {
>         mCoffee = coffee ?? throw new ArgumentNullException("coffee", "coffee should not be null");
>     }
>     public int GetCost()
>     {
>         return mCoffee.GetCost() + 1;
>     }
> 
>     public string GetDescription()
>     {
>         return String.Concat(mCoffee.GetDescription(), ", milk");
>     }
> }
> 
> class WhipCoffee : ICoffee
> {
>     private readonly ICoffee mCoffee;
> 
>     public WhipCoffee(ICoffee coffee)
>     {
>         mCoffee = coffee ?? throw new ArgumentNullException("coffee", "coffee should not be null");
>     }
>     public int GetCost()
>     {
>         return mCoffee.GetCost() + 1;
>     }
> 
>     public string GetDescription()
>     {
>         return String.Concat(mCoffee.GetDescription(), ", whip");
>     }
> }
> 
> class VanillaCoffee : ICoffee
> {
>     private readonly ICoffee mCoffee;
> 
>     public VanillaCoffee(ICoffee coffee)
>     {
>         mCoffee = coffee ?? throw new ArgumentNullException("coffee", "coffee should not be null");
>     }
>     public int GetCost()
>     {
>         return mCoffee.GetCost() + 1;
>     }
> 
>     public string GetDescription()
>     {
>         return String.Concat(mCoffee.GetDescription(), ", vanilla");
>     }
> }
>                     
> ```

Lets make a coffee now

> 
> 
> ``` 
> var myCoffee = new SimpleCoffee();
> Console.WriteLine($"{myCoffee.GetCost():c}"); // $ 5.00
> Console.WriteLine(myCoffee.GetDescription()); // Simple Coffee
> 
> var milkCoffee = new MilkCoffee(myCoffee);
> Console.WriteLine($"{milkCoffee.GetCost():c}"); // $ 6.00
> Console.WriteLine(milkCoffee.GetDescription()); // Simple Coffee, milk
> 
> var whipCoffee = new WhipCoffee(milkCoffee);
> Console.WriteLine($"{whipCoffee.GetCost():c}"); // $ 7.00
> Console.WriteLine(whipCoffee.GetDescription()); // Simple Coffee, milk, whip
> 
> var vanillaCoffee = new VanillaCoffee(whipCoffee);
> Console.WriteLine($"{vanillaCoffee.GetCost():c}"); // $ 8.00
> Console.WriteLine(vanillaCoffee.GetDescription()); // Simple Coffee, milk, whip, vanilla
>                     
> ```



#### Java



Let's take the troll example. First of all we have a simple troll implementing the troll interface

``` 
public interface Troll {
    void attack();
    int getAttackPower();
    void fleeBattle();
}

public class SimpleTroll implements Troll {
    private static final Logger LOGGER = LoggerFactory.getLogger(SimpleTroll.class);

    @Override
    public void attack() {
        LOGGER.info("The troll tries to grab you!");
    }

    @Override
    public int getAttackPower() {
        return 10;
    }

    @Override
    public void fleeBattle() {
        LOGGER.info("The troll shrieks in horror and runs away!");
    }
}
                
```

Next we want to add club for the troll. We can do it dynamically by using a decorator

``` 
public class ClubbedTroll implements Troll {
    private static final Logger LOGGER = LoggerFactory.getLogger(ClubbedTroll.class);
    private Troll decorated;

    public ClubbedTroll(Troll decorated) {
        this.decorated = decorated;
    }

    @Override
    public void attack() {
        decorated.attack();
        LOGGER.info("The troll swings at you with a club!");
    }

    @Override
    public int getAttackPower() {
        return decorated.getAttackPower() + 10;
    }

    @Override
    public void fleeBattle() {
        decorated.fleeBattle();
    }
}
                
```

Here's the troll in action

``` 
// simple troll
Troll troll = new SimpleTroll();
troll.attack(); // The troll tries to grab you!
troll.fleeBattle(); // The troll shrieks in horror and runs away!

// change the behavior of the simple troll by adding a decorator
Troll clubbedTroll = new ClubbedTroll(troll);
clubbedTroll.attack(); // The troll tries to grab you! The troll swings at you with a club!
clubbedTroll.fleeBattle(); // The troll shrieks in horror and runs away!
                
```



#### JavaScript



Lets take coffee for example. First of all we have a simple coffee implementing the coffee interface

``` 
/*
Coffee interface:
getCost()
getDescription()
*/

class SimpleCoffee{

    getCost() {
        return 10
    }

    getDescription() {
        return 'Simple coffee'
    }
}
                
```

We want to make the code extensible to allow options to modify it if required. Lets make some add-ons (decorators)

``` 
class MilkCoffee {
    constructor(coffee) {
        this.coffee = coffee
    }
    getCost() {
        return this.coffee.getCost() + 2
    }
    getDescription() {
        return this.coffee.getDescription() + ', milk'
    }
}

class WhipCoffee {
    constructor(coffee) {
        this.coffee = coffee
    }
    getCost() {
        return this.coffee.getCost() + 5
    }
    getDescription() {
        return this.coffee.getDescription() + ', whip'
    }
}

class VanillaCoffee {
    constructor(coffee) {
        this.coffee = coffee
    }
    getCost() {
        return this.coffee.getCost() + 3
    }
    getDescription() {
        return this.coffee.getDescription() + ', vanilla'
    }
}
                
```

Lets make a coffee now

``` 
let someCoffee

someCoffee = new SimpleCoffee()
console.log(someCoffee.getCost())// 10
console.log(someCoffee.getDescription())// Simple Coffee

someCoffee = new MilkCoffee(someCoffee)
console.log(someCoffee.getCost())// 12
console.log(someCoffee.getDescription())// Simple Coffee, milk

someCoffee = new WhipCoffee(someCoffee)
console.log(someCoffee.getCost())// 17
console.log(someCoffee.getDescription())// Simple Coffee, milk, whip

someCoffee = new VanillaCoffee(someCoffee)
console.log(someCoffee.getCost())// 20
console.log(someCoffee.getDescription())// Simple Coffee, milk, whip, vanilla
                
```



#### PHP



``` 
interface Coffee
{
    public function getCost();
    public function getDescription();
}

class SimpleCoffee implements Coffee
{
    public function getCost() {
        return 10;
    }

    public function getDescription() {
        return 'Simple coffee';
    }
}
                
```

We want to make the code extensible to allow options to modify it if required. Lets make some add-ons (decorators)

``` 
class MilkCoffee implements Coffee
{
    protected $coffee;
    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 2;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', milk';
    }
}

class WhipCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 5;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', whip';
    }
}

class VanillaCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 3;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', vanilla';
    }
}
                
```

Lets make a coffee now

``` 
$someCoffee = new SimpleCoffee();
echo $someCoffee->getCost(); // 10
echo $someCoffee->getDescription(); // Simple Coffee

$someCoffee = new MilkCoffee($someCoffee);
echo $someCoffee->getCost(); // 12
echo $someCoffee->getDescription(); // Simple Coffee, milk

$someCoffee = new WhipCoffee($someCoffee);
echo $someCoffee->getCost(); // 17
echo $someCoffee->getDescription(); // Simple Coffee, milk, whip

$someCoffee = new VanillaCoffee($someCoffee);
echo $someCoffee->getCost(); // 20
echo $someCoffee->getDescription(); // Simple Coffee, milk, whip, vanilla
                
```



#### Python



``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?
The Decorator pattern is used to dynamically add a new feature to an object without changing its implementation. It differs from inheritance because the new feature is added only to that particular object, not to the entire subclass.

*What does this example do?
This example shows a way to add formatting options (boldface and italic) to a text by appending the corresponding tags (<b> and <i>). Also, we can see that decorators can be applied one after the other, since the original text is passed to the bold wrapper, which in turn is passed to the italic wrapper.

*Where is the pattern used practically? The Grok framework uses decorators to add functionalities to methods, like permissions or subscription to an event: http://grok.zope.org/doc/current/reference/decorators.html

*References:
https://sourcemaking.com/design_patterns/decorator

*TL;DR
Adds behaviour to object without affecting its class.
"""

from __future__ import print_function


class TextTag(object):
    """Represents a base text tag"""

    def __init__(self, text):
        self._text = text

    def render(self):
        return self._text

class BoldWrapper(TextTag):
    """Wraps a tag in <b>"""

    def __init__(self, wrapped):
        self._wrapped = wrapped

    def render(self):
        return "<b>{}</b>".format(self._wrapped.render())

class ItalicWrapper(TextTag):
    """Wraps a tag in <i>"""

    def __init__(self, wrapped):
        self._wrapped = wrapped

    def render(self):
        return "<i>{}</i>".format(self._wrapped.render())

if __name__ == '__main__':
    simple_hello = TextTag("hello, world!")
    special_hello = ItalicWrapper(BoldWrapper(simple_hello))
    print("before:", simple_hello.render())
    print("after:", special_hello.render())

### OUTPUT ###
# before: hello, world!
# after: <i><b>hello, world!</b></i>
                
```


