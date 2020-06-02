###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------

# Information Technology : Factory Method Pattern


## Factory Method

<kbd>![](https://www.oodesign.com/images/creational/factory-method-pattern.gif)</kbd>

### Intent

**Factory Method** is a creational design pattern that provides an
interface for creating objects in a superclass, but allows subclasses to
alter the type of objects that will be created.

<kbd>![](./attachments/factory/463530165.png)</kbd>

### Problem

Imagine that you’re creating a logistics management application. The
first version of your app can only handle transportation by trucks, so
the bulk of your code lives inside the `Truck` class.

After a while, your app becomes pretty popular. Each day you receive
dozens of requests from sea transportation companies to incorporate sea
logistics into the app.

<kbd>![](./attachments/factory/463530167.png)</kbd>

Great news, right? But how about the code? At present, most of your code
is coupled to the `Truck` class. Adding `Ships` into the app would
require making changes to the entire codebase. Moreover, if later you
decide to add another type of transportation to the app, you will
probably need to make all of these changes again.

As a result, you will end up with pretty nasty code, riddled with
conditionals that switch the app’s behavior depending on the class of
transportation objects.

### Solution

The Factory Method pattern suggests that you replace direct object
construction calls (using the `new` operator) with calls to a special
*factory* method. Don’t worry: the objects are still created via the
`new` operator, but it’s being called from within the factory method.
Objects returned by a factory method are often referred to as
“products.”

<kbd>![](./attachments/factory/463530168.png)</kbd>

At first glance, this change may look pointless: we just moved the
constructor call from one part of the program to another. However,
consider this: now you can override the factory method in a subclass and
change the class of products being created by the method.

There’s a slight limitation though: subclasses may return different
types of products only if these products have a common base class or
interface. Also, the factory method in the base class should have its
return type declared as this interface.

<kbd>![](./attachments/factory/463530169.png)</kbd>

For example, both `Truck` and `Ship` classes should implement
the`Transport` interface, which declares a method called`deliver`. Each
class implements this method differently: trucks deliver cargo by land,
ships deliver cargo by sea. The factory method in the `RoadLogistics`
class returns truck objects, whereas the factory method in the
`SeaLogistics` class returns ships.

<kbd>![](./attachments/factory/463530170.png)</kbd>

The code that uses the factory method (often called the *client* code)
doesn’t see a difference between the actual products returned by various
subclasses. The client treats all the products as abstract `Transport` .
The client knows that all transport objects are supposed to have the
`deliver` method, but exactly how it works isn’t important to the
client.

### Structure

<kbd>![](./attachments/factory/463530171.png)</kbd>

### Pseudocode

This example illustrates how the **Factory Method** can be used for
creating cross-platform UI elements without coupling the client code to
concrete UI classes.

<kbd>![](./attachments/factory/463530166.png)</kbd>

The base dialog class uses different UI elements to render its window.
Under various operating systems, these elements may look a little bit
different, but they should still behave consistently. A button in
Windows is still a button in Linux.

When the factory method comes into play, you don’t need to rewrite the
logic of the dialog for each operating system. If we declare a factory
method that produces buttons inside the base dialog class, we can later
create a dialog subclass that returns Windows-styled buttons from the
factory method. The subclass then inherits most of the dialog’s code
from the base class, but, thanks to the factory method, can render
Windows-looking buttons on the screen.

For this pattern to work, the base dialog class must work with abstract
buttons: a base class or an interface that all concrete buttons follow.
This way the dialog’s code remains functional, whichever type of buttons
it works with.

Of course, you can apply this approach to other UI elements as well.
However, with each new factory method you add to the dialog, you get
closer to the [Abstract
Factory](https://refactoring.guru/design-patterns/abstract-factory)
pattern. Fear not, we’ll talk about this pattern later.

### Real world example

Consider the case of a hiring manager. It is impossible for one person
to interview for each of the positions. Based on the job opening, she
has to decide and delegate the interview steps to different people.

### In plain words

It provides a way to delegate the instantiation logic to child classes.

### Wikipedia says

In class-based programming, the factory method pattern is a creational
pattern that uses factory methods to deal with the problem of creating
objects without having to specify the exact class of the object that
will be created. This is done by creating objects by calling a factory
method—either specified in an interface and implemented by child
classes, or implemented in a base class and optionally overridden by
derived classes—rather than by calling a constructor.

### Programmatic Example

Taking our hiring manager example above. First of all we have an
interviewer interface and some implementations for it

#### C\#



> 
> 
> ``` 
> interface IInterviewer
> {
>     void AskQuestions();
> }
> 
> class Developer : IInterviewer
> {
>     public void AskQuestions()
>     {
>         Console.WriteLine("Asking about design patterns!");
>     }
> }
> 
> class CommunityExecutive : IInterviewer
> {
>     public void AskQuestions()
>     {
>         Console.WriteLine("Asking about community building!");
>     }
> }
>                     
> ```

Now let us create our `HiringManager`

> 
> 
> ``` 
> abstract class HiringManager
> {
>     // Factory method
>     abstract protected IInterviewer MakeInterviewer();
>     public void TakeInterview()
>     {
>         var interviewer = this.MakeInterviewer();
>         interviewer.AskQuestions();
>     }
> }
> 
>                     
> ```

Now any child can extend it and provide the required interviewer

> 
> 
> ``` 
> class DevelopmentManager : HiringManager
> {
>     protected override IInterviewer MakeInterviewer()
>     {
>         return new Developer();
>     }
> }
> 
>     class MarketingManager : HiringManager
>     {
>         protected override IInterviewer MakeInterviewer()
>         {
>         return new CommunityExecutive();
>     }
> }
>                     
> ```

and then it can be used as

> 
> 
> ``` 
> var devManager = new DevelopmentManager();
> devManager.TakeInterview(); //Output : Asking about design patterns!
> 
> var marketingManager = new MarketingManager();
> marketingManager.TakeInterview();//Output : Asking about community building!
> 
>                     
> ```



#### Java



``` 
public interface Blacksmith {
    Weapon manufactureWeapon(WeaponType weaponType);
}

public class ElfBlacksmith implements Blacksmith {
    public Weapon manufactureWeapon(WeaponType weaponType) {
        return new ElfWeapon(weaponType);
    }
}

public class OrcBlacksmith implements Blacksmith {
    public Weapon manufactureWeapon(WeaponType weaponType) {
        return new OrcWeapon(weaponType);
    }
}
                
```

Now as the customers come the correct type of blacksmith is summoned and
requested weapons are manufactured

``` 
Blacksmith blacksmith = new ElfBlacksmith();
blacksmith.manufactureWeapon(WeaponType.SPEAR);
blacksmith.manufactureWeapon(WeaponType.AXE);
// Elvish weapons are created
                
```



#### PHP



``` 
interface Interviewer
{
    public function askQuestions();
}

class Developer implements Interviewer
{
    public function askQuestions()
    {
        echo 'Asking about design patterns!';
    }
}

class CommunityExecutive implements Interviewer
{
    public function askQuestions()
    {
        echo 'Asking about community building';
    }
}
                
```

Now let us create our `HiringManager`

``` 

abstract class HiringManager
{
    // Factory method
    abstract protected function makeInterviewer(): Interviewer;

    public function takeInterview()
    {
        $interviewer = $this->makeInterviewer();
        $interviewer->askQuestions();
    }
}

                
```

Now any child can extend it and provide the required interviewer

``` 
class DevelopmentManager extends HiringManager
{
    protected function makeInterviewer(): Interviewer
    {
        return new Developer();
    }
}

    class MarketingManager extends HiringManager
    {
        protected function makeInterviewer(): Interviewer
        {
            return new CommunityExecutive();
    }
}               
```

and then it can be used as

``` 
$devManager = new DevelopmentManager();
$devManager->takeInterview(); // Output: Asking about design patterns

$marketingManager = new MarketingManager();
$marketingManager->takeInterview(); // Output: Asking about community building.
                
```



#### Python



``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""*What is this pattern about?
A Factory is an object for creating other objects.

*What does this example do?
The code shows a way to localize words in two languages: English and
Greek. "get_localizer" is the factory function that constructs a
localizer depending on the language chosen. The localizer object will
be an instance from a different class according to the language
localized. However, the main code does not have to worry about which
localizer will be instantiated, since the method "localize" will be called
in the same way independently of the language.

*Where can the pattern be used practically?
The Factory Method can be seen in the popular web framework Django:
http://django.wikispaces.asu.edu/*NEW*+Django+Design+Patterns For
example, in a contact form of a web page, the subject and the message
fields are created using the same form factory (CharField()), even
though they have different implementations according to their
purposes.

*References:
http://ginstrom.com/scribbles/2007/10/08/design-patterns-python-style/

*TL;DR
Creates objects without having to specify the exact class.
"""

from __future__ import unicode_literals
from __future__ import print_function

class GreekLocalizer(object):
    """A simple localizer a la gettext"""

    def __init__(self):
        self.translations = {"dog": "σκύλος", "cat": "γάτα"}

    def localize(self, msg):
        """We'll punt if we don't have a translation"""
        return self.translations.get(msg, msg)

class EnglishLocalizer(object):
    """Simply echoes the message"""

    def localize(self, msg):
        return msg

def get_localizer(language="English"):
    """Factory"""
    localizers = {
        "English": EnglishLocalizer,
        "Greek": GreekLocalizer,
    }
    return localizers[language]()

def main():
    """
    # Create our localizers
    >>> e, g = get_localizer(language="English"), get_localizer(language="Greek")

    # Localize some text
    >>> for msg in "dog parrot cat bear".split():
    ...     print(e.localize(msg), g.localize(msg))
    dog σκύλος
    parrot parrot
    cat γάτα
    bear bear
    """

if __name__ == "__main__":
    import doctest
    doctest.testmod()
                
```





### When to use?

Useful when there is some generic processing in a class but the required
sub-class is dynamically decided at runtime. Or putting it in other
words, when the client doesn't know what exact sub-class it might need.



