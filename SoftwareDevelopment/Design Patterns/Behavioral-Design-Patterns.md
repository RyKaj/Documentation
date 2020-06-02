###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |

------------

<div id="breadcrumb-section">

1.  [Information Technology](index.html)
2.  [3.0 Sofware Development
    Lifecycle](3.0-Sofware-Development-Lifecycle_380470491.html)
3.  [Design Patterns](Design-Patterns_451820045.html)
4.  [1.0 Design Pattern - Programming
    Language](1.0-Design-Pattern---Programming-Language_451820065.html)



# Information Technology : Behavioral Design Patterns





## Chain of Responsibility

### Intent

**Chain of Responsibility** is a behavioral design pattern that lets you
pass requests along a chain of handlers. Upon receiving a request, each
handler decides either to process the request or to pass it to the next
handler in the chain.

<kbd>![](attachments/463529897/463529890.png)

### Problem

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

<kbd>![](attachments/463529897/463529891.png)

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

<kbd>![](attachments/463529897/463529892.png)

### Solution

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

<kbd>![](attachments/463529897/463529893.png)

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

<kbd>![](attachments/463529897/463529894.png)

### Structure

<kbd>![](attachments/463529897/463529895.png)

### Pseudocode

<kbd>![](attachments/463529897/463529896.png)

### Real world example

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

### In plain words

It helps building a chain of objects. Request enters from one end and
keeps going from object to object till it finds the suitable handler.

### Wikipedia says

In object-oriented design, the chain-of-responsibility pattern is a
design pattern consisting of a source of command objects and a series of
processing objects. Each processing object contains logic that defines
the types of command objects that it can handle; the rest are passed to
the next processing object in the chain.

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



### Programmatic Example

#### C\#



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

#### JavaScript

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



#### PHP

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

#### Python

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

## Command

### Intent

**Command** is a behavioral design pattern that turns a request into a
stand-alone object that contains all information about the request. This
transformation lets you parameterize methods with different requests,
delay or queue a request’s execution, and support undoable operations.

<kbd>![](attachments/463529910/463529901.png)

### Problem

Imagine that you’re working on a new text-editor app. Your current task
is to create a toolbar with a bunch of buttons for various operations of
the editor. You created a very neat `Button` class that can be used for
buttons on the toolbar, as well as for generic buttons in various
dialogs.

<kbd>![](attachments/463529910/463529902.png)

While all of these buttons look similar, they’re all supposed to do
different things. Where would you put the code for the various click
handlers of these buttons? The simplest solution is to create tons of
subclasses for each place where the button is used. These subclasses
would contain the code that would have to be executed on a button click.

<kbd>![](attachments/463529910/463529903.png)

Before long, you realize that this approach is deeply flawed. First, you
have an enormous number of subclasses, and that would be okay if you
weren’t risking breaking the code in these subclasses each time you
modify the base `Button` class. Put simply, your GUI code has become
awkwardly dependent on the volatile code of the business logic.

<kbd>![](attachments/463529910/463529904.png)

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

### Solution

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

<kbd>![](attachments/463529910/463529905.png)

The Command pattern suggests that GUI objects shouldn’t send these
requests directly. Instead, you should extract all of the request
details, such as the object being called, the name of the method and the
list of arguments into a separate *command* class with a single method
that triggers this request.

Command objects serve as links between various GUI and business logic
objects. From now on, the GUI object doesn’t need to know what business
logic object will receive the request and how it’ll be processed. The
GUI object just triggers the command, which handles all the details.

<kbd>![](attachments/463529910/463529906.png)

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

<kbd>![](attachments/463529910/463529907.png)

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

### Structure

<kbd>![](attachments/463529910/463529908.png)

### Pseudocode

<kbd>![](attachments/463529910/463529909.png)

### Real world example

A generic example would be you ordering food at a restaurant. You (i.e.
`Client`) ask the waiter (i.e. `Invoker`) to bring some food (i.e.
`Command`) and waiter simply forwards the request to Chef (i.e.
`Receiver`) who has the knowledge of what and how to cook. Another
example would be you (i.e. `Client`) switching on (i.e. `Command`) the
television (i.e. `Receiver`) using a remote control ( `Invoker`).

### In plain words

