###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------

# Information Technology : Visitor Pattern


## Visitor

### Intent

**Visitor** is a behavioral design pattern that lets you separate algorithms from the objects on which they operate.

<img src"./attachments/visitor/463530158.png" />

### Problem

Imagine that your team develops an app which works with geographic information structured as one colossal graph. Each node of the graph may represent a complex entity such as a city, but also more granular things like industries, sightseeing areas, etc. The nodes are connected with others if there’s a road between the real objects that they represent. Under the hood, each node type is represented by its own class, while each specific node is an object.

<img src"./attachments/visitor/463530160.png" />

At some point, you got a task to implement exporting the graph into XML format. At first, the job seemed pretty straightforward. You planned to add an export method to each node class and then leverage recursion to go over each node of the graph, executing the export method. The solution was simple and elegant: thanks to polymorphism, you weren’t coupling the code which called the export method to concrete classes of nodes.

Unfortunately, the system architect refused to allow you to alter existing node classes. He said that the code was already in production and he didn’t want to risk breaking it because of a potential bug in your changes.

<img src"./attachments/visitor/463530161.png" />

Besides, he questioned whether it makes sense to have the XML export code within the node classes. The primary job of these classes was to work with geodata. The XML export behavior would look alien there.

There was another reason for the refusal. It was highly likely that after this feature was implemented, someone from the marketing department would ask you to provide the ability to export into a different format, or request some other weird stuff. This would force you to change those precious and fragile classes again.

### Solution

The Visitor pattern suggests that you place the new behavior into a separate class called *visitor*, instead of trying to integrate it into existing classes. The original object that had to perform the behavior is now passed to one of the visitor’s methods as an argument, providing the method access to all necessary data contained within the object.

Now, what if that behavior can be executed over objects of different classes? For example, in our case with XML export, the actual implementation will probably be a little bit different across various node classes.

But how exactly would we call these methods, especially when dealing with the whole graph? These methods have different signatures, so we can’t use polymorphism. To pick a proper visitor method that’s able to process a given object, we’d need to check its class. Doesn’t this sound like a nightmare?

