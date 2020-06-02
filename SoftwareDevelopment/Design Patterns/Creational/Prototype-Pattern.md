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



# Information Technology : Prototype Pattern





## Prototype

![](https://www.oodesign.com/images/creational/prototype-pattern.gif)

### Intent

**Prototype** is a creational design pattern that lets you copy existing
objects without making your code dependent on their classes.

![](attachments/463530002/463530194.png)

### Problem

Say you have an object, and you want to create an exact copy of it. How
would you do it? First, you have to create a new object of the same
class. Then you have to go through all the fields of the original object
and copy their values over to the new object.

Nice\! But there’s a catch. Not all objects can be copied that way
because some of the object’s fields may be private and not visible from
outside of the object itself.

![](attachments/463530002/463530196.png)

There’s one more problem with the direct approach. Since you have to
know the object’s class to create a duplicate, your code becomes
dependent on that class. If the extra dependency doesn’t scare you,
there’s another catch. Sometimes you only know the interface that the
object follows, but not its concrete class, when, for example, a
parameter in a method accepts any objects that follow some interface.

### Solution

The Prototype pattern delegates the cloning process to the actual
objects that are being cloned. The pattern declares a common interface
for all objects that support cloning. This interface lets you clone an
object without coupling your code to the class of that object. Usually,
such an interface contains just a single `clone` method.

The implementation of the `clone` method is very similar in all classes.
The method creates an object of the current class and carries over all
of the field values of the old object into the new one. You can even
copy private fields because most programming languages let objects
access private fields of other objects that belong to the same class.

An object that supports cloning is called a *prototype*. When your
objects have dozens of fields and hundreds of possible configurations,
cloning them might serve as an alternative to subclassing.

![](attachments/463530002/463530197.png)

Here’s how it works: you create a set of objects, configured in various
ways. When you need an object like the one you’ve configured, you just
clone a prototype instead of constructing a new object from scratch.

### Structure

#### Base Implementation

![](attachments/463530002/463530199.png)

#### Prototype Registry Implementation

![](attachments/463530002/463530200.png)

### Pseudocode

In this example, the **Prototype** pattern lets you produce exact copies
of geometric objects, without coupling the code to their classes.

![](attachments/463530002/463530195.png)

All shape classes follow the same interface, which provides a cloning
method. A subclass may call the parent’s cloning method before copying
its own field values to the resulting object.

### Real world example

Remember dolly? The sheep that was cloned\! Lets not get into the
details but the key point here is that it is all about cloning

### In plain words

Create object based on an existing object through cloning.

### Wikipedia says

The prototype pattern is a creational design pattern in software
development. It is used when the type of objects to create is determined
by a prototypical instance, which is cloned to produce new objects.

In short, it allows you to create a copy of an existing object and
modify it to your needs, instead of going through the trouble of
creating an object from scratch and setting it up.

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
<td>You can clone objects without coupling to their concrete classes.</td>
<td>Cloning complex objects that have circular references might be very tricky.</td>
</tr>
<tr class="even">
<td>You can get rid of repeated initialization code in favor of cloning pre-built prototypes.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td>You can produce complex objects more conveniently.</td>
<td><br />
</td>
</tr>
<tr class="even">
<td>You get an alternative to inheritance when dealing with configuration presets for complex objects.</td>
<td><br />
</td>
</tr>
</tbody>
</table>



### Programmatic Example

#### C\#

> 
> 
> ``` 
> class Sheep
> {
>     public string Name { get; set; }
> 
>     public string Category { get; set; }
> 
>     public Sheep(string name, string category)
>     {
>         Name = name;
>         Category = category;
>     }
> 
>     public Sheep Clone()
>     {
>         return MemberwiseClone() as Sheep;
>     }
> }
>                 
> ```

Then it can be cloned like below

> 
> 
> ``` 
> var original = new Sheep("Jolly", "Mountain Sheep");
> Console.WriteLine(original.Name); // Jolly
> Console.WriteLine(original.Category); // Mountain Sheep
> 
> var cloned = original.Clone();
> cloned.Name = "Dolly";
> Console.WriteLine(cloned.Name); // Dolly
> Console.WriteLine(cloned.Category); // Mountain Sheep
> Console.WriteLine(original.Name); // Jolly
>                 
> ```



#### Java



In Java, it can be easily done by implementing `Cloneable` and
overriding `clone` from `Object`

``` 
class Sheep implements Cloneable {
    private String name;
    public Sheep(String name) { this.name = name; }
    public void setName(String name) { this.name = name; }
    public String getName() { return name; }
    @Override
    public Sheep clone() throws CloneNotSupportedException {
        return new Sheep(name);
    }
}
            
```

Then it can be cloned like below

``` 
Sheep original = new Sheep("Jolly");
System.out.println(original.getName()); // Jolly

// Clone and modify what is required
Sheep cloned = original.clone();
cloned.setName("Dolly");
System.out.println(cloned.getName()); // Dolly
            
```



#### PHP



``` 
class Sheep
{
    protected $name;
    protected $category;

    public function __construct(string $name, string $category = 'Mountain Sheep')
    {
        $this->name = $name;
        $this->category = $category;
    }

    public function setName(string $name)
    {
        $this->name = $name;
    }

    public function getName()
    {
        return $this->name;
    }

    public function setCategory(string $category)
    {
        $this->category = $category;
    }

    public function getCategory()
    {
        return $this->category;
    }
}
            
```

Then it can be cloned like below

``` 
$original = new Sheep('Jolly');
echo $original->getName(); // Jolly
echo $original->getCategory(); // Mountain Sheep

// Clone and modify what is required
$cloned = clone $original;
$cloned->setName('Dolly');
echo $cloned->getName(); // Dolly
echo $cloned->getCategory(); // Mountain sheep                                                              
            
```

Also you could use the magic method `__clone` to modify the cloning
behavior.

#### Python

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?
This patterns aims to reduce the number of classes required by an
application. Instead of relying on subclasses it creates objects by
copying a prototypical instance at run-time.

This is useful as it make it easier to derive new kinds of objects,
when instances of the class have only a few different combinations of
state, and when instantiation is expensive.

*What does this example do?
When the number of prototypes in an application can vary, it can be
useful to keep a Dispatcher (aka, Registry or Manager). This allows
clients to query the Dispatcher for a prototype before cloning a new
instance.

Below provides an example of such Dispatcher, which contains three
copies of the prototype: 'default', 'objecta' and 'objectb'.

*TL;DR
Creates new object instances by cloning prototype.
"""

class Prototype(object):

    value = 'default'

    def clone(self, **attrs):
        """Clone a prototype and update inner attributes dictionary"""
        # Python in Practice, Mark Summerfield
        obj = self.__class__()
        obj.__dict__.update(attrs)
        return obj

class PrototypeDispatcher(object):
    def __init__(self):
        self._objects = {}

    def get_objects(self):
        """Get all objects"""
        return self._objects

    def register_object(self, name, obj):
        """Register an object"""
        self._objects[name] = obj

    def unregister_object(self, name):
        """Unregister an object"""
        del self._objects[name]

def main():
    dispatcher = PrototypeDispatcher()
    prototype = Prototype()

    d = prototype.clone()
    a = prototype.clone(value='a-value', category='a')
    b = prototype.clone(value='b-value', is_checked=True)
    dispatcher.register_object('objecta', a)
    dispatcher.register_object('objectb', b)
    dispatcher.register_object('default', d)
    print([{n: p.value} for n, p in dispatcher.get_objects().items()])


if __name__ == '__main__':
    main()

### OUTPUT ###
# [{'objectb': 'b-value'}, {'default': 'default'}, {'objecta': 'a-value'}]
            
```



### When to use?

When an object is required that is similar to existing object or when
the creation would be expensive as compared to cloning.










