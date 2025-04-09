Another form of API duplication across layers is a pass-through variable, which is a variable that is passed down through a long chain of methods.

> Pass-through variables add complexity because they force all of the intermediate methods to be aware of their existence, even though the methods have no use for the variables. Furthermore, if a new variable comes into existence (for example, a system is initially built without support for certificates, but you later decide to add that support), you may have to modify a large number of interfaces and methods to pass the variable through all of the relevant paths.

![[Pasted image 20250301234040.png]]

Eliminating pass-through variables can be challenging. One approach is to see if there is already an object shared between the topmost and bottommost methods:
there is an object containing other information about network communication, which is available to both main and m3. If so, main can store the certificate information in that object, so it needn’t be passed through all of the intervening methods on the path to m3
![[Pasted image 20250301234027.png]]
However, if there is such an object, then it may itself be a pass-through variable (how else does m3 get access to it?)

Another approach is to store the information in a global variable. This avoids the need to pass the information from method to method, but global variables almost always create
![[Pasted image 20250301234213.png]]

The solution I use most often is to introduce a context object. A context stores all of the application’s global state (anything that would otherwise be a pass-through variable). Most applications have multiple variables in their global state, representing things such as configuration options, shared subsystems, and performance counters. There is one context object per instance of the system. The context allows multiple instances of the system to coexist in a single process, each with its own context.
![[Pasted image 20250301234426.png]]
Contexts are far from an ideal solution. The variables stored in a context have most of the disadvantages of global variables; for example, it may not be obvious why a particular variable is present, or where it is used. Without discipline, a context can turn into a huge grab-bag of data that creates nonobvious dependencies throughout the system. Contexts may also create thread-safety issues; the best way to avoid problems is for variables in a context to be immutable. Unfortunately, I haven’t found a better solution than contexts