# PCY Algorithm

## Handling Larger Datasets in Main Memory

![[Apriori algorithm.png]]

The A-Priori Algorithm is fine as long as the step with the greatest requirement for main memory – typically the counting of the candidate pairs $C_2$ – has enough memory that it can be accomplished without thrashing (repeated moving of data between disk and main memory). Several algorithms have been proposed to cut down on the size of candidate set $C_2$. Here, we consider the PCY Algorithm, which takes advantage of the fact that in the first pass of A-Priori there is typically lots of main memory not needed for the counting of single items.

## The Algorithm of Park, Chen, and Yu

This algorithm, which we call PCY after its authors, exploits the observation that there may be much unused space in main memory on the first pass. If there are a million items and gigabytes of main memory, we do not need more than 10% of the main memory for the two tables suggested in Fig. 6.3 – a translation table from item names to small integers and an array to count those integers. The PCY Algorithm uses that space for an array of integers that generalizes the idea of a Bloom filter. The idea is shown schematically in Fig. 6.5.

![[PCY algorithm.png]]

Think of this array as a hash table, whose buckets hold integers rather than sets of keys (as in an ordinary hash table) or bits (as in a Bloom filter). Pairs of items are hashed to buckets of this hash table. As we examine a basket during the first pass, we not only add 1 to the count for each item in the basket, but we generate all the pairs, using a double loop. We hash each pair, and we add 1 to the bucket into which that pair hashes. Note that the pair itself doesn’t go into the bucket; the pair only affects the single integer in the bucket. 

At the end of the first pass, each bucket has a count, which is the sum of the counts of all the pairs that hash to that bucket. If the count of a bucket is at least as great as the support threshold $s$, it is called a *frequent bucket*. We can say nothing about the pairs that hash to a frequent bucket; they could all be frequent pairs from the information available to us. But if the count of the bucket is less than s (an *infrequent bucket*), we know no pair that hashes to this bucket can be frequent, even if the pair consists of two frequent items. That fact gives us an advantage on the second pass. We can define the set of candidate pairs $C_2$ to be those pairs $\{i,j\}$ such that:

1. $i$ and $j$ are frequent items.
2. $\{i, j\}$ hashes to a frequent bucket.

It is the second condition that distinguishes PCY from A-Priori.

Between the passes of PCY, the hash table is summarized as a bitmap, with one bit for each bucket. The bit is 1 if the bucket is frequent and 0 if not. Thus integers of 32 bits are replaced by single bits, and the bitmap shown in the second pass in Fig. 6.5 takes up only 1/32 of the space that would otherwise be available to store counts. However, if most buckets are infrequent, we expect that the number of pairs being counted on the second pass will be much smaller than the total number of pairs of frequent items. Thus, PCY can handle some data sets without thrashing during the second pass, while A-Priori would run out of main memory and thrash.

---

**Observation**
In pass 1 of A-Priori, most memory is idle
- We store only individual item counts
- *Can we use the idle memory to reduce memory required in pass 2?*

### Pass 1 of PCY: 

In addition to item counts, maintain a hash table with as many buckets as fit in memory

- Keep a count for each bucket into which pairs of items are hashed
	- *For each bucket just keep the count, not the actual pairs that hash to the bucket!*

```
FOR (each basket) :
	FOR (each item in the basket) :
		add 1 to item’s count;
	FOR (each pair of items) :
		hash the pair to a bucket;
		add 1 to the count for that bucket;
```

Few things to note:
- Pairs of items need to be generated from the input file; they are not present in the file
- We are not just interested in the presence of a pair, but we need to see whether it is present at least s (support) times

### Eliminating Candidates using Buckets

**Observation:** 
If a bucket contains a *frequent pair*, then the bucket is surely *frequent*.
However, even without any frequent pair, a bucket can still be frequent.
- So, we cannot use the hash to eliminate any member (pair) of a “frequent” bucket

But, for a bucket with total count less than $s$, none of its pairs can be frequent
- Pairs that hash to this bucket can be eliminated as candidates (even if the pair consists of 2 frequent items)

**Pass 2:** Only count pairs that hash to frequent buckets

### Between Passes

Replace the buckets by a bit-vector:
- 1 means the bucket count exceeded $s$ (call it a frequent bucket); 0 means it did not.

4-byte integer counts are replaced by bits, so the bit-vector requires 1/32 of memory. Also, decide which items are frequent and list them for the second pass

### Pass 2 of PCY: 

Count all pairs $\{i, j\}$ that meet the conditions for being a *candidate pair*:
1. Both $i$ and $j$ are frequent items
2. The pair $\{i,j\}$ hashes to a bucket whose bit in the bit vector is 1 (i.e., a frequent bucket)

*Both conditions are necessary for the pair to have a chance of being frequent*