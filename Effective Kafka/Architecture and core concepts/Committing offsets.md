It has already been said that consumers maintain an internal state with respect to their partition offsets. <u>At some point, that state must be shared with Kafka, so that when a partition is reassigned, the new consumer can resume processing from where the outgoing consumer left off.</u>

- [ ] Persisting the consumer state back to the Kafka cluster is called committing an offset.

<u>If a new consumer takes over the topic, it will commence processing from the last committed offset — hence the plus-one step is essential. (Otherwise, the last processed record would be handled a second time.)</u>

**<u>Controlling the point when an offset is committed provides a great deal of flexibility around delivery guarantees</u>**

at-most-once differs from at-least-once delivery model by simply moving the commit operation from a point before the processing of a record is commenced, to a point sometime after the processing is complete. With this model, should the consumer fail midway through processing a record, it will be re-read following partition reassignment.

By default, a Kafka consumer will automatically commit offsets at an interval of at least every five seconds

An implication of the offset auto-commit feature is that it extends the window of uncommitted offsets beyond the set of in-flight records; in other words, the consumer might finish processing a batch of records without necessarily committing the offsets.
If the consumer’s partitions are then reassigned, the new consumer will end up processing <u>the same batch a second time.</u>
![[Pasted image 20250105201417.png]]

To constrain the window of uncommitted records, one needs to take offset committing into their own hands. This can be done by setting the enable.auto.commit client property to false.

In the at-least-once scenario, a typical consumer implementation will commit its offsets linearly, in tandem with the processing of a record batch. That is, read a record batch from a topic, process the individual records, commit the outstanding offsets, read the next batch, and so on. This is called a poll-process loop

Алгоритм работы консюмера:
1) poll for records from kafka node
![[Pasted image 20250105202936.png]]

2) for each record do process, commit batch on consumer
![[Pasted image 20250105203205.png]]

A common tactic is to process a batch of records concurrently (where this makes sense), using a <u>thread pool</u>, and only confirm the last record when the entire batch is done.

The commit process in Kafka is very efficient, the <u>client library will send commit requests asynchronously to the cluster using an in-memory queue, without blocking the consumer</u>. <u>The client application can register an optional callback, notifying it when the commit has been acknowledged by the cluster</u>. And there is also a blocking variant available should the client application prefer it.

#effectivekafka