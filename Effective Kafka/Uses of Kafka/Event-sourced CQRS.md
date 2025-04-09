![[Pasted image 20241230205012.png]]

Because mutations and queries typically exhibit contrasting runtime characteristics and require vastly different, often contradictory optimisation decisions, the separation of these concerns is conducive to building highly performant systems. The flip side is complexity — requiring multiple datastores and duplication of data — each datastore will maintain a unique projection of the master dataset, built from a dedicated data pipe

#effectivekafka