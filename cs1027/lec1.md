# Lecture 1

* data structures: stacks, queues, lists, trees

## Review: Objects
*  **object:** entities that do actions/be acted upon in Java program
  * **attributes:** data about an object
  * **methods:** actions
<b></b>
* objects belongs to specific class
* can invoke a class' method on any of that class' instance
* objects are defined by classes
* OOP consists of interacting objects
* objects are created by other classes which use them in implementing a programming solution to a problem
* **class definition:**: attribute declarations, constructor defintiions, method definitions
<b></b>
```Java
/* Attribute declarations */
public class Person {
  private String lastName;
  private String firstName;
  private String email;
}
```
* **public:**: you can see it in another class
* **private**: can't be seen, which is where getter and setter methods come into play (methods can also be private or public)
<b></b>
* **constructor**: special method that is automatically called when object is created with *new* operator
  * initialize attributes
```Java
/* the constructor */
public Person(String firstName, String lastName, String email) {
  this.lastName = lastName;
  this.firstName = firstName;
  this.email = email;
}
