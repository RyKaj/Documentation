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



# Information Technology : Simple Factory Pattern

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












