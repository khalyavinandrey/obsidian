An event is a significant state in change, that may be of interest within the domain where this state change occurred, or outside of that domain. Interested parties can be notified of an event by having the originating domain publish some canonical depiction of the event to a well-known conduit — a message broker, a ledger, or a shared datastore of some sort

* Coupling - loosely coupled, largely unaware of one another, only coupled with intermediate channels and representation events - schemas
	* Other solutions:
		* monolith: suffers from uncontrolled complexity growth
		* integration: no autonomous
		* shared data: change to the internal data representation in one system could have a catastrophic effect on another system.
* partially solve resilience problem
* consistency - creates sequential consistency and in causal order

For all its outstanding benefits, EDA is not a panacea and cannot supplant integrated or monolithic systems in all cases.
For instances, EDA is not well-suited to synchronous interactions, as mutual or unilateral awareness among collaborating parties runs contrary to the grain of EDA and negates most of its benefits

It is designed to be used in conjunction with other paradigms and design patterns, such as synchronous request-response style messaging, to solve more general problems. <u>In the areas where it can be applied, it ordinarily leads to significant improvements in the system’s non-functional characteristics. </u><u>Therefore, one should seek to maximise opportunities for event-driven compositions, refactoring the architecture to that extent.</u>

#effectivekafka