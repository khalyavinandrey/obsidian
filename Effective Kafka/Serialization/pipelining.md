![[Pasted image 20250114185456.png]]
<u>The fetching, deserialization, and processing of records has now been separated into three stages, each powered by a dedicated thread</u>. For simplicity, we are going to refer to these as the I/O thread, the polling thread, and the processing thread. The I/O thread is native to the KafkaConsumer and its behaviour is unchanged from the previous example. The polling thread is altered in two crucial ways: 
1. Rather than invoking the EventListener in step 6, the thread will append the received record onto a bounded buffer. In a Java application, we can use an ArrayBlockingQueue or a LinkedBlockingQueue to implement this buffer. This operation will block if the queue is at its maximum capacity. 
2. Instead of committing the offsets of the recent batch, the polling thread will commit just those offsets that have been appended to the ‘pending offsets queue’ by the processing thread.

On the processing thread, we have the following steps: 
1. Remove the queued record from the bounded buffer. This operation will block if the queue is empty. 
2. Invoke the registered EventListener callbacks to process the record. 
3. Having processed the record, append a corresponding entry to the ‘pending offsets queue’. This entry specifies the topic-partition pair for the record, as well as its offset plus one.


