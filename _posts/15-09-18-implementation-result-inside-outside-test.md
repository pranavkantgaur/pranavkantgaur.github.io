---
layout: post
title: Results of implementation of my solution to 3-cell marking problem
---

I have finally implemented the algorithm I proposed in my [previous post](http://pranavkantgaur.github.io/Solutions-to-inside-outside-1/). I have noticed that it is simply not terminating :(. I have checked multiple times to see if there are any infinite loops in there, but it is the [_combinatorial explosion_](https://en.wikipedia.org/wiki/Combinatorial_explosion) which renders this implementation impractical.  
I need to think about a more efficient solution for this problem. One thing that I have noticed about my current solution is that it does not attempt to take advantage of the adjacency of the tetrahedrons which I am marking against given surface mesh(a Linear cell complex). Precisely, it assumes a more general form of problem, that is, given a set of tetrahedrons, mark whether they are inside/outside a given surface mesh. Whereas, my original problem is, given a _mesh of tetrahedrons_, mark each tetrahedron whether it is inside/outside the given surface mesh. As you can clearly notice, tetrahedrons in my problem have an adjacency relation which I at the moment suspect can pave the way for more efficient solution.

