# Content-based Recommendations

Example :

Suppose the only features of movies are the set of actors and the average rating. Consider two movies with five actors each. Two of the actors are in both movies. Also, one movie has an average rating of 3 and the other an average of 4. The vectors look something like

|$A_1$|$A_2$|$A_3$|$A_4$|$A_5$|$A_6$|$A_7$|$A_8$|Rating|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|0|1|1|0|1|1|0|1|3α|
|1|1|0|1|0|1|1|0|4α|

However, there are in principle an infinite number of additional components, each with 0’s for both vectors, representing all the possible actors that neither movie has. Since cosine distance of vectors is not affected by components in which both vectors have 0, we need not worry about the effect of actors that are in neither movie.

The last component shown represents the average rating. We have shown it as having an unknown scaling factor α. In terms of α, we can compute the cosine of the angle between the vectors. The dot product is $2+12α^2$, and the lengths of the vectors are $\sqrt{5+9α^2}$ and $\sqrt{5+16α^2}$. Thus, the cosine of the angle between the vectors is

$$ \frac {2 + 12α2} {\sqrt{25 + 125α^2 + 144α^4}} $$

If we choose $α = 1$, that is, we take the average ratings as they are, then the value of the above expression is $0.816$. If we use $α = 2$, that is, we double the ratings, then the cosine is 0.940. That is, the vectors appear much closer in direction than if we use $α = 1$. Likewise, if we use $α = 1/2$, then the cosine is $0.619$, making the vectors look quite different. We cannot tell which value of $α$ is “right,” but we see that the choice of scaling factor for numerical features affects our decision about how similar items are.