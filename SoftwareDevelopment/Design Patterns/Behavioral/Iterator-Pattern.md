<div id="main" class="aui-page-panel">

<div id="main-header">

<div id="breadcrumb-section">

1.  [Information Technology](index.html)
2.  [3.0 Sofware Development
    Lifecycle](3.0-Sofware-Development-Lifecycle_380470491.html)
3.  [Design Patterns](Design-Patterns_451820045.html)
4.  [1.0 Design Pattern - Programming
    Language](1.0-Design-Pattern---Programming-Language_451820065.html)
5.  [Behavioral Design
    Patterns](Behavioral-Design-Patterns_451820124.html)



# Information Technology : Iterator Pattern


## Iterator

### Intent

Iterator is a behavioral design pattern that lets you traverse elements
of a collection without exposing its underlying representation (list,
stack, tree, etc.).

<kbd>![](attachments/463529918/463529912.png)</kbd>

### Problem

Collections are one of the most used data types in programming.
Nonetheless, a collection is just a container for a group of objects.

<kbd>![](attachments/463529918/463529913.png)</kbd>

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

<kbd>![](attachments/463529918/463529914.png)</kbd>

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

### Solution

The main idea of the Iterator pattern is to extract the traversal
behavior of a collection into a separate object called an *iterator*.

<kbd>![](attachments/463529918/463529915.png)</kbd>

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

### Structure

<kbd>![](attachments/463529918/463529916.png)</kbd>

### Pseudocode

<kbd>![](attachments/463529918/463529917.png)</kbd>

### Real world Example

An old radio set will be a good example of iterator, where user could
start at some channel and then use next or previous buttons to go
through the respective channels. Or take an example of MP3 player or a
TV set where you could press the next and previous buttons to go through
the consecutive channels or in other words they all provide an interface
to iterate through the respective channels, songs or radio stations.

### In plain words

It presents a way to access the elements of an object without exposing
the underlying presentation.

### Wikipedia says

In object-oriented programming, the iterator pattern is a design pattern
in which an iterator is used to traverse a container and access the
container's elements. The iterator pattern decouples algorithms from
containers; in some cases, algorithms are necessarily container-specific
and thus cannot be decoupled.

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
            <td><em>Single Responsibility Principle</em>. You can clean up the client code and the collections by extracting bulky traversal algorithms into separate classes.</td>
            <td>Applying the pattern can be an overkill if your app only works with simple collections.</td>
        </tr>
        <tr class="even">
            <td><em>Open/Closed Principle</em>. You can implement new types of collections and iterators and pass them to existing code without breaking anything.</td>
            <td>Using an iterator may be less efficient than going through elements of some specialized collections directly.</td>
        </tr>
        <tr class="odd">
            <td>You can iterate over the same collection in parallel because each iterator object contains its own iteration state.</td>
            <td><br /></td>
        </tr>
        <tr class="even">
            <td>For the same reason, you can delay an iteration and continue it when needed.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

#### C\#



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



#### JavaScript



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



#### PHP



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



#### Python



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

