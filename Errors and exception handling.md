# [HomePage](README.md)

## Java
Here are the following definitions.
    1. Error: a serious problem that should be notified and should not be caught in a try catch because of its severity
    2. Exception: a sitiuation that isn't program breaking and helps keep the program running
    
A standard try/catch block as follows:

```
try {
} catch (ExceptionType e) {
} 
``` 

Things that should go through a try catch are items that don't comprimise the stability of the program.
So this would include things like files that are not found.

There are other exceptions as well that are harder to catch, like ArrayOutOfBounds.  

Exceptions allow the developer to have things run even if they fail.  It just ensures that the program is still
functional by the end.

Errors are usually not possible to recover from.  Typically this will crash the program and the data is hard to find.

## C#

C# and Java handle these in very similar ways.