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

# Information Technology : Flyweight Pattern

</div>

<div id="content" class="view">

## Flyweight

![](https://www.oodesign.com/images/structural/flyweight-pattern.png)

### Intent

**Flyweight** is a structural design pattern that lets you fit more
objects into the available amount of RAM by sharing common parts of
state between multiple objects instead of keeping all of the data in
each object.

![](attachments/463530018/463530215.png)

### Problem

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

### Solution

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

### Extrinsic state storage

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

### Flyweight and immutability

Since the same flyweight object can be used in different contexts, you
have to make sure that its state can’t be modified. A flyweight should
initialize its state just once, via constructor parameters. It shouldn’t
expose any setters or public fields to other objects.

### Flyweight factory

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

### Structure

![](attachments/463530018/463530221.png)

### Pseudocode

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

### Real world example

Did you ever have fresh tea from some stall? They often make more than
one cup that you demanded and save the rest for any other customer so to
save the resources e.g. gas etc. Flyweight pattern is all about that
i.e. sharing.

### In plain words

It is used to minimize memory usage or computational expenses by sharing
as much as possible with similar objects.

### Wikipedia says

In computer programming, flyweight is a software design pattern. A
flyweight is an object that minimizes memory use by sharing as much data
as possible with other similar objects; it is a way to use objects in
large numbers when a simple repeated representation would use an
unacceptable amount of memory.

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

### Programmatic example

Translating our tea example from above. First of all we have tea types
and tea maker

#### C\#

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

#### Java

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

#### JavaScript

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

#### PHP

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

#### Python

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

</div>

</div>

<div id="footer" role="contentinfo">

<div class="section footer-body">

</div>

</div>
