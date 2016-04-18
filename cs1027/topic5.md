# Topic 5: Unified Modeling Language
* diagrammatic way of showing relationship among classes

## Overview
* **unified modeling language (UML):** standard notation for object-oriented design
  * model object-oriented design
  * overall design: class specifications, how classes interact with each other
  * diagrams use specific icons and notation
  * *language independent*

## UML Class Design
* class represented by rectangle divided into 3 sections
  * **name** of class
  * **attributes** of class
  * **operations** of class

### Features
* attributes and operations may include:
  * **visibility:** public (+) or private (-)
  * **type** of attribute or operations
  * **parameter list** for operations
* attributes and operations may be left incomplete and completed as design is developed
```
visibility variable_name: type
visibility variable_name: type = default_value
visibility method_name(parameter_list): return_type
```

## Set of UML Class Diagrams
* shows classes used in system, *relationships*, *constraints* on connections among classes

### Features
* **association between classes:** represents relationship between objects of classes
  * indicated by *solid line* between classes
  * annotated with **cardinality:** numeric association between classes
    * one-to-one
    * one-to-many ( 1..* )
    * many-to-many ( * .. * )
    * zero-to-many ( 0..* )
* **usage of another class:** broken line with arrow indicates one class makes use of other
  * line can be labeled with a message indicating type of usage
* **implementation of an interface:** indication by broken line with open arrow
  * much like class UML diagram but no attributes

* **inheritance:** arrow on an association line indicates one class is derived from the other
