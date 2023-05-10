# Module 1

- [x] List and Explain Big Data :- 1) Characteristics, 2) Types and 3) Challenges \[5m\]
- [x] What are the characteristics of Big Data? \[5m\].
- [x] What are the three Vs of Big Data? Give two examples of big data case studies. Indicate which Vs are satisfied by these case studies. \[5m\].
---
# Module 2
- [x] Explain Hadoop Ecosystem with core components. Explain its physical architecture. State the limitations of Hadoop. \[10m\] Explain the different Hadoop components. \[10m\]. Short Note on Core Hadoop components \[5m\]. Explain Hadoop architecture with its features. \[5m\]
- [ ] How Big data problems are handled by Hadoop system \[5m\].
- [ ] Explain how Hadoop goals are covered in HDFS \[10m\].
- [ ] Describe the structure of HDFS in a Hadoop ecosystem using a diagram \[5m\].
- [x] Difference between Document data stores and Column family data store. \[5m\]
- [x] Distinguish between Name Node and Data Node. \[5m\]
- [x] Difference between SQL and NoSQL \[5m\]
- [x] Short Note on NoSQL data stores \[5m\]
- [x] Agility is a NoSQL business driver. Justify \[5m\]
- [x] List the different NoSQL data stores. Explain any two diagram \[10m\]. What are the different data architecture patterns in NoSQL? Explain "Key Value" store and "Document" store patterns with relevant examples \[10m\]. What are the different architectural patterns in NoSQL? Explain Graph data store and Column Family Store patterns with relevant examples. \[10m\].
- [x] Short note on NoSQL architectural pattern with example \[5m\]. Explain NoSQL data architectural patterns \[5m\].
- [x] What is BASE properties in NoSQL database ? List two applications of each NoSQL architecture pattern \[10m\].
---
# Module 3
- [x] Explain "Shuffle & Sort" phase and "Reducer" phase in Map Reduce. \[5m\]
- [x] Write a Map Reduce pseudo code to multiply two matrices. Illustrate with an example showing all steps \[10m\]. Write a Map Reduce pseudo code to multiply two matrices. Illustrate the procedure on the following matrices. Clearly show all the steps \[10m\]. 
	$$A = \begin{bmatrix} 1 & 2 \\ 2 & 1 \\ 3 & 4 \end{bmatrix} 
	\;\;\;\;\;\; 
	B = \begin{bmatrix} 1 & 2 \\ 1 & 3 \end{bmatrix}$$
- [x] Explain selection and projection relational algebra operation using MapReduce \[10m\]. List Relational algebra operations. Explain any two using MapReduce \[10m\].
- [x] Short note on MapReduce for Matrix Multiplication \[5m\]. Short note on Matrix-Vector Multiplication by MapReduce \[5m\]. Short note on Matrix Multiplication by MapReduce \[5m\]. 
- [x] Explain Matrix-Matrix multiplication using TWO step MapReduce model \[10m\].
- [x] Short note on MapReduce programming model \[5m\].
- [x] What is the role of a "combiner" in the MapReduce framework? Explain with the help of one example \[5m\]
- [x] Show MapReduce implementation for the following two tasks using pseudocode \[10m\].
	i) Multiplication of two matrices
	ii) Computing group-by and aggregation of a relational table
