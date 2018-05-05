# [HomePage](README.md)

Java and C# both support null, however C# is a little safer in doing so.

## Java

Pretty much the same thing as C#, but does not allow types to be "lifted"

## C#

Supports null values and lifted.  So, lifted puts a wrapper around it so that when someone tries dereferencing a null value,
it automatically throws an exception rather than throwing an error on the system.