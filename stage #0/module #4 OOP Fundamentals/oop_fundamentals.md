# Object Oriented Programming (OOP) Fundamentals
## Introduction
**_Object-Oriented Programming (OOP)_** is a programming methodology, which is based on functioning of software product as a result of interaction of objects, each of which is an instance of a particular class. _**Class**_ is a template of an entity, which defines its initial state and behaviour. _**Object**_ is an existing instance of an entity, which possesses certain state and behaviour. 

## Objects
Object is a core concept to understand OOP. Let's find an example of objects from real-world: a dog. All real-life objects have two main features: state and behaviour. Dogs have the following state: nickname, breed, color, character; and the following behaviour: barking, eating, guarding, wagging tail.
Software objects are conceptually similar to real-world objects: they consist of state and related behavior as well. An object stores its state in fields (variables) and defines its behavior through methods (functions). Methods operate on an object's internal state and serve as the primary mechanism for communication among objects.
More detailed information about objects can be found [here](https://docs.oracle.com/javase/tutorial/java/concepts/object.html).

## Classes
Class is a template, which objects are created from. In the real world, we can find many individual objects, which are of the same kind. There may be thousands of smartphones, which have the same make and model. Each this smartphone was built from the same set of blueprints and therefore contains the same components. In object-oriented terms, we say that somebody's smartphone is an instance of the class of objects known as "smartphones".

Example
```
class Smartphone {

    public Smartphone() {
        // it is a constructor, which a special method  
    }

    boolean isScreenTurnedOn = false; // an initial state of every smartphone is a turned-off screen;

    void turnOnScreen() {
        isScreenTurnedOn = true; // if a method is called, a screen of smartphone will be turned on;
    }

    void turnOffScreen() {
        isScreenTurnedOn = false; // if a method is called, a screen of smartphone will be turned off;
    }
}
```

### Declaration of Classes and its Members

#### Class Declaration
The simplest way to declare class is the following.
```
public class Bicycle {

   // The class has a name "Bicycle";
   
   // This class has no state (fields) and behaviour (methods). 
}
```
Here we declared an empty class body, which is an area between curly-braces ("{}").

#### Fields Declaration
In order to add state for a class, it is necessary to declare a field in a class body.
Field declarations contain three components in thw following order:
- (Optional) Modifier, which can be public, protected, private 
- (Required) Field Type;
- (Required) Field Name.
```
public class Bicycle {
    
    public int speed = 0; // now a class has a state: an initial speed is "0";
      
    // This class still has no state behaviour (methods).
}
```
Modifiers allow us to control, what other classes cann have access to a member field (this theme will be discussed further). Type is a parameter, which describes a structure of a class state. Fields can be of primitive type (int, float, boolean, etc.) and reference type (arrays and other objects). Names should follow the same naming rules and conventions (this theme will be discussed further).

#### Methods Declaration
In order to add behaviour for a class, it is necessary to declare a method in class body.
Method declarations contain components in the following order:
- (Optional) Modifier, which can be public, protected, private
- (Required) Return type;
- (Required) Method Name;
- (Required) Parentheses "()";
- (Required) Method Body.

A special case of return types is "void", which means that a method doesn't return anything. Keyword "return" is obligatory, in case of return type is not "void", and it is placed aside with a returning value. In parentheses there can be a list of parameters, which is input of a method. Such parameters are separated from each other by commas, the parameters consist of two components: type and name. 

```
public class Bicycle {
    
    public int speed = 0;
    
    // New behaviour, which allows a bicycle to move.
    // If a method is called, the following message will be printed: "A bicycle is moving at speed 0".
    public void move() {
        System.out.println("A bicycle is moving at speed " + speed);
    }
    
    // New behavior, which provide a current value of state "speed".
    public int getSpeed() {
        return speed;
    }
    
    // New behaviour, which allows to change a value of state "speed".
    // In order to call a method, it is necessary to pass a value of primitive "int" type, as a parameter.
    // if a method "getSpeed()" is called after that, a new value of "speed" will be returned. 
    public void increaseSpeed(int newSpeed) {
        speed = newSpeed;
    }
    
    // New behaviour, which allows to change a value of state "speed", which doesn't greater than a limit of "20".
    // Note, keyword "return" can be used in "void" case.
    public void increaseSpeed(int newSpeed) { // a parameter 
        if (newSpeed > 20) {
            return; // just terminates an execution of a method without changing a state "speed"
        }
        speed = newSpeed;
    }
}
```