---
# Module 4
- [x] What is a Data Stream Management System? Explain with block diagram \[10m\].
- [x] Difference between DBMS and DSMS \[5m\].
- [x] List the different issues in stream processing \[5m\]. List the different issues and challenges in data stream query processing \[5m\]. List the different issues and challenges in data stream query processing \[5m\].
- [x] Explain Blooms filter for Stream Data Mining \[5m\]. Define Bloom filter. Explain the concept of Bloom filter algorithm with example \[10m\]. Explain Bloom's filter for stream data mining with example \[10m\]. Clearly explain the concept of a Bloom filter with the help of an example \[10m\].
- [x] Explain FM algorithm with example. \[10m\] Explain Flajolet-Martin Algorithm with example \[10m\]
- [x] Suppose a data stream consists of the integers 1,3,2,1,2,3,4,3,1,2,3,1. Let the Hash function being used in $h(x)=6x+1 \; mod \; 5$; estimate the number of distinct in this stream using Flajolet - Martin algorithm. \[10m\]
- [ ] Suppose a data stream consists of the integers 2,1,6,1,5,9,2,3,5. Let the Hash functions all be of the form $h(x)=ax+b \; mod \; 16$ for some a & b. Yo should treat the result as a 4 bit binary integer. Determine the tail length for each stream element and the resulting estimate of the number if distinct elements if the hash function is \[10m\] a) $h(x)=2x+3 \; mod \; 16$; b) $h(x)=4x+1 \; mod \; 16$ and c) $h(x)=5x \; mod \; 16$
- [ ] Suppose a data stream consists of the integers 3,1,4,1,5,9,2,6,5. Let the Hash function being used in $h(x)=3x+1 \; mod \; 5$. Show how the FM algorithm will estimate the number of distinct elements in this stream.
- [x] Given two applications for counting the number of 1's in a long stream of binary values. Using a stream of binary digits, illustrate how DGIM will find the number of 1's \[10m\]. Explain DGIM algorithm for counting ones in a stream with example \[10m\]. Explain DGIM algorithm for counting ones in stream with example. \[10m\]. Given two applications for counting the number of 1's in a long stream of binary values. Using a stream of binary digits, illustrate how DGIM will find the number of 1's \[10m\]. 
- [x] Give the updating buckets approach of DGIM algorithm \[5m\]
---
# Module 5
- [ ] Difference between PCY and Multistage \[5m\]. Difference between Multihash and Multistage \[5m\]. Difference between PCY, Multihash and Multistage \[5m\].
- [x] Short note on PCY algorithm \[5m\]. Explain PCY algorithm with suitable example \[10m\]. Explain clearly with diagram how the PCY algorithm helps to perform frequent itemset mining for large datasets \[10m\]. Explain Park-Chen-Yu algorithm. How memory mapping is done in PCY.
- [x] Explain clearly how SON partition based algorithm helps to perform frequent item set mining for large data sets. How does this algorithm avoid false negatives ? \[10m\]. Explain the SON algorithm for Frequent Pattern mining. Illustrate how MapReduce can be used for implementing this algorithm \[10m\].
- [x] Short note on SON algorithm with Map Reduce \[5m\]. Short note on SON algorithm and MapReduce \[5m\].
- [x] Clearly explain how CURE algorithm can be used to cluster big data sets. \[10m\]. Short note on CURE algorithm \[5m\]. Short note on CURE algorithm \[5m\]. Clearly explain how CURE algorithm can be used to cluster big data sets. \[10m\]. Explain how the CURE algorithm can be used to cluster big data sets \[10m\].
- [x] Short note on clustering using Representatives Algorithm. \[5m\] 
- [ ] Through an example illustrate how the triangular array can be used to optimally store and count pairs in a frequent itemset mining algorithm \[5m\].
- [ ] Imagine there are 100 baskets, numbered 1, 2,…, 100 items, similarly numbered. Item I is in basket J if and only if I divides J evenly. For example, basket 24 is set of items { 1, 2, 3, 4, 6, 8, 12, 24 }. Describe all the association rules that have 100% confidence.
- [x] The snapshot of 10 transactions is given below for online shopping that generates big data. $Threshold \; value = 4$ and $Hash \; function= (i*j) \; mod \; 10$
	$$T_1 = \{1, 2, 3\}, \; T_2 = \{2, 3, 4\}, \; T_3 = \{3, 4, 5\}, \; T_4 = \{4, 5, 6\}, \; T_5 = \{1, 3, 5\}$$
	$$T_6 = \{2, 4, 6\}, \; T_7 = \{1, 3, 4\}, \; T_8 = \{2, 4, 5\}, \; T_9 = \{3, 4, 6\}, \; T_{10} = \{1, 2, 4\}$$
	Find the frequent item sets purchased for such big data by using suitable
---
# Module 6

**Link Analysis : PageRank Definition, Structure of the web, dead ends, Using Page rank in a search engine, Efficient computation of Page Rank: PageRank Iteration Using MapReduce, Topic sensitive Page Rank, link Spam, Hubs and Authorities, HITS Algorithm.**

- [x] Explain the steps of the HITS algorithm \[5m\]. Explain HITS algorithm with example \[10m\].
- [x] Consider the web graph below with six pages (A, B, C, D, E, F) with directed links as follows. 
	$A \to B,C$
	$B \to A,D,E,F$
	$C \to A,F$
	Assume that the PageRank values for any page m at iteration 0 is $PR(m)=1$ and teleportation factor for iterations is $\beta=0.85$. Perform the page rank algorithm and determine the rank for every page at iteration 2. \[10m\]
- [x] List down the steps in modified Page Rank Algorithm to avoid spider trap with one example \[10m\].
- [x] What is the role and effect of Page Rank ? \[5m\] Explain PageRank algorithm with suitable example \[10m\].
- [x] Explain the role and effect of damping factor (teleportation) in Page Rank computation \[5m\].
- [x] Define PageRank. Using the web graph shown below compute the PageRank at every node at the end of the second iteration. Use teleport factor = 0.8 \[10m\].
	![[PageRank Sum 1.svg]]
