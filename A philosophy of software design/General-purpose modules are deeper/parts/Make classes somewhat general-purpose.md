In my experience, the sweet spot is to implement new modules in a <u>somewhat </u>general-purpose fashion

The word “somewhat” is important: don’t get carried away and build something so general-purpose that it is difficult to use for your current needs

Let’s consider an example from a software design class in which students were asked to build simple GUI text editors. The editors had to display a file and allow users to point, click, and type to edit the file. The editors had to support multiple simultaneous views of the same file in different windows; they also had to support multi-level undo and redo for modifications to the file.

In reality, however, this specialization provided little benefit for the user interface code, and it created a high cognitive load for developers working on either the user interface or the text class. The text class ended up with a large number of shallow methods, each of which was only suitable for one user interface operation. Many of the methods, such as delete, were only invoked in a single place. As a result, a developer working on the user interface had to learn about a large number of methods for the text class.
