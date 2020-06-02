###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------


# Information Technology : Creational Design Patterns

<kbd>![Example of Abstract Factory](https://sourcemaking.com/files/v2/content/patterns/Abstract_Factory-preview.png)

## Builder

<kbd>![](https://www.oodesign.com/images/creational/builder-pattern.png)</kbd>

### Intent

**Builder** is a creational design pattern that lets you construct
complex objects step by step. The pattern allows you to produce
different types and representations of an object using the same
construction code.

<kbd>![](./attachments/builder/463530184.png)</kbd>

### Problem

Imagine a complex object that requires laborious, step-by-step
initialization of many fields and nested objects. Such initialization
code is usually buried inside a monstrous constructor with lots of
parameters. Or even worse: scattered all over the client code.

<kbd>![](./attachments/builder/463530188.png)</kbd>

For example, let’s think about how to create a `House` object. To build
a simple house, you need to construct four walls and a floor, install a
door, fit a pair of windows, and build a roof. But what if you want a
bigger, brighter house, with a backyard and other goodies (like a
heating system, plumbing, and electrical wiring)?

The simplest solution is to extend the base `House` class and create a
set of subclasses to cover all combinations of the parameters. But
eventually you’ll end up with a considerable number of subclasses. Any
new parameter, such as the porch style, will require growing this
hierarchy even more.

There’s another approach that doesn’t involve breeding subclasses. You
can create a giant constructor right in the base `House` class with all
possible parameters that control the house object. While this approach
indeed eliminates the need for subclasses, it creates another problem.

<kbd>![](./attachments/builder/463530189.png)</kbd>

In most cases most of the parameters will be unused, making [the
constructor calls pretty
ugly](https://refactoring.guru/smells/long-parameter-list) . For
instance, only a fraction of houses have swimming pools, so the
parameters related to swimming pools will be useless nine times out of
ten.

### Solution

The Builder pattern suggests that you extract the object construction
code out of its own class and move it to separate objects called
*builders*.

<kbd>![](./attachments/builder/463530190.png)</kbd>

The pattern organizes object construction into a set of steps (
`buildWalls`, `buildDoor`, etc.). To create an object, you execute a
series of these steps on a builder object. The important part is that
you don’t need to call all of the steps. You can call only those steps
that are necessary for producing a particular configuration of an
object.

Some of the construction steps might require different implementation
when you need to build various representations of the product. For
example, walls of a cabin may be built of wood, but the castle walls
must be built with stone.

In this case, you can create several different builder classes that
implement the same set of building steps, but in a different manner.
Then you can use these builders in the construction process (i.e., an
ordered set of calls to the building steps) to produce different kinds
of objects.

<kbd>![](./attachments/builder/463530185.png)</kbd>

For example, imagine a builder that builds everything from wood and
glass, a second one that builds everything with stone and iron and a
third one that uses gold and diamonds. By calling the same set of steps,
you get a regular house from the first builder, a small castle from the
second and a palace from the third. However, this would only work if the
client code that calls the building steps is able to interact with
builders using a common interface.

### Director

You can go further and extract a series of calls to the builder steps
you use to construct a product into a separate class called *director*.
The director class defines the order in which to execute the building
steps, while the builder provides the implementation for those steps.

<kbd>![](./attachments/builder/463530186.png)</kbd>

Having a director class in your program isn’t strictly necessary. You
can always call the building steps in a specific order directly from the
client code. However, the director class might be a good place to put
various construction routines so you can reuse them across your program.

In addition, the director class completely hides the details of product
construction from the client code. The client only needs to associate a
builder with a director, launch the construction with the director, and
get the result from the builder.

### Structure

<kbd>![](./attachments/builder/463530191.png)</kbd>

### Pseudocode

This example of the **Builder** pattern illustrates how you can reuse
the same object construction code when building different types of
products, such as cars, and create the corresponding manuals for them.

<kbd>![](./attachments/builder/463530187.png)</kbd>

A car is a complex object that can be constructed in a hundred different
ways. Instead of bloating the `Car` class with a huge constructor, we
extracted the car assembly code into a separate car builder class. This
class has a set of methods for configuring various parts of a car.

If the client code needs to assemble a special, fine-tuned model of a
car, it can work with the builder directly. On the other hand, the
client can delegate the assembly to the director class, which knows how
to use a builder to construct several of the most popular models of
cars.

You might be shocked, but every car needs a manual (seriously, who reads
them?). The manual describes every feature of the car, so the details in
the manuals vary across the different models. That’s why it makes sense
to reuse an existing construction process for both real cars and their
respective manuals. Of course, building a manual isn’t the same as
building a car, and that’s why we must provide another builder class
that specializes in composing manuals. This class implements the same
building methods as its car-building sibling, but instead of crafting
car parts, it describes them. By passing these builders to the same
director object, we can construct either a car or a manual.

The final part is fetching the resulting object. A metal car and a paper
manual, although related, are still very different things. We can’t
place a method for fetching results in the director without coupling the
director to concrete product classes. Hence, we obtain the result of the
construction from the builder which performed the job.

### Real world example

Imagine you are at Hardee's and you order a specific deal, lets say,
"Big Hardee" and they hand it over to you without *any questions*; this
is the example of simple factory. But there are cases when the creation
logic might involve more steps. For example you want a customized Subway
deal, you have several options in how your burger is made e.g what bread
do you want? what types of sauces would you like? What cheese would you
want? etc. In such cases builder pattern comes to the rescue.

### In plain words

Allows you to create different flavors of an object while avoiding
constructor pollution. Useful when there could be several flavors of an
object. Or when there are a lot of steps involved in creation of an
object.

### Wikipedia says

The builder pattern is an object creation software design pattern with
the intentions of finding a solution to the telescoping constructor
anti-pattern.

Having said that let me add a bit about what telescoping constructor
anti-pattern is. At one point or the other we have all seen a
constructor like below:

#### C\#

``` 
public Burger(int size, bool cheese, bool pepperoni, bool lettuce, bool tomato) {
}
                
```



#### Java


``` 
public Hero(Profession profession, String name, HairType hairType, HairColor hairColor, Armor armor, Weapon weapon) {
}
                
```



#### PHP



``` 
public function __construct($size, $cheese = true, $pepperoni = true, $tomato = false, $lettuce = true) {
}

                
```



As you can see; the number of constructor parameters can quickly get out
of hand and it might become difficult to understand the arrangement of
parameters. Plus this parameter list could keep on growing if you would
want to add more options in future. This is called telescoping
constructor anti-pattern.

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
            <td>You can construct objects step-by-step, defer construction steps or run steps recursively.</td>
            <td>The overall complexity of the code increases since the pattern requires creating multiple new classes.</td>
        </tr>
        <tr class="even">
            <td>You can reuse the same construction code when building various representations of products.</td>
            <td><br /></td>
        </tr>
        <tr class="odd">
            <td><em>Single Responsibility Principle</em>. You can isolate complex construction code from the business logic of the product.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

The sane alternative is to use the builder pattern. First of all we have
our burger that we want to make

#### C\#



> 
> 
> ``` 
> class Burger
> {
>     private int mSize;
>     private bool mCheese;
>     private bool mPepperoni;
>     private bool mLettuce;
>     private bool mTomato;
> 
>     public Burger(BurgerBuilder builder)
>     {
>         this.mSize = builder.Size;
>         this.mCheese = builder.Cheese;
>         this.mPepperoni = builder.Pepperoni;
>         this.mLettuce = builder.Lettuce;
>         this.mTomato = builder.Tomato;
>     }
> 
>     public string GetDescription()
>     {
>         var sb = new StringBuilder();
>         sb.Append($"This is {this.mSize} inch Burger. ");
>         return sb.ToString();
>     }
> }
> 
>                     
> ```

And then we have the builder

> 
> 
> ``` 
> class BurgerBuilder {
>     public int Size;
>     public bool Cheese;
>     public bool Pepperoni;
>     public bool Lettuce;
>     public bool Tomato;
> 
>     public BurgerBuilder(int size)
>     {
>         this.Size = size;
>     }
> 
>     public BurgerBuilder AddCheese()
>     {
>         this.Cheese = true;
>         return this;
>     }
> 
>     public BurgerBuilder AddPepperoni()
>     {
>         this.Pepperoni = true;
>         return this;
>     }
> 
>     public BurgerBuilder AddLettuce()
>     {
>         this.Lettuce = true;
>         return this;
>     }
> 
>     public BurgerBuilder AddTomato()
>     {
>         this.Tomato = true;
>         return this;
>     }
> 
>     public Burger Build()
>     {
>         return new Burger(this);
>     }
> }
> 
>                     
> ```

And then it can be used as:

> 
> 
> ``` 
> And then it can be used as:
> var burger = new BurgerBuilder(4).AddCheese()
>                 .AddPepperoni()
>                 .AddLettuce()
>                 .AddTomato()
>                 .Build();
> Console.WriteLine(burger.GetDescription());
>                     
> ```



#### Java



``` 
 public final class Hero {
    private final Profession profession;
    private final String name;
    private final HairType hairType;
    private final HairColor hairColor;
    private final Armor armor;
    private final Weapon weapon;

    private Hero(Builder builder) {
        this.profession = builder.profession;
        this.name = builder.name;
        this.hairColor = builder.hairColor;
        this.hairType = builder.hairType;
        this.weapon = builder.weapon;
        this.armor = builder.armor;
    }
}
                
```

And then we have the builder

``` 
public static class Builder {
    private final Profession profession;
    private final String name;
    private HairType hairType;
    private HairColor hairColor;
    private Armor armor;
    private Weapon weapon;

    public Builder(Profession profession, String name) {
        if (profession == null || name == null) {
        throw new IllegalArgumentException("profession and name can not be null");
        }
        this.profession = profession;
        this.name = name;
    }

    public Builder withHairType(HairType hairType) {
        this.hairType = hairType;
        return this;
    }

    public Builder withHairColor(HairColor hairColor) {
        this.hairColor = hairColor;
        return this;
    }

    public Builder withArmor(Armor armor) {
        this.armor = armor;
        return this;
    }

    public Builder withWeapon(Weapon weapon) {
        this.weapon = weapon;
        return this;
    }

    public Hero build() {
        return new Hero(this);
    }
}
                
```

And then it can be used as:

``` 
Hero mage = new Hero.Builder(Profession.MAGE, "Riobard").withHairColor(HairColor.BLACK).withWeapon(Weapon.DAGGER).build();
                
```



#### PHP



``` 
 class Burger
{
    protected $size;

    protected $cheese = false;
    protected $pepperoni = false;
    protected $lettuce = false;
    protected $tomato = false;

    public function __construct(BurgerBuilder $builder)
    {
        $this->size = $builder->size;
        $this->cheese = $builder->cheese;
        $this->pepperoni = $builder->pepperoni;
        $this->lettuce = $builder->lettuce;
        $this->tomato = $builder->tomato;
    }
}
                
```

And then we have the builder

``` 
class BurgerBuilder
{
    public $size;

    public $cheese = false;
    public $pepperoni = false;
    public $lettuce = false;
    public $tomato = false;

    public function __construct(int $size)
    {
        $this->size = $size;
    }

    public function addPepperoni()
    {
        $this->pepperoni = true;
        return $this;
    }

    public function addLettuce()
    {
        $this->lettuce = true;
        return $this;
    }

    public function addCheese()
    {
        $this->cheese = true;
        return $this;
    }

    public function addTomato()
    {
        $this->tomato = true;
        return $this;
    }

    public function build(): Burger
    {
        return new Burger($this);
    }
}

                
```

And then it can be used as:

``` 
$burger = (new BurgerBuilder(14))
 ->addPepperoni()
 ->addLettuce()
 ->addTomato()
 ->build();
                
```



#### Python



``` 
#!/usr/bin/python
# -*- coding : utf-8 -*-

"""
*What is this pattern about?
It decouples the creation of a complex object and its representation,
so that the same process can be reused to build objects from the same
family.
This is useful when you must separate the specification of an object
from its actual representation (generally for abstraction).

*What does this example do?

The first example achieves this by using an abstract base
class for a building, where the initializer (__init__ method) specifies the
steps needed, and the concrete subclasses implement these steps.

In other programming languages, a more complex arrangement is sometimes
necessary. In particular, you cannot have polymorphic behaviour in a constructor in C++ -
see https://stackoverflow.com/questions/1453131/how-can-i-get-polymorphic-behavior-in-a-c-constructor
- which means this Python technique will not work. The polymorphism
required has to be provided by an external, already constructed
instance of a different class.

In general, in Python this won't be necessary, but a second example showing
this kind of arrangement is also included.

*Where is the pattern used practically?

*References:
https://sourcemaking.com/design_patterns/builder

*TL;DR
Decouples the creation of a complex object and its representation.
"""


# Abstract Building
class Building(object):
    def __init__(self):
        self.build_floor()
        self.build_size()

    def build_floor(self):
        raise NotImplementedError

    def build_size(self):
        raise NotImplementedError

    def __repr__(self):
        return 'Floor: {0.floor} | Size: {0.size}'.format(self)


# Concrete Buildings
class House(Building):
    def build_floor(self):
        self.floor = 'One'

    def build_size(self):
        self.size = 'Big'


class Flat(Building):
    def build_floor(self):
        self.floor = 'More than One'

    def build_size(self):
        self.size = 'Small'


# In some very complex cases, it might be desirable to pull out the building
# logic into another function (or a method on another class), rather than being
# in the base class '__init__'. (This leaves you in the strange situation where
# a concrete class does not have a useful constructor)


class ComplexBuilding(object):
    def __repr__(self):
        return 'Floor: {0.floor} | Size: {0.size}'.format(self)


class ComplexHouse(ComplexBuilding):
    def build_floor(self):
        self.floor = 'One'

    def build_size(self):
        self.size = 'Big and fancy'


def construct_building(cls):
    building = cls()
    building.build_floor()
    building.build_size()
    return building


# Client
if __name__ == "__main__":
    house = House()
    print(house)
    flat = Flat()
    print(flat)

    # Using an external constructor function:
    complex_house = construct_building(ComplexHouse)
    print(complex_house)

### OUTPUT ###
# Floor: One | Size: Big
# Floor: More than One | Size: Small
# Floor: One | Size: Big and fancy
                
```



### When to use?

When there could be several flavors of an object and to avoid the
constructor telescoping. The key difference from the factory pattern is
that; factory pattern is to be used when the creation is a one step
process while builder pattern is to be used when the creation is a multi
step process.


## Abstract Factory

<kbd>![](https://www.oodesign.com/images/creational/abstract-factory-pattern.png)</kbd>

### Intent

**Abstract Factory** is a creational design pattern that lets you
produce families of related objects without specifying their concrete
classes.

<kbd>![](./attachments/abstract/463530174.png)</kbd>

### Problem

Imagine that you’re creating a furniture shop simulator. Your code
consists of classes that represent:

1.  A family of related products, say: `Chair` + `Sofa` + `CoffeeTable`.

2.  Several variants of this family. For example, products `Chair` +
    `Sofa` + `CoffeeTable` are available in these variants: `Modern`,
    `Victorian`, `ArtDeco`.

<kbd>![](./attachments/abstract/463530178.png)</kbd>

You need a way to create individual furniture objects so that they match
other objects of the same family. Customers get quite mad when they
receive non-matching furniture.

<kbd>![](./attachments/abstract/463530175.png)</kbd>

Also, you don’t want to change existing code when adding new products or
families of products to the program. Furniture vendors update their
catalogs very often, and you wouldn’t want to change the core code each
time it happens.

### Solution

The first thing the Abstract Factory pattern suggests is to explicitly
declare interfaces for each distinct product of the product family
(e.g., chair, sofa or coffee table). Then you can make all variants of
products follow those interfaces. For example, all chair variants can
implement the `Chair` interface; all coffee table variants can implement
the `CoffeeTable` interface, and so on.

<kbd>![](./attachments/abstract/463530179.png)</kbd>

The next move is to declare the *Abstract Factory*—an interface with a
list of creation methods for all products that are part of the product
family (for example, `createChair`, `createSofa` and
`createCoffeeTable`). These methods must return **abstract** product
types represented by the interfaces we extracted previously: `Chair`,
`Sofa`, `CoffeeTable` and so on.

<kbd>![](./attachments/abstract/463530180.png)</kbd>

Now, how about the product variants? For each variant of a product
family, we create a separate factory class based on the
`AbstractFactory` interface. A factory is a class that returns products
of a particular kind. For example, the `ModernFurnitureFactory` can only
create `ModernChair`, `ModernSofa` and `ModernCoffeeTable` objects.

The client code has to work with both factories and products via their
respective abstract interfaces. This lets you change the type of a
factory that you pass to the client code, as well as the product variant
that the client code receives, without breaking the actual client code.

<kbd>![](./attachments/abstract/463530176.png)</kbd>

Say the client wants a factory to produce a chair. The client doesn’t
have to be aware of the factory’s class, nor does it matter what kind of
chair it gets. Whether it’s a Modern model or a Victorian-style chair,
the client must treat all chairs in the same manner, using the abstract
`Chair` interface. With this approach, the only thing that the client
knows about the chair is that it implements the `sitOn` method in some
way. Also, whichever variant of the chair is returned, it’ll always
match the type of sofa or coffee table produced by the same factory
object.

There’s one more thing left to clarify: if the client is only exposed to
the abstract interfaces, what creates the actual factory objects?
Usually, the application creates a concrete factory object at the
initialization stage. Just before that, the app must select the factory
type depending on the configuration or the environment settings.

### Structure

<kbd>![](./attachments/abstract/463530181.png)</kbd>

### Pseudocode

This example illustrates how the **Abstract Factory** pattern can be
used for creating cross-platform UI elements without coupling the client
code to concrete UI classes, while keeping all created elements
consistent with a selected operating system.

<kbd>![](./attachments/abstract/463530177.png)</kbd>

The same UI elements in a cross-platform application are expected to
behave similarly, but look a little bit different under different
operating systems. Moreover, it’s your job to make sure that the UI
elements match the style of the current operating system. You wouldn’t
want your program to render macOS controls when it’s executed in
Windows.

The Abstract Factory interface declares a set of creation methods that
the client code can use to produce different types of UI elements.
Concrete factories correspond to specific operating systems and create
the UI elements that match that particular OS.

It works like this: when an application launches, it checks the type of
the current operating system. The app uses this information to create a
factory object from a class that matches the operating system. The rest
of the code uses this factory to create UI elements. This prevents the
wrong elements from being created.

With this approach, the client code doesn’t depend on concrete classes
of factories and UI elements as long as it works with these objects via
their abstract interfaces. This also lets the client code support other
factories or UI elements that you might add in the future.

As a result, you don’t need to modify the client code each time you add
a new variation of UI elements to your app. You just have to create a
new factory class that produces these elements and slightly modify the
app’s initialization code so it selects that class when appropriate.

### Real world example

Extending our door example from Simple Factory. Based on your needs you
might get a wooden door from a wooden door shop, iron door from an iron
shop or a PVC door from the relevant shop. Plus you might need a guy
with different kind of specialities to fit the door, for example a
carpenter for wooden door, welder for iron door etc. As you can see
there is a dependency between the doors now, wooden door needs
carpenter, iron door needs a welder etc.

### In plain words

A factory of factories; a factory that groups the individual but
related/dependent factories together without specifying their concrete
classes.

### Wikipedia says

The abstract factory pattern provides a way to encapsulate a group of
individual factories that have a common theme without specifying their
concrete classes

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
            <td>You can be sure that the products you’re getting from a factory are compatible with each other.</td>
            <td>The code may become more complicated than it should be, since a lot of new interfaces and classes are introduced along with the pattern.</td>
        </tr>
        <tr class="even">
            <td>You avoid tight coupling between concrete products and client code.</td>
            <td><br /></td>
        </tr>
        <tr class="odd">
            <td>S<em>ingle Responsibility Principle</em>. You can extract the product creation code into one place, making the code easier to support.</td>
            <td><br /></td>
        </tr>
        <tr class="even">
            <td><em>Open/Closed Principle</em>. You can introduce new variants of products without breaking existing client code.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

Translating the door example above. First of all we have our `Door`
interface and some implementation for it

#### C\#



> 
> 
> ``` 
> interface IDoor {
>     void GetDescription();
> }
> class WoodenDoor : IDoor
> {
>     public void GetDescription()
>     {
>         Console.WriteLine("I am a wooden door");
>     }
> }
> 
> class IronDoor : IDoor
> {
>     public void GetDescription()
>     {
>         Console.WriteLine("I am a iron door");
>     }
> }
>                     
> ```

Then we have some fitting experts for each door type

> 
> 
> ``` 
> interface IDoorFittingExpert
> {
>     void GetDescription();
> }
> 
> class Welder : IDoorFittingExpert
> {
>     public void GetDescription()
>     {
>         Console.WriteLine("I can only fit iron doors");
>     }
> }
> 
> class Carpenter : IDoorFittingExpert
> {
>     public void GetDescription()
>     {
>         Console.WriteLine("I can only fit wooden doors");
>     }
> }
>                     
> ```

Now we have our abstract factory that would let us make family of
related objects i.e. wooden door factory would create a wooden door and
wooden door fitting expert and iron door factory would create an iron
door and iron door fitting expert

> 
> 
> ``` 
> interface IDoorFactory {
>     IDoor MakeDoor();
>     IDoorFittingExpert MakeFittingExpert();
> }
> 
> // Wooden factory to return carpenter and wooden door
> class WoodenDoorFactory : IDoorFactory
> {
>     public IDoor MakeDoor()
>     {
>         return new WoodenDoor();
>     }
> 
>     public IDoorFittingExpert MakeFittingExpert()
>     {
>         return new Carpenter();
>     }
> }
> 
> // Iron door factory to get iron door and the relevant fitting expert
> class IronDoorFactory : IDoorFactory
> {
>     public IDoor MakeDoor()
>     {
>         return new IronDoor();
>     }
> 
>     public IDoorFittingExpert MakeFittingExpert()
>     {
>         return new Welder();
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
> var woodenDoorFactory = new WoodenDoorFactory();
> 
> var woodenDoor = woodenDoorFactory.MakeDoor();
> var woodenDoorFittingExpert = woodenDoorFactory.MakeFittingExpert();
> 
> woodenDoor.GetDescription(); //Output : I am a wooden door
> woodenDoorFittingExpert.GetDescription();//Output : I can only fit woooden doors
> 
> var ironDoorFactory = new IronDoorFactory();
> 
> var ironDoor = ironDoorFactory.MakeDoor();
> var ironDoorFittingExpert = ironDoorFactory.MakeFittingExpert();
> 
> ironDoor.GetDescription();//Output : I am a iron door
> ironDoorFittingExpert.GetDescription();//Output : I can only fit iron doors
>                     
> ```



#### Java



``` 
public interface Castle {
    String getDescription();
}
public interface King {
    String getDescription();
}
public interface Army {
    String getDescription();
}

// Elven implementations ->
public class ElfCastle implements Castle {
    static final String DESCRIPTION = "This is the Elven castle!";
    @Override
    public String getDescription() {
        return DESCRIPTION;
    }
}
public class ElfKing implements King {
    static final String DESCRIPTION = "This is the Elven king!";
    @Override
    public String getDescription() {
        return DESCRIPTION;
    }
}
public class ElfArmy implements Army {
    static final String DESCRIPTION = "This is the Elven Army!";
    @Override
    public String getDescription() {
        return DESCRIPTION;
    }
}

// Orcish implementations similarly...
                
```

Then we have the abstraction and implementations for the kingdom factory

``` 
public interface KingdomFactory {
    Castle createCastle();
    King createKing();
    Army createArmy();
}

public class ElfKingdomFactory implements KingdomFactory {
    public Castle createCastle() {
        return new ElfCastle();
    }
    public King createKing() {
        return new ElfKing();
    }
    public Army createArmy() {
        return new ElfArmy();
    }
}

public class OrcKingdomFactory implements KingdomFactory {
    public Castle createCastle() {
        return new OrcCastle();
    }
    public King createKing() {
        return new OrcKing();
    }
    public Army createArmy() {
        return new OrcArmy();
    }
}
                
```

Now we have our abstract factory that lets us make family of related
objects i.e. Elven kingdom factory creates Elven castle, king and army
etc.

``` 
KingdomFactory factory = new ElfKingdomFactory();
Castle castle = factory.createCastle();
King king = factory.createKing();
Army army = factory.createArmy();

castle.getDescription();  // Output: This is the Elven castle!
king.getDescription(); // Output: This is the Elven king!
army.getDescription(); // Output: This is the Elven Army!
                
```

Now, we can design a factory for our different kingdom factories. In
this example, we created FactoryMaker, responsible for returning an
instance of either ElfKingdomFactory or OrcKingdomFactory.  
The client can use FactoryMaker to create the desired concrete factory
which, in turn, will produce different concrete objects (Army, King,
Castle).  
In this example, we also used an enum to parameterize which type of
kingdom factory the client will ask for.

``` 
public static class FactoryMaker {
    public enum KingdomType {
        ELF, ORC
    }

    public static KingdomFactory makeFactory(KingdomType type) {
                switch (type) {
                    case ELF:
                        return new ElfKingdomFactory();
                    case ORC:
                        return new OrcKingdomFactory();
                    default:
                        throw new IllegalArgumentException("KingdomType not supported.");
            }
        }
}

public static void main(String[] args) {
    App app = new App();

    LOGGER.info("Elf Kingdom");
    app.createKingdom(FactoryMaker.makeFactory(KingdomType.ELF));
    LOGGER.info(app.getArmy().getDescription());
    LOGGER.info(app.getCastle().getDescription());
    LOGGER.info(app.getKing().getDescription());

    LOGGER.info("Orc Kingdom");
    app.createKingdom(FactoryMaker.makeFactory(KingdomType.ORC));
    -- similar use of the orc factory
}
                
```



#### PHP



``` 
interface Door
{
    public function getDescription();
}

class WoodenDoor implements Door
{
    public function getDescription()
    {
        echo 'I am a wooden door';
    }
}

class IronDoor implements Door
{
    public function getDescription()
    {
        echo 'I am an iron door';
    }
}
                
```

  

Then we have some fitting experts for each door type

``` 
interface DoorFittingExpert
{
    public function getDescription();
}

class Welder implements DoorFittingExpert
{
    public function getDescription()
    {
        echo 'I can only fit iron doors';
    }
}

class Carpenter implements DoorFittingExpert
{
    public function getDescription()
    {
        echo 'I can only fit wooden doors';
    }
}
                
```

Now we have our abstract factory that would let us make family of
related objects i.e. wooden door factory would create a wooden door and
wooden door fitting expert and iron door factory would create an iron
door and iron door fitting expert

``` 
interface DoorFactory
{
    public function makeDoor(): Door;
    public function makeFittingExpert(): DoorFittingExpert;
}

// Wooden factory to return carpenter and wooden door
class WoodenDoorFactory implements DoorFactory
{
    public function makeDoor(): Door
    {
        return new WoodenDoor();
    }

    public function makeFittingExpert(): DoorFittingExpert
    {
        return new Carpenter();
    }
}

// Iron door factory to get iron door and the relevant fitting expert
class IronDoorFactory implements DoorFactory
{
    public function makeDoor(): Door
    {
        return new IronDoor();
    }

    public function makeFittingExpert(): DoorFittingExpert
    {
        return new Welder();
    }
}
                
```

And then it can be used as

``` 
$woodenFactory = new WoodenDoorFactory();

$door = $woodenFactory->makeDoor();
$expert = $woodenFactory->makeFittingExpert();

$door->getDescription(); // Output: I am a wooden door
$expert->getDescription(); // Output: I can only fit wooden doors

// Same for Iron Factory
$ironFactory = new IronDoorFactory();

$door = $ironFactory->makeDoor();
$expert = $ironFactory->makeFittingExpert();

$door->getDescription(); // Output: I am an iron door
$expert->getDescription(); // Output: I can only fit iron doors
                                                            
                
```

As you can see the wooden door factory has encapsulated the `carpenter`
and the `  wooden door  ` also iron door factory has encapsulated the
` iron door  ` and `  welder  ` . And thus it had helped us make sure
that for each of the created door, we do not get a wrong fitting expert.



#### Python



``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?

In Java and other languages, the Abstract Factory Pattern serves to provide an interface for
creating related/dependent objects without need to specify their
actual class.

The idea is to abstract the creation of objects depending on business
logic, platform choice, etc.

In Python, the interface we use is simply a callable, which is "builtin" interface
in Python, and in normal circumstances we can simply use the class itself as
that callable, because classes are first class objects in Python.

*What does this example do?
This particular implementation abstracts the creation of a pet and
does so depending on the factory we chose (Dog or Cat, or random_animal)
This works because both Dog/Cat and random_animal respect a common
interface (callable for creation and .speak()).
Now my application can create pets abstractly and decide later,
based on my own criteria, dogs over cats.

*Where is the pattern used practically?

*References:
https://sourcemaking.com/design_patterns/abstract_factory
http://ginstrom.com/scribbles/2007/10/08/design-patterns-python-style/

*TL;DR
Provides a way to encapsulate a group of individual factories.
"""

import random


class PetShop(object):

    """A pet shop"""

    def __init__(self, animal_factory=None):
        """pet_factory is our abstract factory.  We can set it at will."""

        self.pet_factory = animal_factory

    def show_pet(self):
        """Creates and shows a pet using the abstract factory"""

        pet = self.pet_factory()
        print("We have a lovely {}".format(pet))
        print("It says {}".format(pet.speak()))


class Dog(object):
    def speak(self):
        return "woof"

    def __str__(self):
        return "Dog"


class Cat(object):
    def speak(self):
        return "meow"

    def __str__(self):
        return "Cat"


# Additional factories:

# Create a random animal
def random_animal():
    """Let's be dynamic!"""
    return random.choice([Dog, Cat])()


# Show pets with various factories
if __name__ == "__main__":

    # A Shop that sells only cats
    cat_shop = PetShop(Cat)
    cat_shop.show_pet()
    print("")

    # A shop that sells random animals
    shop = PetShop(random_animal)
    for i in range(3):
        shop.show_pet()
        print("=" * 20)

### OUTPUT ###
# We have a lovely Cat
# It says meow
#
# We have a lovely Dog
# It says woof
# ====================
# We have a lovely Cat
# It says meow
# ====================
# We have a lovely Cat
# It says meow
# ====================
                
```



### When to use?

When there are interrelated dependencies with not-that-simple creation logic involved

## Simple Factory

### Intent

### Problem

### Solution

### Structure

### Pseudocode

### Real world example

Consider, you are building a house and you need doors. You can either
put on your carpenter clothes, bring some wood, glue, nails and all the
tools required to build the door and start building it in your house or
you can simply call the factory and get the built door delivered to you
so that you don't need to learn anything about the door making or to
deal with the mess that comes with making it.

### In plain words

Simple factory simply generates an instance for client without exposing
any instantiation logic to the client

### Wikipedia says

In object-oriented programming (OOP), a factory is an object for
creating other objects – formally a factory is a function or method that
returns objects of a varying prototype or class from some method call,
which is assumed to be "new".

### Programmatic Example

First of all we have a door interface and the implementation

#### C\#

> 
> 
> ``` 
> public interface IDoor
> {
>     int GetHeight();
>     int GetWidth();
> }
> 
> public class WoodenDoor : IDoor
> {
>     private int Height { get; set; }
>     private int Width { get; set; }
> 
>     public WoodenDoor(int height, int width)
>     {
>         this.Height = height;
>         this.Width = width;
>     }
> 
>     public int GetHeight()
>     {
>         return this.Height;
>     }
>     public int GetWidth()
>     {
>         return this.Width;
>     }
> }
>                 
> ```

Then we have our door factory that makes the door and returns it

> 
> 
> ``` 
> public static class DoorFactory
> {
>     public static IDoor MakeDoor(int height, int width)
>     {
>         return new WoodenDoor(height, width);
>     }
> }
> 
>                 
> ```

And then it can be used as

> 
> 
> ``` 
> var door = DoorFactory.MakeDoor(80, 30);
> Console.WriteLine($"Height of Door : {door.GetHeight()}");
> Console.WriteLine($"Width of Door : {door.GetWidth()}");
>                 
> ```

#### PHP

``` 
interface Door
{
    public function getWidth(): float;
    public function getHeight(): float;
}

class WoodenDoor implements Door
{
    protected $width;
    protected $height;

    public function __construct(float $width, float $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getWidth(): float
    {
        return $this->width;
    }

    public function getHeight(): float
    {
        return $this->height;
    }
}
            
```

Then we have our door factory that makes the door and returns it

``` 
class DoorFactory
{
    public static function makeDoor($width, $height): Door
    {
        return new WoodenDoor($width, $height);
    }
}

            
```

And then it can be used as

``` 
// Make me a door of 100x200
$door = DoorFactory::makeDoor(100, 200);

echo 'Width: ' . $door->getWidth();
echo 'Height: ' . $door->getHeight();

// Make me a door of 50x100
$door2 = DoorFactory::makeDoor(50, 100);

            
```

### When to Use?

When creating an object is not just a few assignments and involves some
logic, it makes sense to put it in a dedicated factory instead of
repeating the same code everywhere.



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





## Prototype

<kbd>![](https://www.oodesign.com/images/creational/prototype-pattern.gif)</kbd>

### Intent

**Prototype** is a creational design pattern that lets you copy existing
objects without making your code dependent on their classes.

<kbd>![](./attachments/prototype/463530194.png)</kbd>

### Problem

Say you have an object, and you want to create an exact copy of it. How
would you do it? First, you have to create a new object of the same
class. Then you have to go through all the fields of the original object
and copy their values over to the new object.

Nice\! But there’s a catch. Not all objects can be copied that way
because some of the object’s fields may be private and not visible from
outside of the object itself.

<kbd>![](./attachments/prototype/463530196.png)</kbd>

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

<kbd>![](./attachments/prototype/463530197.png)</kbd>

Here’s how it works: you create a set of objects, configured in various
ways. When you need an object like the one you’ve configured, you just
clone a prototype instead of constructing a new object from scratch.

### Structure

#### Base Implementation

<kbd>![](./attachments/prototype/463530199.png)</kbd>

#### Prototype Registry Implementation

<kbd>![](./attachments/prototype/463530200.png</kbd>

### Pseudocode

In this example, the **Prototype** pattern lets you produce exact copies
of geometric objects, without coupling the code to their classes.

<kbd>![](./attachments/prototype/463530195.png)</kbd>

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
            <td><br /></td>
        </tr>
        <tr class="even">
            <td>You get an alternative to inheritance when dealing with configuration presets for complex objects.</td>
            <td><br /></td>
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

## Singleton

<kbd>![](https://www.oodesign.com/images/creational/singleton-pattern.gif)</kbd>

### Intent

**Singleton** is a creational design pattern that lets you ensure that a
class has only one instance, while providing a global access point to
this instance.

<kbd>![](./attachments/singleton/463530331.png)</kbd>

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
    
    <kbd>![](./attachments/singleton/463530332.png)</kbd>

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

<kbd>![](./attachments/singleton/463530333.png)</kbd>

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
            <td><br /></td>
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


