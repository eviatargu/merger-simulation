# Merger Simulation
These two examples show how to implement merger simulation in R.  
Merger simulation can be done after estimating demand parameters with demand estimation
procedure or with calibrating chosen demand parameters.   
These examples focus on the computational part - the algebra used to solve the 
structural model and the fixed point iteration algorithm. 

## little bit of backround 
Merger simulation of horizontal mergers relys on a stractural model of supply and demand. 
It is customary to assume a Bertrand model with
differentiated products on the supply side and on the supply side, a discrete choice model
is widely used. 

## bertrand model 
In this model, Firm $k \in K$ chooses the prices $\{p_j\}_{j=1}^{n_k}$ of its
products so as to maximize profits. Mathematically, firm $k$ solves:

\begin{align*}
\max_{\{p_j\}_{j=1}^{n_k}} &\sum_{j=1}^{n_k}(\omega_{jk})(p_j - c_j)q_j,
\end{align*}

where $\omega_{ik}$ is the share of product $j$'s profits earned by firm $k$,
so that $\sum\limits_{k\in K} \omega_{jk}\le 1$. $q_j$, the quantity sold of product $j$,  is assumed to
be a twice differentiable function of *all* product prices.

Differentiating profits with respect to each $p_j$  yields the following first order conditions (FOCs):

\begin{align*}
  \partial p_j&\equiv \omega_{jk}q_j +\sum_{j=1}^{n}\omega_{jk}( p_j - c_j)\frac{\partial q_j}{\partial
    p_j}=0& \mbox{ for all $j\in n_k$} 
\end{align*}



## The multinomial logit model  
 
Logit demand is based on a discrete choice model
that assumes that each consumer is
willing to purchase at most a single unit of one product from the
$n$ products available in the market. The assumptions underlying
Logit demand imply that the probability that a consumer
purchases product $j \in n$ is given by

\begin{align*}
  s_j=& \frac{\exp(V_j)}{\sum\limits_{k \in n}\exp(V_k)},&
\end{align*}

where  $s_j$ is product $j$'s *quantity* share and
    $V_j$ is the (average) indirect utility that a consumer
    receives from purchasing product $j$. We assume that $V_j$ takes on
    the following form
    
\begin{align*}
  V_j=&\delta_j + \alpha p_j,&\alpha<0.
\end{align*}


The Logit demand system yields the following own- and cross-price elasticities:

\begin{align*}
  \epsilon_{ii}=&\alpha (1-s_i)p_i \\
  \epsilon_{ij}=&-\alpha s_jp_j
\end{align*}


in the first example a simple multinomial logit is presented as simple as possible, so
the use of the Bertrand equation system and the logit demand function will be as 
simple as possible for understanding.   
The second example is a more practical in a sense that the code can be used for several applications
and that the model is a `one level nested logit' which is more realistic.  
also, the simulation procedure in this case is a little longer so the code is wrapped in
functions for different stages of the process. 
</br>
For more information about the implementation and the theory, one can read: 
[Björnerstedt and Verboven](https://www.stata-journal.com/article.html?article=st0349) 
or the work of [Taragin and Sandfort](https://cran.r-project.org/web/packages/antitrust/index.html)

