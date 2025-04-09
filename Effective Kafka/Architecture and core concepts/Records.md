A record is the most elemental unit of persistence in Kafka
attributes:
* key: optional, grouping related records on the basis of their key
* value: optional (null value is largely pointless), informative payload of record,
* headers: key-value pairs that can optionally annotate a record
* partition number: a zero-based index of the partition that the record appears in
* offset
* timestamp: may be set explicitly by the producer to an arbitrary value, or it may be automatically assigned by the broker when a record is appended to the log

#effectivekafka