# Spider Trap and Taxation

- A spider trap is a set of nodes with no dead ends but no arcs out. 
- These structures can appear intentionally or unintentionally on the Web, and they cause the PageRank calculation to place all the PageRank within the spider traps.
---
Example :

![[Spider Trap graph.png | 400]]

Consider Fig. 5.6, with the arc out of C changed to point to C itself. That change makes C a simple spider trap of one node. The transition matrix for Fig. 5.6 is

![[Spider Trap Matrix.png|250]]

If we perform the usual iteration to compute the PageRank of the nodes, we get

![[Spider Trap calculation 1.png |600]]

As predicted, all the PageRank is at C, since once there a random surfer can
never leave.

---

To avoid the problem illustrated by Example, we modify the calculation of PageRank by allowing each random surfer a small probability of teleporting to a random page, rather than following an out-link from their current page. The iterative step, where we compute a new vector estimate of PageRanks $v^′$ from the current PageRank estimate $v$ and the transition matrix $M$ is

$$v^′ = βMv + (1 − β)e/n$$

where $β$ is a chosen constant, usually in the range $0.8$ to $0.9$, e is a vector of all 1’s with the appropriate number of components, and $n$ is the number of nodes in the Web graph. The term $βMv$ represents the case where, with probability $β$, the random surfer decides to follow an out-link from their present page. The term $(1 − β)e/n$ is a vector each of whose components has value $(1 − β)/n$ and represents the introduction, with probability$ 1 − β$, of a new random surfer at a random page.

---

Example : Let us see how the new approach to computing PageRank fares on the graph of Fig. 5.6. We shall use $β=0.8$ in this example. Thus, the equation for the iteration becomes

![[Spider Trap new Inputs.png | 400]]

Notice that we have incorporated the factor $β$ into $M$ by multiplying each of its elements by $4/5$. The components of the vector $(1 − β)e/n$ are each $1/20$, since $1 − β = 1/5$ and $n=4$. Here are the first few iterations:

![[Spider Trap new calculations.png | 650]]

By being a spider trap, C has managed to get more than half of the PageRank for itself. However, the effect has been limited, and each of the nodes gets some of the PageRank.