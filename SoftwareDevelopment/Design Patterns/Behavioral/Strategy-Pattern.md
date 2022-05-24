###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------

# Information Technology : Strategy Pattern



## Strategy

### Intent

**Strategy** is a behavioral design pattern that lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable.

<img src"./attachments/strategy/463530145.png" />

### Problem

One day you decided to create a navigation app for casual travelers. The app was centered around a beautiful map which helped users quickly orient themselves in any city.

One of the most requested features for the app was automatic route planning. A user should be able to enter an address and see the fastest route to that destination displayed on the map.

The first version of the app could only build the routes over roads. People who traveled by car were bursting with joy. But apparently, not everybody likes to drive on their vacation. So with the next update, you added an option to build walking routes. Right after that, you added another option to let people use public transport in their routes.

However, that was only the beginning. Later you planned to add route building for cyclists. And even later, another option for building routes through all of a city’s tourist attractions.

<img src"./attachments/strategy/463530146.png" />

While from a business perspective the app was a success, the technical part caused you many headaches. Each time you added a new routing algorithm, the main class of the navigator doubled in size. At some point, the beast became too hard to maintain.

Any change to one of the algorithms, whether it was a simple bug fix or a slight adjustment of the street score, affected the whole class, increasing the chance of creating an error in already-working code.

In addition, teamwork became inefficient. Your teammates, who had been hired right after the successful release, complain that they spend too much time resolving merge conflicts. Implementing a new feature requires you to change the same huge class, conflicting with the code produced by other people.

### Solution

The Strategy pattern suggests that you take a class that does something specific in a lot of different ways and extract all of these algorithms into separate classes called *strategies*.

The original class, called *context*, must have a field for storing a reference to one of the strategies. The context delegates the work to a linked strategy object instead of executing it on its own.

The context isn’t responsible for selecting an appropriate algorithm for the job. Instead, the client passes the desired strategy to the context. In fact, the context doesn’t know much about strategies. It works with all strategies through the same generic interface, which only exposes a single method for triggering the algorithm encapsulated within the selected strategy.

This way the context becomes independent of concrete strategies, so you can add new algorithms or modify existing ones without changing the code of the context or other strategies.

<img src"./attachments/strategy/463530147.png" />

In our navigation app, each routing algorithm can be extracted to its own class with a single `buildRoute` method. The method accepts an origin and destination and returns a collection of the route’s checkpoints.

Even though given the same arguments, each routing class might build a different route, the main navigator class doesn’t really care which algorithm is selected since its primary job is to render a set of checkpoints on the map. The class has a method for switching the active routing strategy, so its clients, such as the buttons in the user interface, can replace the currently selected routing behavior with another one.

### Structure

<img src"./attachments/strategy/463530148.png" />

### Pseudocode

#### Real world example

Consider the example of sorting, we implemented bubble sort but the data started to grow and bubble sort started getting very slow. In order to tackle this we implemented Quick sort. But now although the quick sort algorithm was doing better for large datasets, it was very slow for smaller datasets. In order to handle this we implemented a strategy where for small datasets, bubble sort will be used and for larger, quick sort.

#### In plain words

Strategy pattern allows you to switch the algorithm or strategy based upon the situation.

#### Wikipedia says

In computer programming, the strategy pattern (also known as the policy pattern) is a behavioural software design pattern that enables an algorithm's behavior to be selected at runtime.

#### Pros and Cons



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
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

Translating our example from above. First of all we have our strategy interface and different strategy implementations

#### C\#



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



#### JavaScript



Translating our example from above, we can easily implement this strategy in javascript using its feature of first class functions.

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



#### PHP



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



#### Python



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