Allows you to encapsulate actions in objects. The key idea behind this
pattern is to provide the means to decouple client from receiver.

### Wikipedia says

In object-oriented programming, the command pattern is a behavioral
design pattern in which an object is used to encapsulate all information
needed to perform an action or trigger an event at a later time. This
information includes the method name, the object that owns the method
and values for the method parameters.

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



### Programmatic Example

#### C\#



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



#### JavaScript



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



#### PHP

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

## Iterator

### Intent

Iterator is a behavioral design pattern that lets you traverse elements
of a collection without exposing its underlying representation (list,
stack, tree, etc.).

<kbd>![](attachments/463529918/463529912.png)

### Problem

Collections are one of the most used data types in programming.
Nonetheless, a collection is just a container for a group of objects.

<kbd>![](attachments/463529918/463529913.png)

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

<kbd>![](attachments/463529918/463529914.png)

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

<kbd>![](attachments/463529918/463529915.png)

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

<kbd>![](attachments/463529918/463529916.png)

### Pseudocode

<kbd>![](attachments/463529918/463529917.png)

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

## Memento

### Intent

**Memento** is a behavioral design pattern that lets you save and
restore the previous state of an object without revealing the details of
its implementation.

<kbd>![](attachments/463529936/463529928.png)

### Problem

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

<kbd>![](attachments/463529936/463529929.png)

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

<kbd>![](attachments/463529936/463529930.png)

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

### Solution

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

<kbd>![](attachments/463529936/463529931.png)

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

### Structure

#### Implementation based on nested classes

