---
layout: post
title: My guesses at solutions to the 3-cell marking problem
---


In this post, I would like to ponder on the possible solutions to the problem I presented in my [previous post](http://pranavkantgaur.github.io/Inside-Outside-Test/). Just as a recap, the problem is: Given a tetrahedral mesh and a surface mesh(the _region of interest_ or _ROI_), we need to figure out a way to mark _each_ tetrahedron of the given tetrahedralization either as _inside_ or _outside_ ROI. To avoid any confusion I should point out that the surface mesh representing the ROI is defined over vertices of the given tetrahedralization. Further, the title of the post refers to _tetrahedrons_ as 3-cells similarly you can refer _triangles_ as 2-cells following the terminology used [here](http://doc.cgal.org/latest/Combinatorial_map/index.html). As I have discussed [here](http://cs.stackexchange.com/q/26237/15154), I will first attempt to solve this problem in two dimensional domain, where my task simplifies as: Given a triangle mesh and a polygon boundary as input, mark all triangles of the mesh as either _inside_ or _outside_ the boundary.  

An obvious approach to this problem is the extension of the existing solutions to [_Point in Polygon_](http://en.wikipedia.org/wiki/Point_in_polygon) problem. Point in polygon problem is concerned with marking an _arbitrary_ query point as either _inside_ or _outside_ the input polygon. 

Common approach called the _ray casting_ algorithm involves casting a ray in random direction from the query point and compute _number of intersections_ it had with the boundary of the polygon. If the number of intersections are _even_ it implies that the point is _inside_ else the point is marked as _outside_ the polygon boundary. Degenerate condition for this algorithm is when the point lies _very_ near(or onto) to the boundary of the polygon, in which case the marking based on number of intersections fails in general.

However, in our case the problem is simplified by the following facts:  
1. _Point_ will not be arbitrarily positioned but a _representative_ of the query triangle say its [barycenter](en.wiktionary.org/wiki/barycenter).  
2. If the polygonal boundary is _convex_ we do not have to deal with this problem at all because all triangles will be _inside_. 

So, subsequent discussion has significance only for _concave_ boundaries. An algorithm based on _ray casting_ approach for marking triangles can be like this:  

```
1 Add all triangles of the mesh in a queue 'Q'
  1.1 For each triangle 'T' in 'Q':
    1.1.1 Compute Barycenter 'b'
    1.1.2 Generate a ray 'r' in random direction emanating from 'b'
    1.1.3 Compute intersections with each segment of the polygonal boundary
    1.1.4 Count the number of unique intersections, i.e., discard identical intersection points.
    1.1.5 If the number of intersections are 'even', mark 'T' as 'outside', else mark 'T' as 'inside'  
2 Repeat 1 until 'Q' is not Null 
```
Currently, this seems to solve the marking problem in two-dimensional domain but I am keen to have your comments on this. Assuming this approach to be correct, I come back to my original problem of marking 3-cells as _inside_ or _outside_ the given ROI. I think it only amounts to extending above presented approach to 3D domain by replacing triangles _T_ with tetrahedrons and the ROI becomes a polyhedron instead of a polygon. 

Specifically, a 3D version of the above algorithm may look like:

```
1 Add all tetrahedrons of the tetrahedralization in a queue 'Q'
  1.1 For each tetrahedron 'T' in 'Q':
    1.1.1 Compute Barycenter 'b'
    1.1.2 Generate a ray 'r' in random direction emanating from 'b'
    1.1.3 Compute intersections with each polygon(in our case they are triangles) of the polygonal boundary
    1.1.4 Count the number of unique intersections, i.e., discard identical intersection points.
    1.1.5 If the number of intersections are 'even', mark 'T' as 'outside', else mark 'T' as 'inside'  
2 Repeat 1 until 'Q' is not Null 
```

Rough tracing on paper on some toy input examples seems to suggest this approach should work in case of 3D domain as well. But I will be implementing it now. I will report results in the posts to follow.
 
