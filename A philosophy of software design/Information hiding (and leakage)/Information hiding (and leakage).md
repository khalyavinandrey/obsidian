This chapter, and the next few that follow, discuss techniques for creating deep modules.
[[Information hiding]]
[[Information leakage]]
[[Temporal decomposition]]

> When decomposing a system into modules, try not to be influenced by the order in which operations will occur at runtime; that will lead you down the path of temporal decomposition, which will result in information leakage and shallow modules

> Instead, think about the different pieces of knowledge that are needed to carry out the tasks of your application, and design each module to encapsulate one or a few of those pieces of knowledge. This will produce a clean and simple design with deep modules.