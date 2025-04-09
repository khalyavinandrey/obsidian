The role of messaging middleware is to decouple communications between collaborating parties. When a sender publishes a message, there is an assumption that the receiver (or receivers, as there may be multiple such parties) will eventually consume and process the message. Messaging middleware is generally divided into two categories: <u>those that offer at-most-once and those that offer at-least-once guarantees. And then we have Kafka, which has a foot in each camp.</u>

The at-most-once guarantee simply means that a message is never redelivered to its recipient, no matter the contingency. The consumer might read the record, but then fail for whatever reason before processing the record. If the offsets for the said record were committed before the record was processed, then the reassignment of the partition following the consumer’s failure will result in the skipping of the record by the new consumer.

<u>exactly-once semantics are not possible without tight-knit collaboration with the consumer application. As disappointing as it may sound, a messaging platform cannot offer exactly-once guarantees on its own</u>

To achieve the coveted exactly-once semantics, consumers in event streaming applications must be idempotent. In other words, processing the same record repeatedly should have no net effect on the consumer ecosystem

<u>The combination of at-least-once delivery and consumer idempotence collectively leads to exactly-once semantics.</u>


#effectivekafka 