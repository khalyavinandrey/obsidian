[[Partitions]] are too basic to be used effectively on its own

A topic is a logical aggregation of partitions. It comprises one or more partitions, and a partition must be a part of exactly one topic. Topics are fundamental to Kafka, allowing for both parallelism and load balancing.

A producer application may explicitly assign a partition number when publishing a record, although this approach is rarely used. <u>A much more common approach is for the client application to deal exclusively with record keys and values, and have the producer library automatically select a partition on the basis of a record’s key</u>

A producer will digest the byte content of the key using a hash function (Kafka uses murmur2 for this purpose)

Producers rarely care which specific partition the records will map to, only that related records end up in the same partition, and that their order is preserved. Similarly, consumers are largely indifferent to their assigned partitions, so long that they receive the records in the same order as they were published, where those records are causally bound.

#effectivekafka