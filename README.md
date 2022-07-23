# Merger Simulation
In these examples, I show how to implement merger simulation in R.
merger simulation usually comes after estimating an aggregated logit demand system.  
yet, it is possible to calculate post merger equilibrium using calibrated model parameters.  
These examples focus on the computation part of the new equilibrium.   
To calculate the new equilibrium one needs to assume some kind of structural model of 
supply and demand. In horizontal mergers it is customary to assume a Bertrand model with
differentiated products, On the demand side a logit model is often used.   
in the first example a simple multinomial logit is presented as simple as possible, so
the use of the Bertrand equation system and the logit demand function will be as 
simple as possible for understanding.   
The second example is a more practical in a sense that the code can be used for several applications
and that the model is a `one level nested logit' which is more realistic.  
also, the simulation procedure in this case is a little longer so the code is wrapped in
functions for different stages of the process. 
<br>
For more information about the implementation and the theory, one can read: 
[Björnerstedt and Verboven](https://www.stata-journal.com/article.html?article=st0349) 
or the work of [Taragin and Sandfort](https://cran.r-project.org/web/packages/antitrust/index.html)

