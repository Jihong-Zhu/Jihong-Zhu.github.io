---
layout: post
title:  "Rigid-body motion I - Rotation"
date:   '2019-11-17'
categories: Robotics
---
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
We can express rigid-body rotation in two ways:
+ Rotation matrix,
+ Exponential representation (by a vector and a angle).
We will discuss both of them in the following subsections. We will explain the key ideas only.

## Rotation matrix
All 3D rotation matrices (denote with $$\mathbf{R}$$) form the $$SO(3)$$ group that
\\[
  \mathbf{R} \mathbf{R}^T = \mathbf{I}
\\]
A rotation matrix can:
+ express an orientation,
+ change the reference frame,
+ transform a matrix or vector.

# Orientation
Let's consider a fixed frame je in the world $$\{s\}$$ as the reference frame, a rigid body with a body frame $$\{b\}$$ attached. We could express the orientation of the rigid body (wrt) the fixed frame as:
\\[
  \mathbf{R}_{sb}
\\]
When there is no subscription (or with subscription $$s$$), the reference frame is the fixed frame.

# Change the reference frame
Let's consider another frame $$\{c\}$$ in the world, now if we would like to express the body frame $$\{b\}$$ in $$\{c\}$$ instead of $$\{s\}$$, we can

$$\mathbf{R}_{cb} = \mathbf{R}_{cs} \mathbf{R}_{sb}$$

$$\mathbf{R}_{cs}$$ is a matrix that change the reference frame for body frame $$\{b\}$$ from $$\{s\}$$ to $$\{c\}$$.

# Transform a matrix or vector
Let's rotate the rigid body wrt a (unit) vector $$\mathbf{\omega}$$ by $$\theta$$, the rotation matrix can be written as:

$$\mathbf{R}(\mathbf{\omega}, \theta)$$

One thing can be ambiguous is the vector $$\mathbf{\omega}$$. This vector can be defined either wrt the fixed frame $$\mathbf{\omega}_s$$ or the body frame $$\mathbf{\omega}_b$$, the corresponding matrices can be give as:
\\[
  \mathbf{R}_s(\mathbf{\omega}_s, \theta)
\\]
\\[
  \mathbf{R}_b(\mathbf{\omega}_b, \theta)
\\]
The new orientation of the rigid body is then: $$\mathbf{R}_s(\mathbf{\omega}_s, \theta) \mathbf{R}_{sb}$$ and $$\mathbf{R}_{sb} \mathbf{R}_b(\mathbf{\omega}_b, \theta)$$. Even for the same $$\mathbf{R}(\mathbf{\omega}, \theta)$$ value, depending on which frame $$\mathbf{\omega}$$ is defined, we have different orientation of the rigid body.

Once we can express rotation (similar to distance in translation), we also would like to see how to express angular velocity (similar to velocity).

## Angular velocity
Assume a rigid body frame $$\{b\}$$ orientation is given by $$\{\mathbf{x}, \mathbf{y}, \mathbf{z}\}$$, we rotate the frame along (unit) vector $$\mathbf{\omega}$$ by $$\theta$$. It takes time $$t$$ to complete rotation, then the speed of rotation can be regarded as the time derivative of $$\theta$$: $$\dot{\theta}$$.

The angular velocity can be given by $$\mathbf{w} = \dot{\theta} \mathbf{\omega}$$.

The instantaneous rotation for each vector component in $$\{b\}$$:
\\[
  \dot{\mathbf{x}} = \mathbf{w} \times \mathbf{x} = \[\mathbf{w}\] \mathbf{x}
\\]
\\[
  \dot{\mathbf{y}} = \mathbf{w} \times \mathbf{y} = \[\mathbf{w}\] \mathbf{y}
\\]
\\[  
  \dot{\mathbf{z}} = \mathbf{w} \times \mathbf{z} = \[\mathbf{w}\] \mathbf{z}
\\]  
where $$[\mathbf{w}]$$ denotes a screw-symmetric matrix defined by vector $$\mathbf{w}$$.

We define the derivative of rotation matrix $$\mathbf{R}$$ as:
\\[
  \dot{\mathbf{R}} = \mathbf{w} \times \mathbf{R} = \[\mathbf{w}\] \mathbf{R}.
\\]

All the screw symmetric matrices defined by $$\mathbf{w}$$ form a group we denote $$so(3)$$, which is the Lie algebra of Lie group $$SO(3)$$.   
## Exponential representation
From what we discussed previously, instead of representing rotation with rotation matrix $$\mathbf{R}$$ which has 9 parameters, we can also express rotation as a unit vector $$\mathbf{\omega}$$ and the rotation angle $$\theta$$. This is what we refer to as exponential representation of rotation. We are interested in how to transform this representation back to rotation matrix.

## Matrix logarithm of rotation
Instead of transform exponential representation to rotation matrix, here we are interested in the reverse conversion.

This concludes the representation of rotation.
