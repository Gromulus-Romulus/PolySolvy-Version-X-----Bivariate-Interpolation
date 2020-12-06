
## Underlying Background and Theory: ##

The problem of finding an interpolating polynomial for a dataset in multiple variables is an area of extensive numerical research. In this Python project, we explore how this may be done practically for bivariate datasets representing a mystery function f(x,y) -> z.

Recall that Interpolation is the problem of constructing a function p belonging to a finite dimensional linear space from a given set of data (Gasca et al., 2000). p is said to interpolate f if for every sample point x_i within the domain of f, p(x_i) = f(x_i) with 0 <= i <= n.

As we have seen in our numerical analysis class this term, this univariate case is fairly straightforward to solve. From a theoretical standpoint, we saw that a unique interpolation polynomial can be determined from the Lagrange form ...

<img src="https://latex.codecogs.com/gif.latex?p(x)=\sum_{i=0}^{n}{y_il_i(x)}"/>
<img src="https://latex.codecogs.com/gif.latex?l_i(x)=\prod_{j=0,j\neq{i}}^{n}{\frac{x-x_j}{x_i-x_j}"/>

Where i = 0, .., n for n + 1 interpolation nodes, and l_i represents the cardinal polynomial for the ith node. In this respect, the y_i terms act as scaling factors and the l_i acts as a continuous analog to the binary Kronecker delta (Cheney & Kincaid, 2008, p. 126-127).

Other approaches to the interpolation problem include the Hermite and Birkhoff methods, which utilitizes not only the values of the interpolation nodes at given points but also the specified values of their derivatives (Wikipedia, 2020). The Newton approach we learned in class this term approaches the problem from a recursive standpoint using divided differences (Cheney & Kincaid, 2008).

Specifying the form of the interpolation polynomial in the multivariate case however, is extensively more difficult. It requires even more of a basis in core topics in linear algebra - namely the concepts of abstract vector spaces and subspaces.

In their survey of multivariate interpolation methods, Gasca et al. provide of the Lagrangian form for the unique multivariate interpolating polynomial:

<img src="https://latex.codecogs.com/gif.latex?p(x)=\sum_{i=0}^{n}{y_i\prod_{j=0,j\neq{i}}^{n}{H_j}{Hj(xi)}}"/>

Where for each point x_i, a hyperplane Hi containing x_i is chosen, but no other points.

## Contents: ##
  - vmond.py contains the Vandermonde() function along with the Gauss() function it calls; these are used to calculate the coefficient vector used by bivariate.py
  - bivariate.py combines the terms from a coefficient vector produced by Vandermonde() with their corresponding (x^n)(y^n) terms (this is dependent on the size of the data set)
  - graph_bivariate.py contains the graphing functionality of the project. It uses bivariate.py to generate appropriate z-values for a generated range of data points (including those which are being interpolated) and then graphs them using plot_trisurf() from Axes3D. It overlays the interpolating function with the original points that are being interpolated.
  - multivar_interp_generic.py is a file that was used to visualize the power matrix and terms of the bivariate function. It has no functional use in EXAMPLE.py
  - EXAMPLE.py the working example which contains all of the code files compiled along with a series of examples. The intention is that these be run in a jupyter notebook using the IPython kernel (this allows for the interactive graphing).
  
## How To Use EXAMPLE.py: ## 
  - Copy all the code in EXAMPLE.py
  - Open web-browser tab and navigate to https://jupyter.org/try
  - Once there, click on "Try Classic Notebook" and then wait for the page to load
  - Once the page has loaded click on "insert" tab at the top menue, from there click on "Insert Cell Below".
  - Paste the entirety of the copied code from EXAMPLE.py into the "In [ ]" cell that appears
  - Hit "Run" on the top menu and enjoy.
    
    *NOTE: to try other examples enter them at the bottom of the cell (near the other examples) and then press "Run" again. Input must follow the same patterning as the other examples and contain a "square" amount of data points (i.e. 1, 4, 9, etc.). The limitation of using jupyter notebook is that it can't handle running more than 9 points currently. Further development for sets of 16+ is needed.
  
