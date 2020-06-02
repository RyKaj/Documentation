###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------


# Information Technology : Mediator Pattern


## Mediator

### Intent

**Mediator** is a behavioral design pattern that lets you reduce chaotic
dependencies between objects. The pattern restricts direct
communications between the objects and forces them to collaborate only
via a mediator object.

<kbd>![](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/attachments/463529920.png)</kbd>

### Problem

Say you have a dialog for creating and editing customer profiles. It
consists of various form controls such as text fields, checkboxes,
buttons, etc.

<kbd>![](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/attachments/463529921.png)</kbd>

Some of the formBy having this logic implemented directly inside the
code of the form elements you make these elements’ classes much harder
to reuse in other forms of the app. For example, you won’t be able to
use that checkbox class inside another form, because it’s coupled to the
dog’s text field. You can use either all the classes involved in
rendering the profile form, or none at all. elements may interact with
others. For instance, selecting the “I have a dog” checkbox may reveal a
hidden text field for entering the dog’s name. Another example is the
submit button that has to validate values of all fields before saving
the data.

<kbd>![](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/attachments/463529922.png)</kbd>

### Solution

The Mediator pattern suggests that you should cease all direct
communication between the components which you want to make independent
of each other. Instead, these components must collaborate indirectly, by
calling a special mediator object that redirects the calls to
appropriate components. As a result, the components depend only on a
single mediator class instead of being coupled to dozens of their
colleagues.

In our example with the profile editing form, the dialog class itself
may act as the mediator. Most likely, the dialog class is already aware
of all of its sub-elements, so you won’t even need to introduce new
dependencies into this class.

<kbd>![](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/attachments/463529923.png)</kbd>

The most significant change happens to the actual form elements. Let’s
consider the submit button. Previously, each time a user clicked the
button, it had to validate the values of all individual form elements.
Now its single job is to notify the dialog about the click. Upon
receiving this notification, the dialog itself performs the validations
or passes the task to the individual elements. Thus, instead of being
tied to a dozen form elements, the button is only dependent on the
dialog class.

You can go further and make the dependency even looser by extracting the
common interface for all types of dialogs. The interface would declare
the notification method which all form elements can use to notify the
dialog about events happening to those elements. Thus, our submit button
should now be able to work with any dialog that implements that
interface.

This way, the Mediator pattern lets you encapsulate a complex web of
relations between various objects inside a single mediator object. The
fewer dependencies a class has, the easier it becomes to modify, extend
or reuse that class.

### Structure

<kbd>![](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/attachments/463529924.png)</kbd>

### Pseudocode

<kbd>![](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/attachments/463529925.png)</kbd>

A general example would be when you talk to someone on your mobile
phone, there is a network provider sitting between you and them and your
conversation goes through it instead of being directly sent. In this
case network provider is mediator.

### In plain words

Mediator pattern adds a third party object (called mediator) to control
the interaction between two objects (called colleagues). It helps reduce
the coupling between the classes communicating with each other. Because
now they don't need to have the knowledge of each other's
implementation.

### Wikipedia says

In software engineering, the mediator pattern defines an object that
encapsulates how a set of objects interact. This pattern is considered
to be a behavioral pattern due to the way it can alter the program's
running behavior.

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
            <td><em>Single Responsibility Principle</em>. You can extract the communications between various components into a single place, making it easier to comprehend and maintain.</td>
            <td>Over time a mediator can evolve into a <a href="https://refactoring.guru/antipatterns/god-object">God Object</a>.</td>
        </tr>
        <tr class="even">
            <td><em>Open/Closed Principle</em>. You can introduce new mediators without having to change the actual components.</td>
            <td><br /></td>
        </tr>
        <tr class="odd">
            <td>You can reduce coupling between various components of a program.</td>
            <td><br /></td>
        </tr>
        <tr class="even">
            <td>You can reuse individual components more easily.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

#### C\#

Here is the simplest example of a chat room (i.e. mediator) with users
(i.e. colleagues) sending messages to each other.

First of all, we have the mediator i.e. the chat room

> 
> 
> ``` 
> interface IChatRoomMediator
> {
>     void ShowMessage(User user, string message);
> }
> 
> //Mediator
> class ChatRoom : IChatRoomMediator
> {
>     public void ShowMessage(User user, string message)
>     {
>         Console.WriteLine($"{DateTime.Now.ToString("MMMM dd, H:mm")} [{user.GetName()}]:{message}");
>     }
> }
>
> ```

