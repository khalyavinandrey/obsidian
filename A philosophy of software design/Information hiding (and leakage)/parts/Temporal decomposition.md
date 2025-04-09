> One common cause of information leakage is a design style I call temporal decomposition

> Consider an application that reads a file in a particular format, modifies the contents of the file, and then writes the file out again. With temporal decomposition, this application might be broken into three classes: one to read the file, another to perform the modifications, and a third to write out the new version. Both the file reading and file writing steps have knowledge about the file format, which results in information leakage

> The solution is to combine the core mechanisms for reading and writing files into a single class. This class will get used during both the reading and writing phases of the application

> When designing modules, focus on the knowledge that’s needed to perform each task, not the order in which tasks occur

