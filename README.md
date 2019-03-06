# Scarlet-File
___
This is a documentation of the progress made on my project.

Scarlet File is part of the private VastHeap domain project that publishes my researches and software for educational purposes.

This tool is focused on two main features. The first is a custom scripting editor that allows direct interaction with the analyzing process. It can overrides pre-set and hardcoded instructions, as well as introduce new rules.
A simple example would be the following script:

```sh
if file.md5 = {1D420D66250BCAAAED05724FB34008CF,D01628AF9F7FB3F415B357D446FBE6D9,8A4883F5E7AC37444F23279239553878}
    messagebox [File MD5 matches a trusted Microsoft MD5 signature hash, information]
```
Goes without saying that the default operators are functional.

| Operator        |     Explaination       |   
| ------------- |:-------------:| 
|=|Checks if both values are equal / Sets a value|  
|!=|Checks if both values are not equal|    
|>|Checks if the value on the left is larger than that on the right|
|<|Checks if the value on the left is smaller than that on the right|
|>=|Checks if the value on the left is larger than or equal to the one on the right|
|<=|Checks if the value on the left is smaller than or equal to the one on the right|
___

Second feature would be cloud computing. Even though the tool has many features (string, pe headers, and module analysis, and executable extractor); I am aiming to make it all real-time cloud based by using .NET as the multi-threaded serving server, and PHP as the frontend regulator that handles requests, run simple checks and so forth. Progress on this end is limited within my website which is not available to the public unforunately. 
