Suppose we have an $n \times n$ matrix $M$, whose element in row $i$ and column $j$ will be denoted $m_{ij}$. Suppose we also have a vector **v** of length $n$, whose $j$th element is $v_j$. Then the matrix-vector product is the vector $x$ of length $n$, whose $i$th element $x_i$ is given by

$$
x_i = \sum\limits_{j=0}^n m_{ij}v_j
$$

If $n$ = 100, we do not want to use a DFS or MapReduce for this calculation. But this sort of calculation is at the heart of the ranking of Web pages that goes on at search engines, and there, n is in the tens of billions. Let us first assume that n is large, but not so large that vector v cannot fit in main memory and thus be available to every Map task.

The matrix M and the vector v each will be stored in a file of the DFS. We assume that the row-column coordinates of each matrix element will be discoverable, either from its position in the file, or because it is stored with explicit coordinates, as a triple $(i, j, m_{ij})$. We also assume the position of element $v_j$ in the vector v will be discoverable in the analogous way.

**The Map Function:** The Map function is written to apply to one element of M. However, if $v$ is not already read into main memory at the compute node executing a Map task, then $v$ is first read, in its entirety, and subsequently will be available to all applications of the Map function performed at this Map task. Each Map task will operate on a chunk of the matrix M. From each matrix element $m_{ij}$ it produces the key-value pair $(i, m_{ij}v_j)$. Thus, all terms of the sum that make up the component $x_i$ of the matrix-vector product will get the same key, $i$.

**The Reduce Function:** The Reduce function simply sums all the values associated with a given key $i$. The result will be a pair $(i, x_i)$.

---
## If the Vector v Cannot Fit in Main Memory

However, it is possible that the vector v is so large that it will not fit in its entirety in main memory. It is not required that v fit in main memory at a compute node, but if it does not then there will be a very large number of disk accesses as we move pieces of the vector into main memory to multiply components by elements of the matrix. Thus, as an alternative, we can divide the matrix into vertical stripes of equal width and divide the vector into an equal number of horizontal stripes, of the same height. Our goal is to use enough stripes so that the portion of the vector in one stripe can fit conveniently into main memory at a compute node. Below figure suggests what the partition looks like if the matrix and vector are each divided into five stripes.

![[Matrix Vector Multiplication Large.png | 400]]

The $i$th stripe of the matrix multiplies only components from the $i$th stripe of the vector. Thus, we can divide the matrix into one file for each stripe, and do the same for the vector. Each Map task is assigned a chunk from one of the stripes of the matrix and gets the entire corresponding stripe of the vector. The Map and Reduce tasks can then act exactly as was described above for the case where Map tasks get the entire vector.