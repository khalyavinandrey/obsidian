The most important technique for achieving deep modules is information hiding.

The basic idea is that each module should encapsulate a few pieces of knowledge, which represent design decisions. The knowledge is embedded in the module’s implementation but does not appear in its interface, so it is not visible to other modules.

The information hidden within a module usually consists of details about how to implement some mechanism. Here are some examples of information that might be hidden within a module: 
* How to store information in a B-tree, and how to access it efficiently. 
* How to identify the physical disk block corresponding to each logical block within a file. 
* How to implement the TCP network protocol. 
* How to schedule threads on a multi-core processor. 
* How to parse JSON documents.

> Information hiding reduces complexity in two ways. First, it simplifies the interface to a module. The interface reflects a simpler, more abstract view of the module’s functionality and hides the details; this reduces the cognitive load on developers who use the module.

> When designing a new module, you should think carefully about what information can be hidden in that module. If you can hide more information, you should also be able to simplify the module’s interface, and this makes the module deeper.

Information hiding only makes sense when the information being hidden is not needed outside its module. If the information is needed outside the module, then you must not hide it.