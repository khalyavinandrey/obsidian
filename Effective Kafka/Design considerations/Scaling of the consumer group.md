Kafka will allocate partitions approximately evenly among members of a consumer group, up to the width of the topic.

Allocating a fixed number of instances to the group is usually not economical, as it may result in idle capacity, particularly for event streams that exhibit cyclic or bursty loading.

#effectivekafka