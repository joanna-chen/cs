# Topic 10: Java Memory Management
* memory allocation: class, interface, object, running method

## Memory allocation
* **call stack/runtime stack:** used for method information while method is being executed (local var, formal parameters, return value, where method should return to)
* **heap:** *static* information (interfaces, classes), *instance* information (objects)

## Call Stack/Runtime Stack
* memory space used for method information while method is being runtime
* when method invoked, *call frame/activation record* for method is created and pushed onto call stack
* **call frame:** contains address to return to when method ends, method's formal parameters, method's local vars, (return value)

## Heap Space
* **static space:** *one* copy of each class and interface named in program (contains static vars and methods)
* **object space:** information stored about *each* object (value of instance vars, type of object)
* object creation: memory is allocated in *heap* area when object created with ```new```
  * reference var put in call frame on runtime stack
  * object creating using memory in heap

## Memory Deallocation
* method returns
  * on *runtime stack*: call frame is automatically popped off, so memory is *deallocated*
  * object stays on heap even if no longer var referencing it
  * Java has automatic *garbage collection*: identifies objects no longer with var referencing and *deallocates* that memory
