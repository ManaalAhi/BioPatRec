# Introduction #

The conding standard used in this development is based in the proposed MATLAB coding standard by [Sandberg and Wahde at Chalmers University of Technology](http://www.me.chalmers.se/~mwahde/courses/aa/2012/MatlabCodingStandard.pdf)

## Header ##

Every source file must include this [header](Copyright_Notice.md)

## Coding Standard ##

Naming of variables, methods etc, should have descriptive names that give a direct indication to what it does.

### Variables ###

> e.g.: _tmpVar_

First letter shall always be in lower case. If the variable name includes multiple words, all words with the exception of the first shall start with an upper case.

> e.g.: _aLocalVariable_

Variables which lack direct meaning, such as temporary variables inside iterations, may ignore the requirements of having a descriptive name.

### Global variables and constants ###

Any global variable or constant shall be named using only upper case letters. If the name includes multiple words, each word shall be seperated with 

> e.g.: _'''A\_GLOBAL\_VARIABLE'''_


### Iteration varibles ###

For iterations; i, j and k shall be used. If needed, a more descriptive name should be used with i,j or k as a prefix.

> e.g. _iPatterns_

### Abbrevations in variables ###

If an abbrevation is to be used in a variable name, it shall be placed first in the name and be entirely in lower case.

> e.g. _emgSignal_

### Prefixes ###

Use of suitable prefixes is required.

For iterations, use i,j and k.

For quantaties, use n.

If dealing with weight or height, use w or h respectively.

## Functions ##

Names of functions or methods shall begin with upper case. If the function or method name includes multiple words, each word shall begin with upper case.

> _e.g.: ThisIsAFunction();_

See: [CamelCase](http://en.wikipedia.org/wiki/CamelCase)

## GUIs ##

Names of GUIs must start with "GUI_"_

> _e.g.: GUI\_ThisIsAFuction_

Components inside the GUI are consider as a variables so they follow the same criteria as variables with the addition of to letters that identifies it type of component.

> _e.g. A checkbox component would be named "cb\_variable"_

> _e.g. A pushbottom compoenet would be named "pb\_pushbottom"_


## Code layout ##

Code shall be grouped by the use of vertical whitespace to improve the readability of the code.
For iterations, indention shall be used to make it easily visible which lines of code belong to which iteration. If the programming environment does not support automatic indention, this shall be done by two horizontal whitespaces.


Matlab:
```
if ( condition )
   code
   code
else
   code
   code
end
```

C++:
```
if ( condition ){

}else{

}
```


Statements and equations shall be kept as short and simple as possible. Use of temporary variables is highly recommended.