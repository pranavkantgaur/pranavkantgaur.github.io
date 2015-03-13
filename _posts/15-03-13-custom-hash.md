---
layout: post
title: Hash functions for 3D points
---

I have been trying to implement the solution to 3-cell marking problem that I discussed [earlier](http://pranavkantgaur.github.io/Solutions-to-inside-outside-1/). In order to avoid duplicate points of intersection while counting number of intersections of a _random_ ray from the barycenter of each tetrahedron I need to use set representation to store the intersection points.

C++ requires using a hash function for doing comparision while inserting an element in the set. Since my _elements_ are three dimensional, I need to find out an _effective_ hash function for multi-dimensional structures. 

So, this post will contain an active list of hash functions that I find on internet proposed for multdimensional structures. 
