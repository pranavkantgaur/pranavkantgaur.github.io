---
layout: post
title: Learning Combinatorial Maps
---

In an attempt to implement Constrained Delaunay tetrahedralization, I have started to learn about a beautiful concept in topology called _Combinatorial Maps_. This datastructure can be used to represent _orientable_ subdivided d-dimensional objects. Speciality about these structures is that they are _edge centered_ meaning they define all components(called _cells_) of an objectusing a basic element called _dart_ and a set of pointers modelling _incidence_ and _adjacency_ relations between components.  
To avoid repeating a topic which is rather comprehensively covered elsewhere I would refer to [CGAL documentation](http://doc.cgal.org/latest/Combinatorial_map/index.html) on Combinatorial Maps. 