- [ ] For the graph given below show the page ranks of all nodes after running the PageRank algorithm for two iterations with teleportation factor with Beta value = 0.8
	![[PageRank Sum 2.svg]]
- [ ] Compute simplified page rank using damping factor d = 0.9 for web. \[10m\] 
	![[PageRank Sum 3.svg]]
- [x] Compute efficient page rank using damping factor d = 0.8 for web. \[10m\] 
	![[PageRank Sum 4.svg]]
- [ ] Explain SIMRANK Algorithm with example \[10m\].
- [ ] Define Hub and Authority. Compute Hub and Authority score for web. \[10m\].
	![[PageRank Sum 3.svg]]

- [x] Define Hub and Authority. Compute Hub and Authority score for web. \[10m\].

	![[HubAuthority Sum 1.svg]]

**Mining Social-Network Graphs : Social Networks as Graphs, Types , Clustering of Social Network Graphs, Direct Discovery of Communities, Counting triangles using Map-Reduce.**

- [ ] Explain Social Network graph clustering algorithm with example \[10m\].
- [ ] Explain Girvan-Newman algorithm to mine Social Graphs.
- [ ] Write steps of Girvan Newman Algorithm. Explain clustering of Social Network Graphs using GN algorithm with example? \[10m\].
- [ ] What is a "Community" in a Social Network Graph? Explain any one algorithm for finding communities in a Social Graph \[10m\]. What is a "Community" in a Social Network Graph? For the following graph show how the Girvan Newman algorithm finds the different communities \[10m\].
	![[Community Sum 1.svg]]
- [ ] For the graph given below use betweenness factor and find all communities \[10m\].
	![[Community Sum 2.svg]]
- [ ] Consider a Portion of Web Graph shown below \[10m\].
	![[HubAuthority Sum 2.svg]]
	a) Compute the hub and authority scores for all the nodes.
	b) Does this graph contains spider traps? Dead ends? If so, which nodes?
	c) Compute the page rank of the nodes with teleportation $\beta=0.8$? (show two iterations only)


**Recommendation Engines: A Model for Recommendation Systems, Content-Based Recommendations, Collaborative Filtering**

- [ ] Explain different types of recommendation system with real time examples \[10m\]. What are different recommender systems. Explain any one with example \[10m\]. Explain different types of recommendation system with real time examples \[10m\]. Explain models for recommendation system in detail \[10m\].
- [ ] How recommendation is done based on properties of product? Explain with suitable example \[10m\].
- [ ] Explain collaborative filtering system. How is it different from content based system? \[10m\]. Define Collaborative filtering. Using an example of an e-commerce site like Flipkart or Amazon, describe how it can be used to provide recommendations to users \[10m\].
---
- [ ] Give formal definition of the Nearest Neighbor problem. Show how finding plagiarism in documents is NN's problem. What similarity measures is used ? \[10m\]. How finding plagiarism in documents is a nearest neighbor problem \[5m\].
- [ ] What are the shortcomings of nearest neighbor technique in collaborative filtering method? suggest some improvements \[5m\].

# Unknown

- [ ] Find the jaccard distance and cosine distance between the following pairs of set: $X=(0,1,2,4,5,3) \; and \; Y=(5,6,7,9,10,8)$ \[5m\]

- [ ] Find Jaccard distance between { 1, 2, 3, 4} & { 2, 3, 5, 7} and { a, a, a, b } & { a, a, b, b, c }
	Find Hamming Distance between 110011 & 010101 and 11001 & 01011
	Compute the cosine of the angles between (3,-1,2) and (-2,3,1) \[10m\].

- [ ] For the given graph show how clique percolation method will find cliques. \[10m\]

	![[Clique Sum 1.svg]]

- [ ] Define Edit distance. Explain with example \[5m\]

- [ ] Find Cosine Distance between d1 and d2 vector \[5m\]

||||||||||||
|:-:|-|-|-|-|-|-|-|-|-|-|
|**index**|1|2|3|4|5|6|7|8|9|10|
|**d1**|5|2|1|0|0|0|0|1|3|7|
|**d2**|5|2|1|0|0|1|2|2|0|2|

- [ ] Explain different distance measures for Big Data. \[5m\]

- [ ] Explain CAP theorem? How is it different from ACID properties \[5m\]



- [ ] Find Manhattan distance for the points X1=(1,2,2) and X2=(2,5,3)

