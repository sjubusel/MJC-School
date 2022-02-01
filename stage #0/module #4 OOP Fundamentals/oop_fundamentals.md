# Object Oriented Programming (OOP) Fundamentals
## Introduction
**_Object-Oriented Programming (OOP)_** is a programming methodology, which is based on functioning of a software product as a result of interaction of objects, each of which is an instance of a particular class. _**Class**_ is a template of an entity, which defines its initial state and behaviour. _**Object**_ is an existing instance of an entity, which possesses certain state and behaviour. 

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
Field declarations contain three components in the following order:
- (Optional) Modifier, which can be public, protected, private;
- (Required) Field Type;
- (Required) Field Name.
```
public class Bicycle {
    
    public int speed = 0; // now a class has a state: an initial speed is "0";
      
    // This class still has no behaviour (methods).
}
```
Modifiers allow us to control, what other classes can have access to a field (this theme will be discussed further). Type is a parameter, which describes a structure of a class state. Fields can be of primitive type (int, float, boolean, etc.) and reference type (arrays and other objects). Names should follow the same naming rules and conventions (this theme will be discussed further).

#### Methods Declaration
In order to add behaviour for a class, it is necessary to declare a method in class body.
Method declarations contain components in the following order:
- (Optional) Modifier, which can be public, protected, private
- (Required) Return type;
- (Required) Method Name;
- (Required) Parentheses "()";
- (Required) Method Body.

A special case of return types is "void", which means that a method doesn't return anything and just performs actions within a method body. Keyword "return" is obligatory in case of return type is not "void", and it is placed aside with a returning value. Anyway, "return" always terminates an execution of a method. In parentheses there can be a list of parameters, which is input of a method. Such parameters are separated from each other by commas, the parameters consist of two components: type and name. 

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
    
    // New behaviour, which allows to change a value of state "speed", which isn't greater than a limit of "20".
    // Note, keyword "return" can be used in "void" case.
    public void increaseSpeedWithLimit(int newSpeed) { // a parameter named "newSpeed" of the primitive type "int"  
        if (newSpeed > 20) {
            return; // just terminates an execution of a method without changing a state "speed"
        }
        speed = newSpeed;
    }
}
```

### Constructor
In order to start to use a class, it is necessary to create its object. Here are creation steps:
1) Create a variable of an object:
```
Bicycle bicycle; 
```
A created variable doesn't contain object. Variable of reference types (arrays and objects) don't contain objects themselves, they are used in order to store references (addresses) of objects (instances of classes) in memory. Initially, the variable will only have an empty value called `null`. 

2) Initialize a variable by the means of an operator `new`, which invokes a constructor and therefore allocates memory for an object. 
```
bicycle = new Bicycle();
```
The first and the second step can be merged.
```
Bicycle bicycle = new Bicycle();
```

As you may notice a constructor is a special construction, which is obligatory to create an object. Constructor itself is a special method, which is being called while object creation. Requirements for a constructor:
- it must have a name, which is similar to a name of a class;
- it must not have any return value, even "void".

Constructor declarations contain components in the following order:
- (Optional) Modifier, which can be public, protected, private
- (Required) Class Name; 
- (Required) Parentheses "()";
- (Required) Constructor Body.

Obviously you may pay attention that the previous example of a class doesn't have any constructors, but we were able to invoke it. It's because when we don't explicitly write any constructor, the compiler adds a default, no-argument constructor.
```
public Bicycle(){ // a default no-argument constructor with an empty body
}
```
A default no-argument constructor will simply set all members to their default values. "Defaults" for primitive type can be found [here](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html), regarding reference types the default value will be `null`.
A common scenario of using constructors is to define in a constructor's body a required state of an object.
```
public Bicycle(){
    speed = 5; // initilizes a bicycle object with a initial state of speed as "5".
}
```

Constructors can have input parameters as well as in methods. These constructors are called "parameterized". In this case while object creation we may specify values for these parameters. 
```
// An example of a "parametrized" constructor
public Bicycle(int speed){
    this.speed = speed; // initilizes a bicycle object with a initial state of speed defined at the time of object creation
}
```

We may specify several constructors with different parameters in a class, but it is worth noting that if one or more parametrized constructors are specified, the compiler won't add a default, no-argument constructor. In this case if it is required, we will have to specify a no-argument constructor explicitly.

In case when a name of a constructor's parameter and a name of a class field are equal (`name`), it is necessary to use a keyword `this` with a dot (`this.`) before a name of a class field in order to refer it and exclude a conflict of names. The keyword `this` is a reference to an object, which called a current method, where the execution is performed. 

The keyword `this` can be used in order to call a constructor from another constructor.
```
public class Bicycle {

    ...

    public Bicycle(int speedFromConstructor) {
        speed = speedFromConstructor;
    }

    public Bicycle() {
        this(5); // when a default no-argument constructor is called, a new "bicycle" object is created with a state of speed "5"
    }

}
```

### Overloading
Process of specifying of several constructors in one class is called as "overloading", the same refers to methods. "Overloading" is a definition of methods with the same name, but different signatures. Actually such methods are completely different methods, which have only the same name in common. A signature of methods is defined by a name of a method, a quantity and types of its parameters. A return type is not included in a method signature, it means that the following construction lead to a compilation error.
```
public class RandomObject {
    public void method() {
        
    }
    
    public int method() { // Compilation error: "method method() is already defined in class Scratch"
        return 1;
    }
}
```

After creation of an object, we can refer to its fields with the help of their name and can change values of the fields.
```
Bicycle bicycle = new Bicycle(5);
System.out.println(bicycle.speed); // Output: 5
bicycle.speed = 10;
System.out.println(bicycle.speed); // Output: 10
```

