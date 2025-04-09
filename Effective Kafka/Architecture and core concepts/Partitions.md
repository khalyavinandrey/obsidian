Published records are appended to the headend of the encompassing partition

in the absence of producer synchronisation, causal order can only be achieved when a single producer emits records to the same partition. All other combinations — involving multiple unrelated producers or different partitions — may result in a record stream that fails to depict causality

A record’s offset ([[Records]]) uniquely identifies it in the partition. The offset acts as a primary key, allowing for fast, O(1) lookups

The offset is a strictly monotonically-increasing integer in a sparse address space, meaning that each successive offset is always higher than its predecessor, and there may be varying gaps between neighbouring offsets. <u>Gaps might legitimately appear if compaction is enabled or as a result of transactions</u>

![[Pasted image 20250105142626.png]]

Conversely, the <u>high-water mark is the offset immediately following the last successfully replicated record</u>. <u>Consumers are only allowed to read up to the high-water mark</u>. <u>This prevents a consumer from reading unreplicated data that may be lost in the event of leader failure</u>. The equivalent term for a high-water mark is the end offset

#effectivekafka