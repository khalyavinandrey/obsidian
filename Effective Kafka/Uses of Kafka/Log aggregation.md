![[Pasted image 20241230203703.png]]

Dealing with large volumes of log-structured events, typically emitted by application or infrastructure components. <u>Logs may be generated at burst rates that significantly outstrip the ability of querycentric datastores to keep up with log ingestion and indexing, which are regarded as ‘expensive’ operations.</u> Kafka can act as a <u>buffer, offering an intermediate, durable datastore</u>. The ingestion process will act as a sink, eventually collating the logs into a read-optimised database (for example, Elasticsearch or HBase).

#effectivekafka