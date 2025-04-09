it is recommended to keep messages under 1MB to ensure optimal performance via reduced memory pressure and better network utilization.

It's a common anti-pattern in system design interviews to store large blobs of data in Kafka. Kafka is not a database, and it's not meant to store large files. It's meant to store small messages that can be processed quickly.

On good hardware, a single broker can store around 1TB of data and handle around 10,000 messages per second (this is very hand wavy as it depends on message size and hardware specs, but is a useful estimate). If your design does not require more than this, than scaling is likely not a relevant conversation.

TroubleShooting kafka producers and consumers:

Consumer retries:

set up a custom topic to store failed messages to and then have a separate consumer that processes these messages

Performance Optimizations:
грузить батчами в очередь

#systemdesign