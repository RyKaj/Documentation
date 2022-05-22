###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------

# Information Technology : Command Pattern


## Command

### Intent

**Command** is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. This transformation lets you parameterize methods with different requests, delay or queue a request’s execution, and support undoable operations.

<img src"./attachments/command/463529901.png" />

### Problem

Imagine that you’re working on a new text-editor app. Your current task is to create a toolbar with a bunch of buttons for various operations of the editor. You created a very neat `Button` class that can be used for buttons on the toolbar, as well as for generic buttons in various dialogs.

<img src"./attachments/command/463529902.png" />

While all of these buttons look similar, they’re all supposed to do different things. Where would you put the code for the various click handlers of these buttons? The simplest solution is to create tons of subclasses for each place where the button is used. These subclasses would contain the code that would have to be executed on a button click.

<img src"./attachments/command/463529903.png" />

Before long, you realize that this approach is deeply flawed. First, you have an enormous number of subclasses, and that would be okay if you weren’t risking breaking the code in these subclasses each time you modify the base `Button` class. Put simply, your GUI code has become awkwardly dependent on the volatile code of the business logic.

<img src"./attachments/command/463529904.png" />

And here’s the ugliest part. Some operations, such as copying/pasting text, would need to be invoked from multiple places. For example, a user could click a small “Copy” button on the toolbar, or copy something via the context menu, or just hit `Ctrl+C` on the keyboard.

Initially, when our app only had the toolbar, it was okay to place the implementation of various operations into the button subclasses. In other words, having the code for copying text inside the `CopyButton` subclass was fine. But then, when you implement context menus, shortcuts, and other stuff, you have to either duplicate the operation’s code in many classes or make menus dependent on buttons, which is an even worse option.

### Solution

Good software design is often based on the principle of separation of concerns, which usually results in breaking an app into layers. The most common example: a layer for the graphical user interface and another layer for the business logic. The GUI layer is responsible for rendering a beautiful picture on the screen, capturing any input and showing results of what the user and the app are doing. However, when it comes to doing something important, like calculating the trajectory of the moon or composing an annual report, the GUI layer delegates the work to the underlying layer of business logic.

In the code it might look like this: a GUI object calls a method of a business logic object, passing it some arguments. This process is usually described as one object sending another a *request*.

<img src"./attachments/command/463529905.png" />

The Command pattern suggests that GUI objects shouldn’t send these requests directly. Instead, you should extract all of the request details, such as the object being called, the name of the method and the list of arguments into a separate *command* class with a single method that triggers this request.

Command objects serve as links between various GUI and business logic objects. From now on, the GUI object doesn’t need to know what business logic object will receive the request and how it’ll be processed. The GUI object just triggers the command, which handles all the details.

<img src"./attachments/command/463529906.png" />

The next step is to make your commands implement the same interface. Usually it has just a single execution method that takes no parameters. This interface lets you use various commands with the same request sender, without coupling it to concrete classes of commands. As a bonus, now you can switch command objects linked to the sender, effectively changing the sender’s behavior at runtime.

You might have noticed one missing piece of the puzzle, which is the request parameters. A GUI object might have supplied the business-layer object with some parameters. Since the command execution method doesn’t have any parameters, how would we pass the request details to the receiver? It turns out the command should be either pre-configured with this data, or capable of getting it on its own.

<img src"./attachments/command/463529907.png" />

Let’s get back to our text editor. After we apply the Command pattern, we no longer need all those button subclasses to implement various click behaviors. It’s enough to put a single field into the base `Button` class that stores a reference to a command object and make the button execute that command on a click.

You’ll implement a bunch of command classes for every possible operation and link them with particular buttons, depending on the buttons’ intended behavior.

Other GUI elements, such as menus, shortcuts or entire dialogs, can be implemented in the same way. They’ll be linked to a command which gets executed when a user interacts with the GUI element. As you’ve probably guessed by now, the elements related to the same operations will be linked to the same commands, preventing any code duplication.

As a result, commands become a convenient middle layer that reduces coupling between the GUI and business logic layers. And that’s only a fraction of the benefits that the Command pattern can offer\!

### Structure

<img src"./attachments/command/463529908.png" />

### Pseudocode

<img src"./attachments/command/463529909.png" />

### Real world example

A generic example would be you ordering food at a restaurant. You (i.e. `Client`) ask the waiter (i.e. `Invoker`) to bring some food (i.e. `Command`) and waiter simply forwards the request to Chef (i.e. `Receiver`) who has the knowledge of what and how to cook. Another example would be you (i.e. `Client`) switching on (i.e. `Command`) the television (i.e. `Receiver`) using a remote control ( `Invoker`).

### In plain words

Allows you to encapsulate actions in objects. The key idea behind this pattern is to provide the means to decouple client from receiver.

### Wikipedia says

In object-oriented programming, the command pattern is a behavioral design pattern in which an object is used to encapsulate all information needed to perform an action or trigger an event at a later time. This information includes the method name, the object that owns the method and values for the method parameters.

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
            <td><em>Single Responsibility Principle</em>. You can decouple classes that invoke operations from classes that perform these operations.</td>
            <td>The code may become more complicated since you’re introducing a whole new layer between senders and receivers.</td>
        </tr>
        <tr class="even">
            <td><em>Open/Closed Principle</em>. You can introduce new commands into the app without breaking existing client code.</td>
            <td><br /></td>
        </tr>
        <tr class="odd">
            <td>You can implement undo/redo.</td>
            <td><br /></td>
        </tr>
        <tr class="even">
            <td>You can implement deferred execution of operations.</td>
            <td><br /></td>
        </tr>
        <tr class="odd">
            <td>You can assemble a set of simple commands into a complex one.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

#### C\#



First of all we have the receiver that has the implementation of every action that could be performed

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

then we have an interface that each of the commands are going to implement and then we have a set of commands

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

Then we have an `Invoker` with whom the client will interact to process any commands

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

Command pattern can also be used to implement a transaction based system. Where you keep maintaining the history of commands as soon as you execute them. If the final command is successfully executed, all good otherwise just iterate through the history and keep executing the `undo` on all the executed commands.



#### JavaScript



First of all we have the receiver that has the implementation of every action that could be performed

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

then we have an interface that each of the commands are going to implement and then we have a set of commands

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

Then we have an `Invoker` with whom the client will interact to process any commands

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



#### PHP



First of all we have the receiver that has the implementation of every action that could be performed

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

then we have an interface that each of the commands are going to implement and then we have a set of commands

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

Then we have an `Invoker` with whom the client will interact to process any commands

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

Command pattern can also be used to implement a transaction based system. Where you keep maintaining the history of commands as soon as you execute them. If the final command is successfully executed, all good otherwise just iterate through the history and keep executing the undo on all the executed commands.

#### Python

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


