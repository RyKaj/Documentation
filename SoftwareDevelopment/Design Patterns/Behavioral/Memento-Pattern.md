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

</div>

# Information Technology : Memento Pattern

</div>

<div id="content" class="view">

## Memento

### Intent

**Memento** is a behavioral design pattern that lets you save and
restore the previous state of an object without revealing the details of
its implementation.

![](attachments/463529936/463529928.png)

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

### Structure

#### Implementation based on nested classes

The classic implementation of the pattern relies on support for nested
classes, available in many popular programming languages (such as C++,
C\#, and Java).

![](attachments/463529936/463529932.png)

#### Implementation based on an intermediate interface

There’s an alternative implementation, suitable for programming
languages that don’t support nested classes (yeah, PHP, I’m talking
about you).

![](attachments/463529936/463529933.png)

#### Implementation with even stricter encapsulation

There’s another implementation which is useful when you don’t want to
leave even the slightest chance of other classes accessing the state of
the originator through the memento.

![](attachments/463529936/463529934.png)

### Pseudocode

![](attachments/463529936/463529935.png)

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

### Programmatic Example

### C\#

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

#### JavaScript

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

#### PHP

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

#### Python

<div>

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

</div>

</div>

</div>

<div id="footer" role="contentinfo">

<div class="section footer-body">

</div>

</div>
