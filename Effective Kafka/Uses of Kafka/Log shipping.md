![[Pasted image 20241230203910.png]]

Log shipping is a key enabler for another related architectural pattern — event sourcing. Kafka will act as a durable event store, allowing any number of consumers to rebuild a point-in-time snapshot of their application state by replaying all records up to that point in time. Loss of state information in any of the downstream consumers can be recovered by replaying the events from the last stable checkpoint, thereby reducing the need to take frequent backups.

#effectivekafka