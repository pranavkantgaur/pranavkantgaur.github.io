---
layout: post
title: On Self intersection problem
---

These days I have been trying to solve the problem of detecting and removing self-intersections from a three-dimensional(3D) polygonal mesh. In this post(or even possibly in the upcoming posts), I will discuss this problem in detail and my ideas to solve it. So, here goes the problem statement,

Given a physical domain containing multiple geometrically aligned objects. We need to determine their region of contact. Suppose further that we represent this domain in the form of a 3D polygonal mesh. With this in assumption in place, our target of finding the region(s) of contact becomes more concrete. In essence, we need to find set of polygons from each object which overlap with its counterparts from neighbouring objects. 

Lets consider a simple case of two side aligned identical cubes. If we check
