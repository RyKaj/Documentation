###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |


# Information Technology : Chain of Responsibility Pattern



## Chain of Responsibility

### Intent

**Chain of Responsibility** is a behavioral design pattern that lets you pass requests along a chain of handlers. Upon receiving a request, each handler decides either to process the request or to pass it to the next handler in the chain.

<img src"./attachments/chain/463529890.png" />

### Problem

Imagine that you’re working on an online ordering system. You want to restrict access to the system so only authenticated users can create orders. Also, users who have administrative permissions must have full access to all orders.

After a bit of planning, you realized that these checks must be performed sequentially. The application can attempt to authenticate a user to the system whenever it receives a request that contains the user’s credentials. However, if those credentials aren’t correct and authentication fails, there’s no reason to proceed with any other checks.

<img src"./attachments/chain/463529891.png" />

During the next few months, you implemented several more of those sequential checks.

  - One of your colleagues suggested that it’s unsafe to pass raw data straight to the ordering system. So you added an extra validation step to sanitize the data in a request.
  - Later, somebody noticed that the system is vulnerable to brute force password cracking. To negate this, you promptly added a check that filters repeated failed requests coming from the same IP address.
  - Someone else suggested that you could speed up the system by returning cached results on repeated requests containing the same data. Hence, you added another check which lets the request pass through to the system only if there’s no suitable cached response.

<img src"./attachments/chain/463529892.png" />

### Solution

Like many other behavioral design patterns, the **Chain of Responsibility** relies on transforming particular behaviors into stand-alone objects called *handlers*. In our case, each check should be extracted to its own class with a single method that performs the check. The request, along with its data, is passed to this method as an argument.

The pattern suggests that you link these handlers into a chain. Each linked handler has a field for storing a reference to the next handler in the chain. In addition to processing a request, handlers pass the request further along the chain. The request travels along the chain until all handlers have had a chance to process it.

Here’s the best part: a handler can decide not to pass the request further down the chain and effectively stop any further processing.

In our example with ordering systems, a handler performs the processing and then decides whether to pass the request further down the chain. Assuming the request contains the right data, all the handlers can execute their primary behavior, whether it’s authentication checks or caching.

<img src"./attachments/chain/463529893.png" />

However, there’s a slightly different approach (and it’s a bit more canonical) in which, upon receiving a request, a handler decides whether it can process it. If it can, it doesn’t pass the request any further. So it’s either only one handler that processes the request or none at all. This approach is very common when dealing with events in stacks of elements within a graphical user interface.

For instance, when a user clicks a button, the event propagates through the chain of GUI elements that starts with the button, goes along its containers (like forms or panels), and ends up with the main application window. The event is processed by the first element in the chain that’s capable of handling it. This example is also noteworthy because it shows that a chain can always be extracted from an object tree.

<img src"./attachments/chain/463529894.png"/>

### Structure

<img src"./attachments/chain/463529895.png" />

## Pseudocode

<img src"./attachments/chain/463529896.png" />

### Real world example

For example, you have three payment methods (A, B and C) setup in your account; each having a different amount in it. A has 100 USD, B has 300 USD and C having 1000 USD and the preference for payments is chosen as A then B then C. You try to purchase something that is worth 210 USD. Using Chain of Responsibility, first of all account A will be checked if it can make the purchase, if yes purchase will be made and the chain will be broken. If not, request will move forward to account B checking for amount if yes chain will be broken otherwise the request will keep forwarding till it finds the suitable handler. Here A, B and C are links of the chain and the whole phenomenon is Chain of Responsibility.

### In plain words

It helps building a chain of objects. Request enters from one end and keeps going from object to object till it finds the suitable handler.

### Wikipedia says

In object-oriented design, the chain-of-responsibility pattern is a design pattern consisting of a source of command objects and a series of processing objects. Each processing object contains logic that defines the types of command objects that it can handle; the rest are passed to the next processing object in the chain.

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
            <td><br /></td>
        </tr>
        <tr class="odd">
            <td><em>Open/Closed Principle</em>. You can introduce new handlers into the app without breaking the existing client code.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

