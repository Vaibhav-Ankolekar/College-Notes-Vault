# Matrix-Matrix Multiplication with two MapReduce step

If $M$ is a matrix with element $m_{ij}$ in row $i$ and column $j$, and $N$ is a matrix with element $n_{jk}$ in row $j$ and column $k$, then the product $P = MN$ is the matrix $P$ with element $p_{ik}$ in row $i$ and column $k$, where
$$
	p_{ik} = \sum\limits_{j} m_{ij}n_{jk}
$$
It is required that the number of columns of $M$ equals the number of rows of $N$, so the sum over $j$ makes sense.

We can think of a matrix as a relation with three attributes: the row number, the column number, and the value in that row and column. Thus, we could view matrix M as a relation $M(I, J, V )$, with tuples $(i, j, m_{ij})$, and we could view matrix N as a relation $N(J, K, W)$, with tuples $(j, k, n_{jk})$. As large matrices are often sparse (mostly 0’s), and since we can omit the tuples for matrix elements that are 0, this relational representation is often a very good one for a large matrix. However, it is possible that $i$, $j$, and $k$ are implicit in the position of a matrix element in the file that represents it, rather than written explicitly with the element itself. In that case, the Map function will have to be designed to construct the $I$, $J$, and $K$ components of tuples from the position of the data.

The product MN is almost a natural join followed by grouping and aggregation. That is, the natural join of $M(I, J, V )$ and $N(J, K, W)$, having only attribute $J$ in common, would produce tuples $(i, j, k, v, w)$ from each tuple $(i, j, v)$ in $M$ and tuple $(j, k, w)$ in N. This five-component tuple represents the pair of matrix elements $(m_{ij}, n_{jk})$. What we want instead is the product of these elements, that is, the four-component tuple $(i, j, k, v \times w)$, because that represents the product $m_{ij}n_{jk}$. Once we have this relation as the result of one MapReduce operation, we can perform grouping and aggregation, with $I$ and $K$ as the grouping attributes and the sum of $V \times W$ as the aggregation. That is, we can implement matrix multiplication as the cascade of two MapReduce operations, as follows. First:

***The Map Function:*** For each matrix element $m_{ij}$, produce the key value pair $(j, (M, i, m_{ij}))$. Likewise, for each matrix element $n_{jk}$, produce the key value pair $((j, (N, k, n_{jk}))$. Note that $M$ and $N$ in the values are not the matrices themselves. Rather they are names of the matrices or (as we mentioned for the similar Map function used for natural join) better, a bit indicating whether the element comes from $M$ or $N$.

***The Reduce Function:*** For each key j, examine its list of associated values.
For each value that comes from $M$, say $(M, i, m_{ij})$, and each value that comes from $N$, say $(N, k, n_{jk})$, produce a key-value pair with key equal to $(i, k)$ and value equal to the product of these elements, $m_{ij}n_{jk}$.

Now, we perform a grouping and aggregation by another MapReduce operation.

***The Map Function:*** This function is just the identity. That is, for every input element with key $(i, k)$ and value $v$, produce exactly this key-value pair.

***The Reduce Function:*** For each key $(i, k)$, produce the sum of the list of values associated with this key. The result is a pair $((i, k), v)$, where $v$ is the value of the element in row $i$ and column $k$ of the matrix $P = MN$.