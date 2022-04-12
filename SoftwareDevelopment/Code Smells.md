
https://refactoring.guru/refactoring/smells/change-preventers

# Code Smells

## Bloaters
Bloaters are code, methods and classes that have increased to such gargantuan proportions that they are hard to work with. Usually these smells do not crop up right away, rather they accumulate over time as the program evolves (and especially when nobody makes an effort to eradicate them).

### Long method
####Signs and Symptoms
A method contains too many lines of code. Generally, any method longer than ten lines should make you start asking questions.
####Reasons for the Problem
Like the Hotel California, something is always being added to a method but nothing is ever taken out. Since it’s easier to write code than to read it, this “smell” remains unnoticed until the method turns into an ugly, oversized beast.

Mentally, it’s often harder to create a new method than to add to an existing one: “But it’s just two lines, there’s no use in creating a whole method just for that...” Which means that another line is added and then yet another, giving birth to a tangle of spaghetti code.
####Treatment
- To reduce the length of a method body, use Extract Method.
- If local variables and parameters interfere with extracting a method, use Replace Temp with Query, Introduce Parameter Object or Preserve Whole Object.
- If none of the previous recipes help, try moving the entire method to a separate object via Replace Method with Method Object.
- Conditional operators and loops are a good clue that code can be moved to a separate method. For conditionals, use Decompose Conditional. If loops are in the way, try Extract Method.

####Payoff
- Among all types of object-oriented code, classes with short methods live longest. The longer a method or function is, the harder it becomes to understand and maintain it.
- In addition, long methods offer the perfect hiding place for unwanted duplicate code.

####Performance
Does an increase in the number of methods hurt performance, as many people claim? In almost all cases the impact is so negligible that it’s not even worth worrying about.

Plus, now that you have clear and understandable code, you’re more likely to find truly effective methods for restructuring code and getting real performance gains if the need ever arises.

### Primitive Obsession
####Signs and Symptoms
- Use of primitives instead of small objects for simple tasks (such as currency, ranges, special strings for phone numbers, etc.)
- Use of constants for coding information (such as a constant `USER_ADMIN_ROLE = 1` for referring to users with administrator rights.)
- Use of string constants as field names for use in data arrays.

####Reasons for the Problem
- Like most other smells, primitive obsessions are born in moments of weakness. “Just a field for storing some data!” the programmer said. Creating a primitive field is so much easier than making a whole new class, right? And so it was done. Then another field was needed and added in the same way. Lo and behold, the class became huge and unwieldy.
- Primitives are often used to “simulate” types. So instead of a separate data type, you have a set of numbers or strings that form the list of allowable values for some entity. Easy-to-understand names are then given to these specific numbers and strings via constants, which is why they’re spread wide and far.
- Another example of poor primitive use is field simulation. The class contains a large array of diverse data and string constants (which are specified in the class) are used as array indices for getting this data.

####Treatment
- If you have a large variety of primitive fields, it may be possible to logically group some of them into their own class. Even better, move the behavior associated with this data into the class too. For this task, try Replace Data Value with Object.
- If the values of primitive fields are used in method parameters, go with Introduce Parameter Object or Preserve Whole Object.
- When complicated data is coded in variables, use Replace Type Code with Class, Replace Type Code with Subclasses or Replace Type Code with State/Strategy.
- If there are arrays among the variables, use Replace Array with Object.

####Payoff
- Code becomes more flexible thanks to use of objects instead of primitives.
- Better understandability and organization of code. Operations on particular data are in the same place, instead of being scattered. No more guessing about the reason for all these strange constants and why they’re in an array.
- Easier finding of duplicate code.

### Data Clumps
####Signs and Symptoms
Sometimes different parts of the code contain identical groups of variables (such as parameters for connecting to a database). These clumps should be turned into their own classes.

####Reasons for the Problem
- Often these data groups are due to poor program structure or "copypasta programming.
- If you want to make sure whether or not some data is a data clump, just delete one of the data values and see whether the other values still make sense. If this isn’t the case, this is a good sign that this group of variables should be combined into an object.

####Treatment
- If repeating data comprises the fields of a class, use Extract Class to move the fields to their own class.
- If the same data clumps are passed in the parameters of methods, use Introduce Parameter Object to set them off as a class.
- If some of the data is passed to other methods, think about passing the entire data object to the method instead of just individual fields. Preserve Whole Object will help with this.
- Look at the code used by these fields. It may be a good idea to move this code to a data class.

####Payoff
- Improves understanding and organization of code. Operations on particular data are now gathered in a single place, instead of haphazardly throughout the code.
- Reduces code size.

####When to Ignore
Passing an entire object in the parameters of a method, instead of passing just its values (primitive types), may create an undesirable dependency between the two classes.

####Performance


### Large Class
####Signs and Symptoms
A class contains many fields/methods/lines of code.
####Rasons for the Problem
Classes usually start small. But over time, they get bloated as the program grows.

As is the case with long methods as well, programmers usually find it mentally less taxing to place a new feature in an existing class than to create a new class for the feature.
####Treatment
- When a class is wearing - too many (functional) hats, think about splitting it up:
- Extract Class helps if part of the behavior of the large class can be spun off into a separate component.
- Extract Subclass helps if part of the behavior of the large class can be implemented in different ways or is used in rare cases.
- Extract Interface helps if it’s necessary to have a list of the operations and behaviors that the client can use.
- If a large class is responsible for the graphical interface, you may try to move some of its data and behavior to a separate domain object. In doing so, it may be necessary to store copies of some data in two places and keep the data consistent. Duplicate Observed Data offers a way to do this.

