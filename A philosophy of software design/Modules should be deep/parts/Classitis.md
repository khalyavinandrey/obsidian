Unfortunately, the value of deep classes is not widely appreciated today. The conventional wisdom in programming is that classes should be small, not deep

Students are often taught that the most important thing in class design is to break up larger classes into smaller ones. The same advice is often given about methods: “Any method longer than N lines should be divided into multiple methods” (N can be as low as 10). This approach results in large numbers of shallow classes and methods, which add to overall system complexity.

The extreme of the “classes should be small” approach is a syndrome I call classitis, which stems from the mistaken view that “classes are good, so more classes are better.”

Classitis may result in classes that are individually simple, but it increases the complexity of the overall system. Small classes don’t contribute much functionality, so there have to be a lot of them, each with its own interface. These interfaces accumulate to create tremendous complexity at the system level. Small classes also result in a verbose programming style, due to the boilerplate required for each class.

For example, to open a file in order to read serialized objects from it, you must create three different objects: 

FileInputStream fileStream = new FileInputStream(fileName); 
BufferedInputStream bufferedStream = new BufferedInputStream(fileStream);
ObjectInputStream objectStream = new ObjectInputStream(bufferedStream);

If an interface has many features, but most developers only need to be aware of a few of them, the effective complexity of that interface is just the complexity of the commonly used features

> - **Подход "маленьких классов"** (как у Роберта Мартина) хорош для читаемости и поддержки, но может привести к избыточности, если применять его бездумно.
> - **Подход "глубоких классов"** (как у автора текста) делает код более удобным для использования, но требует тщательного проектирования, чтобы не превратить класс в "монстра".
> Лучший подход — это баланс. Классы должны быть достаточно маленькими, чтобы решать одну задачу, но достаточно "глубокими", чтобы не усложнять жизнь разработчику.