The classic implementation of the pattern relies on support for nested
classes, available in many popular programming languages (such as C++,
C\#, and Java).

<kbd>![](attachments/463529936/463529932.png)

#### Implementation based on an intermediate interface

There’s an alternative implementation, suitable for programming
languages that don’t support nested classes (yeah, PHP, I’m talking
about you).

<kbd>![](attachments/463529936/463529933.png)

#### Implementation with even stricter encapsulation

There’s another implementation which is useful when you don’t want to
leave even the slightest chance of other classes accessing the state of
the originator through the memento.

<kbd>![](attachments/463529936/463529934.png)

### Pseudocode

<kbd>![](attachments/463529936/463529935.png)

### Real world example

Take the example of calculator (i.e. originator), where whenever you
perform some calculation the last calculation is saved in memory (i.e.
memento) so that you can get back to it and maybe get it restored using
some action buttons (i.e. caretaker).

### In plain words

Memento pattern is about capturing and storing the current state of an
object in a manner that it can be restored later on in a smooth manner.

### Wikipedia says

The memento pattern is a software design pattern that provides the
ability to restore an object to its previous state (undo via rollback).

Usually useful when you need to provide some sort of undo functionality.

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



### Programmatic Example

### C\#



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



#### JavaScript



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



#### PHP



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



#### Python

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

## Observer

### Intent

**Observer** is a behavioral design pattern that lets you define a
subscription mechanism to notify multiple objects about any events that
happen to the object they’re observing.

<kbd>![](attachments/463529939/463530128.png)

## Problem

Imagine that you have two types of objects: a `Customer` and a `Store`.
The customer is very interested in a particular brand of product (say,
it’s a new model of the iPhone) which should become available in the
store very soon.

The customer could visit the store every day and check product
availability. But while the product is still en route, most of these
trips would be pointless.

<kbd>![](attachments/463529939/463530129.png)

On the other hand, the store could send tons of emails (which might be
considered spam) to all customers each time a new product becomes
available. This would save some customers from endless trips to the
store. At the same time, it’d upset other customers who aren’t
interested in new products.

It looks like we’ve got a conflict. Either the customer wastes time
checking product availability or the store wastes resources notifying
the wrong customers.

### Solution

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

<kbd>![](attachments/463529939/463530130.png)

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

<kbd>![](attachments/463529939/463530131.png)

If your app has several different types of publishers and you want to
make your subscribers compatible with all of them, you can go even
further and make all publishers follow the same interface. This
interface would only need to describe a few subscription methods. The
interface would allow subscribers to observe publishers’ states without
coupling to their concrete classes.

### Structure

<kbd>![](attachments/463529939/463530132.png)

### Pseudocode

<kbd>![](attachments/463529939/463530133.png)

### Real world example

A good example would be the job seekers where they subscribe to some job
posting site and they are notified whenever there is a matching job
opportunity.

### In plain words

Defines a dependency between objects so that whenever an object changes
its state, all its dependents are notified.

### Wikipedia says

The observer pattern is a software design pattern in which an object,
called the subject, maintains a list of its dependents, called
observers, and notifies them automatically of any state changes, usually
by calling one of their methods.

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



### Programmatic Example

#### C\#



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



#### JavaScript



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



#### PHP



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



#### Python



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

## Visitor

### Intent

**Visitor** is a behavioral design pattern that lets you separate
algorithms from the objects on which they operate.

<kbd>![](attachments/463529941/463530158.png)

### Problem

Imagine that your team develops an app which works with geographic
information structured as one colossal graph. Each node of the graph may
represent a complex entity such as a city, but also more granular things
like industries, sightseeing areas, etc. The nodes are connected with
others if there’s a road between the real objects that they represent.
Under the hood, each node type is represented by its own class, while
each specific node is an object.

<kbd>![](attachments/463529941/463530160.png)

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

<kbd>![](attachments/463529941/463530161.png)

Besides, he questioned whether it makes sense to have the XML export
code within the node classes. The primary job of these classes was to
work with geodata. The XML export behavior would look alien there.

There was another reason for the refusal. It was highly likely that
after this feature was implemented, someone from the marketing
department would ask you to provide the ability to export into a
different format, or request some other weird stuff. This would force
you to change those precious and fragile classes again.

### Solution

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

### Structure

<kbd>![](attachments/463529941/463530162.png)

### Pseudocode

In this example, the **Visitor** pattern adds XML export support to the
class hierarchy of geometric shapes.

<kbd>![](attachments/463529941/463530159.png)

### Real world example

Consider someone visiting Dubai. They just need a way (i.e. visa) to
enter Dubai. After arrival, they can come and visit any place in Dubai
on their own without having to ask for permission or to do some leg work
in order to visit any place here; just let them know of a place and they
can visit it. Visitor pattern lets you do just that, it helps you add
places to visit so that they can visit as much as they can without
having to do any legwork.

### In plain words

Visitor pattern lets you add further operations to objects without
having to modify them.

### Wikipedia says

In object-oriented programming and software engineering, the visitor
design pattern is a way of separating an algorithm from an object
structure on which it operates. A practical result of this separation is
the ability to add new operations to existing object structures without
modifying those structures. It is one way to follow the open/closed
principle.

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
<td><br />
</td>
</tr>
</tbody>
</table>



### Programmatic Example

#### C\#



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



#### JavaScript



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



#### PHP



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

## Strategy

### Intent

**Strategy** is a behavioral design pattern that lets you define a
family of algorithms, put each of them into a separate class, and make
their objects interchangeable.

<kbd>![](attachments/463529943/463530145.png)

### Problem

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

<kbd>![](attachments/463529943/463530146.png)

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

### Solution

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

<kbd>![](attachments/463529943/463530147.png)

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

### Structure

<kbd>![](attachments/463529943/463530148.png)

### Pseudocode

#### Real world example

Consider the example of sorting, we implemented bubble sort but the data
started to grow and bubble sort started getting very slow. In order to
tackle this we implemented Quick sort. But now although the quick sort
algorithm was doing better for large datasets, it was very slow for
smaller datasets. In order to handle this we implemented a strategy
where for small datasets, bubble sort will be used and for larger, quick
sort.

#### In plain words

Strategy pattern allows you to switch the algorithm or strategy based
upon the situation.

#### Wikipedia says

In computer programming, the strategy pattern (also known as the policy
pattern) is a behavioural software design pattern that enables an
algorithm's behavior to be selected at runtime.

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
<td><br />
</td>
</tr>
</tbody>
</table>



### Programmatic Example

Translating our example from above. First of all we have our strategy
interface and different strategy implementations

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

## State

### Intent

**State** is a behavioral design pattern that lets an object alter its
behavior when its internal state changes. It appears as if the object
changed its class.

<kbd>![](attachments/463529945/463530136.png)

### Problem

The State pattern is closely related to the concept of a [Finite-State
Machine](https://en.wikipedia.org/wiki/Finite-state_machine).

<kbd>![](attachments/463529945/463530138.png)

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

<kbd>![](attachments/463529945/463530139.png)

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

### Solution

The State pattern suggests that you create new classes for all possible
states of an object and extract all state-specific behaviors into these
classes.

Instead of implementing all behaviors on its own, the original object,
called *context*, stores a reference to one of the state objects that
represents its current state, and delegates all the state-related work
to that object.

<kbd>![](attachments/463529945/463530140.png)

To transition the context into another state, replace the active state
object with another object that represents that new state. This is
possible only if all state classes follow the same interface and the
context itself works with these objects through that interface.

This structure may look similar to the
[Strategy](https://refactoring.guru/design-patterns/strategy) pattern,
but there’s one key difference. In the State pattern, the particular
states may be aware of each other and initiate transitions from one
state to another, whereas strategies almost never know about each other.

### Structure

<kbd>![](attachments/463529945/463530141.png)

### Pseudocode

In this example, the **State** pattern lets the same controls of the
media player behave differently, depending on the current playback
state.

<kbd>![](attachments/463529945/463530137.png)

The main object of the player is always linked to a state object that
performs most of the work for the player. Some actions replace the
current state object of the player with another, which changes the way
the player reacts to user interactions.

### Real world example

Imagine you are using some drawing application, you choose the paint
brush to draw. Now the brush changes its behavior based on the selected
color i.e. if you have chosen red color it will draw in red, if blue
then it will be in blue etc.

### In plain words

It lets you change the behavior of a class when the state changes.

### Wikipedia says

The state pattern is a behavioral software design pattern that
implements a state machine in an object-oriented way. With the state
pattern, a state machine is implemented by implementing each individual
state as a derived class of the state pattern interface, and
implementing state transitions by invoking methods defined by the
pattern's superclass. The state pattern can be interpreted as a strategy
pattern which is able to switch the current strategy through invocations
of methods defined in the pattern's interface.

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



### Programmatic Example

#### C\#



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



### JavaScript



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



#### PHP



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

#### Python



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

## Template Method

### Intent

**Template Method** is a behavioral design pattern that defines the
skeleton of an algorithm in the superclass but lets subclasses override
specific steps of the algorithm without changing its structure.

<kbd>![](attachments/463529947/463530151.png)

### Problem

Imagine that you’re creating a data mining application that analyzes
corporate documents. Users feed the app documents in various formats
(PDF, DOC, CSV), and it tries to extract meaningful data from these docs
in a uniform format.

The first version of the app could work only with DOC files. In the
following version, it was able to support CSV files. A month later, you
“taught” it to extract data from PDF files.

<kbd>![](attachments/463529947/463530153.png)

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

### Solution

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

<kbd>![](attachments/463529947/463530154.png)

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

### Structure

<kbd>![](attachments/463529947/463530155.png)

### Pseudocode

In this example, the **Template Method** pattern provides a “skeleton”
for various branches of artificial intelligence in a simple strategy
video game.

<kbd>![](attachments/463529947/463530152.png)

### Real world example

Suppose we are getting some house built. The steps for building might
look like

  - Prepare the base of house
  - Build the walls
  - Add roof
  - Add other floors

The order of these steps could never be changed i.e. you can't build the
roof before building the walls etc but each of the steps could be
modified for example walls can be made of wood or polyester or stone.

### In plain words

Template method defines the skeleton of how a certain algorithm could be
performed, but defers the implementation of those steps to the children
classes.

### Wikipedia says

In software engineering, the template method pattern is a behavioral
design pattern that defines the program skeleton of an algorithm in an
operation, deferring some steps to subclasses. It lets one redefine
certain steps of an algorithm without changing the algorithm's
structure.

### Pros and Cons



| Pros                                                                                                                                                    | Cons                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| You can let clients override only certain parts of a large algorithm, making them less affected by changes that happen to other parts of the algorithm. | Some clients may be limited by the provided skeleton of an algorithm.                                              |
| You can pull the duplicate code into a superclass.                                                                                                      | You might violate the *Liskov Substitution Principle* by suppressing a default step implementation via a subclass. |
|                                                                                                                                                         | Template methods tend to be harder to maintain the more steps they have.                                           |



#### Programmatic Example

#### C\#



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



#### JavaScript



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



#### Python



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

