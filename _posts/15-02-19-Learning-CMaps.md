---
layout: post
title: Learning Combinatorial Maps
---

In an attempt to implement Constrained Delaunay tetrahedralization, I have started to learn about a beautiful concept in topology called _Combinatorial Maps_. This datastructure can be used to represent _orientable_ subdivided d-dimensional objects. Speciality about these structures is that they are _edge centered_ meaning they define all components(called _cells_) of an objectusing a basic element called _dart_ and a set of pointers modelling _incidence_ and _adjacency_ relations between components.  
I would like to start by first pondering into the type of objects this datastructure can represent, i.e., the _orientable_ subdivided d-dimensional objects. We will use a divide and conquor strategy to understand these objects. So what are _orientable_ objects anyway?

*Orientable surfaces*
Quoting from [mathworld][http://mathworld.wolfram.com/OrientableSurface.html],  
> A regular surface M Rn is called Orientable if each tangent space Mp has a complex structure Jp Mp Mp such that p Jp is a continuous function.  

Well, it is so easy to a programmer isnt it? :) 
Lets try understanding it:
 