Then we have our users i.e. colleagues

> 
> 
> ``` 
> class User
> {
>     private string mName;
>     private IChatRoomMediator mChatRoom;
> 
>     public User(string name, IChatRoomMediator chatroom)
>     {
>         mChatRoom = chatroom;
>         mName = name;
>     }
> 
>     public string GetName()
>     {
>         return mName;
>     }
> 
>     public void Send(string message)
>     {
>         mChatRoom.ShowMessage(this, message);
>     }
> }
>
> ```

And the usage

> 
> 
> ``` 
> var mediator = new ChatRoom();
> 
> var john = new User("John", mediator);
> var jane = new User("Jane", mediator);
> 
> john.Send("Hi there!");
> jane.Send("Hey!");
> 
> //April 14, 20:05[John]:Hi there!
> //April 14, 20:05[Jane]:Hey!
>
> ```



#### JavaScript



Here is the simplest example of a chat room (i.e. mediator) with users
(i.e. colleagues) sending messages to each other.

First of all, we have the mediator i.e. the chat room

``` 
// Mediator
class ChatRoom {
    showMessage(user, message) {
        const time = new Date()
        const sender = user.getName()

        console.log(time + '[' + sender + ']:' + message)
    }
}
                
```

Then we have our users i.e. colleagues

``` 
class User {
    constructor(name, chatMediator) {
        this.name = name
        this.chatMediator = chatMediator
    }
    
    getName() {
        return this.name
    }
    
    send(message) {
        this.chatMediator.showMessage(this, message)
    }
}
                
```

And the usage

``` 
const mediator = new ChatRoom()

const john = new User('John Doe', mediator)
const jane = new User('Jane Doe', mediator)

john.send('Hi there!')
jane.send('Hey!')

// Output will be
// Feb 14, 10:58 [John]: Hi there!
// Feb 14, 10:58 [Jane]: Hey!
                
```



#### PHP



Here is the simplest example of a chat room (i.e. mediator) with users
(i.e. colleagues) sending messages to each other.

First of all, we have the mediator i.e. the chat room

``` 
interface ChatRoomMediator 
{
    public function showMessage(User $user, string $message);
}

// Mediator
class ChatRoom implements ChatRoomMediator
{
    public function showMessage(User $user, string $message)
    {
        $time = date('M d, y H:i');
        $sender = $user->getName();
         echo $time . '[' . $sender . ']:' . $message;
    }
}
                
```

Then we have our users i.e. colleagues

``` 
class User {
    protected $name;
    protected $chatMediator;

    public function __construct(string $name, ChatRoomMediator $chatMediator) {
        $this->name = $name;
        $this->chatMediator = $chatMediator;
    }

    public function getName() {
        return $this->name;
    }

    public function send($message) {
        $this->chatMediator->showMessage($this, $message);
    }
}
                
```

And the usage

``` 
$mediator = new ChatRoom();

$john = new User('John Doe', $mediator);
$jane = new User('Jane Doe', $mediator);

$john->send('Hi there!');
$jane->send('Hey!');

// Output will be
// Feb 14, 10:58 [John]: Hi there!
// Feb 14, 10:58 [Jane]: Hey!
                                                    
                
```



#### Python



``` 
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
https://www.djangospin.com/design-patterns-python/mediator/

Objects in a system communicate through a Mediator instead of directly with each other.
This reduces the dependencies between communicating objects, thereby reducing coupling.

*TL;DR
Encapsulates how a set of objects interact.
"""


class ChatRoom(object):
    """Mediator class"""

    def display_message(self, user, message):
        print("[{} says]: {}".format(user, message))


class User(object):
    """A class whose instances want to interact with each other"""

    def __init__(self, name):
        self.name = name
        self.chat_room = ChatRoom()

    def say(self, message):
        self.chat_room.display_message(self, message)

    def __str__(self):
        return self.name


def main():
    """
    >>> molly = User('Molly')
    >>> mark = User('Mark')
    >>> ethan = User('Ethan')

    >>> molly.say("Hi Team! Meeting at 3 PM today.")
    [Molly says]: Hi Team! Meeting at 3 PM today.
    >>> mark.say("Roger that!")
    [Mark says]: Roger that!
    >>> ethan.say("Alright.")
    [Ethan says]: Alright.
    """


if __name__ == '__main__':
    import doctest
    doctest.testmod()
                
```

