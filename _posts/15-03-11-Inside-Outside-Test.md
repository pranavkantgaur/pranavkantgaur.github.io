---
layout: post
title: Testing whether a tetrahedron lies inside Linear cell complex
---

In this post I want to discuss a practical issue which I am facing right now while implementing an adaptive tetrahedral mesh generator. The problem is straightforward to cast and you can see my [StackExchange question](http://cs.stackexchange.com/q/26237/15154) on the same for better visual understanding. As of today, that question remains unanswered, but I am at a point in my implementation where it cannot be avoided anymore.

So, lets get right into the middle of it without further ado. Given a _convex_ three-dimensional [Linear cell complex](http://doc.cgal.org/latest/Linear_cell_complex/index.html)(or LCC) and a surface mesh representing region of interest in that LCC, we need to label 3-cells of LCC as either _inside_ or _outside_ that region of interest.
