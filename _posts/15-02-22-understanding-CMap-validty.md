---
layout: post
title : Representing a PLC using CGAL's LCC package  
---

After completing an [exercise](https://gist.github.com/pranavkantgaur/54ec0c019422a5377d35#file-cubelcc-cpp) on representing a cube using CGAL's linear cell complex(or [LCC](http://doc.cgal.org/latest/Linear_cell_complex/index.html)), I now come back to my original problem. Given a set of points and triangles in a (say PLY) file, I need to generate the corresponding LCC representation. I will break down this task into following:  
1. For each edge in each triangle get a handle to the triangle sharing that edge.  
2. Compute the sewable dart pairs (d1, d2) from both triangles.  
3. Call sew<2>(d1, d2) to 2-sew d1 and d2.  
One point that I can think of to reduce apparant computation complexity is to remove a triangle from the set once it has been found to be linked with 2 triangles. Since in manifold surfaces a triangle will be connected at most with 2 other triangles only. Further, any of its segment can at most be connected with one other triangle only.


