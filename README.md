# Merger Simulation
Merger simulation is a quantitative tool to create prediction about the 
probable outcome effect of a merger on competition. 
The process includes three stages:  
(1) selection of a structural model of supply
and demand.  
(2) calibration the model's parameters.  
(3) A simulation of the equilibrium that will prevail in the market after the merger.  
  
This repository presents two examples of implementation of simple specification in R for 
horizontal merger.   
for step (1) on the supply side we'll use a Bertrand model with
differentiated products for the supply side. on the demand side versions of logit demand
systems will be uses. this specification is common for competition authorities to work with.
for step (2) the techniques are common, the harder one is implementing demand estimation of the demand function parameters. It is a demanding process both in terms of the required data and in terms of the required scope of work. Another approach is to calibrate the model using carefully selected parameters - this is what we'll do here. 
Finaly for step (3) a new equilibrium needs to be calculated. in case of a non-linear 
demand system, no analytic solution exists so some kind of numeric method is required 
to solve the system - here we'll use fixed point iteration. 


## little bit of backround 
next, we explain a little bit about the chosen structural model. first, the equations 
of the Bertrand model followed by the simple logit demand system.

### Bertrand model with differentiated products  

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



### The multinomial logit model  
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
  
  
## usfull references
</br>
For more information about the mathematical implementation and the theory, one can read: 
[Björnerstedt and Verboven](https://www.stata-journal.com/article.html?article=st0349).
  
To understand more about the Logit demand system (multinumial and nested logit) and 
the implementation is this repository its best to read [berry 1994](https://www.jstor.org/stable/2555829#metadata_info_tab_contents).
  
To get a wider perspective about possible implementations for antitrust practitioners,
see the work of [Taragin and Sandfort](https://cran.r-project.org/web/packages/antitrust/index.html)

and finally, a very good source to understand the procedure of demant estimaion,
a good place to start is [Aviv nevo's practitioner's Guide](https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1430-9134.2000.00513.x)

