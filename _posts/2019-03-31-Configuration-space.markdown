---
layout: post
title:  "Configuration space"
date:   '2019-03-31'
categories: Robotics
---
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

C-space has two important characteristics:
1. DoFs
2. Topology

For the same DoFs, we can have different topologies. A 2D plane is not of the same topology as a sphere, which can also be represented by two quantities: latitude and longitude.
For the same DoFs, we can have different topologies. A 2D plane is not of the same topology as a sphere, which can also be represented by two quantities: latitude and longitude.

# C-space representation
Normally for $$n$$ DoFs rigid bodies we can describe its c-space using $$n$$ linear independent parameters. But, with such representation, we could have singularities. Take latitude and longitude for example, when we are around the poles area, the representation could switch signs, and this will create problem when we try to compute velocity using the representation.

We usually solve the problem by using more parameters with constraints to describe the c-space.

# Non-holonomic constraints
$$n$$ holonomic constraints reduce the DoFs by $$n$$. Yet, there are also constraints that does not reduce the DoFs, and this kind of constraints are called non-holonomic constraints. Hereby give an example:

![image](/asset/coin_rolling.png)

The motion of the circle on the plane can be describe by 4 parameters:
\\[
  q = [x~y~\theta~\tau]^T
\\]
If we have a non-slipping condition on the movement, we are able to define constraints on the velocity of $$q$$:

$$
    \begin{bmatrix}
      \dot{x} \\
      \dot{y}
    \end{bmatrix}
$$
