# [HomePage](README.md)
### C# and java use namespaces quite differently

# Implementing and Using namespaces

## java
### java namespaces are implemented as packages in the directory of the program. In order for an application to run, it's namespace must be declared as the package in all .java files associated with it. Any imported namespaces must be declared using an import. The package the program is contained in must have the same name as the main java file, but in lower case letters.
```Java
package finalproject;

import java.util.ArrayList;
import java.util.Objects;
import java.math.*;

public class FinalProject(){
    ...
}
```
#### In this java example, the namespace of the project is finalproject and it imports two existing classes, ArrayLists and Objects, from java.util, as well as all classes within java.math. When using imports, the import must declare the name of a class inside the package, or the declaration must include a wildcard to import all classes within the package.


## C#
#### In C#, namespaces are implemented as a class structure for an application. Namespaces are not necessarily tied to the directory structure in C# as they are with java. In C#, once a globabl namespace is declared, all namespaces within its scope can be called
```CS
using System;
using DictionaryList = System.Collections.Generic.List<System.Collections.Generic.Dictionary<string, string>>;
//Alias
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Math.Abs(-14));
            //Abs is within the Math namespace, which is in the System namespace

            DictionaryList DictionaryList = new DictionaryList();
            //using alias
        }
    }
}
```
#### In c#, aliases can be created for a namespace, and an individual namespace can be declared with its path.