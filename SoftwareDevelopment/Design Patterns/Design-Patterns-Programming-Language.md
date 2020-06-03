<div id="main" class="aui-page-panel">

<div id="main-header">

<div id="breadcrumb-section">

1.  [Information Technology](index.html)
2.  [3.0 Sofware Development
    Lifecycle](3.0-Sofware-Development-Lifecycle_380470491.html)
3.  [Design Patterns](Design-Patterns_451820045.html)

</div>

# Information Technology : Design Pattern

</div>

<div id="content" class="view">

![](https://about.draw.io/wp-content/uploads/2018/10/UMLdiagrams.png)

There are three kinds of Design Patterns

  - Creational
  - Structural
  - Behavioral

In plain words

> Creational patterns are focused towards how to instantiate an object
> or group of related objects.

Wikipedia says

> In software engineering, creational design patterns are design
> patterns that deal with object creation mechanisms, trying to create
> objects in a manner suitable to the situation. The basic form of
> object creation could result in design problems or added complexity to
> the design. Creational design patterns solve this problem by somehow
> controlling this object creation.

## Creational Design Patterns

### Builder

![](https://www.oodesign.com/images/creational/builder-pattern.png)

#### Intent

**Builder** is a creational design pattern that lets you construct
complex objects step by step. The pattern allows you to produce
different types and representations of an object using the same
construction code.

![](attachments/463529996/463530184.png)

#### Problem

Imagine a complex object that requires laborious, step-by-step
initialization of many fields and nested objects. Such initialization
code is usually buried inside a monstrous constructor with lots of
parameters. Or even worse: scattered all over the client code.

![](attachments/463529996/463530188.png)

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

![](attachments/463529996/463530189.png)

In most cases most of the parameters will be unused, making [the
constructor calls pretty
ugly](https://refactoring.guru/smells/long-parameter-list). For
instance, only a fraction of houses have swimming pools, so the
parameters related to swimming pools will be useless nine times out of
ten.

#### Solution

The Builder pattern suggests that you extract the object construction
code out of its own class and move it to separate objects
called*builders*.

![](attachments/463529996/463530190.png)

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

![](attachments/463529996/463530185.png)

For example, imagine a builder that builds everything from wood and
glass, a second one that builds everything with stone and iron and a
third one that uses gold and diamonds. By calling the same set of steps,
you get a regular house from the first builder, a small castle from the
second and a palace from the third. However, this would only work if the
client code that calls the building steps is able to interact with
builders using a common interface.

#### Director

You can go further and extract a series of calls to the builder steps
you use to construct a product into a separate class called *director*.
The director class defines the order in which to execute the building
steps, while the builder provides the implementation for those steps.

![](attachments/463529996/463530186.png)

Having a director class in your program isn’t strictly necessary. You
can always call the building steps in a specific order directly from the
client code. However, the director class might be a good place to put
various construction routines so you can reuse them across your program.

In addition, the director class completely hides the details of product
construction from the client code. The client only needs to associate a
builder with a director, launch the construction with the director, and
get the result from the builder.

#### Structure

![](attachments/463529996/463530191.png)

#### Pseudocode

This example of the **Builder** pattern illustrates how you can reuse
the same object construction code when building different types of
products, such as cars, and create the corresponding manuals for them.

![](attachments/463529996/463530187.png)

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

#### Real world example

Imagine you are at Hardee's and you order a specific deal, lets say,
"Big Hardee" and they hand it over to you without *any questions*; this
is the example of simple factory. But there are cases when the creation
logic might involve more steps. For example you want a customized Subway
deal, you have several options in how your burger is made e.g what bread
do you want? what types of sauces would you like? What cheese would you
want? etc. In such cases builder pattern comes to the rescue.

#### In plain words

Allows you to create different flavors of an object while avoiding
constructor pollution. Useful when there could be several flavors of an
object. Or when there are a lot of steps involved in creation of an
object.

#### Wikipedia says

The builder pattern is an object creation software design pattern with
the intentions of finding a solution to the telescoping constructor
anti-pattern.

Having said that let me add a bit about what telescoping constructor
anti-pattern is. At one point or the other we have all seen a
constructor like below:

##### C\#

<div>

``` 
public Burger(int size, bool cheese, bool pepperoni, bool lettuce, bool tomato) {
}
                
```

</div>

##### Java

<div>

``` 
public Hero(Profession profession, String name, HairType hairType, HairColor hairColor, Armor armor, Weapon weapon) {
}
            
```

</div>

##### PHP

<div>

``` 
public function __construct($size, $cheese = true, $pepperoni = true, $tomato = false, $lettuce = true)
{
}
                
```

</div>

As you can see; the number of constructor parameters can quickly get out
of hand and it might become difficult to understand the arrangement of
parameters. Plus this parameter list could keep on growing if you would
want to add more options in future. This is called telescoping
constructor anti-pattern.

#### Pros and Cons

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
<td>You can construct objects step-by-step, defer construction steps or run steps recursively.</td>
<td>The overall complexity of the code increases since the pattern requires creating multiple new classes.</td>
</tr>
<tr class="even">
<td>You can reuse the same construction code when building various representations of products.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td><em>Single Responsibility Principle</em>. You can isolate complex construction code from the business logic of the product.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

The sane alternative is to use the builder pattern. First of all we have
our burger that we want to make

##### C\#

<div>

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
> ```

And then it can be used as:

> 
> 
> ``` 
> var burger = new BurgerBuilder(4).AddCheese()
>                 .AddPepperoni()
>                 .AddLettuce()
>                 .AddTomato()
>                 .Build();
> Console.WriteLine(burger.GetDescription());
>                 
> ```

</div>

##### Java

<div>

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

Hero mage = new Hero.Builder(Profession.MAGE, "Riobard").withHairColor(HairColor.BLACK).withWeapon(Weapon.DAGGER).build();
                
```

</div>

##### PHP

<div>

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

</div>

##### Python

<div>

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

</div>

#### When to use?

When there could be several flavors of an object and to avoid the
constructor telescoping. The key difference from the factory pattern is
that; factory pattern is to be used when the creation is a one step
process while builder pattern is to be used when the creation is a multi
step process.

### Abstract Factory

![](https://www.oodesign.com/images/creational/abstract-factory-pattern.png)

#### Intent

**Abstract Factory** is a creational design pattern that lets you
produce families of related objects without specifying their concrete
classes.

![](attachments/463529999/463530174.png)

#### Problem

Imagine that you’re creating a furniture shop simulator. Your code
consists of classes that represent:

1.  A family of related products, say: `Chair` + `Sofa` + `CoffeeTable`.

2.  Several variants of this family. For example, products `Chair` +
    `Sofa` + `CoffeeTable` are available in these variants: `Modern`,
    `Victorian`, `ArtDeco`.

![](attachments/463529999/463530178.png)

You need a way to create individual furniture objects so that they match
other objects of the same family. Customers get quite mad when they
receive non-matching furniture.

![](attachments/463529999/463530175.png)

Also, you don’t want to change existing code when adding new products or
families of products to the program. Furniture vendors update their
catalogs very often, and you wouldn’t want to change the core code each
time it happens.

#### Solution

The first thing the Abstract Factory pattern suggests is to explicitly
declare interfaces for each distinct product of the product family
(e.g., chair, sofa or coffee table). Then you can make all variants of
products follow those interfaces. For example, all chair variants can
implement the `Chair` interface; all coffee table variants can implement
the `CoffeeTable` interface, and so on.

![](attachments/463529999/463530179.png)

The next move is to declare the *Abstract Factory*—an interface with a
list of creation methods for all products that are part of the product
family (for example, `createChair`, `createSofa` and
`createCoffeeTable`). These methods must return **abstract** product
types represented by the interfaces we extracted previously: `Chair`,
`Sofa`, `CoffeeTable` and so on.

![](attachments/463529999/463530180.png)

Now, how about the product variants? For each variant of a product
family, we create a separate factory class based on the
`AbstractFactory` interface. A factory is a class that returns products
of a particular kind. For example, the `ModernFurnitureFactory` can only
create `ModernChair`, `ModernSofa` and `ModernCoffeeTable` objects.

The client code has to work with both factories and products via their
respective abstract interfaces. This lets you change the type of a
factory that you pass to the client code, as well as the product variant
that the client code receives, without breaking the actual client code.

![](attachments/463529999/463530176.png)

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

#### Structure

![](attachments/463529999/463530181.png)

#### Pseudocode

This example illustrates how the **Abstract Factory** pattern can be
used for creating cross-platform UI elements without coupling the client
code to concrete UI classes, while keeping all created elements
consistent with a selected operating system.

![](attachments/463529999/463530177.png)

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

#### Real world example

Extending our door example from Simple Factory. Based on your needs you
might get a wooden door from a wooden door shop, iron door from an iron
shop or a PVC door from the relevant shop. Plus you might need a guy
with different kind of specialities to fit the door, for example a
carpenter for wooden door, welder for iron door etc. As you can see
there is a dependency between the doors now, wooden door needs
carpenter, iron door needs a welder etc.

#### In plain words

A factory of factories; a factory that groups the individual but
related/dependent factories together without specifying their concrete
classes.

#### Wikipedia says

The abstract factory pattern provides a way to encapsulate a group of
individual factories that have a common theme without specifying their
concrete classes

#### Pros and Cons

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
<td>You can be sure that the products you’re getting from a factory are compatible with each other.</td>
<td>The code may become more complicated than it should be, since a lot of new interfaces and classes are introduced along with the pattern.</td>
</tr>
<tr class="even">
<td>You avoid tight coupling between concrete products and client code.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td>S<em>ingle Responsibility Principle</em>. You can extract the product creation code into one place, making the code easier to support.</td>
<td><br />
</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em>. You can introduce new variants of products without breaking existing client code.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

Translating the door example above. First of all we have our `Door`
interface and some implementation for it

##### C\#

<div>

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

</div>

##### Java

<div>

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

</div>

##### PHP

<div>

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

</div>

##### Python

<div>

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

</div>

#### When to use?

When there are interrelated dependencies with not-that-simple creation
logic involved

### Simple Factory

#### Intent

#### Problem

#### Solution

#### Structure

#### Pseudocode

#### Real world example

Consider, you are building a house and you need doors. You can either
put on your carpenter clothes, bring some wood, glue, nails and all the
tools required to build the door and start building it in your house or
you can simply call the factory and get the built door delivered to you
so that you don't need to learn anything about the door making or to
deal with the mess that comes with making it.

#### In plain words

Simple factory simply generates an instance for client without exposing
any instantiation logic to the client

#### Wikipedia says

In object-oriented programming (OOP), a factory is an object for
creating other objects – formally a factory is a function or method that
returns objects of a varying prototype or class from some method call,
which is assumed to be "new".

#### Programmatic Example

First of all we have a door interface and the implementation

##### C\#

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

##### PHP

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

#### When to Use?

When creating an object is not just a few assignments and involves some
logic, it makes sense to put it in a dedicated factory instead of
repeating the same code everywhere.

### Factory Method

![](https://www.oodesign.com/images/creational/factory-method-pattern.gif)

#### Intent

**Factory Method** is a creational design pattern that provides an
interface for creating objects in a superclass, but allows subclasses to
alter the type of objects that will be created.

![](attachments/463530001/463530165.png)

#### Problem

Imagine that you’re creating a logistics management application. The
first version of your app can only handle transportation by trucks, so
the bulk of your code lives inside the `Truck` class.

After a while, your app becomes pretty popular. Each day you receive
dozens of requests from sea transportation companies to incorporate sea
logistics into the app.

![](attachments/463530001/463530167.png)

Great news, right? But how about the code? At present, most of your code
is coupled to the `Truck` class. Adding `Ships` into the app would
require making changes to the entire codebase. Moreover, if later you
decide to add another type of transportation to the app, you will
probably need to make all of these changes again.

As a result, you will end up with pretty nasty code, riddled with
conditionals that switch the app’s behavior depending on the class of
transportation objects.

#### Solution

The Factory Method pattern suggests that you replace direct object
construction calls (using the `new` operator) with calls to a special
*factory* method. Don’t worry: the objects are still created via the
`new` operator, but it’s being called from within the factory method.
Objects returned by a factory method are often referred to as
“products.”

![](attachments/463530001/463530168.png)

At first glance, this change may look pointless: we just moved the
constructor call from one part of the program to another. However,
consider this: now you can override the factory method in a subclass and
change the class of products being created by the method.

There’s a slight limitation though: subclasses may return different
types of products only if these products have a common base class or
interface. Also, the factory method in the base class should have its
return type declared as this interface.

![](attachments/463530001/463530169.png)

For example, both `Truck` and `Ship` classes should implement
the`Transport` interface, which declares a method called`deliver`. Each
class implements this method differently: trucks deliver cargo by land,
ships deliver cargo by sea. The factory method in the `RoadLogistics`
class returns truck objects, whereas the factory method in the
`SeaLogistics` class returns ships.

![](attachments/463530001/463530170.png)

The code that uses the factory method (often called the *client* code)
doesn’t see a difference between the actual products returned by various
subclasses. The client treats all the products as abstract `Transport` .
The client knows that all transport objects are supposed to have the
`deliver` method, but exactly how it works isn’t important to the
client.

#### Structure

![](attachments/463530001/463530171.png)

#### Pseudocode

This example illustrates how the **Factory Method** can be used for
creating cross-platform UI elements without coupling the client code to
concrete UI classes.

![](attachments/463530001/463530166.png)

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

#### Real world example

Consider the case of a hiring manager. It is impossible for one person
to interview for each of the positions. Based on the job opening, she
has to decide and delegate the interview steps to different people.

#### In plain words

It provides a way to delegate the instantiation logic to child classes.

#### Wikipedia says

In class-based programming, the factory method pattern is a creational
pattern that uses factory methods to deal with the problem of creating
objects without having to specify the exact class of the object that
will be created. This is done by creating objects by calling a factory
method—either specified in an interface and implemented by child
classes, or implemented in a base class and optionally overridden by
derived classes—rather than by calling a constructor.

#### Programmatic Example

Taking our hiring manager example above. First of all we have an
interviewer interface and some implementations for it

##### C\#

<div>

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

</div>

##### Java

<div>

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

</div>

##### PHP

<div>

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

</div>

##### Python

<div>

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

</div>

</div>

#### When to use?

Useful when there is some generic processing in a class but the required
sub-class is dynamically decided at runtime. Or putting it in other
words, when the client doesn't know what exact sub-class it might need.

### Prototype

![](https://www.oodesign.com/images/creational/prototype-pattern.gif)

#### Intent

**Prototype** is a creational design pattern that lets you copy existing
objects without making your code dependent on their classes.

![](attachments/463530002/463530194.png)

#### Problem

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

#### Solution

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

#### Structure

##### Base Implementation

![](attachments/463530002/463530199.png)

##### Prototype Registry Implementation

![](attachments/463530002/463530200.png)

#### Pseudocode

In this example, the **Prototype** pattern lets you produce exact copies
of geometric objects, without coupling the code to their classes.

![](attachments/463530002/463530195.png)

All shape classes follow the same interface, which provides a cloning
method. A subclass may call the parent’s cloning method before copying
its own field values to the resulting object.

#### Real world example

Remember dolly? The sheep that was cloned\! Lets not get into the
details but the key point here is that it is all about cloning

#### In plain words

Create object based on an existing object through cloning.

#### Wikipedia says

The prototype pattern is a creational design pattern in software
development. It is used when the type of objects to create is determined
by a prototypical instance, which is cloned to produce new objects.

In short, it allows you to create a copy of an existing object and
modify it to your needs, instead of going through the trouble of
creating an object from scratch and setting it up.

#### Pros and Cons

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

</div>

#### Programmatic Example

##### C\#

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

</div>

##### Java

<div>

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

</div>

##### PHP

<div>

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

##### Python

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

</div>

#### When to use?

When an object is required that is similar to existing object or when
the creation would be expensive as compared to cloning.

### Singleton

![](https://www.oodesign.com/images/creational/singleton-pattern.gif)

#### Intent

**Singleton** is a creational design pattern that lets you ensure that a
class has only one instance, while providing a global access point to
this instance.

![](attachments/463530003/463530331.png)

#### Problem

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

#### Solution

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

#### Structure

![](attachments/463530003/463530333.png)

#### Pseudocode

#### Real world example

There can only be one president of a country at a time. The same
president has to be brought to action, whenever duty calls. President
here is singleton.

#### In plain words

Ensures that only one object of a particular class is ever created.

#### Wikipedia says

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

#### Pros and Cons

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

</div>

#### Programmatic Example

To create a singleton, make the constructor private, disable cloning,
disable extension and create a static variable to house the instance

##### C\#

<div>

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

</div>

##### Java

<div>

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

</div>

##### PHP

<div>

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

</div>

##### Python

<div>

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

## Structural Design Pattern

### Adapter

![](https://www.oodesign.com/images/structural/adapter-pattern.png)

#### Intent

**Adapter** is a structural design pattern that allows objects with
incompatible interfaces to collaborate.

![](attachments/463530012/463530256.png)

#### Problem

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

#### Solution

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

#### Structure

##### Object adapter

This implementation uses the object composition principle: the adapter
implements the interface of one object and wraps the other one. It can
be implemented in all popular programming languages.

![](attachments/463530012/463530261.png)

##### Class adapter

This implementation uses inheritance: the adapter inherits interfaces
from both objects at the same time. Note that this approach can only be
implemented in programming languages that support multiple inheritance,
such as C++.

![](attachments/463530012/463530260.png)

#### Pseudocode

This example of the **Adapter** pattern is based on the classic conflict
between square pegs and round holes.

![](attachments/463530012/463530257.png)

#### Real world example

Consider that you have some pictures in your memory card and you need to
transfer them to your computer. In order to transfer them you need some
kind of adapter that is compatible with your computer ports so that you
can attach memory card to your computer. In this case card reader is an
adapter. Another example would be the famous power adapter; a three
legged plug can't be connected to a two pronged outlet, it needs to use
a power adapter that makes it compatible with the two pronged outlet.
Yet another example would be a translator translating words spoken by
one person to another

#### In plain words

Adapter pattern lets you wrap an otherwise incompatible object in an
adapter to make it compatible with another class.

#### Wikipedia says

In software engineering, the adapter pattern is a software design
pattern that allows the interface of an existing class to be used as
another interface. It is often used to make existing classes work with
others without modifying their source code.

#### Pros and Cons

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

#### Programmatic Example

##### C\#

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

##### Java

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

##### JavaScript

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

##### PHP

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

##### Python

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

### Bridge

![](https://www.oodesign.com/images/structural/bridge-pattern.png)

#### Intent

**Bridge** is a structural design pattern that lets you split a large
class or a set of closely related classes into two separate
hierarchies—abstraction and implementation—which can be developed
independently of each other.

![](attachments/463530014/463530247.png)

#### Problem

*Abstraction?* *Implementation?* Sound scary? Stay calm and let’s
consider a simple example.

Say you have a geometric `Shape` class with a pair of subclasses:
`Circle` and `Square`. You want to extend this class hierarchy to
incorporate colors, so you plan to create `Red` and `Blue` shape
subclasses. However, since you already have two subclasses, you’ll need
to create four class combinations such as `BlueCircle` and `RedSquare`.

![](attachments/463530014/463530251.png)

Adding new shape types and colors to the hierarchy will grow it
exponentially. For example, to add a triangle shape you’d need to
introduce two subclasses, one for each color. And after that, adding a
new color would require creating three subclasses, one for each shape
type. The further we go, the worse it becomes.

#### Solution

This problem occurs because we’re trying to extend the shape classes in
two independent dimensions: by form and by color. That’s a very common
issue with class inheritance.

The Bridge pattern attempts to solve this problem by switching from
inheritance to the object composition. What this means is that you
extract one of the dimensions into a separate class hierarchy, so that
the original classes will reference an object of the new hierarchy,
instead of having all of its state and behaviors within one class.

![](attachments/463530014/463530252.png)

Following this approach, we can extract the color-related code into its
own class with two subclasses: `Red` and `Blue`. The `Shape` class then
gets a reference field pointing to one of the color objects. Now the
shape can delegate any color-related work to the linked color object.
That reference will act as a bridge between the `Shape` and `Color`
classes. From now on, adding new colors won’t require changing the shape
hierarchy, and vice versa.

#### Abstraction and Implementation

The GoF book introduces the terms *Abstraction* and *Implementation* as
part of the Bridge definition. In my opinion, the terms sound too
academic and make the pattern seem more complicated than it really is.
Having read the simple example with shapes and colors, let’s decipher
the meaning behind the GoF book’s scary words.

*Abstraction* (also called *interface*) is a high-level control layer
for some entity. This layer isn’t supposed to do any real work on its
own. It should delegate the work to the *implementation* layer (also
called *platform*).

Note that we’re not talking about *interfaces* or *abstract classes*
from your programming language. These aren’t the same things.

When talking about real applications, the abstraction can be represented
by a graphical user interface (GUI), and the implementation could be the
underlying operating system code (API) which the GUI layer calls in
response to user interactions.

Generally speaking, you can extend such an app in two independent
directions:

  - Have several different GUIs (for instance, tailored for regular
    customers or admins).
  - Support several different APIs (for example, to be able to launch
    the app under Windows, Linux, and MacOS).

In a worst-case scenario, this app might look like a giant spaghetti
bowl, where hundreds of conditionals connect different types of GUI with
various APIs all over the code.

![](attachments/463530014/463530249.png)

You can bring order to this chaos by extracting the code related to
specific interface-platform combinations into separate classes. However,
soon you’ll discover that there are *lots* of these classes. The class
hierarchy will grow exponentially because adding a new GUI or supporting
a different API would require creating more and more classes.

Let’s try to solve this issue with the Bridge pattern. It suggests that
we divide the classes into two hierarchies:

  - Abstraction: the GUI layer of the app.
  - Implementation: the operating systems’ APIs.

![](attachments/463530014/463530248.png)

The abstraction object controls the appearance of the app, delegating
the actual work to the linked implementation object. Different
implementations are interchangeable as long as they follow a common
interface, enabling the same GUI to work under Windows and Linux.

As a result, you can change the GUI classes without touching the
API-related classes. Moreover, adding support for another operating
system only requires creating a subclass in the implementation
hierarchy.

#### Structure

![](attachments/463530014/463530253.png)

#### Pseudocode

This example illustrates how the **Bridge** pattern can help divide the
monolithic code of an app that manages devices and their remote
controls. The `Device` classes act as the implementation, whereas the
`Remote`s act as the abstraction.

![](attachments/463530014/463530250.png)

The base remote control class declares a reference field that links it
with a device object. All remotes work with the devices via the general
device interface, which lets the same remote support multiple device
types.

You can develop the remote control classes independently from the device
classes. All that’s needed is to create a new remote subclass. For
example, a basic remote control might only have two buttons, but you
could extend it with additional features, such as an extra battery or a
touchscreen.

The client code links the desired type of remote control with a specific
device object via the remote’s constructor.

#### Real world example

Consider you have a website with different pages and you are supposed to
allow the user to change the theme. What would you do? Create multiple
copies of each of the pages for each of the themes or would you just
create separate theme and load them based on the user's preferences?
Bridge pattern allows you to do the second i.e.

<https://cloud.githubusercontent.com/assets/11269635/23065293/33b7aea0-f515-11e6-983f-98823c9845ee.png>

#### In Plain Words

Bridge pattern is about preferring composition over inheritance.
Implementation details are pushed from a hierarchy to another object
with a separate hierarchy.

#### Wikipedia says

The bridge pattern is a design pattern used in software engineering that
is meant to "decouple an abstraction from its implementation so that the
two can vary independently"

#### Pros and Cons

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
<td>You can create platform-independent classes and apps.</td>
<td>You might make the code more complicated by applying the pattern to a highly cohesive class.</td>
</tr>
<tr class="even">
<td>The client code works with high-level abstractions. It isn’t exposed to the platform details.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td><em>Open/Closed Principle</em>. You can introduce new abstractions and implementations independently from each other.</td>
<td><br />
</td>
</tr>
<tr class="even">
<td><em>Single Responsibility Principle</em>. You can focus on high-level logic in the abstraction and on platform details in the implementation.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

##### Programmatic Example

##### C\#

<div>

<div id="expander-content-863576251" class="expand-content">

Translating our WebPage example from above. Here we have the 
`WebPage` hierarchy interface

> 
> 
> ``` 
> IWebPage { string GetContent(); 
> } 
> class About : IWebPage { 
>     protected ITheme theme; 
>     public About( ITheme theme) { 
>         this. theme = theme; 
>     } 
>     public string GetContent() { 
>         return $"About page in {
>             theme.GetColor()}"; 
>         } 
>     } 
> class Careers : IWebPage { 
>     protected ITheme theme; 
>     public Careers( ITheme theme) { 
>         this. theme = theme; 
>     } 
>     public string GetContent() { 
>     return $"Careers page in {theme.GetColor()}"; 
>     } 
> }
>                         
> ```

And the separate theme hierarchy

> 
> 
> ``` 
> interface ITheme {
>     string GetColor();
> }
> 
> class DarkTheme : ITheme {
>     public string GetColor() {
>         return "Dark Black";
>     }
> }
> 
> class LightTheme : ITheme {
>     public string GetColor() {
>         return "Off White";
>     }
> }
> 
> class AquaTheme : ITheme {
>     public string GetColor()
>     {
>         return "Light blue";
>     }
> }
>                         
> ```

And both the hierarchies

> 
> 
> ``` 
> var darkTheme = new DarkTheme();
> var lightTheme = new LightTheme();
> 
> var about= new About(darkTheme);
> var careers = new Careers(lightTheme);
> 
> Console.WriteLine(about.GetContent()); //Output: About page in Dark Black
> Console.WriteLine(careers.GetContent()); //Output: Careers page in Off White
>                         
> ```

</div>

##### Java

<div>

Translating our weapon example from above. Here we have the `Weapon`
hierarchy

``` 
public interface Weapon {
    void wield();
    void swing();
    void unwield();
    Enchantment getEnchantment();
}

public class Sword implements Weapon {
    private final Enchantment enchantment;

    public Sword(Enchantment enchantment) {
        this.enchantment = enchantment;
    }

    @Override
    public void wield() {
        LOGGER.info("The sword is wielded.");
        enchantment.onActivate();
    }

    @Override
    public void swing() {
        LOGGER.info("The sword is swinged.");
        enchantment.apply();
    }

    @Override
    public void unwield() {
        LOGGER.info("The sword is unwielded.");
        enchantment.onDeactivate();
    }

    @Override
    public Enchantment getEnchantment() {
        return enchantment;
    }
}

public class Hammer implements Weapon {
    private final Enchantment enchantment;

    public Hammer(Enchantment enchantment) {
        this.enchantment = enchantment;
    }

    @Override
    public void wield() {
        LOGGER.info("The hammer is wielded.");
        enchantment.onActivate();
    }

    @Override
    public void swing() {
        LOGGER.info("The hammer is swinged.");
        enchantment.apply();
    }

    @Override
    public void unwield() {
        LOGGER.info("The hammer is unwielded.");
        enchantment.onDeactivate();
    }

    @Override
    public Enchantment getEnchantment() {
        return enchantment;
    }
}
                    
```

And the separate enchantment hierarchy

``` 
public interface Enchantment {
    void onActivate();
    void apply();
    void onDeactivate();
}

public class FlyingEnchantment implements Enchantment {
    @Override
    public void onActivate() {
        LOGGER.info("The item begins to glow faintly.");
    }

    @Override
    public void apply() {
        LOGGER.info("The item flies and strikes the enemies finally returning to owner's hand.");
    }

    @Override
    public void onDeactivate() {
        LOGGER.info("The item's glow fades.");
    }
}

public class SoulEatingEnchantment implements Enchantment {
    @Override
    public void onActivate() {
        LOGGER.info("The item spreads bloodlust.");
    }

    @Override
    public void apply() {
        LOGGER.info("The item eats the soul of enemies.");
    }

    @Override
    public void onDeactivate() {
        LOGGER.info("Bloodlust slowly disappears.");
    }
}
                    
```

And both the hierarchies in action

``` 
Sword enchantedSword = new Sword(new SoulEatingEnchantment());
enchantedSword.wield();
enchantedSword.swing();
enchantedSword.unwield();
// The sword is wielded.
// The item spreads bloodlust.
// The sword is swinged.
// The item eats the soul of enemies.
// The sword is unwielded.
// Bloodlust slowly disappears.

Hammer hammer = new Hammer(new FlyingEnchantment());
hammer.wield();
hammer.swing();
hammer.unwield();
// The hammer is wielded.
// The item begins to glow faintly.
// The hammer is swinged.
// The item flies and strikes the enemies finally returning to owner's hand.
// The hammer is unwielded.
// The item's glow fades.
                    
```

</div>

##### JavaScript

<div>

Translating our WebPage example from above. Here we have the `WebPage`
hierarchy

``` 
/*
Webpage interface :
constructor(theme)
getContent()
*/

class About{ 
    constructor(theme) {
        this.theme = theme
    }

    getContent() {
        return "About page in " + this.theme.getColor()
    }
}

class Careers{
    constructor(theme) {
        this.theme = theme
    }
   
    getContent() {
        return "Careers page in " + this.theme.getColor()
    } 
}
                    
```

And the separate theme hierarchy

``` 
/*
Theme interface :

getColor()
*/

class DarkTheme{
    getColor() {
        return 'Dark Black'
    }
}
class LightTheme{
    getColor() {
        return 'Off white'
    }
}
class AquaTheme{
    getColor() {
        return 'Light blue'
    }
}
                    
```

And both the hierarchies

``` 
const darkTheme = new DarkTheme()

const about = new About(darkTheme)
const careers = new Careers(darkTheme)

console.log(about.getContent() )// "About page in Dark Black"
console.log(careers.getContent() )// "Careers page in Dark Black"
                    
```

</div>

##### PHP

<div>

``` 
interface WebPage {  
    public function __construct(Theme $theme);  
    public function getContent(); 
} 
class About implements WebPage {  
    protected $theme;  
    public function __construct(Theme $theme)  {  
        $this->theme = $theme;  
    }  
    public function getContent()  {  
        return "About page in " . $this->theme->getColor();  
    } 
} 
class Careers implements WebPage {  
    protected $theme;  
    public function __construct(Theme $theme)  {  
        $this->theme = $theme;  
    }  
    public function getContent()  {  
        return "Careers page in " . $this->theme->getColor();  
    } 
}
                    
```

And the separate theme hierarchy

``` 
interface Theme {
    public function getColor();
}

class DarkTheme implements Theme {
    public function getColor() {
        return 'Dark Black';
    }
}
class LightTheme implements Theme {
    public function getColor() {
        return 'Off white';
    }
}
class AquaTheme implements Theme {
    public function getColor() {
        return 'Light blue';
    }
}
                    
```

And both the hierarchies

``` 
$darkTheme = new DarkTheme();

$about = new About($darkTheme);
$careers = new Careers($darkTheme);

echo $about->getContent(); // "About page in Dark Black";
echo $careers->getContent(); // "Careers page in Dark Black";
                    
```

</div>

##### Python

<div>

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*References:
http://en.wikibooks.org/wiki/Computer_Science_Design_Patterns/Bridge_Pattern#Python

*TL;DR
Decouples an abstraction from its implementation.
"""

# ConcreteImplementor 1/2
class DrawingAPI1(object):
    def draw_circle(self, x, y, radius):
        print('API1.circle at {}:{} radius {}'.format(x, y, radius))

# ConcreteImplementor 2/2
class DrawingAPI2(object):
    def draw_circle(self, x, y, radius):
        print('API2.circle at {}:{} radius {}'.format(x, y, radius))

# Refined Abstraction
class CircleShape(object):
    def __init__(self, x, y, radius, drawing_api):
        self._x = x
        self._y = y
        self._radius = radius
        self._drawing_api = drawing_api

    # low-level i.e. Implementation specific
    def draw(self):
        self._drawing_api.draw_circle(self._x, self._y, self._radius)

    # high-level i.e. Abstraction specific
    def scale(self, pct):
        self._radius *= pct

def main():
    shapes = (CircleShape(1, 2, 3, DrawingAPI1()), CircleShape(5, 7, 11, DrawingAPI2()))

    for shape in shapes:
        shape.scale(2.5)
        shape.draw()

if __name__ == '__main__':
    main()

### OUTPUT ###
# API1.circle at 1:2 radius 7.5
# API2.circle at 5:7 radius 27.5
                    
```

</div>

### Composite

![](https://www.oodesign.com/images/structural/composite-pattern.png)

#### Intent

**Composite** is a structural design pattern that lets you compose
objects into tree structures and then work with these structures as if
they were individual objects.

![](attachments/463530015/463530240.png)

#### Problem

Using the Composite pattern makes sense only when the core model of your
app can be represented as a tree.

For example, imagine that you have two types of objects: `Products` and
`Boxes`. A `Box` can contain several `Products` as well as a number of
smaller `Boxes`. These little `Boxes` can also hold some `Products` or
even smaller `Boxes`, and so on.

Say you decide to create an ordering system that uses these classes.
Orders could contain simple products without any wrapping, as well as
boxes stuffed with products...and other boxes. How would you determine
the total price of such an order?

![](attachments/463530015/463530243.png)

You could try the direct approach: unwrap all the boxes, go over all the
products and then calculate the total. That would be doable in the real
world; but in a program, it’s not as simple as running a loop. You have
to know the classes of `Products` and `Boxes` you’re going through, the
nesting level of the boxes and other nasty details beforehand. All of
this makes the direct approach either too awkward or even impossible.

#### Solution

The Composite pattern suggests that you work with `Products` and `Boxes`
through a common interface which declares a method for calculating the
total price.

How would this method work? For a product, it’d simply return the
product’s price. For a box, it’d go over each item the box contains, ask
its price and then return a total for this box. If one of these items
were a smaller box, that box would also start going over its contents
and so on, until the prices of all inner components were calculated. A
box could even add some extra cost to the final price, such as packaging
cost.

![](attachments/463530015/463530241.png)

The greatest benefit of this approach is that you don’t need to care
about the concrete classes of objects that compose the tree. You don’t
need to know whether an object is a simple product or a sophisticated
box. You can treat them all the same via the common interface. When you
call a method, the objects themselves pass the request down the tree.

#### Structure

![](attachments/463530015/463530244.png)

#### Pseudocode

In this example, the **Composite** pattern lets you implement stacking
of geometric shapes in a graphical editor.

![](attachments/463530015/463530242.png)

The `CompoundGraphic` class is a container that can comprise any number
of sub-shapes, including other compound shapes. A compound shape has the
same methods as a simple shape. However, instead of doing something on
its own, a compound shape passes the request recursively to all its
children and “sums up” the result.

The client code works with all shapes through the single interface
common to all shape classes. Thus, the client doesn’t know whether it’s
working with a simple shape or a compound one. The client can work with
very complex object structures without being coupled to concrete classes
that form that structure.

#### Real world example

Every organization is composed of employees. Each of the employees has
the same features i.e. has a salary, has some responsibilities, may or
may not report to someone, may or may not have some subordinates etc.

#### In plain words

Composite pattern lets clients treat the individual objects in a uniform
manner.

#### Wikipedia says

In software engineering, the composite pattern is a partitioning design
pattern. The composite pattern describes that a group of objects is to
be treated in the same way as a single instance of an object. The intent
of a composite is to "compose" objects into tree structures to represent
part-whole hierarchies. Implementing the composite pattern lets clients
treat individual objects and compositions uniformly.

#### Pros and Cons

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
<td>You can work with complex tree structures more conveniently: use polymorphism and recursion to your advantage.</td>
<td>It might be difficult to provide a common interface for classes whose functionality differs too much. In certain scenarios, you’d need to overgeneralize the component interface, making it harder to comprehend.</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em>. You can introduce new element types into the app without breaking the existing code, which now works with the object tree.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

Taking our employees example from above. Here we have different employee
types

##### C\#

<div>

> 
> 
> ``` 
> 
> interface IEmployee
> {
>     float GetSalary();
>     string GetRole();
>     string GetName();
> }
> 
> class Developer : IEmployee {
>     private string mName;
>     private float mSalary;
> 
>     public Developer(string name, float salary) {
>         this.mName = name;
>         this.mSalary = salary;
>     }
> 
>     public float GetSalary() {
>         return this.mSalary;
>     }
> 
>     public string GetRole() {
>         return "Developer";
>     }
> 
>     public string GetName() {
>         return this.mName;
>     }
> }
> 
> class Designer : IEmployee {
>     private string mName;
>     private float mSalary;
> 
>     public Designer(string name, float salary) {
>         this.mName = name;
>         this.mSalary = salary;
>     }
> 
>     public float GetSalary() {
>         return this.mSalary;
>     }
> 
>     public string GetRole() {
>         return "Designer";
>     }
> 
>     public string GetName() {
>         return this.mName;
>     }
> }
>                     
> ```

Then we have an organization which consists of several different types
of employees

> 
> 
> ``` 
> class Organization {
>     protected List <IEmployee> employees;
> 
>     public Organization() {
>         employees = new List<IEmployee>();
>     }
> 
>     public void AddEmployee(IEmployee employee) {
>         employees.Add(employee);
>     }
> 
>     public float GetNetSalaries() {
>         float netSalary = 0;
> 
>         foreach (var e in employees) {
>             netSalary += e.GetSalary();
>         }
>         return netSalary;
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
> //Arrange Employees, Organization and add employees
> var developer = new Developer("John", 5000);
> var designer = new Designer("Arya", 5000);
> 
> var organization = new Organization();
> organization.AddEmployee(developer);
> organization.AddEmployee(designer);
> 
> Console.WriteLine($"Net Salary of Employees in Organization is {organization.GetNetSalaries():c}");
> //Ouptut: Net Salary of Employees in Organization is $10000.00
>                     
> ```

</div>

##### Java

<div>

Taking our sentence example from above. Here we have the base class and
different printable types

``` 
public abstract class LetterComposite {
    private List <LetterComposite> children = new ArrayList<>();
    public void add(LetterComposite letter) {
        children.add(letter);
    }
    public int count() {
        return children.size();
    }
    protected void printThisBefore() {}
    protected void printThisAfter() {}
    public void print() {
        printThisBefore();
        for (LetterComposite letter : children) {
            letter.print();
        }
        printThisAfter();
    }
}

public class Letter extends LetterComposite {
    private char c;
    public Letter(char c) {
        this.c = c;
    }
    @Override
    protected void printThisBefore() {
        System.out.print(c);
    }
}

public class Word extends LetterComposite {
    public Word(List<Letter> letters) {
        for (Letter l : letters) {
            this.add(l);
        }
    }
    @Override
    protected void printThisBefore() {
        System.out.print(" ");
    }
}

public class Sentence extends LetterComposite {
    public Sentence(List<Word> words) {
        for (Word w : words) {
            this.add(w);
        }
    }
    @Override
    protected void printThisAfter() {
        System.out.print(".");
    }
}
                
```

Then we have a messenger to carry messages

``` 
public class Messenger {
    LetterComposite messageFromOrcs() {
        List<Word> words = new ArrayList<>();
        words.add(new Word(Arrays.asList(new Letter('W'), new Letter('h'), new Letter('e'), new Letter('r'), new Letter('e'))));
        words.add(new Word(Arrays.asList(new Letter('t'), new Letter('h'), new Letter('e'), new Letter('r'), new Letter('e'))));
        words.add(new Word(Arrays.asList(new Letter('i'), new Letter('s'))));
        words.add(new Word(Arrays.asList(new Letter('a'))));
        words.add(new Word(Arrays.asList(new Letter('w'), new Letter('h'), new Letter('i'), new Letter('p'))));
        words.add(new Word(Arrays.asList(new Letter('t'), new Letter('h'), new Letter('e'), new Letter('r'), new Letter('e'))));
        words.add(new Word(Arrays.asList(new Letter('i'), new Letter('s'))));
        words.add(new Word(Arrays.asList(new Letter('a'))));
        words.add(new Word(Arrays.asList(new Letter('w'), new Letter('a'), new Letter('y'))));
        return new Sentence(words);
    }

    LetterComposite messageFromElves() {
        List<Word> words = new ArrayList<>();
        words.add(new Word(Arrays.asList(new Letter('M'), new Letter('u'), new Letter('c'), new Letter('h'))));
        words.add(new Word(Arrays.asList(new Letter('w'), new Letter('i'), new Letter('n'), new Letter('d'))));
        words.add(new Word(Arrays.asList(new Letter('p'), new Letter('o'), new Letter('u'), new Letter('r'), new Letter('s'))));
        words.add(new Word(Arrays.asList(new Letter('f'), new Letter('r'), new Letter('o'), new Letter('m'))));
        words.add(new Word(Arrays.asList(new Letter('y'), new Letter('o'), new Letter('u'), new Letter('r'))));
        words.add(new Word(Arrays.asList(new Letter('m'), new Letter('o'), new Letter('u'), new Letter('t'), new Letter('h'))));
        return new Sentence(words);
    }
}
                
```

And then it can be used as

``` 
LetterComposite orcMessage = new Messenger().messageFromOrcs();
orcMessage.print(); // Where there is a whip there is a way.
LetterComposite elfMessage = new Messenger().messageFromElves();
elfMessage.print(); // Much wind pours from your mouth.
                
```

</div>

##### JavaScript

<div>

Taking our employees example from above. Here we have different employee
types

``` 
/*
Employee interface :

constructor(name, salary)
getName()
setSalary()
getSalary()
getRoles()
*/

class Developer {
    constructor(name, salary) {
        this.name = name
        this.salary = salary
    }

    getName() {
        return this.name
    }

    setSalary(salary) {
        this.salary = salary
    }

    getSalary() {
        return this.salary
    }

    getRoles() {
        return this.roles
    }

    develop() {
        /* */
    }
}

class Designer {

    constructor(name, salary) {
        this.name = name
        this.salary = salary
    }

    getName() {
        return this.name
    }

    setSalary(salary) {
        this.salary = salary
    }

    getSalary() {
        return this.salary
    }

    getRoles() {
        return this.roles
    }

    design() {
        /* */
    }
}
                
```

Then we have an organization which consists of several different types
of employees

``` 
class Organization {
    constructor(){
        this.employees = []
    }

    addEmployee(employee) {
        this.employees.push(employee)
    }

    getNetSalaries() {
        let netSalary = 0

        this.employees.forEach(employee => {
            netSalary += employee.getSalary()
        })

        return netSalary
    }
}

                
```

And then it can be used as

``` 
// Prepare the employees
const john = new Developer('John Doe', 12000)
const jane = new Designer('Jane', 10000)

// Add them to organization
const organization = new Organization()
organization.addEmployee(john)
organization.addEmployee(jane)

console.log("Net salaries: " , organization.getNetSalaries()) // Net Salaries: 22000
                
```

</div>

##### PHP

<div>

``` 
interface Employee
{
    public function __construct(string $name, float $salary);
    public function getName(): string;
    public function setSalary(float $salary);
    public function getSalary(): float;
    public function getRoles(): array;
}

class Developer implements Employee
{
    protected $salary;
    protected $name;
    protected $roles;
 
    public function __construct(string $name, float $salary) {
        $this->name = $name;
        $this->salary = $salary;
    }

    public function getName(): string {
        return $this->name;
    }

    public function setSalary(float $salary) {
        $this->salary = $salary;
    }

    public function getSalary(): float {
        return $this->salary;
    }

    public function getRoles(): array {
        return $this->roles;
    }
}

class Designer implements Employee
{
    protected $salary;
    protected $name;
    protected $roles;

    public function __construct(string $name, float $salary)
    {
        $this->name = $name;
        $this->salary = $salary;
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function setSalary(float $salary)
    {
        $this->salary = $salary;
    }

    public function getSalary(): float
    {
        return $this->salary;
    }

    public function getRoles(): array
    {
        return $this->roles;
    }
}
                
```

Then we have an organization which consists of several different types
of employees

``` 
class Organization
{
    protected $employees;

    public function addEmployee(Employee $employee) {
        $this->employees[] = $employee;
    }

    public function getNetSalaries(): float {
        $netSalary = 0;

        foreach ($this->employees as $employee) {
            $netSalary += $employee->getSalary();
        }

        return $netSalary;
    }
}
                
```

Then we have an organization which consists of several different types
of employees

``` 
// Prepare the employees
$john = new Developer('John Doe', 12000);
$jane = new Designer('Jane Doe', 15000);

// Add them to organization
$organization = new Organization();
$organization->addEmployee($john);
$organization->addEmployee($jane);

echo "Net salaries: " . $organization->getNetSalaries(); // Net Salaries: 27000
                
```

</div>

##### Python

<div>

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?
The composite pattern describes a group of objects that is treated the
same way as a single instance of the same type of object. The intent of
a composite is to "compose" objects into tree structures to represent
part-whole hierarchies. Implementing the composite pattern lets clients
treat individual objects and compositions uniformly.

*What does this example do?
The example implements a graphic class，which can be either an ellipse
or a composition of several graphics. Every graphic can be printed.

*Where is the pattern used practically?
In graphics editors a shape can be basic or complex. An example of a
simple shape is a line, where a complex shape is a rectangle which is
made of four line objects. Since shapes have many operations in common
such as rendering the shape to screen, and since shapes follow a
part-whole hierarchy, composite pattern can be used to enable the
program to deal with all shapes uniformly.

*References:
https://en.wikipedia.org/wiki/Composite_pattern
https://infinitescript.com/2014/10/the-23-gang-of-three-design-patterns/

*TL;DR
Describes a group of objects that is treated as a single instance.
"""

class Graphic:
    def render(self):
        raise NotImplementedError("You should implement this.")

class CompositeGraphic(Graphic):
    def __init__(self):
        self.graphics = []

    def render(self):
        for graphic in self.graphics:
            graphic.render()

    def add(self, graphic):
        self.graphics.append(graphic)

    def remove(self, graphic):
        self.graphics.remove(graphic)


class Ellipse(Graphic):
    def __init__(self, name):
        self.name = name

    def render(self):
        print("Ellipse: {}".format(self.name))

if __name__ == '__main__':
    ellipse1 = Ellipse("1")
    ellipse2 = Ellipse("2")
    ellipse3 = Ellipse("3")
    ellipse4 = Ellipse("4")

    graphic1 = CompositeGraphic()
    graphic2 = CompositeGraphic()

    graphic1.add(ellipse1)
    graphic1.add(ellipse2)
    graphic1.add(ellipse3)
    graphic2.add(ellipse4)

    graphic = CompositeGraphic()

    graphic.add(graphic1)
    graphic.add(graphic2)

    graphic.render()

### OUTPUT ###
# Ellipse: 1
# Ellipse: 2
# Ellipse: 3
# Ellipse: 4    
                
```

</div>

### Decorator

![](https://www.oodesign.com/images/structural/decorator-pattern.png)

#### Intent

**Decorator** is a structural design pattern that lets you attach new
behaviors to objects by placing these objects inside special wrapper
objects that contain the behaviors.

![](attachments/463530016/463530229.png)

#### Problem

Imagine that you’re working on a notification library which lets other
programs notify their users about important events.

The initial version of the library was based on the `Notifier` class
that had only a few fields, a constructor and a single `send` method.
The method could accept a message argument from a client and send the
message to a list of emails that were passed to the notifier via its
constructor. A third-party app which acted as a client was supposed to
create and configure the notifier object once, and then use it each time
something important happened.

![](attachments/463530016/463530231.png)

At some point, you realize that users of the library expect more than
just email notifications. Many of them would like to receive an SMS
about critical issues. Others would like to be notified on Facebook and,
of course, the corporate users would love to get Slack notifications.

![](attachments/463530016/463530235.png)

How hard can that be? You extended the `Notifier` class and put the
additional notification methods into new subclasses. Now the client was
supposed to instantiate the desired notification class and use it for
all further notifications.

But then someone reasonably asked you, “Why can’t you use several
notification types at once? If your house is on fire, you’d probably
want to be informed through every channel.”

You tried to address that problem by creating special subclasses which
combined several notification methods within one class. However, it
quickly became apparent that this approach would bloat the code
immensely, not only the library code but the client code as well.

![](attachments/463530016/463530233.png)

You have to find some other way to structure notifications classes so
that their number won’t accidentally break some Guinness record.

#### Solution

Extending a class is the first thing that comes to mind when you need to
alter an object’s behavior. However, inheritance has several serious
caveats that you need to be aware of.

  - Inheritance is static. You can’t alter the behavior of an existing
    object at runtime. You can only replace the whole object with
    another one that’s created from a different subclass.
  - Subclasses can have just one parent class. In most languages,
    inheritance doesn’t let a class inherit behaviors of multiple
    classes at the same time.

One of the ways to overcome these caveats is by using *Aggregation* or
*Composition* instead of *Inheritance*. Both of the alternatives work
almost the same way: one object *has a* reference to another and
delegates it some work, whereas with inheritance, the object itself *is*
able to do that work, inheriting the behavior from its superclass.

With this new approach you can easily substitute the linked “helper”
object with another, changing the behavior of the container at runtime.
An object can use the behavior of various classes, having references to
multiple objects and delegating them all kinds of work.
Aggregation/composition is the key principle behind many design
patterns, including Decorator. On that note, let’s return to the pattern
discussion.

![](attachments/463530016/463530234.png)

*Wrapper* is the alternative nickname for the Decorator pattern that
clearly expresses the main idea of the pattern. A “wrapper” is an object
that can be linked with some “target” object. The wrapper contains the
same set of methods as the target and delegates to it all requests it
receives. However, the wrapper may alter the result by doing something
either before or after it passes the request to the target.

When does a simple wrapper become the real decorator? As I mentioned,
the wrapper implements the same interface as the wrapped object. That’s
why from the client’s perspective these objects are identical. Make the
wrapper’s reference field accept any object that follows that interface.
This will let you cover an object in multiple wrappers, adding the
combined behavior of all the wrappers to it.

In our notifications example, let’s leave the simple email notification
behavior inside the base `Notifier` class, but turn all other
notification methods into decorators.

![](attachments/463530016/463530232.png)

The client code would need to wrap a basic notifier object into a set of
decorators that match the client’s preferences. The resulting objects
will be structured as a stack.

![](attachments/463530016/463530236.png)

The last decorator in the stack would be the object that the client
actually works with. Since all decorators implement the same interface
as the base notifier, the rest of the client code won’t care whether it
works with the “pure” notifier object or the decorated one.

We could apply the same approach to other behaviors such as formatting
messages or composing the recipient list. The client can decorate the
object with any custom decorators, as long as they follow the same
interface as the others.

#### Structure

![](attachments/463530016/463530237.png)

#### Pseudocode

In this example, the **Decorator** pattern lets you compress and encrypt
sensitive data independently from the code that actually uses this data.

![](attachments/463530016/463530230.png)

The application wraps the data source object with a pair of decorators.
Both wrappers change the way the data is written to and read from the
disk:

  - Just before the data is **written to disk**, the decorators encrypt
    and compress it. The original class writes the encrypted and
    protected data to the file without knowing about the change.

  - Right after the data is **read from disk**, it goes through the same
    decorators, which decompress and decode it.

The decorators and the data source class implement the same interface,
which makes them all interchangeable in the client code.

#### Real world example

Imagine you run a car service shop offering multiple services. Now how
do you calculate the bill to be charged? You pick one service and
dynamically keep adding to it the prices for the provided services till
you get the final cost. Here each type of service is a decorator.

#### In plain words

Decorator pattern lets you dynamically change the behavior of an object
at run time by wrapping them in an object of a decorator class.

#### Wikipedia says

In object-oriented programming, the decorator pattern is a design
pattern that allows behavior to be added to an individual object, either
statically or dynamically, without affecting the behavior of other
objects from the same class. The decorator pattern is often useful for
adhering to the Single Responsibility Principle, as it allows
functionality to be divided between classes with unique areas of
concern.

#### Pros and Cons

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
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

Lets take coffee for example. First of all we have a simple coffee
implementing the coffee interface

##### C\#

<div>

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

We want to make the code extensible to allow options to modify it if
required. Lets make some add-ons (decorators)

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

</div>

##### Java

<div>

Let's take the troll example. First of all we have a simple troll
implementing the troll interface

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

Next we want to add club for the troll. We can do it dynamically by
using a decorator

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

</div>

##### JavaScript

<div>

Lets take coffee for example. First of all we have a simple coffee
implementing the coffee interface

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

We want to make the code extensible to allow options to modify it if
required. Lets make some add-ons (decorators)

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

</div>

##### PHP

<div>

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

We want to make the code extensible to allow options to modify it if
required. Lets make some add-ons (decorators)

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

</div>

##### Python

<div>

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?
The Decorator pattern is used to dynamically add a new feature to an
object without changing its implementation. It differs from
inheritance because the new feature is added only to that particular
object, not to the entire subclass.

*What does this example do?
This example shows a way to add formatting options (boldface and
italic) to a text by appending the corresponding tags (<b> and
<i>). Also, we can see that decorators can be applied one after the other,
since the original text is passed to the bold wrapper, which in turn
is passed to the italic wrapper.

*Where is the pattern used practically?
The Grok framework uses decorators to add functionalities to methods,
like permissions or subscription to an event:
http://grok.zope.org/doc/current/reference/decorators.html

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

</div>

### Factory Method

![](https://www.oodesign.com/images/creational/factory-method-pattern.gif)

#### Intent

**Factory Method** is a creational design pattern that provides an
interface for creating objects in a superclass, but allows subclasses to
alter the type of objects that will be created.

![](attachments/463530001/463530165.png)

#### Problem

Imagine that you’re creating a logistics management application. The
first version of your app can only handle transportation by trucks, so
the bulk of your code lives inside the `Truck` class.

After a while, your app becomes pretty popular. Each day you receive
dozens of requests from sea transportation companies to incorporate sea
logistics into the app.

![](attachments/463530001/463530167.png)

Great news, right? But how about the code? At present, most of your code
is coupled to the `Truck` class. Adding `Ships` into the app would
require making changes to the entire codebase. Moreover, if later you
decide to add another type of transportation to the app, you will
probably need to make all of these changes again.

As a result, you will end up with pretty nasty code, riddled with
conditionals that switch the app’s behavior depending on the class of
transportation objects.

#### Solution

The Factory Method pattern suggests that you replace direct object
construction calls (using the `new` operator) with calls to a special
*factory* method. Don’t worry: the objects are still created via the
`new` operator, but it’s being called from within the factory method.
Objects returned by a factory method are often referred to as
“products.”

![](attachments/463530001/463530168.png)

At first glance, this change may look pointless: we just moved the
constructor call from one part of the program to another. However,
consider this: now you can override the factory method in a subclass and
change the class of products being created by the method.

There’s a slight limitation though: subclasses may return different
types of products only if these products have a common base class or
interface. Also, the factory method in the base class should have its
return type declared as this interface.

![](attachments/463530001/463530169.png)

For example, both `Truck` and `Ship` classes should implement the
`Transport` interface, which declares a method called `deliver`. Each
class implements this method differently: trucks deliver cargo by land,
ships deliver cargo by sea. The factory method in the `RoadLogistics`
class returns truck objects, whereas the factory method in the
`SeaLogistics` class returns ships.

![](attachments/463530001/463530170.png)

The code that uses the factory method (often called the *client* code)
doesn’t see a difference between the actual products returned by various
subclasses. The client treats all the products as abstract `Transport`.
The client knows that all transport objects are supposed to have the
`deliver` method, but exactly how it works isn’t important to the
client.

#### Structure

![](attachments/463530001/463530171.png)

#### Pseudocode

This example illustrates how the **Factory Method** can be used for
creating cross-platform UI elements without coupling the client code to
concrete UI classes.

![](attachments/463530001/463530166.png)

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

#### Real world example

Consider the case of a hiring manager. It is impossible for one person
to interview for each of the positions. Based on the job opening, she
has to decide and delegate the interview steps to different people.

#### In plain words

It provides a way to delegate the instantiation logic to child classes.

#### Wikipedia says

In class-based programming, the factory method pattern is a creational
pattern that uses factory methods to deal with the problem of creating
objects without having to specify the exact class of the object that
will be created. This is done by creating objects by calling a factory
method—either specified in an interface and implemented by child
classes, or implemented in a base class and optionally overridden by
derived classes—rather than by calling a constructor.

#### Programmatic Example

Taking our hiring manager example above. First of all we have an
interviewer interface and some implementations for it

##### C\#

<div>

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
>     public void TakeInterview() {
>         var interviewer = this.MakeInterviewer();
>         interviewer.AskQuestions();
>     }
> }
>                     
> ```

Now any child can extend it and provide the required interviewer

> 
> 
> ``` 
> class DevelopmentManager : HiringManager
> {
>     protected override IInterviewer MakeInterviewer() {
>         return new Developer();
>     }
> }
> 
> class MarketingManager : HiringManager
> {
>     protected override IInterviewer MakeInterviewer() {
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
> ```

</div>

##### Java

<div>

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

</div>

##### PHP

<div>

``` 
interface Interviewer {
    public function askQuestions();
}

class Developer implements Interviewer {
    public function askQuestions() {
        echo 'Asking about design patterns!';
    }
}

class CommunityExecutive implements Interviewer {
    public function askQuestions() {
        echo 'Asking about community building';
    }
}
                
```

Now let us create our `HiringManager`

``` 
abstract class HiringManager {
    // Factory method
    abstract protected function makeInterviewer(): Interviewer;

    public function takeInterview() {
        $interviewer = $this->makeInterviewer();
        $interviewer->askQuestions();
    }
}
                
```

Now any child can extend it and provide the required interviewer

``` 
class DevelopmentManager extends HiringManager {
    protected function makeInterviewer(): Interviewer {
        return new Developer();
    }
}

class MarketingManager extends HiringManager {
    protected function makeInterviewer(): Interviewer {
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

</div>

##### Python

<div>

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

</div>

#### When to use?

Useful when there is some generic processing in a class but the required
sub-class is dynamically decided at runtime. Or putting it in other
words, when the client doesn't know what exact sub-class it might need.

</div>

### Flyweight

![](https://www.oodesign.com/images/structural/flyweight-pattern.png)

#### Intent

**Flyweight** is a structural design pattern that lets you fit more
objects into the available amount of RAM by sharing common parts of
state between multiple objects instead of keeping all of the data in
each object.

![](attachments/463530018/463530215.png)

#### Problem

To have some fun after long working hours, you decided to create a
simple video game: players would be moving around a map and shooting
each other. You chose to implement a realistic particle system and make
it a distinctive feature of the game. Vast quantities of bullets,
missiles, and shrapnel from explosions should fly all over the map and
deliver a thrilling experience to the player.

Upon its completion, you pushed the last commit, built the game and sent
it to your friend for a test drive. Although the game was running
flawlessly on your machine, your friend wasn’t able to play for long. On
his computer, the game kept crashing after a few minutes of gameplay.
After spending several hours digging through debug logs, you discovered
that the game crashed because of an insufficient amount of RAM. It
turned out that your friend’s rig was much less powerful than your own
computer, and that’s why the problem emerged so quickly on his machine.

The actual problem was related to your particle system. Each particle,
such as a bullet, a missile or a piece of shrapnel was represented by a
separate object containing plenty of data. At some point, when the
carnage on a player’s screen reached its climax, newly created particles
no longer fit into the remaining RAM, so the program crashed.

![](attachments/463530018/463530217.png)

#### Solution

On closer inspection of the `Particle` class, you may notice that the
color and sprite fields consume a lot more memory than other fields.
What’s worse is that these two fields store almost identical data across
all particles. For example, all bullets have the same color and sprite.

![](attachments/463530018/463530218.png)

Other parts of a particle’s state, such as coordinates, movement vector
and speed, are unique to each particle. After all, the values of these
fields change over time. This data represents the always changing
context in which the particle exists, while the color and sprite remain
constant for each particle.

This constant data of an object is usually called the *intrinsic state*.
It lives within the object; other objects can only read it, not change
it. The rest of the object’s state, often altered “from the outside” by
other objects, is called the *extrinsic state*.

The Flyweight pattern suggests that you stop storing the extrinsic state
inside the object. Instead, you should pass this state to specific
methods which rely on it. Only the intrinsic state stays within the
object, letting you reuse it in different contexts. As a result, you’d
need fewer of these objects since they only differ in the intrinsic
state, which has much fewer variations than the extrinsic.

![](attachments/463530018/463530220.png)

Let’s return to our game. Assuming that we had extracted the extrinsic
state from our particle class, only three different objects would
suffice to represent all particles in the game: a bullet, a missile, and
a piece of shrapnel. As you’ve probably guessed by now, an object that
only stores the intrinsic state is called a flyweight.

#### Extrinsic state storage

Where does the extrinsic state move to? Some class should still store
it, right? In most cases, it gets moved to the container object, which
aggregates objects before we apply the pattern.

In our case, that’s the main `Game` object that stores all particles in
the `particles` field. To move the extrinsic state into this class, you
need to create several array fields for storing coordinates, vectors,
and speed of each individual particle. But that’s not all. You need
another array for storing references to a specific flyweight that
represents a particle. These arrays must be in sync so that you can
access all data of a particle using the same index.

![](attachments/463530018/463530219.png)

A more elegant solution is to create a separate context class that would
store the extrinsic state along with reference to the flyweight object.
This approach would require having just a single array in the container
class.

Wait a second\! Won’t we need to have as many of these contextual
objects as we had at the very beginning? Technically, yes. But the thing
is, these objects are much smaller than before. The most
memory-consuming fields have been moved to just a few flyweight objects.
Now, a thousand small contextual objects can reuse a single heavy
flyweight object instead of storing a thousand copies of its data.

#### Flyweight and immutability

Since the same flyweight object can be used in different contexts, you
have to make sure that its state can’t be modified. A flyweight should
initialize its state just once, via constructor parameters. It shouldn’t
expose any setters or public fields to other objects.

#### Flyweight factory

For more convenient access to various flyweights, you can create a
factory method that manages a pool of existing flyweight objects. The
method accepts the intrinsic state of the desired flyweight from a
client, looks for an existing flyweight object matching this state, and
returns it if it was found. If not, it creates a new flyweight and adds
it to the pool.

There are several options where this method could be placed. The most
obvious place is a flyweight container. Alternatively, you could create
a new factory class. Or you could make the factory method static and put
it inside an actual flyweight class.

#### Structure

![](attachments/463530018/463530221.png)

#### Pseudocode

In this example, the **Flyweight** pattern helps to reduce memory usage
when rendering millions of tree objects on a canvas.

![](attachments/463530018/463530216.png)

The pattern extracts the repeating intrinsic state from a main `Tree`
class and moves it into the flyweight class `TreeType`.

Now instead of storing the same data in multiple objects, it’s kept in
just a few flyweight objects and linked to appropriate `Tree` objects
which act as contexts. The client code creates new tree objects using
the flyweight factory, which encapsulates the complexity of searching
for the right object and reusing it if needed.

#### Real world example

Did you ever have fresh tea from some stall? They often make more than
one cup that you demanded and save the rest for any other customer so to
save the resources e.g. gas etc. Flyweight pattern is all about that
i.e. sharing.

#### In plain words

It is used to minimize memory usage or computational expenses by sharing
as much as possible with similar objects.

#### Wikipedia says

In computer programming, flyweight is a software design pattern. A
flyweight is an object that minimizes memory use by sharing as much data
as possible with other similar objects; it is a way to use objects in
large numbers when a simple repeated representation would use an
unacceptable amount of memory.

#### Pros and Cons

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
<td>You can save lots of RAM, assuming your program has tons of similar objects.</td>
<td>You might be trading RAM over CPU cycles when some of the context data needs to be recalculated each time somebody calls a flyweight method.</td>
</tr>
<tr class="even">
<td><br />
</td>
<td>The code becomes much more complicated. New team members will always be wondering why the state of an entity was separated in such a way.</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic example

Translating our tea example from above. First of all we have tea types
and tea maker

##### C\#

<div>

> // Anything that will be cached is flyweight.
> 
> ``` 
> // Anything that will be cached is flyweight.
> // Types of tea here will be flyweights.
> class KarakTea
> {
> }
> 
> // Acts as a factory and saves the tea
> class TeaMaker
> {
>     private Dictionary<string, KarakTea> mAvailableTea = new Dictionary<string, KarakTea>();
> 
>     public KarakTea Make(string preference)
>     {
>         if (!mAvailableTea.ContainsKey(preference)) {
>             mAvailableTea[preference] = new KarakTea();
>         }
> 
>         return mAvailableTea[preference];
>     }
> }
>                     
> ```

Then we have the `TeaShop` which takes orders and serves them

> 
> 
> ``` 
> class TeaShop
> {
>     private Dictionary<int,KarakTea> mOrders = new Dictionary<int,KarakTea>();
>     private readonly TeaMaker mTeaMaker;
> 
>     public TeaShop(TeaMaker teaMaker) {
>         mTeaMaker = teaMaker ?? throw new ArgumentNullException("teaMaker", "teaMaker cannot be null");
>     }
> 
>     public void TakeOrder(string teaType, int table) {
>         mOrders[table] = mTeaMaker.Make(teaType);
>     }
> 
>     public void Serve() {
>             foreach(var table  in mOrders.Keys ){
>             Console.WriteLine($"Serving Tea to table # {table}");
>         }
>     }
> }
>                     
> ```

And it can be used as below

> 
> 
> ``` 
> var teaMaker = new TeaMaker();
> var teaShop = new TeaShop(teaMaker);
> 
> teaShop.TakeOrder("less sugar", 1);
> teaShop.TakeOrder("more milk", 2);
> teaShop.TakeOrder("without sugar", 5);
> 
> teaShop.Serve();
> // Serving tea to table# 1
> // Serving tea to table# 2
> // Serving tea to table# 5
> 
>                     
> ```

</div>

##### Java

<div>

Translating our alchemist shop example from above. First of all we have
different potion types

``` 
public interface Potion {
    void drink();
}

public class HealingPotion implements Potion {
    private static final Logger LOGGER = LoggerFactory.getLogger(HealingPotion.class);
    
    @Override
    public void drink() {
        LOGGER.info("You feel healed. (Potion={})", System.identityHashCode(this));
    }
}

public class HolyWaterPotion implements Potion {
    private static final Logger LOGGER = LoggerFactory.getLogger(HolyWaterPotion.class);
  
    @Override
    public void drink() {
        LOGGER.info("You feel blessed. (Potion={})", System.identityHashCode(this));
    }
}

public class InvisibilityPotion implements Potion {
    private static final Logger LOGGER = LoggerFactory.getLogger(InvisibilityPotion.class);

    @Override
    public void drink() {
        LOGGER.info("You become invisible. (Potion={})", System.identityHashCode(this));
    }
}
                
```

Then the actual Flyweight object which is the factory for creating
potions

``` 
public class PotionFactory {
private final Map <PotionType, Potion> potions;

public PotionFactory() {
    potions = new EnumMap<>(PotionType.class);
}

Potion createPotion(PotionType type) {
    Potion potion = potions.get(type);
    if (potion == null) {
        switch (type) {
            case HEALING:
                potion = new HealingPotion();
                potions.put(type, potion);
                break;
            case HOLY_WATER:
                potion = new HolyWaterPotion();
                potions.put(type, potion);
                break;
            case INVISIBILITY:
                potion = new InvisibilityPotion();
                potions.put(type, potion);
                break;
            default:
                break;
        }
    }
    return potion;
    }
}
                
```

And it can be used as below

``` 
PotionFactory factory = new PotionFactory();
factory.createPotion(PotionType.INVISIBILITY).drink(); // You become invisible. (Potion=6566818)
factory.createPotion(PotionType.HEALING).drink(); // You feel healed. (Potion=648129364)
factory.createPotion(PotionType.INVISIBILITY).drink(); // You become invisible. (Potion=6566818)
factory.createPotion(PotionType.HOLY_WATER).drink(); // You feel blessed. (Potion=1104106489)
factory.createPotion(PotionType.HOLY_WATER).drink(); // You feel blessed. (Potion=1104106489)
factory.createPotion(PotionType.HEALING).drink(); // You feel healed. (Potion=648129364)
                
```

</div>

##### JavaScript

<div>

Translating our tea example from above. First of all we have tea types
and tea maker

``` 
// Anything that will be cached is flyweight. 
// Types of tea here will be flyweights.
class KarakTea {
}

// Acts as a factory and saves the tea
class TeaMaker {
    constructor(){
        this.availableTea = {}
    }

    make(preference) {
        this.availableTea[preference] = this.availableTea[preference] || (new KarakTea())
        return this.availableTea[preference]
    }
}
                
```

Then we have the `TeaShop` which takes orders and serves them

``` 
class TeaShop {
    constructor(teaMaker) {
        this.teaMaker = teaMaker
        this.orders = []
    }

    takeOrder(teaType, table) {
        this.orders[table] = this.teaMaker.make(teaType)
    }

    serve() {
        this.orders.forEach((order, index) => {
            console.log('Serving tea to table#' + index)
        })
    }
}
                
```

And it can be used as below

``` 
const teaMaker = new TeaMaker()
const shop = new TeaShop(teaMaker)

shop.takeOrder('less sugar', 1)
shop.takeOrder('more milk', 2)
shop.takeOrder('without sugar', 5)

shop.serve()
// Serving tea to table# 1
// Serving tea to table# 2
// Serving tea to table# 5
                
```

</div>

##### PHP

<div>

``` 
// Anything that will be cached is flyweight.
// Types of tea here will be flyweights.
class KarakTea
{
}

// Acts as a factory and saves the tea
class TeaMaker
{
    protected $availableTea = [];

    public function make($preference)
    {
        if (empty($this->availableTea[$preference])) {
            $this->availableTea[$preference] = new KarakTea();
        }

        return $this->availableTea[$preference];
    }
}
                
```

Then we have the `TeaShop` which takes orders and serves them

``` 
class TeaShop
{
    protected $orders;
    protected $teaMaker;

    public function __construct(TeaMaker $teaMaker)
    {
        $this->teaMaker = $teaMaker;
    }

    public function takeOrder(string $teaType, int $table)
    {
        $this->orders[$table] = $this->teaMaker->make($teaType);
    }

    public function serve()
    {
        foreach ($this->orders as $table => $tea) {
            echo "Serving tea to table# " . $table;
        }
    }
}
                
```

And it can be used as below

``` 
 $teaMaker = new TeaMaker();
$shop = new TeaShop($teaMaker);

$shop->takeOrder('less sugar', 1);
$shop->takeOrder('more milk', 2);
$shop->takeOrder('without sugar', 5);

$shop->serve();
// Serving tea to table# 1
// Serving tea to table# 2
// Serving tea to table# 5
                
```

</div>

##### Python

<div>

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*What is this pattern about?
This pattern aims to minimise the number of objects that are needed by
a program at run-time. A Flyweight is an object shared by multiple
contexts, and is indistinguishable from an object that is not shared.

The state of a Flyweight should not be affected by it's context, this
is known as its intrinsic state. The decoupling of the objects state
from the object's context, allows the Flyweight to be shared.

*What does this example do?
The example below sets-up an 'object pool' which stores initialised
objects. When a 'Card' is created it first checks to see if it already
exists instead of creating a new one. This aims to reduce the number of
objects initialised by the program.

*References:
http://codesnipers.com/?q=python-flyweights
https://python-patterns.guide/gang-of-four/flyweight/

*Examples in Python ecosystem:
https://docs.python.org/3/library/sys.html#sys.intern

*TL;DR
Minimizes memory usage by sharing data with other similar objects.
"""

import weakref

class Card(object):
    """The Flyweight"""

    # Could be a simple dict.
    # With WeakValueDictionary garbage collection can reclaim the object
    # when there are no other references to it.
    _pool = weakref.WeakValueDictionary()

    def __new__(cls, value, suit):
        # If the object exists in the pool - just return it
        obj = cls._pool.get(value + suit)
        # otherwise - create new one (and add it to the pool)
        if obj is None:
            obj = object.__new__(Card)
            cls._pool[value + suit] = obj
            # This row does the part we usually see in `__init__`
            obj.value, obj.suit = value, suit
        return obj

    # If you uncomment `__init__` and comment-out `__new__` -
    #   Card becomes normal (non-flyweight).
    # def __init__(self, value, suit):
    #     self.value, self.suit = value, suit

    def __repr__(self):
        return "<Card: %s%s>" % (self.value, self.suit)

def main():
    """
    >>> c1 = Card('9', 'h')
    >>> c2 = Card('9', 'h')
    >>> c1, c2
    (<Card: 9h>, <Card: 9h>)
    >>> c1 == c2
    True
    >>> c1 is c2
    True

    >>> c1.new_attr = 'temp'
    >>> c3 = Card('9', 'h')
    >>> hasattr(c3, 'new_attr')
    True

    >>> Card._pool.clear()
    >>> c4 = Card('9', 'h')
    >>> hasattr(c4, 'new_attr')
    False
    """

if __name__ == "__main__":
    import doctest
    doctest.testmod()
                
```

</div>

### Proxy

![](https://www.oodesign.com/images/structural/proxy-pattern.png)

#### Intent

**Proxy** is a structural design pattern that lets you provide a
substitute or placeholder for another object. A proxy controls access to
the original object, allowing you to perform something either before or
after the request gets through to the original object.

![](attachments/463530019/463530208.png)

#### Problem

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

#### Solution

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

#### Structure

![](attachments/463530019/463530212.png)

#### Pseudocode

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

#### Real world example

Have you ever used an access card to go through a door? There are
multiple options to open that door i.e. it can be opened either using
access card or by pressing a button that bypasses the security. The
door's main functionality is to open but there is a proxy added on top
of it to add some functionality. Let me better explain it using the code
example below.

#### In plain words

Using the proxy pattern, a class represents the functionality of another
class.

#### Wikipedia says

A proxy, in its most general form, is a class functioning as an
interface to something else. A proxy is a wrapper or agent object that
is being called by the client to access the real serving object behind
the scenes. Use of the proxy can simply be forwarding to the real
object, or can provide additional logic. In the proxy extra
functionality can be provided, for example caching when operations on
the real object are resource intensive, or checking preconditions before
operations on the real object are invoked.

#### Pros and Cons

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

</div>

#### Programmatic Example

Taking our security door example from above. Firstly we have the door
interface and an implementation of door

##### C\#

<div>

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

</div>

##### Java

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

</div>

##### JavaScript

<div>

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

</div>

##### PHP

<div>

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

</div>

Yet another example would be some sort of data-mapper implementation.
For example, I recently made an ODM (Object Data Mapper) for MongoDB
using this pattern where I wrote a proxy around mongo classes while
utilizing the magic method `  __call()  `. All the method calls were
proxied to the original mongo class and result retrieved was returned as
it is but in case of  `find` or `findOne` data was mapped to the
required class objects and the object was returned instead of `Cursor`.

##### Python

<div>

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

</div>

## Behavioral Design Pattern

### Chain of Responsibility

#### Intent

**Chain of Responsibility** is a behavioral design pattern that lets you
pass requests along a chain of handlers. Upon receiving a request, each
handler decides either to process the request or to pass it to the next
handler in the chain.

![](attachments/463529897/463529890.png)

#### Problem

Imagine that you’re working on an online ordering system. You want to
restrict access to the system so only authenticated users can create
orders. Also, users who have administrative permissions must have full
access to all orders.

After a bit of planning, you realized that these checks must be
performed sequentially. The application can attempt to authenticate a
user to the system whenever it receives a request that contains the
user’s credentials. However, if those credentials aren’t correct and
authentication fails, there’s no reason to proceed with any other
checks.

![](attachments/463529897/463529891.png)

During the next few months, you implemented several more of those
sequential checks.

  - One of your colleagues suggested that it’s unsafe to pass raw data
    straight to the ordering system. So you added an extra validation
    step to sanitize the data in a request.

  - Later, somebody noticed that the system is vulnerable to brute force
    password cracking. To negate this, you promptly added a check that
    filters repeated failed requests coming from the same IP address.

  - Someone else suggested that you could speed up the system by
    returning cached results on repeated requests containing the same
    data. Hence, you added another check which lets the request pass
    through to the system only if there’s no suitable cached response.

![](attachments/463529897/463529892.png)

#### Solution

Like many other behavioral design patterns, the **Chain of
Responsibility** relies on transforming particular behaviors into
stand-alone objects called *handlers*. In our case, each check should be
extracted to its own class with a single method that performs the check.
The request, along with its data, is passed to this method as an
argument.

The pattern suggests that you link these handlers into a chain. Each
linked handler has a field for storing a reference to the next handler
in the chain. In addition to processing a request, handlers pass the
request further along the chain. The request travels along the chain
until all handlers have had a chance to process it.

Here’s the best part: a handler can decide not to pass the request
further down the chain and effectively stop any further processing.

In our example with ordering systems, a handler performs the processing
and then decides whether to pass the request further down the chain.
Assuming the request contains the right data, all the handlers can
execute their primary behavior, whether it’s authentication checks or
caching.

![](attachments/463529897/463529893.png)

However, there’s a slightly different approach (and it’s a bit more
canonical) in which, upon receiving a request, a handler decides whether
it can process it. If it can, it doesn’t pass the request any further.
So it’s either only one handler that processes the request or none at
all. This approach is very common when dealing with events in stacks of
elements within a graphical user interface.

For instance, when a user clicks a button, the event propagates through
the chain of GUI elements that starts with the button, goes along its
containers (like forms or panels), and ends up with the main application
window. The event is processed by the first element in the chain that’s
capable of handling it. This example is also noteworthy because it shows
that a chain can always be extracted from an object tree.

![](attachments/463529897/463529894.png)

#### Structure

![](attachments/463529897/463529895.png)

#### Pseudocode

![](attachments/463529897/463529896.png)

#### Real world example

For example, you have three payment methods (A, B and C) setup in your
account; each having a different amount in it. A has 100 USD, B has 300
USD and C having 1000 USD and the preference for payments is chosen
as A then B then C. You try to purchase something that is worth 210
USD. Using Chain of Responsibility, first of all account A will be
checked if it can make the purchase, if yes purchase will be made and
the chain will be broken. If not, request will move forward to
account B checking for amount if yes chain will be broken otherwise
the request will keep forwarding till it finds the suitable handler.
Here A, B and C are links of the chain and the whole phenomenon is Chain
of Responsibility.

#### In plain words

It helps building a chain of objects. Request enters from one end and
keeps going from object to object till it finds the suitable handler.

#### Wikipedia says

In object-oriented design, the chain-of-responsibility pattern is a
design pattern consisting of a source of command objects and a series of
processing objects. Each processing object contains logic that defines
the types of command objects that it can handle; the rest are passed to
the next processing object in the chain.

#### Pros and Cons

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
<td>You can control the order of request handling.</td>
<td>Some requests may end up unhandled.</td>
</tr>
<tr class="even">
<td><em>Single Responsibility Principle</em>. You can decouple classes that invoke operations from classes that perform operations.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td><em>Open/Closed Principle</em>. You can introduce new handlers into the app without breaking the existing client code.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

##### C\#

<div>

Translating our account example above. First of all we have a base
account having the logic for chaining the accounts together and some
accounts

> 
> 
> ``` 
> abstract class Account
> {
>     private Account mSuccessor;
>     protected decimal mBalance;
> 
>     public void SetNext(Account account)
>     {
>         mSuccessor = account;
>     }
> 
>     public void Pay(decimal amountTopay)
>     {
>         if (CanPay(amountTopay))
>         {
>             Console.WriteLine($"Paid {amountTopay:c} using {this.GetType().Name}.");
>         }
>             else if (this.mSuccessor != null)
>         {
>             Console.WriteLine($"Cannot pay using {this.GetType().Name}. Proceeding..");
>             mSuccessor.Pay(amountTopay);
>         }
>         else
>         {
>             throw new Exception("None of the accounts have enough balance");
>         }
>     }
>     private bool CanPay(decimal amount)
>     {
>         return mBalance >= amount;
>     }
> }
> 
> class Bank : Account
> {
>     public Bank(decimal balance)
>     {
>         this.mBalance = balance;
>     }
> }
> 
> class Paypal : Account
> {
>     public Paypal(decimal balance)
>     {
>         this.mBalance = balance;
>     }
> }
> 
> class Bitcoin : Account
> {
>     public Bitcoin(decimal balance)
>     {
>         this.mBalance = balance;
>     }
> }
>                 
> ```

Now let's prepare the chain using the links defined above (i.e. Bank,
Paypal, Bitcoin)

> 
> 
> ``` 
> // Let's prepare a chain like below
> // $bank->$paypal->$bitcoin
> //
> // First priority bank
> // If bank can't pay then paypal
> // If paypal can't pay then bit coin
> var bank = new Bank(100);          // Bank with balance 100
> var paypal = new Paypal(200);      // Paypal with balance 200
> var bitcoin = new Bitcoin(300);    // Bitcoin with balance 300
> 
> bank.SetNext(paypal);
> paypal.SetNext(bitcoin);
> 
> // Let's try to pay using the first priority i.e. bank
> bank.Pay(259);
> // Output will be
> // ==============
> // Cannot pay using bank. Proceeding ..
> // Cannot pay using paypal. Proceeding ..:
> // Paid 259 using Bitcoin!
>                 
> ```

##### JavaScript

Translating our account example above. First of all we have a base
account having the logic for chaining the accounts together and some
accounts

> 
> 
> ``` 
> class Account {
> 
>     setNext(account) {
>         this.successor = account
>     }
>     
>     pay(amountToPay) {
>         if (this.canPay(amountToPay)) {
>             console.log(`Paid ${amountToPay} using ${this.name}`)
>         } else if (this.successor) {
>             console.log(`Cannot pay using ${this.name}. Proceeding...`)
>             this.successor.pay(amountToPay)
>         } else {
>             console.log('None of the accounts have enough balance')
>         }
>     }
>     
>     canPay(amount) {
>         return this.balance >= amount
>     }
> }
> 
> class Bank extends Account {
>     constructor(balance) {
>         super()
>         this.name = 'bank'
>         this.balance = balance
>     }
> }
> 
> class Paypal extends Account {
>     constructor(balance) {
>         super()        
>         this.name = 'Paypal'
>         this.balance = balance
>     }
> }
> 
> class Bitcoin extends Account {
>     constructor(balance) {
>         super()        
>         this.name = 'bitcoin'
>         this.balance = balance
>     }
> }
>                     
> ```

Now let's prepare the chain using the links defined above (i.e. Bank,
Paypal, Bitcoin)

> 
> 
> ``` 
> // Let's prepare a chain like below
> // bank.paypal.bitcoin
> //
> // First priority bank
> // If bank can't pay then paypal
> // If paypal can't pay then bit coin
> 
> const bank = new Bank(100)          // Bank with balance 100
> const paypal = new Paypal(200)      // Paypal with balance 200
> const bitcoin = new Bitcoin(300)    // Bitcoin with balance 300
> 
> bank.setNext(paypal)
> paypal.setNext(bitcoin)
> 
> // Let's try to pay using the first priority i.e. bank
> bank.pay(259)
> 
> // Output will be
> // ==============
> // Cannot pay using bank. Proceeding ..
> // Cannot pay using paypal. Proceeding ..: 
> // Paid 259 using Bitcoin!
> 
>                     
> ```

</div>

##### PHP

Translating our account example above. First of all we have a base
account having the logic for chaining the accounts together and some
accounts

> 
> 
> ``` 
> abstract class Account
> {
>     protected $successor;
>     protected $balance;
> 
>     public function setNext(Account $account)
>     {
>         $this->successor = $account;
>     }
> 
>     public function pay(float $amountToPay)
>     {
>         if ($this->canPay($amountToPay)) {
>             echo sprintf('Paid %s using %s' . PHP_EOL, $amountToPay, get_called_class());
>         } elseif ($this->successor) {
>             echo sprintf('Cannot pay using %s. Proceeding ..' . PHP_EOL, get_called_class());
>             $this->successor->pay($amountToPay);
>         } else {
>             throw new Exception('None of the accounts have enough balance');
>         }
>     }
> 
>     public function canPay($amount): bool
>     {
>         return $this->balance >= $amount;
>         }
> }
> 
> class Bank extends Account
> {
>     protected $balance;
> 
>     public function __construct(float $balance)
>     {
>         $this->balance = $balance;
>     }
> }
> 
> class Paypal extends Account
> {
>     protected $balance;
> 
>     public function __construct(float $balance)
>     {
>         $this->balance = $balance;
>     }
> }
> 
>     class Bitcoin extends Account
>     {
>     protected $balance;
> 
>     public function __construct(float $balance)
>     {
>         $this->balance = $balance;
>     }
> }
> 
>                 
> ```

Now let's prepare the chain using the links defined above (i.e. Bank,
Paypal, Bitcoin)

> 
> 
> ``` 
> // Let's prepare a chain like below
> // $bank->$paypal->$bitcoin
> //
> // First priority bank
> // If bank can't pay then paypal
> // If paypal can't pay then bit coin
> 
> $bank = new Bank(100); // Bank with balance 100
> $paypal = new Paypal(200); // Paypal with balance 200
> $bitcoin = new Bitcoin(300); // Bitcoin with balance 300
> 
> $bank->setNext($paypal);
> $paypal->setNext($bitcoin);
> 
> // Let's try to pay using the first priority i.e. bank
> $bank->pay(259);
> 
> // Output will be
> // ==============
> // Cannot pay using bank. Proceeding ..
> // Cannot pay using paypal. Proceeding ..:
> // Paid 259 using Bitcoin!
> 
>                 
> ```

##### Python

    #!/usr/bin/env python
    # -*- coding: utf-8 -*-
    
    """
    *What is this pattern about?
    
    The Chain of responsibility is an object oriented version of the
    `if ... elif ... elif ... else ...` idiom, with the
    benefit that the condition–action blocks can be dynamically rearranged
    and reconfigured at runtime.
    
    This pattern aims to decouple the senders of a request from its
    receivers by allowing request to move through chained
    receivers until it is handled.
    
    Request receiver in simple form keeps a reference to a single successor.
    As a variation some receivers may be capable of sending requests out
    in several directions, forming a `tree of responsibility`.
    
    *TL;DR
    Allow a request to pass down a chain of receivers until it is handled.
    """
    
    import abc
    
    class Handler(metaclass=abc.ABCMeta):
    
        def __init__(self, successor=None):
            self.successor = successor
    
        def handle(self, request):
            """
            Handle request and stop.
            If can't - call next handler in chain.
    
            As an alternative you might even in case of success
            call the next handler.
            """
            res = self.check_range(request)
            if not res and self.successor:
                self.successor.handle(request)
    
        @abc.abstractmethod
        def check_range(self, request):
            """Compare passed value to predefined interval"""
    
    class ConcreteHandler0(Handler):
        """Each handler can be different.
        Be simple and static...
        """
    
        @staticmethod
        def check_range(request):
            if 0 <= request < 10:
                print("request {} handled in handler 0".format(request))
                return True
    
    class ConcreteHandler1(Handler):
        """... With it's own internal state"""
    
        start, end = 10, 20
    
        def check_range(self, request):
            if self.start <= request < self.end:
                print("request {} handled in handler 1".format(request))
                return True
    
    class ConcreteHandler2(Handler):
        """... With helper methods."""
    
        def check_range(self, request):
            start, end = self.get_interval_from_db()
            if start <= request < end:
                print("request {} handled in handler 2".format(request))
                return True
    
        @staticmethod
        def get_interval_from_db():
            return (20, 30)
    
    
    class FallbackHandler(Handler):
        @staticmethod
        def check_range(request):
            print("end of chain, no handler for {}".format(request))
            return False
    
    def main():
        """
        >>> h0 = ConcreteHandler0()
        >>> h1 = ConcreteHandler1()
        >>> h2 = ConcreteHandler2(FallbackHandler())
        >>> h0.successor = h1
        >>> h1.successor = h2
    
        >>> requests = [2, 5, 14, 22, 18, 3, 35, 27, 20]
        >>> for request in requests:
        ...     h0.handle(request)
        request 2 handled in handler 0
        request 5 handled in handler 0
        request 14 handled in handler 1
        request 22 handled in handler 2
        request 18 handled in handler 1
        request 3 handled in handler 0
        end of chain, no handler for 35
        request 27 handled in handler 2
        request 20 handled in handler 2
        """
    
    
    if __name__ == "__main__":
        import doctest
        doctest.testmod(optionflags=doctest.ELLIPSIS)

### Command

#### Intent

**Command** is a behavioral design pattern that turns a request into a
stand-alone object that contains all information about the request. This
transformation lets you parameterize methods with different requests,
delay or queue a request’s execution, and support undoable operations.

![](attachments/463529910/463529901.png)

#### Problem

Imagine that you’re working on a new text-editor app. Your current task
is to create a toolbar with a bunch of buttons for various operations of
the editor. You created a very neat `Button` class that can be used for
buttons on the toolbar, as well as for generic buttons in various
dialogs.

![](attachments/463529910/463529902.png)

While all of these buttons look similar, they’re all supposed to do
different things. Where would you put the code for the various click
handlers of these buttons? The simplest solution is to create tons of
subclasses for each place where the button is used. These subclasses
would contain the code that would have to be executed on a button click.

![](attachments/463529910/463529903.png)

Before long, you realize that this approach is deeply flawed. First, you
have an enormous number of subclasses, and that would be okay if you
weren’t risking breaking the code in these subclasses each time you
modify the base `Button` class. Put simply, your GUI code has become
awkwardly dependent on the volatile code of the business logic.

![](attachments/463529910/463529904.png)

And here’s the ugliest part. Some operations, such as copying/pasting
text, would need to be invoked from multiple places. For example, a user
could click a small “Copy” button on the toolbar, or copy something via
the context menu, or just hit `Ctrl+C` on the keyboard.

Initially, when our app only had the toolbar, it was okay to place the
implementation of various operations into the button subclasses. In
other words, having the code for copying text inside the `CopyButton`
subclass was fine. But then, when you implement context menus,
shortcuts, and other stuff, you have to either duplicate the operation’s
code in many classes or make menus dependent on buttons, which is an
even worse option.

#### Solution

Good software design is often based on the principle of separation of
concerns, which usually results in breaking an app into layers. The most
common example: a layer for the graphical user interface and another
layer for the business logic. The GUI layer is responsible for rendering
a beautiful picture on the screen, capturing any input and showing
results of what the user and the app are doing. However, when it comes
to doing something important, like calculating the trajectory of the
moon or composing an annual report, the GUI layer delegates the work to
the underlying layer of business logic.

In the code it might look like this: a GUI object calls a method of a
business logic object, passing it some arguments. This process is
usually described as one object sending another a *request*.

![](attachments/463529910/463529905.png)

The Command pattern suggests that GUI objects shouldn’t send these
requests directly. Instead, you should extract all of the request
details, such as the object being called, the name of the method and the
list of arguments into a separate *command* class with a single method
that triggers this request.

Command objects serve as links between various GUI and business logic
objects. From now on, the GUI object doesn’t need to know what business
logic object will receive the request and how it’ll be processed. The
GUI object just triggers the command, which handles all the details.

![](attachments/463529910/463529906.png)

The next step is to make your commands implement the same interface.
Usually it has just a single execution method that takes no parameters.
This interface lets you use various commands with the same request
sender, without coupling it to concrete classes of commands. As a bonus,
now you can switch command objects linked to the sender, effectively
changing the sender’s behavior at runtime.

You might have noticed one missing piece of the puzzle, which is the
request parameters. A GUI object might have supplied the business-layer
object with some parameters. Since the command execution method doesn’t
have any parameters, how would we pass the request details to the
receiver? It turns out the command should be either pre-configured with
this data, or capable of getting it on its own.

![](attachments/463529910/463529907.png)

Let’s get back to our text editor. After we apply the Command pattern,
we no longer need all those button subclasses to implement various click
behaviors. It’s enough to put a single field into the base `Button`
class that stores a reference to a command object and make the button
execute that command on a click.

You’ll implement a bunch of command classes for every possible operation
and link them with particular buttons, depending on the buttons’
intended behavior.

Other GUI elements, such as menus, shortcuts or entire dialogs, can be
implemented in the same way. They’ll be linked to a command which gets
executed when a user interacts with the GUI element. As you’ve probably
guessed by now, the elements related to the same operations will be
linked to the same commands, preventing any code duplication.

As a result, commands become a convenient middle layer that reduces
coupling between the GUI and business logic layers. And that’s only a
fraction of the benefits that the Command pattern can offer\!

#### Structure

![](attachments/463529910/463529908.png)

#### Pseudocode

![](attachments/463529910/463529909.png)

#### Real world example

A generic example would be you ordering food at a restaurant. You (i.e.
`Client`) ask the waiter (i.e. `Invoker`) to bring some food (i.e.
`Command`) and waiter simply forwards the request to Chef (i.e.
`Receiver`) who has the knowledge of what and how to cook. Another
example would be you (i.e. `Client`) switching on (i.e. `Command`) the
television (i.e. `Receiver`) using a remote control ( `Invoker`).

#### In plain words

Allows you to encapsulate actions in objects. The key idea behind this
pattern is to provide the means to decouple client from receiver.

#### Wikipedia says

In object-oriented programming, the command pattern is a behavioral
design pattern in which an object is used to encapsulate all information
needed to perform an action or trigger an event at a later time. This
information includes the method name, the object that owns the method
and values for the method parameters.

#### Pros and Cons

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
<td><em>Single Responsibility Principle</em>. You can decouple classes that invoke operations from classes that perform these operations.</td>
<td>The code may become more complicated since you’re introducing a whole new layer between senders and receivers.</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em>. You can introduce new commands into the app without breaking existing client code.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td>You can implement undo/redo.</td>
<td><br />
</td>
</tr>
<tr class="even">
<td>You can implement deferred execution of operations.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td>You can assemble a set of simple commands into a complex one.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

##### C\#

<div>

First of all we have the receiver that has the implementation of every
action that could be performed

``` 
// Receiver
class Bulb
{
    public void TurnOn()
    {
        Console.WriteLine("Bulb has been lit");
    }

    public void TurnOff()
    {
        Console.WriteLine("Darkness!");
    }
}
                
```

then we have an interface that each of the commands are going to
implement and then we have a set of commands

``` 
interface ICommand
{
    void Execute();
    void Undo();
    void Redo();
}

// Command
class TurnOn : ICommand
{
    private Bulb mBulb;

    public TurnOn(Bulb bulb)
    {
        mBulb = bulb ?? throw new ArgumentNullException("Bulb", "Bulb cannot be null");
    }

    public void Execute()
    {
        mBulb.TurnOn();
    }

    public void Undo()
    {
        mBulb.TurnOff();
    }

    public void Redo()
    {
        Execute();
    }
}

class TurnOff : ICommand
{
    private Bulb mBulb;

    public TurnOff(Bulb bulb)
    {
        mBulb = bulb ?? throw new ArgumentNullException("Bulb", "Bulb cannot be null");
    }

    public void Execute()
    {
        mBulb.TurnOff();
    }

    public void Undo()
    {
        mBulb.TurnOn();
    }

    public void Redo()
    {
        Execute();
    }
}
                
```

Then we have an `Invoker` with whom the client will interact to process
any commands

``` 
// Invoker
class RemoteControl
{
    public void Submit(ICommand command)
    {
        command.Execute();
    }
}
                
```

Finally let's see how we can use it in our client

``` 
var bulb = new Bulb();

var turnOn = new TurnOn(bulb);
var turnOff = new TurnOff(bulb);

var remote = new RemoteControl();
remote.Submit(turnOn); // Bulb has been lit!
remote.Submit(turnOff); // Darkness!

Console.ReadLine();
                
```

Command pattern can also be used to implement a transaction based
system. Where you keep maintaining the history of commands as soon as
you execute them. If the final command is successfully executed, all
good otherwise just iterate through the history and keep executing the
`undo` on all the executed commands.

</div>

##### JavaScript

<div>

First of all we have the receiver that has the implementation of every
action that could be performed

``` 
// Receiver
class Bulb {
    turnOn() {
        console.log('Bulb has been lit')
    }
    
    turnOff() {
        console.log('Darkness!')
    }
}
                
```

then we have an interface that each of the commands are going to
implement and then we have a set of commands

``` 
/*
Command interface :

 execute()
 undo()
 redo()
*/

// Command
class TurnOnCommand {
    constructor(bulb) {
        this.bulb = bulb
    }
    
    execute() {
        this.bulb.turnOn()
    }
    
    undo() {
        this.bulb.turnOff()
    }
    
    redo() {
        this.execute()
    }
}

class TurnOffCommand {
    constructor(bulb) {
        this.bulb = bulb
    }
    
    execute() {
        this.bulb.turnOff()
    }
    
    undo() {
        this.bulb.turnOn()
    }
    
    redo() {
        this.execute()
    }
}
                
```

Then we have an `Invoker` with whom the client will interact to process
any commands

``` 
// Invoker
class RemoteControl {
    submit(command) {
        command.execute()
    }
}
                
```

Finally let's see how we can use it in our client

``` 
const bulb = new Bulb()

const turnOn = new TurnOnCommand(bulb)
const turnOff = new TurnOffCommand(bulb)

const remote = new RemoteControl()
remote.submit(turnOn) // Bulb has been lit!
remote.submit(turnOff) // Darkness!
                
```

</div>

##### PHP

First of all we have the receiver that has the implementation of every
action that could be performed

``` 
// Receiver
class Bulb
{
    public function turnOn()
    {
        echo "Bulb has been lit";
    }

    public function turnOff()
    {
        echo "Darkness!";
    }
}
                
```

then we have an interface that each of the commands are going to
implement and then we have a set of commands

``` 
interface Command
{
    public function execute();
    public function undo();
    public function redo();
}

// Command
class TurnOn implements Command
{
    protected $bulb;

    public function __construct(Bulb $bulb)
    {
        $this->bulb = $bulb;
    }

    public function execute()
    {
        $this->bulb->turnOn();
    }

    public function undo()
    {
        $this->bulb->turnOff();
    }

    public function redo()
    {
        $this->execute();
    }
}

class TurnOff implements Command
{
    protected $bulb;

    public function __construct(Bulb $bulb)
    {
        $this->bulb = $bulb;
    }

    public function execute()
    {
        $this->bulb->turnOff();
    }

    public function undo()
    {
        $this->bulb->turnOn();
    }

    public function redo()
    {
        $this->execute();
    }
}
                
```

Then we have an `Invoker` with whom the client will interact to process
any commands

``` 
// Invoker
class RemoteControl
{
    public function submit(Command $command)
    {
        $command->execute();
    }
}
                
```

Finally let's see how we can use it in our client

``` 
$bulb = new Bulb();

$turnOn = new TurnOn($bulb);
$turnOff = new TurnOff($bulb);

$remote = new RemoteControl();
$remote->submit($turnOn); // Bulb has been lit!
$remote->submit($turnOff); 
// Darkness!
                
```

Command pattern can also be used to implement a transaction based
system. Where you keep maintaining the history of commands as soon as
you execute them. If the final command is successfully executed, all
good otherwise just iterate through the history and keep executing
the undo on all the executed commands.

##### Python

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
*TL;DR
Encapsulates all information needed to perform an action or trigger an event.

*Examples in Python ecosystem:
Django HttpRequest (without `execute` method):
 https://docs.djangoproject.com/en/2.1/ref/request-response/#httprequest-objects
"""

from __future__ import print_function
import os

class MoveFileCommand(object):
    def __init__(self, src, dest):
        self.src = src
        self.dest = dest

    def execute(self):
        self.rename(self.src, self.dest)

    def undo(self):
        self.rename(self.dest, self.src)

    def rename(self, src, dest):
        print(u"renaming %s to %s" % (src, dest))
        os.rename(src, dest)

def main():
    """
    >>> from os.path import lexists

    >>> command_stack = [
    ...     MoveFileCommand('foo.txt', 'bar.txt'),
    ...     MoveFileCommand('bar.txt', 'baz.txt')
    ... ]

    # Verify that none of the target files exist
    >>> assert not lexists("foo.txt")
    >>> assert not lexists("bar.txt")
    >>> assert not lexists("baz.txt")

    # Create empty file
    >>> open("foo.txt", "w").close()

    # Commands can be executed later on
    >>> for cmd in command_stack:
    ...     cmd.execute()
    renaming foo.txt to bar.txt
    renaming bar.txt to baz.txt

    # And can also be undone at will
    >>> for cmd in reversed(command_stack):
    ...     cmd.undo()
    renaming baz.txt to bar.txt
    renaming bar.txt to foo.txt

    >>> os.unlink("foo.txt")
    """

if __name__ == "__main__":
    import doctest
    doctest.testmod()
                
```

### Iterator

#### Intent

Iterator is a behavioral design pattern that lets you traverse elements
of a collection without exposing its underlying representation (list,
stack, tree, etc.).

![](attachments/463529918/463529912.png)

#### Problem

Collections are one of the most used data types in programming.
Nonetheless, a collection is just a container for a group of objects.

![](attachments/463529918/463529913.png)

Most collections store their elements in simple lists. However, some of
them are based on stacks, trees, graphs and other complex data
structures.

But no matter how a collection is structured, it must provide some way
of accessing its elements so that other code can use these elements.
There should be a way to go through each element of the collection
without accessing the same elements over and over.

This may sound like an easy job if you have a collection based on a
list. You just loop over all of the elements. But how do you
sequentially traverse elements of a complex data structure, such as a
tree? For example, one day you might be just fine with depth-first
traversal of a tree. Yet the next day you might require breadth-first
traversal. And the next week, you might need something else, like random
access to the tree elements.

![](attachments/463529918/463529914.png)

Adding more and more traversal algorithms to the collection gradually
blurs its primary responsibility, which is efficient data storage.
Additionally, some algorithms might be tailored for a specific
application, so including them into a generic collection class would be
weird.

On the other hand, the client code that’s supposed to work with various
collections may not even care how they store their elements. However,
since collections all provide different ways of accessing their
elements, you have no option other than to couple your code to the
specific collection classes.

#### Solution

The main idea of the Iterator pattern is to extract the traversal
behavior of a collection into a separate object called an *iterator*.

![](attachments/463529918/463529915.png)

In addition to implementing the algorithm itself, an iterator object
encapsulates all of the traversal details, such as the current position
and how many elements are left till the end. Because of this, several
iterators can go through the same collection at the same time,
independently of each other.

Usually, iterators provide one primary method for fetching elements of
the collection. The client can keep running this method until it doesn’t
return anything, which means that the iterator has traversed all of the
elements.

All iterators must implement the same interface. This makes the client
code compatible with any collection type or any traversal algorithm as
long as there’s a proper iterator. If you need a special way to traverse
a collection, you just create a new iterator class, without having to
change the collection or the client.

#### Structure

![](attachments/463529918/463529916.png)

#### Pseudocode

![](attachments/463529918/463529917.png)

#### Real world Example

An old radio set will be a good example of iterator, where user could
start at some channel and then use next or previous buttons to go
through the respective channels. Or take an example of MP3 player or a
TV set where you could press the next and previous buttons to go through
the consecutive channels or in other words they all provide an interface
to iterate through the respective channels, songs or radio stations.

#### In plain words

It presents a way to access the elements of an object without exposing
the underlying presentation.

#### Wikipedia says

In object-oriented programming, the iterator pattern is a design pattern
in which an iterator is used to traverse a container and access the
container's elements. The iterator pattern decouples algorithms from
containers; in some cases, algorithms are necessarily container-specific
and thus cannot be decoupled.

#### Pros and Cons

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
<td><em>Single Responsibility Principle</em>. You can clean up the client code and the collections by extracting bulky traversal algorithms into separate classes.</td>
<td>Applying the pattern can be an overkill if your app only works with simple collections.</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em>. You can implement new types of collections and iterators and pass them to existing code without breaking anything.</td>
<td>Using an iterator may be less efficient than going through elements of some specialized collections directly.</td>
</tr>
<tr class="odd">
<td>You can iterate over the same collection in parallel because each iterator object contains its own iteration state.</td>
<td><br />
</td>
</tr>
<tr class="even">
<td>For the same reason, you can delay an iteration and continue it when needed.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

##### C\#

<div>

First of all we have RadioStation

> 
> 
> ``` 
> class RadioStation
> {
>     private float mFrequency;
> 
>     public RadioStation(float frequency)
>     {
>         mFrequency = frequency;
>     }
> 
>     public float GetFrequecy()
>     {
>         return mFrequency;
>     }
> }
>                     
> ```

Then we have our iterator

> 
> 
> ``` 
> class StationList : IEnumerable<RadioStation>
> {
>     List <RadioStation> mStations = new List<RadioStation>();
> 
>     public RadioStation this[int index]
>     {
>         get { return mStations[index]; }
>         set { mStations.Insert(index, value); }
>     }
> 
>     public void Add(RadioStation station)
>     {
>         mStations.Add(station);
>     }
> 
>     public void Remove(RadioStation station)
>     {
>         mStations.Remove(station);
>     }
> 
>     public IEnumerator<RadioStation> GetEnumerator()
>     {
>         return this.GetEnumerator();
>     }
> 
>     IEnumerator IEnumerable.GetEnumerator()
>     {
>         //Use can switch to this internal collection if you do not want to transform
>         //return mStations.GetEnumerator();
> 
>         //use this if you want to transform the object before rendering
>         foreach (var x in mStations)
>         {
>           yield return x;
>         }
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
> var stations = new StationList();
> var station1 = new RadioStation(89);
> stations.Add(station1);
> 
> var station2 = new RadioStation(101);
> stations.Add(station2);
> 
> var station3 = new RadioStation(102);
> stations.Add(station3);
> 
> foreach(var x in stations)
> {
>   Console.Write(x.GetFrequecy());
> }
> 
> var q = stations.Where(x => x.GetFrequecy() == 89).FirstOrDefault();
> Console.WriteLine(q.GetFrequecy());
> 
> Console.ReadLine();
>                     
> ```

</div>

##### JavaScript

<div>

Translating our radio stations example from above. First of all we have
`RadioStation`

> 
> 
> ``` 
> class RadioStation {
>     constructor(frequency) {
>         this.frequency = frequency    
>     }
>     
>     getFrequency() {
>         return this.frequency
>     }
> }
>                     
> ```

Then we have our iterator

> 
> 
> ``` 
> class StationList {
>     constructor(){
>         this.stations = []
>     }
> 
>     addStation(station) {
>         this.stations.push(station)
>     }
>     
>     removeStation(toRemove) {
>         const toRemoveFrequency = toRemove.getFrequency()
>         this.stations = this.stations.filter(station => {
>             return station.getFrequency() !== toRemoveFrequency
>         })
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
> const stationList = new StationList()
> 
> stationList.addStation(new RadioStation(89))
> stationList.addStation(new RadioStation(101))
> stationList.addStation(new RadioStation(102))
> stationList.addStation(new RadioStation(103.2))
> 
> stationList.stations.forEach(station => console.log(station.getFrequency()))
> 
> stationList.removeStation(new RadioStation(89)) // Will remove station 89
> 
>                     
> ```

</div>

##### PHP

<div>

First of all we have RadioStation

``` 
class RadioStation
{
    protected $frequency;

    public function __construct(float $frequency)
    {
        $this->frequency = $frequency;
    }

    public function getFrequency(): float
    {
        return $this->frequency;
    }
}
                
```

Then we have our iterator

``` 
use Countable;
use Iterator;

class StationList implements Countable, Iterator
{
    /** @var RadioStation[] $stations */
    protected $stations = [];

    /** @var int $counter */
    protected $counter;

    public function addStation(RadioStation $station)
    {
        $this->stations[] = $station;
    }

    public function removeStation(RadioStation $toRemove)
    {
        $toRemoveFrequency = $toRemove->getFrequency();
        $this->stations = array_filter($this->stations, function (RadioStation $station) use ($toRemoveFrequency) {
        return $station->getFrequency() !== $toRemoveFrequency;
        });
    }

    public function count(): int
    {
        return count($this->stations);
    }

    public function current(): RadioStation
    {
        return $this->stations[$this->counter];
    }

    public function key()
    {
        return $this->counter;
    }

    public function next()
    {
        $this->counter++;
    }

    public function rewind()
    {
        $this->counter = 0;
    }

    public function valid(): bool
    {
        return isset($this->stations[$this->counter]);
    }
}

                
```

And then it can be used as

``` 
$stationList = new StationList();

$stationList->addStation(new RadioStation(89));
$stationList->addStation(new RadioStation(101));
$stationList->addStation(new RadioStation(102));
$stationList->addStation(new RadioStation(103.2));

foreach($stationList as $station) {
    echo $station->getFrequency() . PHP_EOL;
}

$stationList->removeStation(new RadioStation(89)); // Will remove station 89
                
```

</div>

##### Python

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
http://ginstrom.com/scribbles/2007/10/08/design-patterns-python-style/
Implementation of the iterator pattern with a generator

*TL;DR
Traverses a container and accesses the container's elements.
"""

from __future__ import print_function

def count_to(count):
    """Counts by word numbers, up to a maximum of five"""
    numbers = ["one", "two", "three", "four", "five"]
    for number in numbers[:count]:
        yield number

# Test the generator
count_to_two = lambda: count_to(2)
count_to_five = lambda: count_to(5)

def main():
    """
    # Counting to two...
    >>> for number in count_to_two():
    ...     print(number)
    one
    two

    # Counting to five...
    >>> for number in count_to_five():
    ...     print(number)
    one
    two
    three
    four
    five
    """

if __name__ == "__main__":
    import doctest
    doctest.testmod()
                
```

### Memento

#### Intent

**Memento** is a behavioral design pattern that lets you save and
restore the previous state of an object without revealing the details of
its implementation.

![](attachments/463529936/463529928.png)

#### Problem

Imagine that you’re creating a text editor app. In addition to simple
text editing, your editor can format text, insert inline images, etc.

At some point, you decided to let users undo any operations carried out
on the text. This feature has become so common over the years that
nowadays people expect every app to have it. For the implementation, you
chose to take the direct approach. Before performing any operation, the
app records the state of all objects and saves it in some storage.
Later, when a user decides to revert an action, the app fetches the
latest snapshot from the history and uses it to restore the state of all
objects.

![](attachments/463529936/463529929.png)

Let’s think about those state snapshots. How exactly would you produce
one? You’d probably need to go over all the fields in an object and copy
their values into storage. However, this would only work if the object
had quite relaxed access restrictions to its contents. Unfortunately,
most real objects won’t let others peek inside them that easily, hiding
all significant data in private fields.

Ignore that problem for now and let’s assume that our objects behave
like hippies: preferring open relations and keeping their state public.
While this approach would solve the immediate problem and let you
produce snapshots of objects’ states at will, it still has some serious
issues. In the future, you might decide to refactor some of the editor
classes, or add or remove some of the fields. Sounds easy, but this
would also require changing the classes responsible for copying the
state of the affected objects.

![](attachments/463529936/463529930.png)

But there’s more. Let’s consider the actual “snapshots” of the editor’s
state. What data does it contain? At a bare minimum, it must contain the
actual text, cursor coordinates, current scroll position, etc. To make a
snapshot, you’d need to collect these values and put them into some kind
of container.

Most likely, you’re going to store lots of these container objects
inside some list that would represent the history. Therefore the
containers would probably end up being objects of one class. The class
would have almost no methods, but lots of fields that mirror the
editor’s state. To allow other objects to write and read data to and
from a snapshot, you’d probably need to make its fields public. That
would expose all the editor’s states, private or not. Other classes
would become dependent on every little change to the snapshot class,
which would otherwise happen within private fields and methods without
affecting outer classes.

It looks like we’ve reached a dead end: you either expose all internal
details of classes, making them too fragile, or restrict access to their
state, making it impossible to produce snapshots. Is there any other way
to implement the "undo"?

#### Solution

All problems that we’ve just experienced are caused by broken
encapsulation. Some objects try to do more than they are supposed to. To
collect the data required to perform some action, they invade the
private space of other objects instead of letting these objects perform
the actual action.

The Memento pattern delegates creating the state snapshots to the actual
owner of that state, the *originator* object. Hence, instead of other
objects trying to copy the editor’s state from the “outside,” the editor
class itself can make the snapshot since it has full access to its own
state.

The pattern suggests storing the copy of the object’s state in a special
object called *memento*. The contents of the memento aren’t accessible
to any other object except the one that produced it. Other objects must
communicate with mementos using a limited interface which may allow
fetching the snapshot’s metadata (creation time, the name of the
performed operation, etc.), but not the original object’s state
contained in the snapshot.

![](attachments/463529936/463529931.png)

Such a restrictive policy lets you store mementos inside other objects,
usually called *caretakers*. Since the caretaker works with the memento
only via the limited interface, it’s not able to tamper with the state
stored inside the memento. At the same time, the originator has access
to all fields inside the memento, allowing it to restore its previous
state at will.

In our text editor example, we can create a separate history class to
act as the caretaker. A stack of mementos stored inside the caretaker
will grow each time the editor is about to execute an operation. You
could even render this stack within the app’s UI, displaying the history
of previously performed operations to a user.

When a user triggers the undo, the history grabs the most recent memento
from the stack and passes it back to the editor, requesting a roll-back.
Since the editor has full access to the memento, it changes its own
state with the values taken from the memento.

#### Structure

##### Implementation based on nested classes

The classic implementation of the pattern relies on support for nested
classes, available in many popular programming languages (such as C++,
C\#, and Java).

![](attachments/463529936/463529932.png)

##### Implementation based on an intermediate interface

There’s an alternative implementation, suitable for programming
languages that don’t support nested classes (yeah, PHP, I’m talking
about you).

![](attachments/463529936/463529933.png)

##### Implementation with even stricter encapsulation

There’s another implementation which is useful when you don’t want to
leave even the slightest chance of other classes accessing the state of
the originator through the memento.

![](attachments/463529936/463529934.png)

#### Pseudocode

![](attachments/463529936/463529935.png)

#### Real world example

Take the example of calculator (i.e. originator), where whenever you
perform some calculation the last calculation is saved in memory (i.e.
memento) so that you can get back to it and maybe get it restored using
some action buttons (i.e. caretaker).

#### In plain words

Memento pattern is about capturing and storing the current state of an
object in a manner that it can be restored later on in a smooth manner.

#### Wikipedia says

The memento pattern is a software design pattern that provides the
ability to restore an object to its previous state (undo via rollback).

Usually useful when you need to provide some sort of undo functionality.

#### Pros and Cons

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
<td>You can produce snapshots of the object’s state without violating its encapsulation.</td>
<td>The app might consume lots of RAM if clients create mementos too often.</td>
</tr>
<tr class="even">
<td>You can simplify the originator’s code by letting the caretaker maintain the history of the originator’s state.</td>
<td>Caretakers should track the originator’s lifecycle to be able to destroy obsolete mementos.</td>
</tr>
<tr class="odd">
<td><br />
</td>
<td>Most dynamic programming languages, such as PHP, Python and JavaScript, can’t guarantee that the state within the memento stays untouched.</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

#### C\#

<div>

Lets take an example of text editor which keeps saving the state from
time to time and that you can restore if you want.

First of all we have our memento object that will be able to hold the
editor state

> 
> 
> ``` 
> class EditorMemento
> {
>     private string mContent;
> 
>     public EditorMemento(string content)
>     {
>         mContent = content;
>     }
> 
>     public string Content
>     {
>         get{ return mContent; }
>     }
> }
>                     
> ```

Then we have our editor i.e. originator that is going to use memento
object

> 
> 
> ``` 
> class Editor {
>     private string mContent = string.Empty;
>     private EditorMemento memento;
> 
>     public Editor()
>     {
>         memento = new EditorMemento(string.Empty);
>     }
> 
>     public void Type(string words)
>     {
>         mContent = String.Concat(mContent," ", words);
>     }
> 
>     public string Content
>     {
>         get{ return mContent; }
>     }
> 
>     public void Save() {
>         memento = new EditorMemento(mContent);
>     }
> 
>     public void Restore()
>     {
>         mContent = memento.Content;
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
> var editor = new Editor();
> 
> //Type some stuff
> editor.Type("This is the first sentence.");
> editor.Type("This is second.");
> 
> // Save the state to restore to : This is the first sentence. This is second.
> editor.Save();
> 
> //Type some more
> editor.Type("This is third.");
> 
> //Output the content
> Console.WriteLine(editor.Content); // This is the first sentence. This is second. This is third.
> 
> //Restoring to last saved state
> editor.Restore();
> 
> Console.Write(editor.Content); // This is the first sentence. This is second
>                     
> ```

</div>

##### JavaScript

<div>

Lets take an example of text editor which keeps saving the state from
time to time and that you can restore if you want.

First of all we have our memento object that will be able to hold the
editor state

``` 
class EditorMemento {
    constructor(content) {
        this._content = content
    }
    
    getContent() {
        return this._content
    }
}
                
```

Then we have our editor i.e. originator that is going to use memento
object

``` 
class Editor {
    constructor(){
        this._content = ''
    }
    
    type(words) {
        this._content = this._content + ' ' + words
    }
    
    getContent() {
        return this._content
    }
    
    save() {
        return new EditorMemento(this._content)
    }
    
    restore(memento) {
        this._content = memento.getContent()
    }
}
                
```

And then it can be used as

``` 
const editor = new Editor()

// Type some stuff
editor.type('This is the first sentence.')
editor.type('This is second.')

// Save the state to restore to : This is the first sentence. This is second.
const saved = editor.save()

// Type some more
editor.type('And this is third.')

// Output: Content before Saving
console.log(editor.getContent())// This is the first sentence. This is second. And this is third.

// Restoring to last saved state
editor.restore(saved)

console.log(editor.getContent()) // This is the first sentence. This is second.
                
```

</div>

##### PHP

<div>

Lets take an example of text editor which keeps saving the state from
time to time and that you can restore if you want.

First of all we have our memento object that will be able to hold the
editor state

``` 
class EditorMemento
{
    protected $content;

    public function __construct(string $content)
    {
        $this->content = $content;
    }

    public function getContent()
    {
        return $this->content;
    }
}
                
```

Then we have our editor i.e. originator that is going to use memento
object

``` 
class Editor
{
    protected $content = '';

    public function type(string $words)
    {
        $this->content = $this->content . ' ' . $words;
    }

    public function getContent()
    {
        return $this->content;
    }

    public function save()
    {
        return new EditorMemento($this->content);
    }

    public function restore(EditorMemento $memento)
    {
        $this->content = $memento->getContent();
    }
}
                
```

And then it can be used as

``` 
$editor = new Editor();

// Type some stuff
$editor->type('This is the first sentence.');
$editor->type('This is second.');

// Save the state to restore to : This is the first sentence. This is second.
$saved = $editor->save();

// Type some more
$editor->type('And this is third.');

// Output: Content before Saving
echo $editor->getContent(); // This is the first sentence. This is second. And this is third.

// Restoring to last saved state
$editor->restore($saved);

$editor->getContent(); // This is the first sentence. This is second.
                
```

</div>

##### Python

``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
http://code.activestate.com/recipes/413838-memento-closure/

*TL;DR
Provides the ability to restore an object to its previous state.
"""

from copy import copy
from copy import deepcopy


def memento(obj, deep=False):
    state = deepcopy(obj.__dict__) if deep else copy(obj.__dict__)

    def restore():
        obj.__dict__.clear()
        obj.__dict__.update(state)

    return restore


class Transaction(object):
    """A transaction guard.

    This is, in fact, just syntactic sugar around a memento closure.
    """

    deep = False
    states = []

    def __init__(self, deep, *targets):
        self.deep = deep
        self.targets = targets
        self.commit()

    def commit(self):
        self.states = [memento(target, self.deep) for target in self.targets]

    def rollback(self):
        for a_state in self.states:
            a_state()


class Transactional(object):
    """Adds transactional semantics to methods. Methods decorated  with

    @Transactional will rollback to entry-state upon exceptions.
    """

    def __init__(self, method):
        self.method = method

    def __get__(self, obj, T):
        def transaction(*args, **kwargs):
            state = memento(obj)
            try:
                return self.method(obj, *args, **kwargs)
            except Exception as e:
                state()
                raise e

        return transaction


class NumObj(object):
    def __init__(self, value):
        self.value = value

    def __repr__(self):
        return '<%s: %r>' % (self.__class__.__name__, self.value)

    def increment(self):
        self.value += 1

    @Transactional
    def do_stuff(self):
        self.value = '1111'  # <- invalid value
        self.increment()  # <- will fail and rollback


def main():
    """
    >>> num_obj = NumObj(-1)
    >>> print(num_obj)
    <NumObj: -1>

    >>> a_transaction = Transaction(True, num_obj)

    >>> try:
    ...    for i in range(3):
    ...        num_obj.increment()
    ...        print(num_obj)
    ...    a_transaction.commit()
    ...    print('-- committed')
    ...    for i in range(3):
    ...        num_obj.increment()
    ...        print(num_obj)
    ...    num_obj.value += 'x'  # will fail
    ...    print(num_obj)
    ... except Exception:
    ...    a_transaction.rollback()
    ...    print('-- rolled back')
    <NumObj: 0>
    <NumObj: 1>
    <NumObj: 2>
    -- committed
    <NumObj: 3>
    <NumObj: 4>
    <NumObj: 5>
    -- rolled back

    >>> print(num_obj)
    <NumObj: 2>

    >>> print('-- now doing stuff ...')
    -- now doing stuff ...

    >>> try:
    ...    num_obj.do_stuff()
    ... except Exception:
    ...    print('-> doing stuff failed!')
    ...    import sys
    ...    import traceback
    ...    traceback.print_exc(file=sys.stdout)
    -> doing stuff failed!
    Traceback (most recent call last):
    ...
    TypeError: ...str...int...

    >>> print(num_obj)
    <NumObj: 2>
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod(optionflags=doctest.ELLIPSIS)
                
```

### Observer

#### Intent

**Observer** is a behavioral design pattern that lets you define a
subscription mechanism to notify multiple objects about any events that
happen to the object they’re observing.

![](attachments/463529939/463530128.png)

### Problem

Imagine that you have two types of objects: a `Customer` and a `Store`.
The customer is very interested in a particular brand of product (say,
it’s a new model of the iPhone) which should become available in the
store very soon.

The customer could visit the store every day and check product
availability. But while the product is still en route, most of these
trips would be pointless.

![](attachments/463529939/463530129.png)

On the other hand, the store could send tons of emails (which might be
considered spam) to all customers each time a new product becomes
available. This would save some customers from endless trips to the
store. At the same time, it’d upset other customers who aren’t
interested in new products.

It looks like we’ve got a conflict. Either the customer wastes time
checking product availability or the store wastes resources notifying
the wrong customers.

#### Solution

The object that has some interesting state is often called *subject* ,
but since it’s also going to notify other objects about the changes to
its state, we’ll call it *publisher*. All other objects that want to
track changes to the publisher’s state are called *subscribers*.

The Observer pattern suggests that you add a subscription mechanism to
the publisher class so individual objects can subscribe to or
unsubscribe from a stream of events coming from that publisher. Fear
not\! Everything isn’t as complicated as it sounds. In reality, this
mechanism consists of 1) an array field for storing a list of references
to subscriber objects and 2) several public methods which allow adding
subscribers to and removing them from that list.

![](attachments/463529939/463530130.png)

Now, whenever an important event happens to the publisher, it goes over
its subscribers and calls the specific notification method on their
objects.

Real apps might have dozens of different subscriber classes that are
interested in tracking events of the same publisher class. You wouldn’t
want to couple the publisher to all of those classes. Besides, you might
not even know about some of them beforehand if your publisher class is
supposed to be used by other people.

That’s why it’s crucial that all subscribers implement the same
interface and that the publisher communicates with them only via that
interface. This interface should declare the notification method along
with a set of parameters that the publisher can use to pass some
contextual data along with the notification.

![](attachments/463529939/463530131.png)

If your app has several different types of publishers and you want to
make your subscribers compatible with all of them, you can go even
further and make all publishers follow the same interface. This
interface would only need to describe a few subscription methods. The
interface would allow subscribers to observe publishers’ states without
coupling to their concrete classes.

#### Structure

![](attachments/463529939/463530132.png)

#### Pseudocode

![](attachments/463529939/463530133.png)

#### Real world example

A good example would be the job seekers where they subscribe to some job
posting site and they are notified whenever there is a matching job
opportunity.

#### In plain words

Defines a dependency between objects so that whenever an object changes
its state, all its dependents are notified.

#### Wikipedia says

The observer pattern is a software design pattern in which an object,
called the subject, maintains a list of its dependents, called
observers, and notifies them automatically of any state changes, usually
by calling one of their methods.

#### Pros and Cons

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
<td><em>Open/Closed Principle</em>. You can introduce new subscriber classes without having to change the publisher’s code (and vice versa if there’s a publisher interface).</td>
<td>Subscribers are notified in random order.</td>
</tr>
<tr class="even">
<td>You can establish relations between objects at runtime.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

##### C\#

<div>

Translating our example from above. First of all we have job seekers
that need to be notified for a job posting

> 
> 
> ``` 
> class JobPost
> {
>     public string Title { get; private set; }
> 
>     public JobPost(string title)
>     {
>         Title = title;
>     }
> }
> class JobSeeker : IObserver <JobPost>
> {
>     public string Name { get; private set; }
> 
>     public JobSeeker(string name)
>     {
>         Name = name;
>     }
> 
>     //Method is not being called by JobPostings class currently
>     public void OnCompleted()
>     {
>         //No Implementation
>     }
> 
>     //Method is not being called by JobPostings class currently
>     public void OnError(Exception error)
>     {
>         //No Implementation
>     }
> 
>     public void OnNext(JobPost value)
>     {
>         Console.WriteLine($"Hi {Name} ! New job posted: {value.Title}");
>     }
> }
>                     
> ```

Then we have our job postings to which the job seekers will subscribe

> 
> 
> ``` 
> class JobPostings : IObservable<JobPost>
> {
>   private List <IObserver <JobPost>> mObservers;
>   private List <JobPost> mJobPostings;
> 
>   public JobPostings()
>   {
>     mObservers = new List<IObserver<JobPost>>();
>     mJobPostings = new List<JobPost>();
>   }
> 
>   public IDisposable Subscribe(IObserver<JobPost> observer)
>   {
>     // Check whether observer is already registered. If not, add it
>     if (!mObservers.Contains(observer))
>     {
>       mObservers.Add(observer);
>     }
>     return new Unsubscriber<JobPost>(mObservers, observer);
>   }
> 
>   private void Notify(JobPost jobPost)
>   {
>     foreach(var observer in mObservers)
>     {
>       observer.OnNext(jobPost);
>     }
>   }
> 
>   public void AddJob(JobPost jobPost)
>   {
>     mJobPostings.Add(jobPost);
>     Notify(jobPost);
>   }
> 
> }
> 
> internal class Unsubscriber<JobPost> : IDisposable
> {
>   private List<IObserver<JobPost>> mObservers;
>   private IObserver<JobPost> mObserver;
> 
>   internal Unsubscriber(List<IObserver<JobPost>> observers, IObserver<JobPost> observer)
>   {
>     this.mObservers = observers;
>     this.mObserver = observer;
>   }
> 
>   public void Dispose()
>   {
>     if (mObservers.Contains(mObserver))
>       mObservers.Remove(mObserver);
>   }
> }
>                         
> ```

Then it can be used as

> 
> 
> ``` 
> //Create Subscribers
> var johnDoe = new JobSeeker("John Doe");
> var janeDoe = new JobSeeker("Jane Doe");
> 
> //Create publisher and attch subscribers
> var jobPostings = new JobPostings();
> jobPostings.Subscribe(johnDoe);
> jobPostings.Subscribe(janeDoe);
> 
> //Add a new job and see if subscribers get notified
> jobPostings.AddJob(new JobPost("Software Engineer"));
> 
> //Output
> // Hi John Doe! New job posted: Software Engineer
> // Hi Jane Doe! New job posted: Software Engineer
> 
> Console.ReadLine();
>                     
> ```

</div>

##### JavaScript

<div>

Translating our example from above. First of all we have job seekers
that need to be notified for a job posting

> 
> 
> ``` 
> const JobPost = title => ({
>     title: title
> })
> 
> class JobSeeker {
>     constructor(name) {
>         this._name = name
>     }
> 
>     notify(jobPost) {
>         console.log(this._name, 'has been notified of a new posting :', jobPost.title)
>     }
> }
>                     
> ```

Then we have our job postings to which the job seekers will subscribe

> 
> 
> ``` 
> class JobBoard {
>     constructor() {
>         this._subscribers = []
>     }
> 
>     subscribe(jobSeeker) {
>         this._subscribers.push(jobSeeker)
>     }
> 
>     addJob(jobPosting) {
>         this._subscribers.forEach(subscriber => {
>             subscriber.notify(jobPosting)
>         })
>     }
> }
>                     
> ```

Then it can be used as

> 
> 
> ``` 
> // Create subscribers
> const jonDoe = new JobSeeker('John Doe')
> const janeDoe = new JobSeeker('Jane Doe')
> const kaneDoe = new JobSeeker('Kane Doe')
> 
> // Create publisher and attach subscribers
> const jobBoard = new JobBoard()
> jobBoard.subscribe(jonDoe)
> jobBoard.subscribe(janeDoe)
> 
> // Add a new job and see if subscribers get notified
> jobBoard.addJob(JobPost('Software Engineer'))
> 
> // Output
> // John Doe has been notified of a new posting : Software Engineer
> // Jane Doe has been notified of a new posting : Software Engineer
>                     
> ```

</div>

##### PHP

<div>

Translating our example from above. First of all we have job seekers
that need to be notified for a job posting

> 
> 
> ``` 
> class JobPost
> {
>     protected $title;
> 
>     public function __construct(string $title)
>     {
>         $this->title = $title;
>     }
> 
>     public function getTitle()
>     {
>         return $this->title;
>     }
> }
> 
> class JobSeeker implements Observer
> {
>     protected $name;
> 
>     public function __construct(string $name)
>     {
>         $this->name = $name;
>     }
> 
>     public function onJobPosted(JobPost $job)
>     {
>         // Do something with the job posting
>         echo 'Hi ' . $this->name . '! New job posted: '. $job->getTitle();
>     }
> }
>                     
> ```

Then we have our job postings to which the job seekers will subscribe

> 
> 
> ``` 
> class EmploymentAgency implements Observable
> {
>     protected $observers = [];
> 
>     protected function notify(JobPost $jobPosting)
>     {
>         foreach ($this->observers as $observer) {
>             $observer->onJobPosted($jobPosting);
>         }
>     }
> 
>     public function attach(Observer $observer)
>     {
>         $this->observers[] = $observer;
>     }
> 
>     public function addJob(JobPost $jobPosting)
>     {
>         $this->notify($jobPosting);
>     }
> }
>                     
> ```

Then it can be used as

> 
> 
> ``` 
> // Create subscribers
> $johnDoe = new JobSeeker('John Doe');
> $janeDoe = new JobSeeker('Jane Doe');
> 
> // Create publisher and attach subscribers
> $jobPostings = new EmploymentAgency();
> $jobPostings->attach($johnDoe);
> $jobPostings->attach($janeDoe);
> 
> // Add a new job and see if subscribers get notified
> $jobPostings->addJob(new JobPost('Software Engineer'));
> 
> // Output
> // Hi John Doe! New job posted: Software Engineer
> // Hi Jane Doe! New job posted: Software Engineer
>                     
> ```

</div>

##### Python

<div>

> 
> 
> ``` 
> #!/usr/bin/env python
> # -*- coding: utf-8 -*-
> 
> """
> http://code.activestate.com/recipes/131499-observer-pattern/
> 
> *TL;DR
> Maintains a list of dependents and notifies them of any state changes.
> 
> *Examples in Python ecosystem:
> Django Signals: https://docs.djangoproject.com/en/2.1/topics/signals/
> Flask Signals: http://flask.pocoo.org/docs/1.0/signals/
> """
> 
> from __future__ import print_function
> 
> 
> class Subject(object):
>     def __init__(self):
>         self._observers = []
> 
>     def attach(self, observer):
>         if observer not in self._observers:
>             self._observers.append(observer)
> 
>     def detach(self, observer):
>         try:
>             self._observers.remove(observer)
>         except ValueError:
>             pass
> 
>     def notify(self, modifier=None):
>         for observer in self._observers:
>             if modifier != observer:
>                 observer.update(self)
> 
> 
> # Example usage
> class Data(Subject):
>     def __init__(self, name=''):
>         Subject.__init__(self)
>         self.name = name
>         self._data = 0
> 
>     @property
>     def data(self):
>         return self._data
> 
>     @data.setter
>     def data(self, value):
>         self._data = value
>         self.notify()
> 
> 
> class HexViewer:
>     def update(self, subject):
>         print(u'HexViewer: Subject %s has data 0x%x' % (subject.name, subject.data))
> 
> 
> class DecimalViewer:
>     def update(self, subject):
>         print(u'DecimalViewer: Subject %s has data %d' % (subject.name, subject.data))
> 
> 
> # Example usage...
> def main():
>     """
>     >>> data1 = Data('Data 1')
>     >>> data2 = Data('Data 2')
>     >>> view1 = DecimalViewer()
>     >>> view2 = HexViewer()
>     >>> data1.attach(view1)
>     >>> data1.attach(view2)
>     >>> data2.attach(view2)
>     >>> data2.attach(view1)
> 
>     >>> data1.data = 10
>     DecimalViewer: Subject Data 1 has data 10
>     HexViewer: Subject Data 1 has data 0xa
> 
>     >>> data2.data = 15
>     HexViewer: Subject Data 2 has data 0xf
>     DecimalViewer: Subject Data 2 has data 15
> 
>     >>> data1.data = 3
>     DecimalViewer: Subject Data 1 has data 3
>     HexViewer: Subject Data 1 has data 0x3
> 
>     >>> data2.data = 5
>     HexViewer: Subject Data 2 has data 0x5
>     DecimalViewer: Subject Data 2 has data 5
> 
>     # Detach HexViewer from data1 and data2
>     >>> data1.detach(view2)
>     >>> data2.detach(view2)
> 
>     >>> data1.data = 10
>     DecimalViewer: Subject Data 1 has data 10
> 
>     >>> data2.data = 15
>     DecimalViewer: Subject Data 2 has data 15
>     """
> 
> 
> if __name__ == "__main__":
>     import doctest
>     doctest.testmod()
>                     
> ```

### Visitor

#### Intent

**Visitor** is a behavioral design pattern that lets you separate
algorithms from the objects on which they operate.

![](attachments/463529941/463530158.png)

#### Problem

Imagine that your team develops an app which works with geographic
information structured as one colossal graph. Each node of the graph may
represent a complex entity such as a city, but also more granular things
like industries, sightseeing areas, etc. The nodes are connected with
others if there’s a road between the real objects that they represent.
Under the hood, each node type is represented by its own class, while
each specific node is an object.

![](attachments/463529941/463530160.png)

At some point, you got a task to implement exporting the graph into XML
format. At first, the job seemed pretty straightforward. You planned to
add an export method to each node class and then leverage recursion to
go over each node of the graph, executing the export method. The
solution was simple and elegant: thanks to polymorphism, you weren’t
coupling the code which called the export method to concrete classes of
nodes.

Unfortunately, the system architect refused to allow you to alter
existing node classes. He said that the code was already in production
and he didn’t want to risk breaking it because of a potential bug in
your changes.

![](attachments/463529941/463530161.png)

Besides, he questioned whether it makes sense to have the XML export
code within the node classes. The primary job of these classes was to
work with geodata. The XML export behavior would look alien there.

There was another reason for the refusal. It was highly likely that
after this feature was implemented, someone from the marketing
department would ask you to provide the ability to export into a
different format, or request some other weird stuff. This would force
you to change those precious and fragile classes again.

#### Solution

The Visitor pattern suggests that you place the new behavior into a
separate class called *visitor*, instead of trying to integrate it into
existing classes. The original object that had to perform the behavior
is now passed to one of the visitor’s methods as an argument, providing
the method access to all necessary data contained within the object.

Now, what if that behavior can be executed over objects of different
classes? For example, in our case with XML export, the actual
implementation will probably be a little bit different across various
node classes.

But how exactly would we call these methods, especially when dealing
with the whole graph? These methods have different signatures, so we
can’t use polymorphism. To pick a proper visitor method that’s able to
process a given object, we’d need to check its class. Doesn’t this sound
like a nightmare?

You might ask, why don’t we use method overloading? That’s when you give
all methods the same name, even if they support different sets of
parameters. Unfortunately, even assuming that our programming language
supports it at all (as Java and C\# do), it won’t help us. Since the
exact class of a node object is unknown in advance, the overloading
mechanism won’t be able to determine the correct method to execute.
It’ll default to the method that takes an object of the base `Node`
class.

However, the Visitor pattern addresses this problem. It uses a technique
called [Double
Dispatch](https://refactoring.guru/design-patterns/visitor-double-dispatch),
which helps to execute the proper method on an object without cumbersome
conditionals. Instead of letting the client select a proper version of
the method to call, how about we delegate this choice to objects we’re
passing to the visitor as an argument? Since the objects know their own
classes, they’ll be able to pick a proper method on the visitor less
awkwardly. They “accept” a visitor and tell it what visiting method
should be executed.

#### Structure

![](attachments/463529941/463530162.png)

#### Pseudocode

In this example, the **Visitor** pattern adds XML export support to the
class hierarchy of geometric shapes.

![](attachments/463529941/463530159.png)

#### Real world example

Consider someone visiting Dubai. They just need a way (i.e. visa) to
enter Dubai. After arrival, they can come and visit any place in Dubai
on their own without having to ask for permission or to do some leg work
in order to visit any place here; just let them know of a place and they
can visit it. Visitor pattern lets you do just that, it helps you add
places to visit so that they can visit as much as they can without
having to do any legwork.

#### In plain words

Visitor pattern lets you add further operations to objects without
having to modify them.

#### Wikipedia says

In object-oriented programming and software engineering, the visitor
design pattern is a way of separating an algorithm from an object
structure on which it operates. A practical result of this separation is
the ability to add new operations to existing object structures without
modifying those structures. It is one way to follow the open/closed
principle.

#### Pros and Cons

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
<td><em>Open/Closed Principle</em> . You can introduce a new behavior that can work with objects of different classes without changing these classes.</td>
<td>You need to update all visitors each time a class gets added to or removed from the element hierarchy.</td>
</tr>
<tr class="even">
<td><em>Single Responsibility Principle</em> . You can move multiple versions of the same behavior into the same class.</td>
<td>Visitors might lack the necessary access to the private fields and methods of the elements that they’re supposed to work with.</td>
</tr>
<tr class="odd">
<td>A visitor object can accumulate some useful information while working with various objects. This might be handy when you want to traverse some complex object structure, such as an object tree, and apply the visitor to each object of this structure.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

##### C\#

<div>

Let's take an example of a zoo simulation where we have several
different kinds of animals and we have to make them Sound. Let's
translate this using visitor pattern

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

We could have done this simply by having an inheritance hierarchy for
the animals but then we would have to modify the animals whenever we
would have to add new actions to animals. But now we will not have to
change them. For example, let's say we are asked to add the jump
behavior to the animals, we can simply add that by creating a new
visitor i.e.

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
>                 
> ```

</div>

##### JavaScript

<div>

Let's take an example of a zoo simulation where we have several
different kinds of animals and we have to make them Sound. Let's
translate this using visitor pattern

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

We could have done this simply by having a inheritance hierarchy for the
animals but then we would have to modify the animals whenever we would
have to add new actions to animals. But now we will not have to change
them. For example, let's say we are asked to add the jump behavior to
the animals, we can simply add that by creating a new visitor i.e.

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

</div>

##### PHP

<div>

Let's take an example of a zoo simulation where we have several
different kinds of animals and we have to make them Sound. Let's
translate this using visitor pattern

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

We could have done this simply by having an inheritance hierarchy for
the animals but then we would have to modify the animals whenever we
would have to add new actions to animals. But now we will not have to
change them. For example, let's say we are asked to add the jump
behavior to the animals, we can simply add that by creating a new
visitor i.e.

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

</div>

##### Python

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
> An interesting recipe could be found in
> Brian Jones, David Beazley "Python Cookbook" (2013):
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

### Strategy

#### Intent

**Strategy** is a behavioral design pattern that lets you define a
family of algorithms, put each of them into a separate class, and make
their objects interchangeable.

![](attachments/463529943/463530145.png)

#### Problem

One day you decided to create a navigation app for casual travelers. The
app was centered around a beautiful map which helped users quickly
orient themselves in any city.

One of the most requested features for the app was automatic route
planning. A user should be able to enter an address and see the fastest
route to that destination displayed on the map.

The first version of the app could only build the routes over roads.
People who traveled by car were bursting with joy. But apparently, not
everybody likes to drive on their vacation. So with the next update, you
added an option to build walking routes. Right after that, you added
another option to let people use public transport in their routes.

However, that was only the beginning. Later you planned to add route
building for cyclists. And even later, another option for building
routes through all of a city’s tourist attractions.

![](attachments/463529943/463530146.png)

While from a business perspective the app was a success, the technical
part caused you many headaches. Each time you added a new routing
algorithm, the main class of the navigator doubled in size. At some
point, the beast became too hard to maintain.

Any change to one of the algorithms, whether it was a simple bug fix or
a slight adjustment of the street score, affected the whole class,
increasing the chance of creating an error in already-working code.

In addition, teamwork became inefficient. Your teammates, who had been
hired right after the successful release, complain that they spend too
much time resolving merge conflicts. Implementing a new feature requires
you to change the same huge class, conflicting with the code produced by
other people.

#### Solution

The Strategy pattern suggests that you take a class that does something
specific in a lot of different ways and extract all of these algorithms
into separate classes called *strategies*.

The original class, called *context*, must have a field for storing a
reference to one of the strategies. The context delegates the work to a
linked strategy object instead of executing it on its own.

The context isn’t responsible for selecting an appropriate algorithm for
the job. Instead, the client passes the desired strategy to the context.
In fact, the context doesn’t know much about strategies. It works with
all strategies through the same generic interface, which only exposes a
single method for triggering the algorithm encapsulated within the
selected strategy.

This way the context becomes independent of concrete strategies, so you
can add new algorithms or modify existing ones without changing the code
of the context or other strategies.

![](attachments/463529943/463530147.png)

In our navigation app, each routing algorithm can be extracted to its
own class with a single `buildRoute` method. The method accepts an
origin and destination and returns a collection of the route’s
checkpoints.

Even though given the same arguments, each routing class might build a
different route, the main navigator class doesn’t really care which
algorithm is selected since its primary job is to render a set of
checkpoints on the map. The class has a method for switching the active
routing strategy, so its clients, such as the buttons in the user
interface, can replace the currently selected routing behavior with
another one.

#### Structure

![](attachments/463529943/463530148.png)

#### Pseudocode

##### Real world example

Consider the example of sorting, we implemented bubble sort but the data
started to grow and bubble sort started getting very slow. In order to
tackle this we implemented Quick sort. But now although the quick sort
algorithm was doing better for large datasets, it was very slow for
smaller datasets. In order to handle this we implemented a strategy
where for small datasets, bubble sort will be used and for larger, quick
sort.

##### In plain words

Strategy pattern allows you to switch the algorithm or strategy based
upon the situation.

##### Wikipedia says

In computer programming, the strategy pattern (also known as the policy
pattern) is a behavioural software design pattern that enables an
algorithm's behavior to be selected at runtime.

##### Pros and Cons

<div class="table-wrap">

<table>
<thead>
<tr class="header">
<th>Pro</th>
<th>Con</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>You can swap algorithms used inside an object at runtime.</td>
<td>If you only have a couple of algorithms and they rarely change, there’s no real reason to overcomplicate the program with new classes and interfaces that come along with the pattern.</td>
</tr>
<tr class="even">
<td>You can isolate the implementation details of an algorithm from the code that uses it.</td>
<td>Clients must be aware of the differences between strategies to be able to select a proper one.</td>
</tr>
<tr class="odd">
<td>You can replace inheritance with composition.</td>
<td>A lot of modern programming languages have functional type support that lets you implement different versions of an algorithm inside a set of anonymous functions. Then you could use these functions exactly as you’d have used the strategy objects, but without bloating your code with extra classes and interfaces.</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em>. You can introduce new strategies without having to change the context.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

Translating our example from above. First of all we have our strategy
interface and different strategy implementations

##### C\#

<div>

> 
> 
> ``` 
> interface ISortStrategy
> {
>     List<int> Sort(List <int> dataset);
> }
> 
> class BubbleSortStrategy : ISortStrategy
> {
>     public List <int> Sort(List<int> dataset)
>     {
>         Console.WriteLine("Sorting using Bubble Sort !");
>         return dataset;
>     }
> }
> 
> class QuickSortStrategy : ISortStrategy
> {
>     public List <int> Sort(List<int> dataset)
>     {
>         Console.WriteLine("Sorting using Quick Sort !");
>         return dataset;
>     }
> }
>                     
> ```

And then we have our client that is going to use any strategy

> 
> 
> ``` 
> class Sorter
> {
>     private readonly ISortStrategy mSorter;
> 
>     public Sorter(ISortStrategy sorter)
>     {
>         mSorter = sorter;
>     }
> 
>     public List<int> Sort(List<int> unSortedList)
>     {
>         return mSorter.Sort(unSortedList);
>     }
> }
>                     
> ```

And it can be used as

> 
> 
> ``` 
> var unSortedList = new List<int> { 1, 10, 2, 16, 19 };
> 
> var sorter = new Sorter(new BubbleSortStrategy());
> sorter.Sort(unSortedList); // // Output : Sorting using Bubble Sort !
> 
> sorter = new Sorter(new QuickSortStrategy());
> sorter.Sort(unSortedList); // // Output : Sorting using Quick Sort !
> 
>                     
> ```

</div>

##### JavaScript

<div>

Translating our example from above, we can easily implement this
strategy in javascript using its feature of first class functions.

> 
> 
> ``` 
>  const bubbleSort = dataset => {
>     console.log('Sorting with bubble sort')
>     // ...
>     // ...
>     return dataset
> }
> 
> const quickSort = dataset => {
>     console.log('Sorting with quick sort')
>     // ...
>     // ...
>     return dataset
> }
>                     
> ```

And then we have our client that is going to use any strategy

> 
> 
> ``` 
> const sorter = dataset => {
>     if(dataset.length > 5){
>         return quickSort
>     } else {
>         return bubbleSort
>     }
> }
>                     
> ```

And it can be used as

> 
> 
> ``` 
> const longDataSet = [1, 5, 4, 3, 2, 8]
> const shortDataSet = [1, 5, 4]
> 
> const sorter1 = sorter(longDataSet)
> const sorter2 = sorter(shortDataSet)
> 
> sorter1(longDataSet) // Output : Sorting with quick sort
> sorter2(shortDataSet) // Output : Sorting with bubble sort
> 
>                     
> ```

</div>

##### PHP

<div>

> 
> 
> ``` 
> interface SortStrategy
> {
>     public function sort(array $dataset): array;
> }
> 
> class BubbleSortStrategy implements SortStrategy
> {
>     public function sort(array $dataset): array
>     {
>         echo "Sorting using bubble sort";
> 
>         // Do sorting
>         return $dataset;
>     }
> }
> 
> class QuickSortStrategy implements SortStrategy
> {
>     public function sort(array $dataset): array
>     {
>         echo "Sorting using quick sort";
> 
>         // Do sorting
>         return $dataset;
>     }
> }
> 
>                     
> ```

And then we have our client that is going to use any strategy

> 
> 
> ``` 
> class Sorter
> {
>     protected $sorter;
> 
>     public function __construct(SortStrategy $sorter)
>     {
>         $this->sorter = $sorter;
>     }
> 
>     public function sort(array $dataset): array
>     {
>         return $this->sorter->sort($dataset);
>     }
> }
>                     
> ```

And it can be used as

> 
> 
> ``` 
> $dataset = [1, 5, 4, 3, 2, 8];
> 
> $sorter = new Sorter(new BubbleSortStrategy());
> $sorter->sort($dataset); // Output : Sorting using bubble sort
> 
> $sorter = new Sorter(new QuickSortStrategy());
> $sorter->sort($dataset); // Output : Sorting using quick sort
>                     
> ```

</div>

##### Python

<div>

> 
> 
> ``` 
> #!/usr/bin/env python
> # -*- coding: utf-8 -*-
> 
> """
> *What is this pattern about?
> Define a family of algorithms, encapsulate each one, and make them interchangeable.
> Strategy lets the algorithm vary independently from clients that use it.
> 
> *TL;DR
> Enables selecting an algorithm at runtime.
> """
> 
> 
> class Order:
>     def __init__(self, price, discount_strategy=None):
>         self.price = price
>         self.discount_strategy = discount_strategy
> 
>     def price_after_discount(self):
>         if self.discount_strategy:
>             discount = self.discount_strategy(self)
>         else:
>             discount = 0
>         return self.price - discount
> 
>     def __repr__(self):
>         fmt = "<Price: {}, price after discount: {}>"
>         return fmt.format(self.price, self.price_after_discount())
> 
> def ten_percent_discount(order):
>     return order.price * 0.10
> 
> def on_sale_discount(order):
>     return order.price * 0.25 + 20
> 
> def main():
>     """
>     >>> Order(100)
>     <Price: 100, price after discount: 100>
> 
>     >>> Order(100, discount_strategy=ten_percent_discount)
>     <Price: 100, price after discount: 90.0>
> 
>     >>> Order(1000, discount_strategy=on_sale_discount)
>     <Price: 1000, price after discount: 730.0>
>     """
> 
> 
> if __name__ == "__main__":
>     import doctest
>     doctest.testmod()
>                     
> ```

### State

#### Intent

**State** is a behavioral design pattern that lets an object alter its
behavior when its internal state changes. It appears as if the object
changed its class.

![](attachments/463529945/463530136.png)

#### Problem

The State pattern is closely related to the concept of a [Finite-State
Machine](https://en.wikipedia.org/wiki/Finite-state_machine).

![](attachments/463529945/463530138.png)

The main idea is that, at any given moment, there’s a *finite* number of
*states* which a program can be in. Within any unique state, the program
behaves differently, and the program can be switched from one state to
another instantaneously. However, depending on a current state, the
program may or may not switch to certain other states. These switching
rules, called *transitions*, are also finite and predetermined.

You can also apply this approach to objects. Imagine that we have a
`Document` class. A document can be in one of three states: `Draft`,
`Moderation` and `Published`. The `publish` method of the document works
a little bit differently in each state:

  - In `Draft`, it moves the document to moderation.
  - In `Moderation`, it makes the document public, but only if the
    current user is an administrator.
  - In `Published`, it doesn’t do anything at all.

![](attachments/463529945/463530139.png)

State machines are usually implemented with lots of conditional
operators ( `if` or `switch` ) that select the appropriate behavior
depending on the current state of the object. Usually, this “state” is
just a set of values of the object’s fields. Even if you’ve never heard
about finite-state machines before, you’ve probably implemented a state
at least once. Does the following code structure ring a bell?

The biggest weakness of a state machine based on conditionals reveals
itself once we start adding more and more states and state-dependent
behaviors to the `Document` class. Most methods will contain monstrous
conditionals that pick the proper behavior of a method according to the
current state. Code like this is very difficult to maintain because any
change to the transition logic may require changing state conditionals
in every method.

The problem tends to get bigger as a project evolves. It’s quite
difficult to predict all possible states and transitions at the design
stage. Hence, a lean state machine built with a limited set of
conditionals can grow into a bloated mess over time.

#### Solution

The State pattern suggests that you create new classes for all possible
states of an object and extract all state-specific behaviors into these
classes.

Instead of implementing all behaviors on its own, the original object,
called *context*, stores a reference to one of the state objects that
represents its current state, and delegates all the state-related work
to that object.

![](attachments/463529945/463530140.png)

To transition the context into another state, replace the active state
object with another object that represents that new state. This is
possible only if all state classes follow the same interface and the
context itself works with these objects through that interface.

This structure may look similar to the
[Strategy](https://refactoring.guru/design-patterns/strategy) pattern,
but there’s one key difference. In the State pattern, the particular
states may be aware of each other and initiate transitions from one
state to another, whereas strategies almost never know about each other.

#### Structure

![](attachments/463529945/463530141.png)

#### Pseudocode

In this example, the **State** pattern lets the same controls of the
media player behave differently, depending on the current playback
state.

![](attachments/463529945/463530137.png)

The main object of the player is always linked to a state object that
performs most of the work for the player. Some actions replace the
current state object of the player with another, which changes the way
the player reacts to user interactions.

#### Real world example

Imagine you are using some drawing application, you choose the paint
brush to draw. Now the brush changes its behavior based on the selected
color i.e. if you have chosen red color it will draw in red, if blue
then it will be in blue etc.

#### In plain words

It lets you change the behavior of a class when the state changes.

#### Wikipedia says

The state pattern is a behavioral software design pattern that
implements a state machine in an object-oriented way. With the state
pattern, a state machine is implemented by implementing each individual
state as a derived class of the state pattern interface, and
implementing state transitions by invoking methods defined by the
pattern's superclass. The state pattern can be interpreted as a strategy
pattern which is able to switch the current strategy through invocations
of methods defined in the pattern's interface.

#### Pros and Cons

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
<td><em>Single Responsibility Principle</em> . Organize the code related to particular states into separate classes.</td>
<td>Applying the pattern can be overkill if a state machine has only a few states or rarely changes.</td>
</tr>
<tr class="even">
<td><em>Open/Closed Principle</em> . Introduce new states without changing existing state classes or the context.</td>
<td><br />
</td>
</tr>
<tr class="odd">
<td>Simplify the code of the context by eliminating bulky state machine conditionals.</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

#### Programmatic Example

##### C\#

<div>

Let's take an example of text editor, it lets you change the state of
text that is typed i.e. if you have selected bold, it starts writing in
bold, if italic then in italics etc.

First of all we have our state interface and some state implementations

> 
> 
> ``` 
> interface IWritingState {
>     void Write(string words);
> }
> 
> class UpperCase : IWritingState
> {
>     public void Write(string words)
>     {
>         Console.WriteLine(words.ToUpper());
>     }
> }
> 
> class LowerCase : IWritingState
> {
>     public void Write(string words)
>     {
>         Console.WriteLine(words.ToLower());
>     }
> }
> 
> class DefaultText : IWritingState
> {
>     public void Write(string words)
>     {
>         Console.WriteLine(words);
>     }
> }
>                     
> ```

Then we have our editor

> 
> 
> ``` 
> class TextEditor {
>     private IWritingState mState;
> 
>     public TextEditor()
>     {
>         mState = new DefaultText();
>     }
> 
>     public void SetState(IWritingState state)
>     {
>         mState = state;
>     }
> 
>     public void Type(string words)
>     {
>         mState.Write(words);
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
> var editor = new TextEditor();
> 
> editor.Type("First line");
> 
> editor.SetState(new UpperCase());
> 
> editor.Type("Second Line");
> editor.Type("Third Line");
> 
> editor.SetState(new LowerCase());
> 
> editor.Type("Fourth Line");
> editor.Type("Fifthe Line");
> 
> // Output:
> // First line
> // SECOND LINE
> // THIRD LINE
> // fourth line
> // fifth line
> 
>                     
> ```

</div>

#### JavaScript

<div>

Let's take an example of text editor, it let's you change the state of
text that is typed i.e. if you have selected bold, it starts writing in
bold, if italic then in italics etc.

First of all we have our transformation functions

> 
> 
> ``` 
> const upperCase = inputString => inputString.toUpperCase()
> const lowerCase = inputString => inputString.toLowerCase()
> const defaultTransform = inputString => inputString
>                     
> ```

Then we have our editor

> 
> 
> ``` 
> class TextEditor {
>     constructor(transform) {
>         this._transform = transform
>     }
>     
>     setTransform(transform) {
>         this._transform = transform
>     }
>     
>     type(words) {
>         console.log(this._transform(words))
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
>  const editor = new TextEditor(defaultTransform)
> 
> editor.type('First line')
> 
> editor.setTransform(upperCase)
> 
> editor.type('Second line')
> editor.type('Third line')
> 
> editor.setTransform(lowerCase)
> 
> editor.type('Fourth line')
> editor.type('Fifth line')
> 
> // Output:
> // First line
> // SECOND LINE
> // THIRD LINE
> // fourth line
> // fifth line
>                     
> ```

</div>

##### PHP

<div>

Let's take an example of text editor, it lets you change the state of
text that is typed i.e. if you have selected bold, it starts writing in
bold, if italic then in italics etc.

First of all we have our state interface and some state implementations

> 
> 
> ``` 
> interface WritingState
> {
>     public function write(string $words);
> }
> 
> class UpperCase implements WritingState
> {
>     public function write(string $words)
>     {
>         echo strtoupper($words);
>     }
> }
> 
> class LowerCase implements WritingState
> {
>     public function write(string $words)
>     {
>         echo strtolower($words);
>     }
> }
> 
> class DefaultText implements WritingState
> {
>     public function write(string $words)
>     {
>         echo $words;
>     }
> }
>                     
> ```

Then we have our editor

> 
> 
> ``` 
> class TextEditor
> {
>     protected $state;
> 
>     public function __construct(WritingState $state)
>     {
>         $this->state = $state;
>     }
> 
>     public function setState(WritingState $state)
>     {
>         $this->state = $state;
>     }
> 
>     public function type(string $words)
>     {
>         $this->state->write($words);
>     }
> }
>                     
> ```

And then it can be used as

> 
> 
> ``` 
> $editor = new TextEditor(new DefaultText());
> 
> $editor->type('First line');
> 
> $editor->setState(new UpperCase());
> 
> $editor->type('Second line');
> $editor->type('Third line');
> 
> $editor->setState(new LowerCase());
> 
> $editor->type('Fourth line');
> $editor->type('Fifth line');
> 
> // Output:
> // First line
> // SECOND LINE
> // THIRD LINE
> // fourth line
> // fifth line                                                                           
>                     
> ```

##### Python

<div>

> 
> 
> ``` 
> #!/usr/bin/env python
> # -*- coding: utf-8 -*-
> 
> """
> Implementation of the state pattern
> 
> http://ginstrom.com/scribbles/2007/10/08/design-patterns-python-style/
> 
> *TL;DR
> Implements state as a derived class of the state pattern interface.
> Implements state transitions by invoking methods from the pattern's superclass.
> """
> 
> from __future__ import print_function
> 
> 
> class State(object):
> 
>     """Base state. This is to share functionality"""
> 
>     def scan(self):
>         """Scan the dial to the next station"""
>         self.pos += 1
>         if self.pos == len(self.stations):
>             self.pos = 0
>         print(u"Scanning... Station is %s %s" % (self.stations[self.pos], self.name))
> 
> 
> class AmState(State):
>     def __init__(self, radio):
>         self.radio = radio
>         self.stations = ["1250", "1380", "1510"]
>         self.pos = 0
>         self.name = "AM"
> 
>     def toggle_amfm(self):
>         print(u"Switching to FM")
>         self.radio.state = self.radio.fmstate
> 
> 
> class FmState(State):
>     def __init__(self, radio):
>         self.radio = radio
>         self.stations = ["81.3", "89.1", "103.9"]
>         self.pos = 0
>         self.name = "FM"
> 
>     def toggle_amfm(self):
>         print(u"Switching to AM")
>         self.radio.state = self.radio.amstate
> 
> 
> class Radio(object):
> 
>     """A radio.     It has a scan button, and an AM/FM toggle switch."""
> 
>     def __init__(self):
>         """We have an AM state and an FM state"""
>         self.amstate = AmState(self)
>         self.fmstate = FmState(self)
>         self.state = self.amstate
> 
>     def toggle_amfm(self):
>         self.state.toggle_amfm()
> 
>     def scan(self):
>         self.state.scan()
> 
> 
> # Test our radio out
> def main():
>     radio = Radio()
>     actions = [radio.scan] * 2 + [radio.toggle_amfm] + [radio.scan] * 2
>     actions *= 2
> 
>     for action in actions:
>         action()
> 
> 
> if __name__ == '__main__':
>     main()
> 
> 
> OUTPUT = """
> Scanning... Station is 1380 AM
> Scanning... Station is 1510 AM
> Switching to FM
> Scanning... Station is 89.1 FM
> Scanning... Station is 103.9 FM
> Scanning... Station is 81.3 FM
> Scanning... Station is 89.1 FM
> Switching to AM
> Scanning... Station is 1250 AM
> Scanning... Station is 1380 AM
> """
>                         
> ```

### Template Method

#### Intent

**Template Method** is a behavioral design pattern that defines the
skeleton of an algorithm in the superclass but lets subclasses override
specific steps of the algorithm without changing its structure.

![](attachments/463529947/463530151.png)

#### Problem

Imagine that you’re creating a data mining application that analyzes
corporate documents. Users feed the app documents in various formats
(PDF, DOC, CSV), and it tries to extract meaningful data from these docs
in a uniform format.

The first version of the app could work only with DOC files. In the
following version, it was able to support CSV files. A month later, you
“taught” it to extract data from PDF files.

![](attachments/463529947/463530153.png)

At some point, you noticed that all three classes have a lot of similar
code. While the code for dealing with various data formats was entirely
different in all classes, the code for data processing and analysis is
almost identical. Wouldn’t it be great to get rid of the code
duplication, leaving the algorithm structure intact?

There was another problem related to client code that used these
classes. It had lots of conditionals that picked a proper course of
action depending on the class of the processing object. If all three
processing classes had a common interface or a base class, you’d be able
to eliminate the conditionals in client code and use polymorphism when
calling methods on a processing object.

#### Solution

The Template Method pattern suggests that you break down an algorithm
into a series of steps, turn these steps into methods, and put a series
of calls to these methods inside a single “template method.” The steps
may either be `abstract`, or have some default implementation. To use
the algorithm, the client is supposed to provide its own subclass,
implement all abstract steps, and override some of the optional ones if
needed (but not the template method itself).

Let’s see how this will play out in our data mining app. We can create a
base class for all three parsing algorithms. This class defines a
template method consisting of a series of calls to various
document-processing steps.

![](attachments/463529947/463530154.png)

At first, we can declare all steps `abstract`, forcing the subclasses to
provide their own implementations for these methods. In our case,
subclasses already have all necessary implementations, so the only thing
we might need to do is adjust signatures of the methods to match the
methods of the superclass.

Now, let’s see what we can do to get rid of the duplicate code. It looks
like the code for opening/closing files and extracting/parsing data is
different for various data formats, so there’s no point in touching
those methods. However, implementation of other steps, such as analyzing
the raw data and composing reports, is very similar, so it can be pulled
up into the base class, where subclasses can share that code.

As you can see, we’ve got two types of steps:

  - *abstract steps* must be implemented by every subclass
  - *optional steps* already have some default implementation, but still
    can be overridden if needed

There’s another type of step, called *hooks*. A hook is an optional step
with an empty body. A template method would work even if a hook isn’t
overridden. Usually, hooks are placed before and after crucial steps of
algorithms, providing subclasses with additional extension points for an
algorithm.

The template method approach can be used in mass housing construction.
The architectural plan for building a standard house may contain several
extension points that would let a potential owner adjust some details of
the resulting house.

Each building step, such as laying the foundation, framing, building
walls, installing plumbing and wiring for water and electricity, etc.,
can be slightly changed to make the resulting house a little bit
different from others.

#### Structure

![](attachments/463529947/463530155.png)

#### Pseudocode

In this example, the **Template Method** pattern provides a “skeleton”
for various branches of artificial intelligence in a simple strategy
video game.

![](attachments/463529947/463530152.png)

#### Real world example

Suppose we are getting some house built. The steps for building might
look like

  - Prepare the base of house
  - Build the walls
  - Add roof
  - Add other floors

The order of these steps could never be changed i.e. you can't build the
roof before building the walls etc but each of the steps could be
modified for example walls can be made of wood or polyester or stone.

#### In plain words

Template method defines the skeleton of how a certain algorithm could be
performed, but defers the implementation of those steps to the children
classes.

#### Wikipedia says

In software engineering, the template method pattern is a behavioral
design pattern that defines the program skeleton of an algorithm in an
operation, deferring some steps to subclasses. It lets one redefine
certain steps of an algorithm without changing the algorithm's
structure.

#### Pros and Cons

<div class="table-wrap">

| Pros                                                                                                                                                    | Cons                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| You can let clients override only certain parts of a large algorithm, making them less affected by changes that happen to other parts of the algorithm. | Some clients may be limited by the provided skeleton of an algorithm.                                              |
| You can pull the duplicate code into a superclass.                                                                                                      | You might violate the *Liskov Substitution Principle* by suppressing a default step implementation via a subclass. |
|                                                                                                                                                         | Template methods tend to be harder to maintain the more steps they have.                                           |

</div>

##### Programmatic Example

##### C\#

<div>

Imagine we have a build tool that helps us test, lint, build, generate
build reports (i.e. code coverage reports, linting report etc) and
deploy our app on the test server.

First of all we have our base class that specifies the skeleton for the
build algorithm

> 
> 
> ``` 
> abstract class Builder
> {
>     // Template method
>     public void Build()
>     {
>         Test();
>         Lint();
>         Assemble();
>         Deploy();
>     }
> 
>     abstract public void Test();
>     abstract public void Lint();
>     abstract public void Assemble();
>     abstract public void Deploy();
> }
>                         
> ```

Then we can have our implementations

> 
> 
> ``` 
> class AndroidBuilder : Builder
> {
>     public override void Assemble()
>     {
>         Console.WriteLine("Assembling the android build");
>     }
> 
>     public override void Deploy()
>     {
>         Console.WriteLine("Deploying android build to server");
>     }
> 
>     public override void Lint()
>     {
>         Console.WriteLine("Linting the android code");
>     }
> 
>     public override void Test()
>     {
>         Console.WriteLine("Running android tests");
>     }
> }
> 
> class IosBuilder : Builder
> {
>     public override void Assemble()
>     {
>         Console.WriteLine("Assembling the ios build");
>     }
> 
>     public override void Deploy()
>     {
>         Console.WriteLine("Deploying ios build to server");
>     }
> 
>     public override void Lint()
>     {
>         Console.WriteLine("Linting the ios code");
>     }
> 
>     public override void Test()
>     {
>         Console.WriteLine("Running ios tests");
>     }
> }
>                         
> ```

And then it can be used as

> 
> 
> ``` 
> var androidBuilder = new AndroidBuilder();
> androidBuilder.Build();
> 
> // Output:
> // Running android tests
> // Linting the android code
> // Assembling the android build
> // Deploying android build to server
> 
> var iosBuilder = new IosBuilder();
> iosBuilder.Build();
> 
> // Output:
> // Running ios tests
> // Linting the ios code
> // Assembling the ios build
> // Deploying ios build to server
>                         
> ```

</div>

##### JavaScript

<div>

Imagine we have a build tool that helps us test, lint, build, generate
build reports (i.e. code coverage reports, linting report etc) and
deploy our app on the test server.

First of all we have our base class that specifies the skeleton for the
build algorithm

> 
> 
> ``` 
> class Builder {
>     // Template method 
>     build() {
>         this.test()
>         this.lint()
>         this.assemble()
>         this.deploy()
>     }
> }
> 
>                         
> ```

Then we can have our implementations

> 
> 
> ``` 
> class AndroidBuilder extends Builder {
>     test() {
>         console.log('Running android tests')
>     }
>     
>     lint() {
>         console.log('Linting the android code')
>     }
>     
>     assemble() {
>         console.log('Assembling the android build')
>     }
>     
>     deploy() {
>         console.log('Deploying android build to server')
>     }
> }
> 
> class IosBuilder extends Builder {
>     test() {
>         console.log('Running ios tests')
>     }
>     
>     lint() {
>         console.log('Linting the ios code')
>     }
>     
>     assemble() {
>         console.log('Assembling the ios build')
>     }
>     
>     deploy() {
>         console.log('Deploying ios build to server')
>     }
> }
>                         
> ```

And then it can be used as

> 
> 
> ``` 
> const androidBuilder = new AndroidBuilder()
> androidBuilder.build()
> 
> // Output:
> // Running android tests
> // Linting the android code
> // Assembling the android build
> // Deploying android build to server
> 
> const iosBuilder = new IosBuilder()
> iosBuilder.build()
> 
> // Output:
> // Running ios tests
> // Linting the ios code
> // Assembling the ios build
> // Deploying ios build to server
> 
>                         
> ```

</div>

##### Python

<div>

> 
> 
> ``` 
> #!/usr/bin/env python
> # -*- coding: utf-8 -*-
> 
> """
> An example of the Template pattern in Python
> 
> *TL;DR
> Defines the skeleton of a base algorithm, deferring definition of exact
> steps to subclasses.
> 
> *Examples in Python ecosystem:
> Django class based views: https://docs.djangoproject.com/en/2.1/topics/class-based-views/
> """
> 
> 
> def get_text():
>     return "plain-text"
> 
> 
> def get_pdf():
>     return "pdf"
> 
> 
> def get_csv():
>     return "csv"
> 
> 
> def convert_to_text(data):
>     print("[CONVERT]")
>     return "{} as text".format(data)
> 
> 
> def saver():
>     print("[SAVE]")
> 
> 
> def template_function(getter, converter=False, to_save=False):
>     data = getter()
>     print("Got `{}`".format(data))
> 
>     if len(data) <= 3 and converter:
>         data = converter(data)
>     else:
>         print("Skip conversion")
> 
>     if to_save:
>         saver()
> 
>     print("`{}` was processed".format(data))
> 
> 
> def main():
>     """
>     >>> template_function(get_text, to_save=True)
>     Got `plain-text`
>     Skip conversion
>     [SAVE]
>     `plain-text` was processed
> 
>     >>> template_function(get_pdf, converter=convert_to_text)
>     Got `pdf`
>     [CONVERT]
>     `pdf as text` was processed
> 
>     >>> template_function(get_csv, to_save=True)
>     Got `csv`
>     Skip conversion
>     [SAVE]
>     `csv` was processed
>     """
> 
> 
> if __name__ == "__main__":
>     import doctest
>     doctest.testmod()
> 
>                         
> ```

</div>

</div>

<div id="footer" role="contentinfo">

<div class="section footer-body">

Document generated by Confluence on May 21, 2020 14:36

<div id="footer-logo">

[Atlassian](http://www.atlassian.com/)

</div>

</div>

</div>

</div>

</div>

</div>
