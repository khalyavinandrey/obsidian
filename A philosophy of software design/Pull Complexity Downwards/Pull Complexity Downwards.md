it is more important for a module to have a simple interface than a simple implementation.
Configuration parameters are an example of moving complexity upwards instead of down. Rather than determining a particular behavior internally, a class can export a few parameters that control its behavior, such as the size of a cache or the number of times to retry a request before giving up. Users of the class must then specify appropriate values for the parameters.

> Pulling complexity down makes the most sense if (a) the complexity being pulled down is closely related to the class’s existing functionality, (b) pulling the complexity down will result in many simplifications elsewhere in the application, and (c) pulling the complexity down simplifies the class’s interface. Remember that the goal is to minimize overall system complexity.

