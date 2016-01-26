# Topic 4: Inheritance

## Overview
* **inheritance:** mechanism for deriving new class from existing one
  * can reuse existing classes
  * can organize classes in hierarchal manner

## Terminology
* **subclass:** the derived new class, also called the *child class* or the *derived class*
* **superclass:** from which the subclass inherits the attributes and methods, also called the *parent class* or *base class*
* use ```extends``` to make a subclass
```java
public class Square extends Rectangle {
  // stuff  
}
```

## Inheriting Visibility
* *public* variables and methods: children can access them directly (*except* the constructor)
* *private* variables and methods: children *cannot* access them directly
  * because this would violate encapsulation
* *protected* may be accessed directly by any class in the same package or by any subclass

## ```super``` Reference
* used in derived class to refer to its parent class
* access those members of parent class that are not inherited
* *invoking parent's constructor:* first line of child's constructor should be ```super(...);```
* allows invoke parent class method that was overridden in child class

### Superclass Variables
* variable of *superclass* type may reference object of *subclass* type
* variable of *subclass* type may not reference object of *superclass* type

## Is-a Relationship
* derived class *is a* more specific version of original class
* eg. a  ```Square``` object *is a* ```Rectangle```

## Overriding Methods
* derived class can define method with *same signature* as method in parent class
* child's method then **overrides** the parent's method
* *Note:* method defined with ```final``` modifier cannot be overridden

## Polymorphism
* **polymorphism:** principle that behavior can vary, depending on the type of object being manipulated
* with inheritance, a variable can refer to objects of different types during its lifetime

### Dynamic (Late) Binding
* **dynamic binding/late binding:** which method should be invoked is not known until run time, not known at compile time
* when a *superclass* variable references object of *subclass* type and method is invoked on object
  * the method must exist in superclass or there will be compiler error
  * if method also exists in the subclass, method from subclass is invoked (*overriding*)
  * if the method does not exist in the subclass, the method from the superclass is invoked

## Casting

### Casting Primitive Types
* changes the representation from one type to another
```java
int i, j, n;
n = (int) Math.random( ); // the brackets cast it to that type
double q = i / (double) j;
```

### Casting Reference Variables
* can cast from one class type to another within inheritance hierarchy
  * it can be cast lower
```java
Rectangle r = new Square(5);
System.out.println(( (Square) r).getSide( ));
```

## ```instanceof``` Operator
* tests whether referenced object in instance of particular class, returns boolean
* it's an operator!
```java
if (r instanceof Square)
{
System.out.println(((Square)r).getSide( ));
}
```

## Class Hierarchies
* derived class can be parent of classes derived from it
* single parent class can have many child classes
* **siblings:** children of same parent

## Java's Class Hierarchy (Object Class)
* class ```Object``` is at top of class hierarchy
  * defined in java.lang package

### ```Object``` methods
* **```toString``` method:** returns string containing *class name* followed by *hash code*
* **```equals``` method:** returns ```true``` if two object references refer to the same object
  * if current instance is reference type, it will test for reference equality
  * if current instance is value type, it will test for value equality

## More on ```Object``` Class
* variable of type ```Object``` can reference an object of any type
  * array whose elements are of type ```Object``` can store any type of object, can even have mix of object types
* when element of array is obtained, it can be cast to particular (sub)class type 
