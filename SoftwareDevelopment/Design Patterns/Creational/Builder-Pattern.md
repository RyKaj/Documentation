###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------


# Information Technology : Builder Pattern

## Builder

<kbd>![](https://www.oodesign.com/images/creational/builder-pattern.png)</kbd>

### Intent

**Builder** is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.

<img src"./attachments/builder/463530184.png" />

### Problem

Imagine a complex object that requires laborious, step-by-step initialization of many fields and nested objects. Such initialization code is usually buried inside a monstrous constructor with lots of parameters. Or even worse: scattered all over the client code.

<img src"./attachments/builder/463530188.png" />

For example, let’s think about how to create a `House` object. To build a simple house, you need to construct four walls and a floor, install a door, fit a pair of windows, and build a roof. But what if you want a bigger, brighter house, with a backyard and other goodies (like a heating system, plumbing, and electrical wiring)?

The simplest solution is to extend the base `House` class and create a set of subclasses to cover all combinations of the parameters. But eventually you’ll end up with a considerable number of subclasses. Any new parameter, such as the porch style, will require growing this hierarchy even more.

There’s another approach that doesn’t involve breeding subclasses. You can create a giant constructor right in the base `House` class with all possible parameters that control the house object. While this approach indeed eliminates the need for subclasses, it creates another problem.

<img src"./attachments/builder/463530189.png" />

In most cases most of the parameters will be unused, making [the constructor calls pretty ugly](https://refactoring.guru/smells/long-parameter-list) . For instance, only a fraction of houses have swimming pools, so the parameters related to swimming pools will be useless nine times out of ten.

### Solution

The Builder pattern suggests that you extract the object construction code out of its own class and move it to separate objects called *builders*.

<img src"./attachments/builder/463530190.png" />

The pattern organizes object construction into a set of steps ( `buildWalls`, `buildDoor`, etc.). To create an object, you execute a series of these steps on a builder object. The important part is that you don’t need to call all of the steps. You can call only those steps that are necessary for producing a particular configuration of an object.

Some of the construction steps might require different implementation when you need to build various representations of the product. For example, walls of a cabin may be built of wood, but the castle walls must be built with stone.

In this case, you can create several different builder classes that implement the same set of building steps, but in a different manner. Then you can use these builders in the construction process (i.e., an  ordered set of calls to the building steps) to produce different kinds of objects.

<img src"./attachments/builder/463530185.png" />

For example, imagine a builder that builds everything from wood and glass, a second one that builds everything with stone and iron and a third one that uses gold and diamonds. By calling the same set of steps, you get a regular house from the first builder, a small castle from the second and a palace from the third. However, this would only work if the client code that calls the building steps is able to interact with builders using a common interface.

### Director

You can go further and extract a series of calls to the builder steps you use to construct a product into a separate class called *director*. The director class defines the order in which to execute the building steps, while the builder provides the implementation for those steps.

<img src"./attachments/builder/463530186.png" />

Having a director class in your program isn’t strictly necessary. You can always call the building steps in a specific order directly from the client code. However, the director class might be a good place to put various construction routines so you can reuse them across your program.

In addition, the director class completely hides the details of product construction from the client code. The client only needs to associate a builder with a director, launch the construction with the director, and get the result from the builder.

### Structure

<img src"./attachments/builder/463530191.png" />

### Pseudocode

This example of the **Builder** pattern illustrates how you can reuse the same object construction code when building different types of products, such as cars, and create the corresponding manuals for them.

<img src"./attachments/builder/463530187.png" />

A car is a complex object that can be constructed in a hundred different ways. Instead of bloating the `Car` class with a huge constructor, we extracted the car assembly code into a separate car builder class. This class has a set of methods for configuring various parts of a car.

If the client code needs to assemble a special, fine-tuned model of a car, it can work with the builder directly. On the other hand, the client can delegate the assembly to the director class, which knows how to use a builder to construct several of the most popular models of cars.

You might be shocked, but every car needs a manual (seriously, who reads them?). The manual describes every feature of the car, so the details in the manuals vary across the different models. That’s why it makes sense to reuse an existing construction process for both real cars and their respective manuals. Of course, building a manual isn’t the same as building a car, and that’s why we must provide another builder class that specializes in composing manuals. This class implements the same building methods as its car-building sibling, but instead of crafting car parts, it describes them. By passing these builders to the same director object, we can construct either a car or a manual.

The final part is fetching the resulting object. A metal car and a paper manual, although related, are still very different things. We can’t place a method for fetching results in the director without coupling the director to concrete product classes. Hence, we obtain the result of the construction from the builder which performed the job.

### Real world example

Imagine you are at Hardee's and you order a specific deal, lets say, "Big Hardee" and they hand it over to you without *any questions*; this is the example of simple factory. But there are cases when the creation  logic might involve more steps. For example you want a customized Subway deal, you have several options in how your burger is made e.g what bread do you want? what types of sauces would you like? What cheese would you want? etc. In such cases builder pattern comes to the rescue.

### In plain words

Allows you to create different flavors of an object while avoiding constructor pollution. Useful when there could be several flavors of an object. Or when there are a lot of steps involved in creation of an object.

### Wikipedia says

The builder pattern is an object creation software design pattern with the intentions of finding a solution to the telescoping constructor anti-pattern.

Having said that let me add a bit about what telescoping constructor anti-pattern is. At one point or the other we have all seen a constructor like below:

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



As you can see; the number of constructor parameters can quickly get out of hand and it might become difficult to understand the arrangement of parameters. Plus this parameter list could keep on growing if you would want to add more options in future. This is called telescoping constructor anti-pattern.

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

The sane alternative is to use the builder pattern. First of all we have our burger that we want to make

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
It decouples the creation of a complex object and its representation, so that the same process can be reused to build objects from the same family.
This is useful when you must separate the specification of an object from its actual representation (generally for abstraction).

*What does this example do?

The first example achieves this by using an abstract base class for a building, where the initializer (__init__ method) specifies the steps needed, and the concrete subclasses implement these steps.

In other programming languages, a more complex arrangement is sometimes necessary. In particular, you cannot have polymorphic behaviour in a constructor in C++ -
see https://stackoverflow.com/questions/1453131/how-can-i-get-polymorphic-behavior-in-a-c-constructor
- which means this Python technique will not work. The polymorphism required has to be provided by an external, already constructed instance of a different class.

In general, in Python this won't be necessary, but a second example showing this kind of arrangement is also included.

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

When there could be several flavors of an object and to avoid the constructor telescoping. The key difference from the factory pattern is that; factory pattern is to be used when the creation is a one step process while builder pattern is to be used when the creation is a multi step process.


