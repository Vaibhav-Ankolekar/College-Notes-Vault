# Grouping and Aggregation by MapReduce

As with the join, we shall discuss the minimal example of grouping and aggregation, where there is one grouping attribute and one aggregation. Let $R(A, B, C)$ be a relation to which we apply the operator $\gamma_{A,\theta(B)}(R)$. Map will perform the grouping, while Reduce does the aggregation.

**The Map Function:** For each tuple $(a, b, c)$ produce the key-value pair $(a, b)$.

**The Reduce Function:** Each key a represents a group. Apply the aggregation operator $\theta$ to the list \[$b_1, b_2, ..., b_n$\] of $B$-values associated with key $a$. The output is the pair $(a, x)$, where $x$ is the result of applying $\theta$ to the list. For example, if $\theta$ is $SUM$, then $x = b_1 + b_2 + · · · + b_n$, and if $\theta$ is $MAX$, then $x$ is the largest of $b_1, b_2, . . . , b_n$.

If there are several grouping attributes, then the key is the list of the values of a tuple for all these attributes. If there is more than one aggregation, then the Reduce function applies each of them to the list of values associated with a given key and produces a tuple consisting of the key, including components for all grouping attributes if there is more than one, followed by the results of each of the aggregations.