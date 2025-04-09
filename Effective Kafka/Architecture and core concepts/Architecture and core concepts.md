![[Pasted image 20250102145302.png]]

[[Broker nodes]]
[[Zookeeper nodes]]
[[Producers]]
[[Consumers]]
[[Total and partial order]]
[[Records]]
[[Partitions]]
[[Topics]]
[[Committing offsets]]
[[Free consumers]]

![[Pasted image 20250105205305.png]]

• A cluster hosts multiple topics, each having an assigned leader and zero or more follower replicas. 
• Topics are subdivided into partitions, with each partition forming an independent, totally-ordered sequence within a wider, partially-ordered stream. 
• Multiple producers are able to publish to a topic, picking a partition at will. The partition may be selected directly — by specifying a partition number, or indirectly — by way of a record key, which deterministically hashes to a partition number.
• Partitions in a topic can be load-balanced across a population of consumers in a consumer group, allocating partitions approximately evenly among the members of that group. 
• A consumer in a group is not guaranteed a partition assignment. Where the group’s population outnumbers the partitions, some consumers will remain idle until this balance equalises or tips in favour of the other side.
• A consumer will commit the offset of a record when it is done processing it. The commits are directed to a consumer coordinator, which will end up written to an internal __consumer_- offsets topic. The offset of the record is incremented by one before committing, to prevent unnecessary replay. 
• Partitions may be manually assigned to free consumers. If necessary, an entire topic may be assigned to a single free consumer — this is done by individually assigning all partitions.

#effectivekafka
