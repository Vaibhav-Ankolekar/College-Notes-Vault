# Role and Effect of damping factor (teleportation) Page Rank computation

Page rank is a function that assigns a real number to each page in the web (or at least to that portion of the web that has been crawled and its links discovered). The intent is that the higher the page rank of a page the more important it is.

The page rank can be calculated using $v^\prime = M.v$, where $v$ is the vector of page ranks and $M$ is the transpose of page links graph (*transition matrix*)

While calculating page rank there are two problems:

1. Dead ends
	- A page which do not have any out link is called a dead end.
	- To calculate page rank dead ends are removed recursively.
2. Spider Trap
	- It is a set of nodes with no dead ends but no out links other than a link to itself.
	- While calculating page ranks, they place all the PageRank within the spider traps.

To avoid the problem of spider traps, we modify the calculation of PageRank by allowing each random surfer a small probability of teleporting to a random page, rather than following an out-link from their current page. The equation for calculating PageRank gets modified as :

$$
v^\prime = \beta Mv + (1 - \beta)e/n
$$

where $\beta$ is a chosen constant, usually in the range 0.8 to 0.9, $e$ is a vector of all 1’s with the appropriate number of components, and $n$ is the number of nodes in the Web graph. The term $\beta Mv$ represents the case where, with probability $\beta$, the random surfer decides to follow an out-link from their present page. The teleportation factor takes care of dead ends also by introducing the term $(1-\beta)/n$. Thus the sum of components in vector r will never reach to zero because of teleportation.