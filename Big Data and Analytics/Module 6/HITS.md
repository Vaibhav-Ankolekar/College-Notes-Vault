 # Hubs and Authorities

This hubs-and-authorities algorithm, sometimes called HITS (hyperlink-induced topic search), was originally intended not as a preprocessing step before handling search queries, as PageRank is, but as a step to be done along with the processing of a search query, to rank only the responses to that query.

## The Intuition Behind HITS

While PageRank assumes a one-dimensional notion of importance for pages, HITS views important pages as having two flavors of importance.

1. Certain pages are valuable because they provide information about a topic. These pages are called authorities.
2. Other pages are valuable not because they provide information about any topic, but because they tell you where to go to find out about that topic. These pages are called hubs.

Just as PageRank uses the recursive definition of importance that “a page is important if important pages link to it,” HITS uses a mutually recursive definition of two concepts: “a page is a good hub if it links to good authorities, and a page is a good authority if it is linked to by good hubs.”

**Example:** A typical department at a university maintains a Web page listing all the courses offered by the department, with links to a page for each course, telling about the course – the instructor, the text, an outline of the course content, and so on. If you want to know about a certain course, you need the page for that course; the departmental course list will not do. The course page is an authority for that course. However, if you want to find out what courses the department is offering, it is not helpful to search for each courses’ page; you need the page with the course list first. This page is a hub for information about courses.

## Formalizing Hubbiness and Authority

To formalize the above intuition, we shall assign two scores to each Web page. One score represents the hubbiness of a page – that is, the degree to which it is a good hub, and the second score represents the degree to which the page is a good authority. Assuming that pages are enumerated, we represent these scores by vectors $h$ and $a$. The $i$th component of $h$ gives the hubbiness of the $i$th page, and the $i$th component of $a$ gives the authority of the same page.

While importance is divided among the successors of a page, as expressed by the transition matrix of the Web, the normal way to describe the computation of hubbiness and authority is to add the authority of successors to estimate hubbiness and to add hubbiness of predecessors to estimate authority. If that is all we did, then the hubbiness and authority values would typically grow beyond bounds. Thus, we normally scale the values of the vectors $h$ and $a$ so that the largest component is 1. An alternative is to scale so that the sum of components is 1.

To describe the iterative computation of h and a formally, we use the link matrix of the Web, $L$. If we have n pages, then $L$ is an $n \times n$ matrix, and $L_{ij} = 1$ if there is a link from page $i$ to page $j$, and $L_{ij} = 0$ if not. We shall also have need for $L^T$, the transpose of $L$. That is, $L^T_{ij} = 1$ if there is a link from page $j$ to page $i$, and $L^T_{ij} = 0$ otherwise. Notice that $L^T$ is similar to the matrix $M$ that we used for PageRank, but where $L^T$ has 1, $M$ has a fraction – 1 divided by the number of out-links from the page represented by that column.

Start with $h$ a vector of all 1’s.
1. Compute $a = L^Th$ and then scale so the largest component is 1.
2. Next, compute $h = La$ and scale again.

Now, we have a new h and can repeat steps $(1)$ and $(2)$ until at some iteration the changes to the two vectors are sufficiently small that we can stop and accept the current values as the limit.

**Example:** 

![[HITS example.png | 500]]

Let us perform the first two iterations of the HITS algorithm on the Web of Fig. 5.18. In Fig. 5.20 we see the succession of vectors computed. The first column is the initial h, all 1’s. In the second column, we have estimated the relative authority of pages by computing LTh, thus giving each page the sum of the hubbinesses of its predecessors. The third column gives us the first estimate of a. It is computed by scaling the second column; in this case we have divided each component by 2, since that is the largest value in the second column.

![[HITS example L.png | 600]]

The fourth column is La. That is, we have estimated the hubbiness of each page by summing the estimate of the authorities of each of its successors. Then, the fifth column scales the fourth column. In this case, we divide by 3, since that is the largest value in the fourth column. Columns six through nine repeat the process outlined in our explanations for columns two through five, but with the better estimate of hubbiness given by the fifth column.

![[HITS example h a.png | 500]]

The limit of this process may not be obvious, but it can be computed by a simple program. The limits are:

![[HITS example limit.png | 330]]

This result makes sense. First, we notice that the hubbiness of E is surely 0, since it leads nowhere. The hubbiness of C depends only on the authority of E and vice versa, so it should not surprise us that both are 0. A is the greatest hub, since it links to the three biggest authorities, B, C, and D. Also, B and C are the greatest authorities, since they are linked to by the two biggest hubs, A and D.