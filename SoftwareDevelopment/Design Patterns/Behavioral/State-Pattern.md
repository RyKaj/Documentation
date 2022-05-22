###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Design Patterns](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/Design%20Patterns/README.md) |
------------

# Information Technology : State Pattern


## State

### Intent

**State** is a behavioral design pattern that lets an object alter its behavior when its internal state changes. It appears as if the object changed its class.

<img src"./attachments/state/463530136.png" />

### Problem

The State pattern is closely related to the concept of a [Finite-State Machine](https://en.wikipedia.org/wiki/Finite-state_machine).

<img src"./attachments/state/463530138.png" />

The main idea is that, at any given moment, there’s a *finite* number of *states* which a program can be in. Within any unique state, the program behaves differently, and the program can be switched from one state to another instantaneously. However, depending on a current state, the program may or may not switch to certain other states. These switching rules, called *transitions*, are also finite and predetermined.

You can also apply this approach to objects. Imagine that we have a `Document` class. A document can be in one of three states: `Draft`, `Moderation` and `Published`. The `publish` method of the document works a little bit differently in each state:

  - In `Draft`, it moves the document to moderation.
  - In `Moderation`, it makes the document public, but only if the current user is an administrator.
  - In `Published`, it doesn’t do anything at all.

<img src"./attachments/state/463530139.png" />

State machines are usually implemented with lots of conditional operators ( `if` or `switch` ) that select the appropriate behavior depending on the current state of the object. Usually, this “state” is just a set of values of the object’s fields. Even if you’ve never heard about finite-state machines before, you’ve probably implemented a state at least once. Does the following code structure ring a bell?

The biggest weakness of a state machine based on conditionals reveals itself once we start adding more and more states and state-dependent behaviors to the `Document` class. Most methods will contain monstrous conditionals that pick the proper behavior of a method according to the current state. Code like this is very difficult to maintain because any change to the transition logic may require changing state conditionals in every method.

The problem tends to get bigger as a project evolves. It’s quite difficult to predict all possible states and transitions at the design stage. Hence, a lean state machine built with a limited set of conditionals can grow into a bloated mess over time.

### Solution

The State pattern suggests that you create new classes for all possible states of an object and extract all state-specific behaviors into these classes.

Instead of implementing all behaviors on its own, the original object, called *context*, stores a reference to one of the state objects that represents its current state, and delegates all the state-related work to that object.

<img src"./attachments/state/463530140.png" />

To transition the context into another state, replace the active state object with another object that represents that new state. This is possible only if all state classes follow the same interface and the context itself works with these objects through that interface.

This structure may look similar to the [Strategy](https://refactoring.guru/design-patterns/strategy) pattern, but there’s one key difference. In the State pattern, the particular states may be aware of each other and initiate transitions from one state to another, whereas strategies almost never know about each other.

### Structure

<img src"./attachments/state/463530141.png" />

### Pseudocode

In this example, the **State** pattern lets the same controls of the media player behave differently, depending on the current playback state.

<img src"./attachments/state/463530137.png" />

The main object of the player is always linked to a state object that performs most of the work for the player. Some actions replace the current state object of the player with another, which changes the way the player reacts to user interactions.

### Real world example

Imagine you are using some drawing application, you choose the paint brush to draw. Now the brush changes its behavior based on the selected color i.e. if you have chosen red color it will draw in red, if blue then it will be in blue etc.

### In plain words

It lets you change the behavior of a class when the state changes.

### Wikipedia says

The state pattern is a behavioral software design pattern that implements a state machine in an object-oriented way. With the state pattern, a state machine is implemented by implementing each individual state as a derived class of the state pattern interface, and implementing state transitions by invoking methods defined by the pattern's superclass. The state pattern can be interpreted as a strategy pattern which is able to switch the current strategy through invocations of methods defined in the pattern's interface.

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
            <td><br /></td>
        </tr>
        <tr class="odd">
            <td>Simplify the code of the context by eliminating bulky state machine conditionals.</td>
            <td><br /></td>
        </tr>
    </tbody>
</table>



### Programmatic Example

#### C\#



Let's take an example of text editor, it lets you change the state of text that is typed i.e. if you have selected bold, it starts writing in bold, if italic then in italics etc.

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



Let's take an example of text editor, it let's you change the state of text that is typed i.e. if you have selected bold, it starts writing in bold, if italic then in italics etc.

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



Let's take an example of text editor, it lets you change the state of text that is typed i.e. if you have selected bold, it starts writing in bold, if italic then in italics etc.

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

