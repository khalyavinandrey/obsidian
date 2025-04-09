<u>change amplification</u>: a seemingly simple change requires code modifications in many different places. One of the goals of good design is to reduce the amount of code that is affected by each design decision, so design changes don’t require very many code modifications

<u>cognitive load</u>: how much a developer needs to know in order to complete a task. Cognitive load arises in many ways, such as APIs with many methods, global variables, inconsistencies, and dependencies between modules

> Sometimes an approach that requires more lines of code is actually simpler, because it reduces cognitive load.

<u>unknown unknowns</u>: it is not obvious which pieces of code must be modified to complete a task, or what information a developer must have to carry out the task successfully. An unknown unknown means that there is something you need to know, but there is no way for you to find out what it is, or even whether there is an issue.

Change amplification is annoying, but as long as it is clear which code needs to be modified, the system will work once the change has been completed. Similarly, a high cognitive load will increase the cost of a change, but if it is clear which information to read, the change is still likely to be correct. With unknown unknowns, it is unclear what to do or whether a proposed solution will even work. The only way to be certain is to read every line of code in the system, which is impossible for systems of any size. Even this may not be sufficient, because a change may depend on a subtle design decision that was never documented.

> One of the most important goals of good design is for a system to be obvious. This is the opposite of high cognitive load and unknown unknowns. In an obvious system, a developer can quickly understand how the existing code works and what is required to make a change.