#### C\#



Translating our account example above. First of all we have a base account having the logic for chaining the accounts together and some accounts

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
>         else if (this.mSuccessor != null)
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

Now let's prepare the chain using the links defined above (i.e. Bank, Paypal, Bitcoin)

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



Translating our account example above. First of all we have a base account having the logic for chaining the accounts together and some accounts

> 
> 
> ``` 
> class Account {
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
>                         
> ```

Now let's prepare the chain using the links defined above (i.e. Bank, Paypal, Bitcoin)

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
> ```



#### PHP



Translating our account example above. First of all we have a base account having the logic for chaining the accounts together and some accounts

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
>     }
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
> class Bitcoin extends Account
> {
>     protected $balance;
> 
>     public function __construct(float $balance)
>     {
>         $this->balance = $balance;
>     }
> }
>                         
> ```

    Now let's prepare the chain using the links defined above (i.e. Bank, Paypal, Bitcoin)

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
> 
> The Chain of responsibility is an object oriented version of the
> `if ... elif ... elif ... else ...` idiom, with the
> benefit that the condition–action blocks can be dynamically rearranged
> and reconfigured at runtime.
> 
> This pattern aims to decouple the senders of a request from its
> receivers by allowing request to move through chained
> receivers until it is handled.
> 
> Request receiver in simple form keeps a reference to a single successor.
> As a variation some receivers may be capable of sending requests out
> in several directions, forming a `tree of responsibility`.
> 
> *TL;DR
> Allow a request to pass down a chain of receivers until it is handled.
> """
> 
> import abc
> 
> class Handler(metaclass=abc.ABCMeta):
> 
> def __init__(self, successor=None):
> self.successor = successor
> 
> def handle(self, request):
> """
> Handle request and stop.
> If can't - call next handler in chain.
> 
> As an alternative you might even in case of success
> call the next handler.
> """
> res = self.check_range(request)
> if not res and self.successor:
> self.successor.handle(request)
> 
> @abc.abstractmethod
> def check_range(self, request):
> """Compare passed value to predefined interval"""
> 
> 
> class ConcreteHandler0(Handler):
> """Each handler can be different.
> Be simple and static...
> """
> 
> @staticmethod
> def check_range(request):
> if 0 <= request < 10:
> print("request {} handled in handler 0".format(request))
> return True
> 
> class ConcreteHandler1(Handler):
> """... With it's own internal state"""
> 
> start, end = 10, 20
> 
> def check_range(self, request):
> if self.start <= request < self.end:
> print("request {} handled in handler 1".format(request))
> return True
> 
> class ConcreteHandler2(Handler):
> """... With helper methods."""
> 
> def check_range(self, request):
> start, end = self.get_interval_from_db()
> if start <= request < end:
> print("request {} handled in handler 2".format(request))
> return True
> 
> @staticmethod
> def get_interval_from_db():
> return (20, 30)
> 
> class FallbackHandler(Handler):
> @staticmethod
> def check_range(request):
> print("end of chain, no handler for {}".format(request))
> return False
> 
> def main():
> """
> >>> h0 = ConcreteHandler0()
> >>> h1 = ConcreteHandler1()
> >>> h2 = ConcreteHandler2(FallbackHandler())
> >>> h0.successor = h1
> >>> h1.successor = h2
> 
> >>> requests = [2, 5, 14, 22, 18, 3, 35, 27, 20]
> >>> for request in requests:
> ...     h0.handle(request)
> request 2 handled in handler 0
> request 5 handled in handler 0
> request 14 handled in handler 1
> request 22 handled in handler 2
> request 18 handled in handler 1
> request 3 handled in handler 0
> end of chain, no handler for 35
> request 27 handled in handler 2
> request 20 handled in handler 2
> """
> 
> if __name__ == "__main__":
> import doctest
> doctest.testmod(optionflags=doctest.ELLIPSIS)
>                     
> ```

