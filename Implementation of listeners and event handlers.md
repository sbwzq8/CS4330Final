# [HomePage](README.md)

Event Handlers/Listeners functions are very similar in both Java and C# with minor differences.

## Java

Listeners and Handlers are considered pretty analogous in Java, though a small definition difference remains.

In Java Listeners and Handlers can be considered to be pretty analogous although a small difference.

1. Listener - watches for an event to be fired, like a key press.  

2. Handler - handlers deal with events.  This is what to do with the action for the listener

In Java, both Handler's and Listener's are given in the JDK as libraries already and can be implemented on an object of the programmer's choosing. 

## C#

Event handler's take a tad more work in C# because they involve delegates.  A delegate is assigned to the event of the object you want to handle the event with the event handler.

Here is an example with the event.

```
Key.Press += new EventHanlder(Key_Press);

private void Key_Press(object send, EventArgs event) {
    something();
}
```
