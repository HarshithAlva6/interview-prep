**Basics -**
1. Variables point to objects/values in memory. Python is a high-level, interpreted, general-purpose programming language.
2. Type Conversion - 
Implicit(Automatic : Python always converts smaller data types to larger data types to avoid the loss of data)
Explicit(Manual : using int, str)
3. Raise Exceptions - Using try...except...finally
4. Conditions, Functions, Loops
5. Lists - Dynamic sized Arrays which aren't homogeneous.
6. Tuples - An immutable version of List.
7. Sets - Unordered collection data type that is iterable, mutable, and has no duplicate elements. 
8. Dictionary - Collection that stores data values like a map

**Modules:** File containing Python statements and definitions. Python package is a collection of python modules. Python module is a single python file.
execute help('modules') command in Python shell to get the list of *built-in modules*.
**Lambda:** Python Lambda Functions are anonymous function means that the function is without a name. x = lambda args: statements
**Decorator** takes a function, extends it and returns. Yes, a function can return a function. Python can simplify the use of decorators with the @ symbol.
**Iterator:** Object that can be iterated upon, meaning that you can traverse through all the values. LTSD are iterables, with iter() and next()
**Regular expressions** are a powerful language for matching text patterns. 
1. re.search() method takes a regular expression pattern and a string and searches for that pattern within the string. If the search is successful, search() returns a match object[match.group()] or None otherwise.
2. findall() finds *all* the matches and returns them as a list of strings, with each string representing one match.
a, X, 9, < -- ordinary characters just match themselves exactly.
. (a period) -- matches any single character except newline '\n'
\w -- (lowercase w) matches a "word" character: a letter or digit or underbar [a-zA-Z0-9_]. 
\W (upper case W) matches any non-word character, i.e., whole word.
\b -- boundary between word and non-word
\s -- (lowercase s) matches a single whitespace character -- space, newline, return, tab, form [ \n\r\t\f]. 
\S (upper case S) matches any non-whitespace character.
\t, \n, \r -- tab, newline, return
\d -- decimal digit [0-9] 
^ = start, $ = end -- match the start or end of the string
\ -- inhibit the "specialness" of a character. 

**Data Structures -**
1. Arrays and Linked Lists
2. Hash Table, Map, HashMap, Dictionary or Associative are all the names of the same data structure. 
3. Stacks(LIFO), Queues(FIFO), Heaps(Priority Queue)
4. Binary Search trees
5. Recursion

**Package Managers** allow you to manage the dependencies using   PyPI and Pip