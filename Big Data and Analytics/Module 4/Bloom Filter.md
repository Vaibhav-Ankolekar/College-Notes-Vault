# Bloom filter

A Bloom filter is a data structure that offers a membership query mechanism where the answer to a lookup is one of two values: a definitive no, meaning that the item being looked up doesn’t exist in the Bloom filter, or a maybe, meaning that there’s a probability that the item exists. Bloom filters are popular due to their space efficiencies. They represent the existence of N elements requires much less than N positions in the data structure, which is why the membership query can yield false positive results. The amount of false positives in a Bloom filter can be tuned, which we’ll discuss shortly.

Bloom filters are used in BigTable and in HBase to remove the need to read blocks from disk to determine if they contain a key. They’re also used in distributed network applications such as Squid to share cache details between its multiple instances without having to replicate the whole cache or incur a network I/O hit in the case of cache misses.

The implementation of Bloom filters is simple. They use a bit array of size m bits, where initially each bit is set to 0 (zero). They also contain k hash functions, which are used to map elements to k locations in the bit array.

**A Bloom filter consists of:**
1. An array of $n$ bits, initially all 0’s.
2. A collection of hash functions $h_1, h_2, ..., h_k$. Each hash function maps “key” values to $n$ buckets, corresponding to the n bits of the bit-array.
3. A set $S$ of $m$ key values.

To add an element into a Bloom filter, it’s hashed k times, and a modulo of the hashed value and the size of the bit array is used to map the hashed value to a specific bit array location. That bit in the bit array is then toggled to 1 (one). Figure 7.21 shows three elements being added to a Bloom filter and their locations in the bit array.

![[Bloom Filter adding elements.png | 400]]

To check the membership of an element in the Bloom filter, just like with the add operation, the element is hashed k times and each hash key is used to index into the bit array. A true response to the membership query is only returned in cases where all k bit array locations are set to 1. Otherwise, the response to the query is false. Figure 7.22 shows an example of a membership query where the item was previously added to the Bloom filter, and therefore all the bit array locations contained a 1. This is an example of a true positive membership result because the element had been previously added to the Bloom filter.

![[Bloom Filter True Positive.png]]

The next example shows how you can get a false positive result for a membership query. The element being queried is d, which hadn’t been added to the Bloom filter. As it happens, all k hashes for d are mapped to locations that are set to 1 from other elements. This is an example of collision in the Bloom filter where the result is a false positive. Figure 7.23 shows this example in action.

![[Bloom Filter False Positive.png]]