####Payoff
- Refactoring of these classes spares developers from needing to remember a large number of attributes for a class.
- In many cases, splitting large classes into parts avoids duplication of code and functionality.

### Long Parameters List
####Signs and Symptoms
More than three or four parameters for a method.
####Reasons for the Problem
A long list of parameters might happen after several types of algorithms are merged in a single method. A long list may have been created to control which algorithm will be run and how.

Long parameter lists may also be the byproduct of efforts to make classes more independent of each other. For example, the code for creating specific objects needed in a method was moved from the method to the code for calling the method, but the created objects are passed to the method as parameters. Thus the original class no longer knows about the relationships between objects, and dependency has decreased. But if several of these objects are created, each of them will require its own parameter, which means a longer parameter list.

It’s hard to understand such lists, which become contradictory and hard to use as they grow longer. Instead of a long list of parameters, a method can use the data of its own object. If the current object doesn’t contain all necessary data, another object (which will get the necessary data) can be passed as a method parameter.

####Treatment
- Check what values are passed to parameters. If some of the arguments are just results of method calls of another object, use Replace Parameter with Method Call. This object can be placed in the field of its own class or passed as a method parameter.
- Instead of passing a group of data received from another object as parameters, pass the object itself to the method, by using Preserve Whole Object.
- If there are several unrelated data elements, sometimes you can merge them into a single parameter object via Introduce Parameter Object.


####Payoff
- More readable, shorter code.
- Refactoring may reveal previously unnoticed duplicate code.

####When to Ignore
Don&#39;t get rid of parameters if doing so would cause unwanted dependency between classes.

##Object-Orientation Abusers

###Switch Statement
#### Signs and Symptons
You have a complex `switch` operator or sequence of `if` statements.
#### Reasons for the Problem
Relatively rare use of `switch` and `case` operators is one of the hallmarks of object-oriented code. Often code for a single `switch` can be scattered in different places in the program. When a new condition is added, you have to find all the `switch` code and modify it.

As a rule of thumb, when you see `switch` you should think of polymorphism.

#### Treatment
- To isolate `switch` and put it in the right class, you may need Extract Method and then Move Method.
- If a `switch` is based on type code, such as when the program’s runtime mode is switched, use Replace Type Code with Subclasses or Replace Type Code with State/Strategy.
- After specifying the inheritance structure, use Replace Conditional with Polymorphism.
- If there aren’t too many conditions in the operator and they all call same method with different parameters, polymorphism will be superfluous. If this case, you can break that method into multiple smaller methods with Replace Parameter with Explicit Methods and change the `switch` accordingly.
- If one of the conditional options is `null`, use Introduce Null Object.

#### Payoff
Improved code organization.

#### When to Ignore
- When a `switch` operator performs simple actions, there’s no reason to make code changes.
- Often `switch` operators are used by factory design patterns (Factory Method or Abstract Factory) to select a created class.

###Temporary Field
#### Signs and Symptons
Temporary fields get their values (and thus are needed by objects) only under certain circumstances. Outside of these circumstances, they’re empty.

#### Reasons for the Problem
Oftentimes, temporary fields are created for use in an algorithm that requires a large amount of inputs. So instead of creating a large number of parameters in the method, the programmer decides to create fields for this data in the class. These fields are used only in the algorithm and go unused the rest of the time.

This kind of code is tough to understand. You expect to see data in object fields but for some reason they’re almost always empty.

#### Treatment
- Temporary fields and all code operating on them can be put in a separate class via Extract Class. In other words, you’re creating a method object, achieving the same result as if you would perform Replace Method with Method Object.
- Introduce Null Object and integrate it in place of the conditional code which was used to check the temporary field values for existence.

#### Payoff
Better code clarity and organization.

###Refused Bequest
#### Signs and Symptons
If a subclass uses only some of the methods and properties inherited from its parents, the hierarchy is off-kilter. The unneeded methods may simply go unused or be redefined and give off exceptions.

#### Reasons for the Problem
Someone was motivated to create inheritance between classes only by the desire to reuse the code in a superclass. But the superclass and subclass are completely different.

#### Treatment
- If inheritance makes no sense and the subclass really does have nothing in common with the superclass, eliminate inheritance in favor of Replace Inheritance with Delegation.
- If inheritance is appropriate, get rid of unneeded fields and methods in the subclass. Extract all fields and methods needed by the subclass from the parent class, put them in a new subclass, and set both classes to inherit from it (Extract Superclass).

#### Payoff
Improves code clarity and organization. You will no longer have to wonder why the `Dog` class is inherited from the `Chair` class (even though they both have 4 legs).

###Alternative Classes with Different Interfaces
#### Signs and Symptons
Two classes perform identical functions but have different method names.

#### Reasons for the Problem
The programmer who created one of the classes probably didn’t know that a functionally equivalent class already existed.

#### Treatment
Try to put the interface of classes in terms of a common denominator:
- Rename Methods to make them identical in all alternative classes.
- Move Method, Add Parameter and Parameterize Method to make the signature and implementation of methods the same.
- If only part of the functionality of the classes is duplicated, try using Extract Superclass. In this case, the existing classes will become subclasses.
- After you have determined which treatment method to use and implemented it, you may be able to delete one of the classes.

#### Payoff
- You get rid of unnecessary duplicated code, making the resulting code less bulky.
- Code becomes more readable and understandable (you no longer have to guess the reason for creation of a second class performing the exact same functions as the first one).

#### When to Ignore
Sometimes merging classes is impossible or so difficult as to be pointless. One example is when the alternative classes are in different libraries that each have their own version of the class.


