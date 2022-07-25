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
For step (1) on the supply side we'll use a Bertrand model with
differentiated products for the supply side. on the demand side versions of logit demand
systems will be uses. this specification is common for competition authorities to work with.  
For step (2) the techniques are common, the harder one is implementing demand estimation of the demand function parameters. It is a demanding process both in terms of the required data and in terms of the required scope of work. Another approach is to calibrate the model using carefully selected parameters - this is what we'll do here.   
Finaly for step (3) a new equilibrium needs to be calculated. in case of a non-linear 
demand system, no analytic solution exists so some kind of numeric method is required 
to solve the system - here we'll use fixed point iteration. 


  
## Usfull references
</br>
For more information about the mathematical implementation and the theory, one can read: 
[Björnerstedt and Verboven](https://www.stata-journal.com/article.html?article=st0349).
  
To understand more about the Logit demand system (multinumial and nested logit) and 
the implementation is this repository its best to read [berry 1994](https://www.jstor.org/stable/2555829#metadata_info_tab_contents).
  
To get a wider perspective about possible implementations for antitrust practitioners,
see the work of [Taragin and Sandfort](https://cran.r-project.org/web/packages/antitrust/index.html)

and finally, a very good source to understand the procedure of demant estimaion,
a good place to start is [Aviv nevo's practitioner's Guide](https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1430-9134.2000.00513.x)

## little bit of backround 
next, we explain a little bit about the chosen structural model. first, the equations 
of the Bertrand model followed by the simple logit demand system.

### Bertrand model with differentiated products  

In this model, Firm $k \in K$ chooses the prices $\{p_j\}_{j=1}^{n_k}$ of its
products so as to maximize profits. Mathematically, firm $k$ solves:

![](https://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20%5Cmax_%7B%5C%7Bp_j%5C%7D_%7Bj%3D1%7D%5E%7Bn_k%7D%7D%20%26%5Csum_%7Bj%3D1%7D%5E%7Bn_k%7D%28%5Comega_%7Bjk%7D%29%28p_j%20-%20c_j%29q_j%2C%20%5Cend%7Balign*%7D)
