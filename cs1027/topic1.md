# Topic 1: Object Oriented Programming

## Objects
* **attributes/fields/instance variables:** data about an object
* **methods:** actions
* objects belong to specific class
* OOP consist of interacting objects
* objects are defined by classes
* objects are created by other classes (*client classes*) which use them

## Class
* **class definition:** attribute declarations, constructor definitions, method definitions

### Constructor
* special method called when object is created with ```new``` operator
```Java
/**
* Constructor initializes the person's name
* and email address
*/
public Person(String firstName, String lastName,String email) {
this.lastName = lastName;
this.firstName = firstName;
this.email = email;
}
```

#### Overloading
* constructor can be written multiple times with different parameter lists
```Java
/**
* Constructor creates Person array of default size
*/
public SocialNetwork () {
friendList = new Person[DEFAULT_MAX_FRIENDS];
numFriends = 0;
}
/**
* Constructor creates Person array of specified size
* @param max maximum size of array
*/
public SocialNetwork(int max) {
friendList = new Person[max];
numFriends = 0;
}
```

### Terminology
* **scope:** parts of code in which those variables are known
* **accessor methods:** getters
* **modifier methods:** setters
* ```final```: represents a constant
*  ```[]```: array declarations
* **formal parameter:** variable in the parameter list in the method definition
* **actual parameter:** when method is invoked with parameter
* **modularity:** subdividing large problem into smaller components or *modules* to make solution easier
* **information hiding:** making implementation details inaccessible
* **encapsulation:** combining data and operations on the data (they are combined in class definition)
