Kafka’s producer-topic-consumer topology adheres to a flexible and highly generalised multipoint-to-multipoint model, meaning that there may be any number of producers and consumers simultaneously interacting with a topic
Depending on the actual solution context, topologies may also be point-to-multipoint, multipoint-to-point, and point-to-point

A consumer is a process or thread that attaches to a Kafka cluster via a client library. A consumer generally, but not necessarily, operates as part of an encompassing consumer group. <u>Consumer groups are effectively a load-balancing mechanism within Kafka — distributing partition assignments approximately evenly among the individual consumer instances within the group</u>. When the first consumer in a group subscribes to the topic, it will receive all partitions in that topic. When a second consumer subsequently joins, it will get approximately half of the partitions, relieving the first consumer of half of its prior load. The process runs in reverse when consumers leave (by disconnecting or timing out) — the remaining consumers will absorb a greater number of partitions.

<u>A consumer internally maintains an offset that points to the next record in a partition, advancing the offset for every successive read</u>. In fact, a consumer maintains a vector of such offsets — one for each assigned partition.

When a consumer first subscribes to a topic, whereby no offsets have been registered for the encompassing consumer group, <u>it may elect to start at either the head-end or the tail-end of the topic</u>. Thereafter, the consumer will acquire an offset vector and will advance the offsets internally, in line with the consumption of records.

![[Pasted image 20250105151055.png]]


As part of fulfilling the subscriptions, Kafka will allocate partitions among the members of each group. In turn, each group will acquire and maintain a dedicated set of offsets that reflect the overall progress of the group through the topic.

![[Pasted image 20250105151204.png]]

consumers A2 and B0 aren’t there. That is because Kafka ensures that a partition may only be assigned to at most one consumer within its consumer group
In this manner, consumer groups are not only a load-balancing mechanism, but also a fence-like exclusion control, used to <u>build highly performant pipelines without sacrificing safety, particularly when there is a requirement that a record may only be handled by one thread or process at any given time.
</u>

Consumer groups also ensure <u>availability</u>, satisfying the liveness property of a distributed consumer ecosystem

By periodically reading records from a topic, the consumer implicitly signals to the cluster that it is in a ‘healthy’ state, thereby extending the lease over its partition assignment. Should the consumer fail to read again within the allowable deadline, it will be deemed faulty and its partitions will be reassigned — apportioned among the remaining ‘healthy’ consumers within its group.

#effectivekafka