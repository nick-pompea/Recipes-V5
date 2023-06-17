# Heap vs Stack

* class = heap reference to value
* struct = stack just value, and faster



 Value
 * struct, enum, string, int, etc
 * stored in stack
 * faster
 * thread safe by default
 * passing copy of data
 
 
 Reference
 * class, actor, function
 * stored in heap
 * slower but syncinized
 * not thread safe
 * passing reference (to reference instance is called pointer)

 
 Stack
 * stores value types 
 * each thread has its own stack
 * variables are stored directly to memory
 
 Heap
 * stores reference types
 * shared across threads
 
 
 
 Struct
 * based on value
 * can be mutated
 * stored in stack
 
 Class
 * references (aka Instances)
 * does not mutate, can just change value in the actual reference
 * stored in heap
 * classes can inherited from other classes
 
 Actor
 * same as class but thread safe
 
 
 ---
 when to use
 
 * Struct - data models, views
 * class - view model
 * actors - data manager, or shared classes
 
 Links:
- https://blog.onewayfirst.com/ios/post...
- https://stackoverflow.com/questions/2...
- https://medium.com/@vinayakkini/swift...
- https://stackoverflow.com/questions/2...
- https://stackoverflow.com/questions/2...
- https://stackoverflow.com/questions/2...
- https://www.backblaze.com/blog/whats-...
- https://medium.com/doyeona/automatic-...

[Youtube Tutorial](https://www.youtube.com/watch?v=-JLenSTKEcA)
