# Scripting documentation
# Overhaul is due. This is old documentation.
___
### (1) Implemented features
- Case insensitive for code and inputs (Unless stated otherwise by a **"(s)"** at the end of the input, ex: "if abc = ABC **(s)**" will return false)
 
- Code indenting is only _required_ for the first main "**if statement**", which is on purpose and intended for a more flexible scripting experience. [All code statements/events do not require an indent; **_Check section (2)_**]
![Image](https://image.prntscr.com/image/fQKccDyTTuicdmj5ZcbvPw.png)
 
- Comparing against singular or array values is possible (Example: _"if file.size = 1234"_ or _"if file.size = {123, 456, 789}"_) -- Array values are separated by "," and surrounded by double-brackets, **“{xx,yy}”**.
 
- Retrieving the matched and actual values from the previous met "if statement" is possible by using the keyword **(m)** for the "Matched Value" or **(v)** for the "Actual Value".
> Matched Value is the input given by the user, however the Actual Value is the absolute one extracted by the program.

Say the following "if statement" is executed and returns **true** (_Returns true indicates that the **condition is met**, in this case the size of the file being larger **">"** than 1000 bytes_) :
 ```sh
 if file.size > 1000
     messagebox[File size is {v} and is larger than {m}]
 ```


> Note: **(m)** also supports arrays, meaning it will return only the value matched from the array.
 
- Messageboxes support different styles; **Information**, **Critical** & **Exclamation**. This is done by adding a style name at the end of the messagebox text separated by a ",".
**Example Code**:
```
Messagebox[This is an information box, information|critical|exclamation]
```
___
### (2) Current Statements/Events;
**What are statements?** They are events with the ability to be fired independently, without or after an "**if statement**".

**( ) - Optional Value | « » - Required Value**

> If statement - Script Syntax: **if** __«method»__ __«operator»__ __«input»__
>- **«Method»**: Is a value retrievable from the program
>- **«Operator»**: Allows for comparison between the Method retrieved value and the **«input»**
>- **«Input»**: Value given by the user in comparison with the Method

> Messagebox - Script Syntax: **messagebox** **[«text», (style)]**
>- **«text»** is the message the user wishes to prompt
>- **(style)** is the messagebox style, either **information**, **critical** or **exclamation**.

> **Reload/Restart/Reopen** - Any of these events reload the program

> **Exit/Close/End** - Any of these events close the program

### (3) Current Methods;
> **File.Size** : Size of the file loaded
- **Supported Operators**: (=, !=, <, >, <=, >=)
- **Type**: Integer
- **Special Characters**: (mb, mbytes, kb, kbytes)
- **ReadOnly**

> **File.MD5** : MD5 hash of the loaded file
- **Supported Operators**: (=, !=)
- **Type**: String
- **ReadOnly**
- **Supports array inputs**

> **File.SHA1** : SHA1 hash of the loaded file
- **Supported Operators**: (=, !=)
- **Type**: String
- **ReadOnly**
- **Supports array inputs**

> **Scan.Type** : The selected string scanning option
- **Supported Operators**: (=, !=)
- **Type**: String
- **Read/Write**: (Default, Advanced, Misc)
___
### (4a) If Statement
To begin with, an indent is single press of the Tab button, which means the line of code is a follow-up to a certain met condition.

**If Statements** are powerful if correctly used. As implied by the name, they are statements which check if a particular condition is met or not. If an **if condition** returns **true** (the condition is met), any indented code below it will execute. However, if an **if condition** is not met yet the code below it is _not_ indented at least **once**, this code will execute no matter what. [**Check _section (1)_**]

One way to execute code while the **if statement**'s condition is not met is by using **"else"**, if the condition is _not_ met (returns false), any indent code that follows the **else** statement will run. However, if the **if condition is met** (returns true), the code that follows else will not run.

Code:
```sh
if file.size > 10mb
    messagebox[File size is larger than 10mb]
    else
    messagebox[File size is smaller than 10mb]
```
**Explained If statement code is provided in _section (3)_**

___
### (4b) Arrays & Singular Values
File Inspect's scripting language strong point is the ability to dodge and foresee possible code errors, thus most common mistakes the user may make is already countered, which includes comparisons.

### FAQ:
**What's an array?** It's a list of values, each assigned with its own ID (Referred to as "index"), which can be compared against another array list, singular value or to be overwritten completely by either if it supports Read/Write.

**What if a method does not support array inputs but was assigned with one?** This specific code line will be dodged and not executed while returning compilation error to notify the user.

**What if a method returns an array list but was compared against a singular value?** It will loop within the method's array list and return true if the singular input value is found within the array. (Supports overwriting if the method allows it)

**What if a method returns a singular value but was compared against an array list?** It will loop within the given array and return true if the method's value is found within. (Does not support overwritting)

**All methods and their array leniency are listed at _section (3)_** 

**What if a method accepts array lists and was given one?** The given array list will overwrite the method's array which cannot be undone.

Code:
```sh
if file.md5 = {1D420D66250BCAAAED05724FB34008CF,D01628AF9F7FB3F415B357D446FBE6D9,8A4883F5E7AC37444F23279239553878}
    messagebox [File MD5 matches a trusted Microsoft MD5 signature hash, information]
```

**All values in the array list are separated by ",". Any spaces found at the start or end of an array value are ignored when comparing to improve accuracy**

Currently it is unimplemented to return an array value's index, or to modify/delete an array value using an index.

___
### (4c) Operators & Inputs
**What are operators?** They keywords which allow for comparisons to be done. Operators can be used when reading or writing a value.

| Operator        |     Explaination       |   
| ------------- |:-------------:| 
|=|Checks if both values are equal / Sets a value|  
|!=|Checks if both values are not equal|    
|>|Checks if the value on the left is larger than that on the right|
|<|Checks if the value on the left is smaller than that on the right|
|>=|Checks if the value on the left is larger than or equal to the one on the right|
|<=|Checks if the value on the left is smaller than or equal to the one on the right|

An example between retrieving and overwriting a value:
```sh
if scan.type = default
    messagebox[Scan Type is default]
```
```sh
if scan.type = default
    scan.type = advanced
    messagebox[Scan Type was default and is now set to advanced. Overwritting a value does not require an if statement either]
```


---
### (5) Pending implementation;
> Addition of "or/and" statements

> Adding a debug mode in the program where it shows the highlighted forum's control reference ID/Name (Which would allow for further scripting expansion, Ex: executing code only when an event is fired). **Pseudocode**:


```sh
on button_load click
    messagebox[The load button was clicked]
 ```
or
 ```sh
on file load
    messagebox[File has been loaded]
 ```
> Adding more events; removal of a string, changing text/forecolor of labels, cancelling an event (..)
