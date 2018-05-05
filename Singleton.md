# [HomePage](README.md)


Singleton's are used in very similar ways in both Java and C#

## Java

Singleton's are a class that has only one instance.  They take advantage of static classes and are usful for things like database licenses.

For something to be a singleton in Java, you must incllude a private construtor and an initializer to make sure there aren't an other objects created.  To access this class one would use the getInstance class.

Tutorialspoint.com has an example of with the following. 

```
public class Singleton {

    private static Singleton singleton = new Singleton( );

    private Singleton() { }

    public static Singleton getInstance( ) {
        return singleton;
    }

}
```
    
This is a prefect example of singletons.

The given Singleton is also thread safe as well, because the Singleton at class load time and any call of getInstance calls the already created instance.  

A lazy instance of a singleton which is special below:

```
public class MySingle {

private static MySingle instance = null;
private MySingle() {
    
}

public static MySingle getInstance() {
    if(instance == null) {
        instance = new MySingle();
    }
    return instance;
  }
}
```
    
## C#

In C#, singleton's are implemented in a similar way, except it is also includes lazy implementation.