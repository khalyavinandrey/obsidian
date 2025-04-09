> In an ideal world, each module would be completely independent of the others: a developer could work in any of the modules without knowing anything about any of the other modules.
> Unfortunately, this ideal is not achievable.
> Modules must work together by calling each others’s functions or methods. As a result, modules must know something about each other. There will be dependencies between the modules: if one module changes, other modules may need to change to match.

> The goal of modular design is to minimize the dependencies between modules.

> The best modules are those whose interfaces are much simpler than their implementations. Such modules have two advantages. First, a simple interface minimizes the complexity that a module imposes on the rest of the system. Second, if a module is modified in a way that does not change its interface, then no other module will be affected by the modification. If a module’s interface is much simpler than its implementation, there will be many aspects of the module that can be changed without affecting other modules.