The reason why a distributed architecture is often chosen — assuming it is chosen correctly — is to enable the compartmentalisation of the problem domain. It can, if necessary, be decomposed into smaller chunks and solved in partial isolation, typically by different teams — then progressively integrated into a complete whole

Problems:
* coupling - Components are often inadvertently made aware of each other. This is called coupling — the degree of interdependence between software components. The lower the coupling, the greater the propensity of the system to evolve to meet new requirements, performance demands, and operational challenges
	* solution: Use of an asynchronous communication style and message-oriented middleware to segregate components
		* следовательно очереди сообщений частично решают проблему связанности сервисов
* resilience
* consistency - The stronger the consistency level, the more synchronisation is necessary to maintain it. The greater the requirement for consistency, the less distributed a system will be. Distributed systems must be tolerant of network partitions, but in achieving this tolerance, they will have to either give up consistency or availability guarantees

[[Event-Driven Architecture]]

#effectivekafka