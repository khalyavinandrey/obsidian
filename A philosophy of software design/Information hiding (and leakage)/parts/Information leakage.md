The opposite of information hiding is information leakage. Information leakage occurs when a design decision is reflected in multiple modules

> This creates a dependency between the modules: any change to that design decision will require changes to all of the involved modules. If a piece of information is reflected in the interface for a module, then by definition it has been leaked

> Information leakage is one of the most important red flags in software design. One of the best skills you can learn as a software designer is a high level of sensitivity to information leakage

> If the affected classes are relatively small and closely tied to the leaked information, it may make sense to merge them into a single class. Another possible approach is to pull the information out of all of the affected classes and create a new class that encapsulates just that information

One team used two different classes for receiving HTTP requests; the first class read the request from the network connection into a string, and the second class parsed the string. This is an example of a temporal decomposition (“first we read the request, then we parse it”). Information leakage occurred because an HTTP request can’t be read without parsing much of the message

As a result, both classes needed to understand most of the structure of HTTP requests, and parsing code was duplicated in both classes

Because the classes shared so much information, it would have been better to merge them into a single class that handles both request reading and parsing. This provides better information hiding, since it isolates all knowledge of the request format in one class, and it also provides a simpler interface to callers (just one method to invoke).

> This example illustrates a general theme in software design: information hiding can often be improved by making a class slightly larger

> Of course, it is possible to take the notion of larger classes too far (such as a single class for the entire application). Chapter 9 will discuss conditions under which it makes sense to separate code into multiple smaller classes.

> Most of the student projects made two good choices with respect to parameter handling. First, they recognized that server applications don’t care whether a parameter is specified in the header line or the body of the request, so they hid this distinction from callers and merged the parameters from both locations together. Second, they hid knowledge of URL encoding: the HTTP parser decodes parameter values before returning them to the Web server, so that the value of the comment parameter in Figure 5.1 will be returned as “What a cute baby!”, not “What+a+cute+baby%21”). In both of these cases, information hiding resulted in simpler APIs for the code using the HTTP module.

> The best features are the ones you get without even knowing they exist.