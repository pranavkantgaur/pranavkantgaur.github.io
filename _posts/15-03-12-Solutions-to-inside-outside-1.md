---
layout: post
title: My guesses at solutions to the 3-cell marking problem
---


In this post, I would like to ponder on the possible solutions to the problem I presented in my previous post. Just as a recap, the problem is: Given a tetrahedral mesh and a surface mesh(the _region of interest_ or _ROI_), we need to figure out a way to mark _each_ tetrahedron of the given tetrahedralization either as _inside_ or _outside_ region of interest. To avoid any confusion I should point out that the surface mesh representing the ROI is defined over vertices of the given tetrahedralization. As I have discussed [here](http://cs.stackexchange.com/q/26237/15154), I will first attempt to solve this problem in two dimensional domain, where my task simplifies as: Given a polygonal mesh and a polygon boundary as input mark all polygons of the mesh as either _inside_ or _outside_ the boundary.  

First obvious approach to this problem is the extension of the existing solutions to [_Point in Polygon_](en.wikipedia.org/wiki/Point_in_polygon) problem. Point in polygon problem is concerned with marking an _arbitrary_ query point as either _inside_ or _outside_ the input polygon. 

Common approach called the _ray casting_ algorithm involves casting a ray in random direction from the query point and compute _number of intersections_ it had with the boundary of the polygon. If the number of intersections are _even_ it implies that the point is _inside_ else the point is marked as _outside_ the polygon boundary. Degenerate condition for this algorithm is when the point lies _very_ near(or onto) to the boundary of the polygon, in which case the marking based on number of intersections fails in general.

However, in our case the problem is simplified by the following facts:  
1. _Point_ will not be arbitrarily positioned but a _representative_ of the query polygon say the [barycenter](en.wiktionary.org/wiki/barycenter) of the query polygon.  
2. If the polygonal boundary is _convex_ we do not have to deal with this problem at all because all polygons will be _inside_. 

So, subsequent discussion has significance only for _concave_ boundaries. An algorithm based on _ray casting_ approach for marking polygons can be like this:  

```
1 Add all polygons of the mesh in a queue 'Q'
  1.1 For each polygon 'P' in 'Q':
    1.1.1 Compute Barycenter 'b'
    1.1.2 Generate a ray 'r' in random direction emanating from 'b'
    1.1.3 Compute intersections with each segment of the polygonal boundary
    1.1.4 Count the number of unique intersections, i.e., discard identical intersection points.
    1.1.5 If number of intersections are 'even', mark 'P' as 'outside', else mark 'P' as 'inside'  
2 Repeat 1 untill 'Q' is not Null 
```
