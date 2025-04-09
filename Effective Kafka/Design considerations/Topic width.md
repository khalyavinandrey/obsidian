increasing the number of partitions creates more opportunities for the consumer ecosystem to process records in parallel. Getting the topic width right is essential to a performant event streaming architecture

Regrettably, Kafka does not make this easy for us. Kafka only permits non-destructive resizing of topics when increasing the partition count.
Decreasing the number of partitions is a destructive operation — requiring the topic to be created anew, and manually repopulated.

increasing the number of partitions, in addition to consuming extra file handles, will result in increased memory utilisation on the brokers.
A similar impact will be felt on consumers, sans the file handles, which also employ per-partition buffers for fetching records

A further impact of wide topics may be felt due to the limitations of the inter-broker replication process and its underlying threading model. Specifically, a broker will allocate one thread for every other broker that it maintains a connection with, which covers the set of replicated partitions — where the two peers have a leader-follower relationship.
The replication threads may act as a bottleneck when shuttling records from the partition leader to in-sync replicas, and thereby impact the publishing latency when the producer requests all replicas to acknowledge the writes.

Confluent — one of the major contributors to Apache Kafka — recommends limiting the number of partitions per broker to 100 × b × r, where b is the number of brokers in a Kafka cluster and r is the replication factor
#effectivekafka