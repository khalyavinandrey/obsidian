Here are some questions you can ask yourself, which will help you to find the right balance between general-purpose and special-purpose for an interface.

<u>What is the simplest interface that will cover all my current needs?</u>

If you reduce the number of methods in an API without reducing its overall capabilities, then you are probably creating more general-purpose methods. The specialpurpose text API had at least three methods for deleting text: backspace, delete, and deleteSelection. The more general-purpose API had only one method for deleting text, which served all three purposes. Reducing the number of methods makes sense only as long as the API for each individual method stays simple; if you have to introduce lots of additional arguments in order to reduce the number of methods, then you may not really be simplifying things.

<u>In how many situations will this method be used?</u>

If a method is designed for one particular use, such as the backspace method, that is a red flag that it may be too special-purpose. See if you can replace several special-purpose methods with a single general-purpose method.

<u>Is this API easy to use for my current needs?</u>

If you have to write a lot of additional code to use a class for your current purpose, that’s a red flag that the interface doesn’t provide the right functionality