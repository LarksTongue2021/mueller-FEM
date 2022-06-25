# transition_path_theory_FEM_distmesh
Finds the committor function, the reactive current, and the transition rate for 2D problems using finite element method on mesh generated by P.-O. Persson's distmesh algorithm
The Bondary Value Problem for the committor function for the overamped Langevin dynamics 

dX = - \nabla V(X)dt + \sqrt{2\beta^{-1}}dW 

in the domain with a reflecting boundary given by D: = {x : V(x) \le Vbdry} 

\nabla \cdot ( \exp(-\beta V(x)) \nabla q(x)) = 0, x \in D \ (A\cup B)

q(x) = 0, x \in A

q(x) = 1, x \in B

The finite element solver is rewritten on python and adapted from:
Title: Remarks around 50 lines of Matlab: short finite element implementation
Authors: Jochen Alberty, Carsten Carstensen and Stefan A. Funken
Journal: Numerical Algorithms 20 (1999) 117–137
https://www.math.hu-berlin.de/~cc/cc_homepage/download/1999-AJ_CC_FS-50_Lines_of_Matlab.pdf

The mesh generator is Per-Olof Persson's distmesh algorithm rewritten on python:
http://persson.berkeley.edu/distmesh/

The package consists of the following files:
distmesh.py (all functions needed for triangular mesh generation are there)
FEM_TPT.py (all functions for computing the committor, the reactive current, and the transition rate are there)
face_TPT_driver.ipynb (shows how to compute the committor, the reactive current, and the transition rate on the example of the Face potential)

Important settings in face_TPT_driver.ipynb:
The Face potential has four local minima: the "eyes" are the deepest minima, and the "nose" and the "mouth" are shallower minima that can be considered as a dynamical trap.

--> The sets A and B are circles around the eyes centered at (xa,ya), (xb,yb), of radii ra and rb, respectively.

--> The outer boundary is the level set of the potential {(x,y) : V(x,y) = Vbdry}. 

--> h0: The important parameter that determines how fine is the mesh is h0, the desired length of mesh edge.

--> generate_mesh: The boolean variable generate_mesh determines whether the mesh needs to be generated or read from the files.

--> Set generate_mesh = True for the first run. The generated mesh will be saved to files. If you want to experiment further with the same mesh, set generate_mesh = False. Then it will be read from the files.

--> q: The variable q is the committor at the mesh points.

--> Rcurrent: The variable Rcurrent is Npts-by-2 array with components of the reactive current at the mesh points.

--> Rrate: The variable Rrate is the transition rate.

The mesh points, the committor, the reactive current are saved into a csv file.
