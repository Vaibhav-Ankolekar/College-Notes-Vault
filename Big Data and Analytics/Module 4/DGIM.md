# DGIM Algorithm

## Counting Ones in a Window

We now turn our attention to counting problems for streams. Suppose we have a window of length $N$ on a binary stream. We want at all times to be able to answer queries of the form “how many 1’s are there in the last k bits?” for any $k \leq N$.

## The Datar-Gionis-Indyk-Motwani Algorithm

This version of the algorithm uses $O(\log_2 N)$ bits to represent a window of $N$ bits, and allows us to estimate the number of 1’s in the window with an error of no more than 50%.

To begin, each bit of the stream has a *timestamp*, the position in which it arrives. The first bit has timestamp 1, the second has timestamp 2, and so on. Since we only need to distinguish positions within the window of length $N$, we shall represent timestamps modulo $N$, so they can be represented by $\log_2 N$ bits. If we also store the total number of bits ever seen in the stream (i.e., the most recent timestamp) modulo $N$, then we can determine from a timestamp modulo $N$ where in the current window the bit with that timestamp is.

We divide the window into *buckets*, consisting of:
1. The timestamp of its right (most recent) end.
2. The number of 1’s in the bucket. This number must be a power of 2, and we refer to the number of 1’s as the *size* of the bucket.

To represent a bucket, we need $\log_2 N$ bits to represent the timestamp (modulo $N$) of its right end. To represent the number of 1’s we only need $\log_2 \log_2 N$ bits. The reason is that we know this number $i$ is a power of $2$, say $2^j$, so we can represent $i$ by coding $j$ in binary. Since $j$ is at most $\log_2 N$, it requires $\log_2 \log_2 N$ bits. Thus, $O(\log N)$ bits suffice to represent a bucket.

There are six rules that must be followed when representing a stream by buckets.
- The right end of a bucket is always a position with a 1.
- Every position with a 1 is in some bucket.
- No position is in more than one bucket.
- There are one or two buckets of any given size, up to some maximum size.
- All sizes must be a power of 2.
- Buckets cannot decrease in size as we move to the left (back in time).

![[DGIM example 1.png]]

Example : Figure 4.2 shows a bit stream divided into buckets in a way that satisfies the DGIM rules. At the right (most recent) end we see two buckets of size 1. To its left we see one bucket of size 2. Note that this bucket covers four positions, but only two of them are 1. Proceeding left, we see two buckets of size 4, and we suggest that a bucket of size 8 exists further left. Notice that it is OK for some 0’s to lie between buckets. Also, observe from Fig. 4.2 that the buckets do not overlap; there are one or two of each size up to the largest size, and sizes only increase moving left.

## Maintaining the DGIM Conditions

Suppose we have a window of length $N$ properly represented by buckets that satisfy the DGIM conditions. When a new bit comes in, we may need to modify the buckets, so they continue to represent the window and continue to satisfy the DGIM conditions. First, whenever a new bit enters:

- Check the leftmost (earliest) bucket. If its timestamp has now reached the current timestamp minus $N$, then this bucket no longer has any of its 1’s in the window. Therefore, drop it from the list of buckets.

Now, we must consider whether the new bit is 0 or 1. If it is 0, then no further change to the buckets is needed. If the new bit is a 1, however, we may need to make several changes. First:

- Create a new bucket with the current timestamp and size 1.

If there was only one bucket of size 1, then nothing more needs to be done. However, if there are now three buckets of size 1, that is one too many. We fix this problem by combining the leftmost (earliest) two buckets of size 1.

- To combine any two adjacent buckets of the same size, replace them by one bucket of twice the size. The timestamp of the new bucket is the timestamp of the rightmost (later in time) of the two buckets.

Combining two buckets of size 1 may create a third bucket of size 2. If so, we combine the leftmost two buckets of size 2 into a bucket of size 4. That, in turn, may create a third bucket of size 4, and if so we combine the leftmost two into a bucket of size 8. This process may ripple through the bucket sizes, but there are at most $\log_2 N$ different sizes, and the combination of two adjacent buckets of the same size only requires constant time. As a result, any new bit can be processed in $O(\log N)$ time.

Example : Suppose we start with the buckets of Fig. 4.2 and a 1 enters. First, the leftmost bucket evidently has not fallen out of the window, so we do not drop any buckets. We create a new bucket of size 1 with the current timestamp, say $t$. There are now three buckets of size 1, so we combine the leftmost two. They are replaced with a single bucket of size 2. Its timestamp is $t − 2$, the timestamp of the bucket on the right (i.e., the rightmost bucket that actually appears in Fig. 4.2.

![[DGIM example 2.png]]

There are now two buckets of size 2, but that is allowed by the DGIM rules. Thus, the final sequence of buckets after the addition of the 1 is as shown in Fig. 4.3.

## Query Answering in the DGIM Algorithm

Suppose we are asked how many 1’s there are in the last $k$ bits of the window, for some $1 \leq k \leq N$. Find the bucket $b$ with the earliest timestamp that includes at least some of the $k$ most recent bits. Estimate the number of 1’s to be the sum of the sizes of all the buckets to the right (more recent) than bucket $b$, plus half the size of $b$ itself.

![[DGIM example 1.png]]

Example : Suppose the stream is that of Fig. 4.2, and $k = 10$. Then the query asks for the number of 1’s in the ten rightmost bits, which happen to be `0110010110`. Let the current timestamp (time of the rightmost bit) be $t$. Then the two buckets with one 1, having timestamps $t − 1$ and $t − 2$ are completely included in the answer. The bucket of size 2, with timestamp $t − 4$, is also completely included. However, the rightmost bucket of size 4, with timestamp $t − 8$ is only partly included. We know it is the last bucket to contribute to the answer, because the next bucket to its left has timestamp less than $t − 9$ and thus is completely out of the window. On the other hand, we know the buckets to its right are completely inside the range of the query because of the existence of a bucket to their left with timestamp $t − 9$ or greater.

Our estimate of the number of 1’s in the last ten positions is thus 6. This number is the two buckets of size 1, the bucket of size 2, and half the bucket of size 4 that is partially within range. Of course the correct answer is 5.

$$ 
Count\;of\;1's = (1)+(2)+\left( 4 \times \frac{1}{2} \right) = 5 
$$

Suppose the above estimate of the answer to a query involves a bucket $b$ of size $2^j$ that is partially within the range of the query. Let us consider how far from the correct answer $c$ our estimate could be. There are two cases: the estimate could be larger or smaller than $c$.

Case 1: The estimate is less than $c$. In the worst case, all the 1’s of $b$ are actually within the range of the query, so the estimate misses half bucket b, or $2^{j−1}$ 1’s. But in this case, $c$ is at least $2j$; in fact it is at least $2j+1 − 1$, since there is at least one bucket of each of the sizes $2j−1, 2j−2, . . . , 1$. We conclude that our estimate is at least 50% of $c$.

Case 2: The estimate is greater than $c$. In the worst case, only the rightmost bit of bucket $b$ is within range, and there is only one bucket of each of the sizes smaller than $b$. Then $c = 1 + 2^{j−1} + 2^{j−2} + ... + 1 = 2^j$ and the estimate we give is $2^{j−1} + 2^{j−1} + 2^{j−2} + ... + 1 = 2^j + 2^{j−1} − 1$. We see that the estimate is no more than 50% greater than $c$.