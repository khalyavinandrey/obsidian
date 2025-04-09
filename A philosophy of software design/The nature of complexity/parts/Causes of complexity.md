the next step is to understand what causes complexity, so that we can design systems to avoid the problems

Complexity is caused by two things: dependencies and obscurity.

* a dependency exists when a given piece of code cannot be understood and modified in isolation. the code relates in some way to other code, and the other code must be considered and/or modified if the given code is changed.
* changing the code for the sender almost always requires corresponding changes at the receiver, and vice versa

> one of the goals of software design is to reduce the number of dependencies and to make the dependencies that remain as simple and obvious as possible

The second cause of complexity is obscurity. Obscurity occurs when important information is not obvious. A simple example is a variable name that is so generic that it doesn’t carry much useful information (e.g., time). Or, the documentation for a variable might not specify its units, so the only way to find out is to scan code for places where the variable is used.

> In many cases, obscurity comes about because of inadequate documentation;
> The need for extensive documentation is often a red flag that the design isn’t quite right.

> Dependencies lead to change amplification and a high cognitive load. Obscurity creates unknown unknowns, and also contributes to cognitive load. If we can find design techniques that minimize dependencies and obscurity, then we can reduce the complexity of software.