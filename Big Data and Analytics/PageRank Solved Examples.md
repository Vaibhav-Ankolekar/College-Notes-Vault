Consider the web graph below with six pages (A, B, C, D, E, F) with directed links as follows. 
	$A \to B,C$
	$B \to A,D,E,F$
	$C \to A,F$
Assume that the PageRank values for any page m at iteration 0 is $PR(m)=1$ and teleportation factor for iterations is $\beta=0.85$. Perform the page rank algorithm and determine the rank for every page at iteration 2. \[10m\]

Define PageRank. Using the web graph shown below compute the PageRank at every node at the end of the second iteration. Use teleport factor = 0.8 \[10m\].

![[PageRank Sum 1.svg]]

Solution :-

Transition Matrix

$$
M \;\;\;\;\; = \;\;\;\;\;
\begin{array}{cc} 
	& \begin{array}{cccccc} A \; & \; B \; & \; C \; & \; D \; & \; E \; & \; F \\ \end{array} \\
	\begin{array}{cccccc} A \\ B \\ C \\ D \\ E \\ F \end{array} &
	\left[
		\begin{array}{cccccc}
		0 & 1/2 & 1/2 & 0 & 0 & 0 \\
		1/2 & 0 & 0 & 0 & 0 & 0 \\
		1/2 & 0 & 0 & 0 & 0 & 0 \\
		0 & 1/4 & 0 & 0 & 0 & 0 \\
		0 & 1/4 & 0 & 0 & 0 & 0 \\
		0 & 1/4 & 1/2 & 0 & 0 & 0
		\end{array}
	\right]
\end{array}
$$

---