You might ask, why don’t we use method overloading? That’s when you give all methods the same name, even if they support different sets of parameters. Unfortunately, even assuming that our programming language supports it at all (as Java and C\# do), it won’t help us. Since the exact class of a node object is unknown in advance, the overloading mechanism won’t be able to determine the correct method to execute. It’ll default to the method that takes an object of the base `Node` class.

However, the Visitor pattern addresses this problem. It uses a technique called [Double Dispatch](https://refactoring.guru/design-patterns/visitor-double-dispatch), which helps to execute the proper method on an object without cumbersome conditionals. Instead of letting the client select a proper version of the method to call, how about we delegate this choice to objects we’re passing to the visitor as an argument? Since the objects know their own classes, they’ll be able to pick a proper method on the visitor less awkwardly. They “accept” a visitor and tell it what visiting method should be executed.

### Structure

<img src"./attachments/visitor/463530162.png" />

### Pseudocode

In this example, the **Visitor** pattern adds XML export support to the class hierarchy of geometric shapes.

<img src"./attachments/visitor/463530159.png" />

### Real world example

Consider someone visiting Dubai. They just need a way (i.e. visa) to enter Dubai. After arrival, they can come and visit any place in Dubai on their own without having to ask for permission or to do some leg work in order to visit any place here; just let them know of a place and they can visit it. Visitor pattern lets you do just that, it helps you add places to visit so that they can visit as much as they can without having to do any legwork.

### In plain words

Visitor pattern lets you add further operations to objects without having to modify them.

### Wikipedia says

In object-oriented programming and software engineering, the visitor design pattern is a way of separating an algorithm from an object structure on which it operates. A practical result of this separation is the ability to add new operations to existing object structures without modifying those structures. It is one way to follow the open/closed principle.

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
            <td><em>Open/Closed Principle</em> . You can introduce a new behavior that can work with objects of different classes without changing these classes.</td>
            <td>You need to update all visitors each time a class gets added to or removed from the element hierarchy.</td>
        </tr>
        <tr class="even">
            <td><em>Single Responsibility Principle</em> . You can move multiple versions of the same behavior into the same class.</td>
            <td>Visitors might lack the necessary access to the private fields and methods of the elements that they’re supposed to work with.</td>
        </tr>
        <tr class="odd">
            <td>A visitor object can accumulate some useful information while working with various objects. This might be handy when you want to traverse some complex object structure, such as an object tree, and apply the visitor to each object of this structure.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

#### C\#



Let's take an example of a zoo simulation where we have several different kinds of animals and we have to make them Sound. Let's translate this using visitor pattern

> 
> 
> ``` 
> // Visitee 
> interface IAnimal
> {
>   void Accept(IAnimalOperation operation);
> }
> 
> // Visitor
> interface IAnimalOperation
> {
>   void VisitMonkey(Monkey monkey);
>   void VisitLion(Lion lion);
>   void VisitDolphin(Dolphin dolphin);
> }
>
> ```

Then we have our implementations for the animals

> 
> 
> ``` 
> class Monkey : IAnimal
> {
>     public void Shout()
>     {
>         Console.WriteLine("Oooh o aa aa!");
>     }
> 
>     public void Accept(IAnimalOperation operation)
>     {
>         operation.VisitMonkey(this);
>     }
> }
> 
> class Lion : IAnimal
> {
>     public void Roar()
>     {
>         Console.WriteLine("Roaar!");
>     }
> 
>     public void Accept(IAnimalOperation operation)
>     {
>         operation.VisitLion(this);
>     }
> }
> 
> class Dolphin : IAnimal
> {
>     public void Speak()
>     {
>         Console.WriteLine("Tuut tittu tuutt!");
>     }
> 
>     public void Accept(IAnimalOperation operation)
>     {
>         operation.VisitDolphin(this);
>     }
> }
>
> ```

Let's implement our visitor

> 
> 
> ``` 
> Let's implement our visitor
> class Speak : IAnimalOperation
> {
>     public void VisitDolphin(Dolphin dolphin)
>     {
>         dolphin.Speak();
>     }
> 
>     public void VisitLion(Lion lion)
>     {
>         lion.Roar();
>     }
> 
>     public void VisitMonkey(Monkey monkey)
>     {
>         monkey.Shout();
>     }
> }
>
> ```

And then it can be used as

> 
> 
> ``` 
> var monkey = new Monkey();
> var lion = new Lion();
> var dolphin = new Dolphin();
> 
> var speak = new Speak();
> 
> monkey.Accept(speak);    // Ooh oo aa aa!
> lion.Accept(speak);      // Roaaar!
> dolphin.Accept(speak);   // Tuut tutt tuutt!
> 
>
> ```

We could have done this simply by having an inheritance hierarchy for the animals but then we would have to modify the animals whenever we would have to add new actions to animals. But now we will not have to change them. For example, let's say we are asked to add the jump behavior to the animals, we can simply add that by creating a new visitor i.e.

> 
> 
> ``` 
> class Jump : IAnimalOperation
> {
>     public void VisitDolphin(Dolphin dolphin)
>     {
>         Console.WriteLine("Walked on water a little and disappeared!");
>     }
> 
>     public void VisitLion(Lion lion)
>     {
>         Console.WriteLine("Jumped 7 feet! Back on the ground!");
>     }
> 
>     public void VisitMonkey(Monkey monkey)
>     {
>         Console.WriteLine("Jumped 20 feet high! on to the tree!");
>     }
> }
>
> ```

And for the usage

> 
> 
> ``` 
> var jump = new Jump();
> 
> monkey.Accept(speak);   // Ooh oo aa aa!
> monkey.Accept(jump);    // Jumped 20 feet high! on to the tree!
> 
> lion.Accept(speak);     // Roaaar!
> lion.Accept(jump);      // Jumped 7 feet! Back on the ground!
> 
> dolphin.Accept(speak);  // Tuut tutt tuutt!
> dolphin.Accept(jump);   // Walked on water a little and disappeared
> 
> ```



#### JavaScript



Let's take an example of a zoo simulation where we have several different kinds of animals and we have to make them Sound. Let's translate this using visitor pattern

We have our implementations for the animals

> 
> 
> ``` 
> class Monkey {
>     shout() {
>         console.log('Ooh oo aa aa!')
>     }
> 
>     accept(operation) {
>         operation.visitMonkey(this)
>     }
> }
> 
> class Lion {
>     roar() {
>         console.log('Roaaar!')
>     }
>     
>     accept(operation) {
>         operation.visitLion(this)
>     }
> }
> 
> class Dolphin {
>     speak() {
>         console.log('Tuut tuttu tuutt!')
>     }
>     
>     accept(operation) {
>         operation.visitDolphin(this)
>     }
> }
> 
>                     
> ```

Let's implement our visitor

> 
> 
> ``` 
> const speak = {
>     visitMonkey(monkey){
>         monkey.shout()
>     },
>     visitLion(lion){
>         lion.roar()
>     },
>     visitDolphin(dolphin){
>         dolphin.speak()
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
>  const monkey = new Monkey()
> const lion = new Lion()
> const dolphin = new Dolphin()
> 
> monkey.accept(speak)    // Ooh oo aa aa! 
> lion.accept(speak)      // Roaaar!
> dolphin.accept(speak)   // Tuut tutt tuutt!
>                     
> ```

We could have done this simply by having a inheritance hierarchy for the animals but then we would have to modify the animals whenever we would have to add new actions to animals. But now we will not have to change them. For example, let's say we are asked to add the jump behavior to the animals, we can simply add that by creating a new visitor i.e.

> 
> 
> ``` 
> const jump = {
>     visitMonkey(monkey) {
>         console.log('Jumped 20 feet high! on to the tree!')
>     },
>     visitLion(lion) {
>         console.log('Jumped 7 feet! Back on the ground!')
>     },
>     visitDolphin(dolphin) {
>         console.log('Walked on water a little and disappeared')
>     }
> }
> 
>                     
> ```

And for the usage

> 
> 
> ``` 
> monkey.accept(speak)   // Ooh oo aa aa!
> monkey.accept(jump)    // Jumped 20 feet high! on to the tree!
> 
> lion.accept(speak)     // Roaaar!
> lion.accept(jump)      // Jumped 7 feet! Back on the ground! 
> 
> dolphin.accept(speak)  // Tuut tutt tuutt! 
> dolphin.accept(jump)   // Walked on water a little and disappeared
> 
>                     
> ```



#### PHP



Let's take an example of a zoo simulation where we have several different kinds of animals and we have to make them Sound. Let's translate this using visitor pattern

> 
> 
> ``` 
> //Visitee
> interface Animal
> {
>     public function accept(AnimalOperation $operation);
> }
> 
> // Visitor
> interface AnimalOperation
> {
>     public function visitMonkey(Monkey $monkey);
>     public function visitLion(Lion $lion);
>     public function visitDolphin(Dolphin $dolphin);
> }
>                 
> ```

    Then we have our implementations for the animals

> 
> 
> ``` 
> class Monkey implements Animal
> {
>     public function shout()
>     {
>         echo 'Ooh oo aa aa!';
>     }
> 
>     public function accept(AnimalOperation $operation)
>     {
>         $operation->visitMonkey($this);
>     }
>     }
> 
>     class Lion implements Animal
>     {
>         public function roar()
>         {
>             echo 'Roaaar!';
>         }
> 
>         public function accept(AnimalOperation $operation)
>         {
>             $operation->visitLion($this);
>         }
>     }
> 
>     class Dolphin implements Animal
>     {
>         public function speak()
>         {
>             echo 'Tuut tuttu tuutt!';
>         }
> 
>     public function accept(AnimalOperation $operation)
>     {
>         $operation->visitDolphin($this);
>     }
> }
>                 
> ```

    Let's implement our visitor

> 
> 
> ``` 
> class Speak implements AnimalOperation
> {
>     public function visitMonkey(Monkey $monkey)
>     {
>         $monkey->shout();
>     }
> 
>     public function visitLion(Lion $lion)
>     {
>         $lion->roar();
>     }
> 
>     public function visitDolphin(Dolphin $dolphin)
>     {
>         $dolphin->speak();
>     }
> }
>                 
> ```

    And then it can be used as

> 
> 
> ``` 
> $monkey = new Monkey();
> $lion = new Lion();
> $dolphin = new Dolphin();
> 
> $speak = new Speak();
> 
> $monkey->accept($speak); // Ooh oo aa aa! 
> $lion->accept($speak); // Roaaar!
> $dolphin->accept($speak); // Tuut tutt tuutt!
>                 
> ```

We could have done this simply by having an inheritance hierarchy for the animals but then we would have to modify the animals whenever we would have to add new actions to animals. But now we will not have to change them. For example, let's say we are asked to add the jump behavior to the animals, we can simply add that by creating a new visitor i.e.

> 
> 
> ``` 
> class Jump implements AnimalOperation
> {
>     public function visitMonkey(Monkey $monkey)
>     {
>         echo 'Jumped 20 feet high! on to the tree!';
>     }
> 
>     public function visitLion(Lion $lion)
>     {
>         echo 'Jumped 7 feet! Back on the ground!';
>     }
> 
>     public function visitDolphin(Dolphin $dolphin)
>     {
>         echo 'Walked on water a little and disappeared';
>     }
> }
>                 
> ```

    And for the usage

> 
> 
> ``` 
> $jump = new Jump();
> 
> $monkey->accept($speak); // Ooh oo aa aa!
> $monkey->accept($jump); // Jumped 20 feet high! on to the tree!
> 
> $lion->accept($speak); // Roaaar!
> $lion->accept($jump); // Jumped 7 feet! Back on the ground!
> 
> $dolphin->accept($speak); // Tuut tutt tuutt!
> $dolphin->accept($jump); // Walked on water a little and disappeared
>                 
> ```



#### Python

> 
> 
> ``` 
> #!/usr/bin/env python
> # -*- coding: utf-8 -*-
> 
> """
> http://peter-hoffmann.com/2010/extrinsic-visitor-pattern-python-inheritance.html
> 
> *TL;DR
> Separates an algorithm from an object structure on which it operates.
> 
> An interesting recipe could be found in Brian Jones, David Beazley "Python Cookbook" (2013):
> - "8.21. Implementing the Visitor Pattern"
> - "8.22. Implementing the Visitor Pattern Without Recursion"
> 
> *Examples in Python ecosystem:
> - Python's ast.NodeVisitor: https://github.com/python/cpython/blob/master/Lib/ast.py#L250
> which is then being used e.g. in tools like `pyflakes`.
> - `Black` formatter tool implements it's own: https://github.com/ambv/black/blob/master/black.py#L718
> """
> 
> 
> class Node(object):
>     pass
> 
> 
> class A(Node):
>     pass
> 
> 
> class B(Node):
>     pass
> 
> 
> class C(A, B):
>     pass
> 
> 
> class Visitor(object):
>     def visit(self, node, *args, **kwargs):
>         meth = None
>         for cls in node.__class__.__mro__:
>             meth_name = 'visit_' + cls.__name__
>             meth = getattr(self, meth_name, None)
>             if meth:
>                 break
> 
>         if not meth:
>             meth = self.generic_visit
>         return meth(node, *args, **kwargs)
> 
>     def generic_visit(self, node, *args, **kwargs):
>         print('generic_visit ' + node.__class__.__name__)
> 
>     def visit_B(self, node, *args, **kwargs):
>         print('visit_B ' + node.__class__.__name__)
> 
> 
> def main():
>     """
>     >>> a, b, c = A(), B(), C()
>     >>> visitor = Visitor()
> 
>     >>> visitor.visit(a)
>     generic_visit A
> 
>     >>> visitor.visit(b)
>     visit_B B
> 
>     >>> visitor.visit(c)
>     visit_B C
>     """
> 
> 
> if __name__ == "__main__":
>     import doctest
>     doctest.testmod()
>                 
> ```

