---
layout: post
title: Understanding the symbolic perturbation adopted in CGAL
---

I am studying a paper by CGAL authors describing their approach to symbolic perturbation technique. This approach has been used in ```Delaunay_triangulation_3``` class to be able to compute _unique_ Delaunay triangulation even in the presence of _degneracies_  in the input. So, before starting my discussion on CGAL solution to degenerate point configuration, I will discuss the problem itself.  
Lets consider problem in more convinient 3D space. The problem can be formulated as:  Given a set of points with _atleast_ one 5-point set in cospherical arrangement(the _degenerate_ condition), we need to find a _unique_ Delaunay triangulation of the point set. Now why this problem is a problem is because as per definition of Delaunay triangulation the circumsphere of every tetrahedron will not have any input point _inside_ it. But since we already have 5 cospherical points, it allows for two possible triangulations of these 5 points and hence the input. So the challenge lies in avoiding this _ambiguity_ and come up with a unique triangulation still.  
Natually, it seems that if we change the input points so that 5 _cospherical_ points do not exist this ambiguity will not appear, but it will change the problem statement. Further, it raises another question as to _how_ to determine the perturbation/modification of the points?  
It was proposed by Edlesbrunner to instead perturb the points _symbolically_. It in essence means to change the problem definition itself, but it is changed in a way such that it converges to the original problem in limiting cases as we will see later in our discussion of CGAL paper.  
Now, lets come back to the approach proposed and implemented by CGAL guys. They have described their approach in a report [here](https://hal.inria.fr/inria-00166710/file/soda.pdf).   
*** TO BE CONTINUED...***
