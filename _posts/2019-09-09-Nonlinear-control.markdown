---
layout: post
title:  "Nonlinear stability"
date:   '2019-08-17'
categories: Nonlinear Control
---
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
**_All these writings are based on my understanding and not given any rigorous math proves_**

The major difference between stability of a linear and nonlinear system is that for linear system once the system is stable, it is global exponentially stable. But for nonlinear system, we define a step by step stable definition.
## Local stability
Consider stability in the subset of the whole state space (Around equilibrium points).
# Lyapunov indirect method
The indirect method considers linearization of the nonlinear system dynamic at the equilibrium point(s) for stability.
\\[
  \dot{\mathbf{x}} = \frac{\delta \mathbf{f}}{\delta \mathbf{x}} |_ {\mathbf{x} = 0} + \text{higher order terms}
\\]
If the linearized system is strictly stable, we say that the equilibrium is local asymptotic stable. If it is not stable, then the equilibrium is not stable.

If it is marginally stable, no conclusion can be drawn. **It means that the stability of the equilibrium is decided in the higer order terms.**

The method is not very good in the sense that:
* Nonlinear system with marginally stable linearization can't be checked for stability
* In cases that we need to design control laws for stabilizing nonlinear system, using linearization could make the input term disappear

As we already see, the indirect (linearization) method has some disadvantages in analyzing the nonlinear stability. Below we defines formally all stability condition and the way to prove stability.
# Lyapunov stability (Only local)
Local stability in the Lyapunov sense is a bounded condition. Basically it says that if the system starts within a bounded region $$r$$, there exists an upper bound $$R$$ that the state trajectory never goes outside of $$R$$ ($$R$$ must be a subset of the state space).

**Local Lyapunov stability does not say anything about convergence. It is all about boundedness.**
# Asymptotic stability
A stronger condition will be local asymptotic stability. It also defines a local bound $$r$$, and if the system starts inside $$r$$, the system will go to equilibrium when time approach infinity.

**Local asymptotic stability states that system will converge to equilibrium when time approaches infinity.**
# Exponential stability
This is just to say that the system approaches equilibrium in an exponential manner.
## Global stability
For global asymptotic and exponential stability just means that the local bound $$r$$ in local case is the whole state space. Basically it means you can start anywhere in the state space, and you will end it up in the equilibrium.
## Lyapunov direct method
How to check for these stabilities?
# Local case:
For Lyapunov stability, one needs to find a (**Scalar**) Lyapunov function $$V(\mathbf{x})$$ within $$r$$ such that:
* $$V(\mathbf{x})$$ is positive definite
* $$\dot{V}(\mathbf{x})$$ is **negative semi-definite** (Note that $$\dot{V}(\mathbf{x}) = \frac{\delta \mathbf{V}}{\delta \mathbf{x}} \dot{\mathbf{x}}$$)

For asymptotic stability, one needs to have
* $$\dot{V}(\mathbf{x})$$ is **negative definite**

The reason why it is the case: let's assmue the system state starts inside $$r$$ with a $$V(\mathbf{x}_ s) = V_ s$$, we can find in the state space a contour within $$R$$ such that the lowest value on this contour is $$V_ s$$. Since $$\dot{V}(\mathbf{x})$$ is **negative semi-definite**, the state trajectory will never move out of the contour within $$R$$. When $$\dot{V}(\mathbf{x})$$ is **negative definite** the state not only will **not** move out of $$R$$, it will also converge to the equilibrium (as it is always decreasing.)
# Global case:
Similar to the definition, for the global case, the condition is that local bound $$r$$ in local case is the whole state space. But this is not enough for global asymptotic stability we added a third condition (radially unboundedness):
* if $$\|\mathbf{x}\| \rightarrow \infty$$ then $$V(\mathbf{x}) \rightarrow \infty$$

This is just to avoid we have open contours in $$V(\mathbf{x})$$ that the state diverges from the equilibrium.

If we already have all the above criteria to check for stability, why should we bother to have the **LaSalle's invariance principle**? The answer is very simple, these conditions are **sufficient** but **NOT** necessary conditions.

It means that even if these conditions are not fulfilled, the system might still be stable (one kind or another). **LaSalle's invariance principle** is one fix to still derive asymptotic stability even the conditions are not strictly fulfilled.
## LaSalle's invariance principle
This invariance principle specifically deal with when $$\dot{V}(\mathbf{x})$$ is **negative semi-definite**. In previous definition, we can't derive asymptotic stability. Yet, in a lot of cases (such as the pendulum), the system is indeed asymptotically stable. Take the pendulum (with damping term) for example, if using system's total energy as Lyapunov function, what will happen is $$\dot{V}(\mathbf{x})$$ is dependent solely on $$\dot{\mathbf{x}}$$, and it is not negative definite as $$\dot{V}(\mathbf{x}) = 0$$ anytime when $$\dot{\mathbf{x}} = 0$$ ($$\mathbf{x}$$ not necessarily 0). But the system is actually asymptotically stable.

What **LaSalle's invariance principle** suggests is that $$\ddot{\mathbf{x}} = 0$$ only at equilibrium, then the system is still asymptotically stable. Since at other places when $$\dot{V}(\mathbf{x}) = 0$$, $$\ddot{\mathbf{x}} \neq 0$$, therefore the system will not settle at the position.

A bit more formal definition is given below.

**invariant set**: A set $$\mathbf{G}$$ is an invariant set of a dynamic system if any state starts inside $$\mathbf{G}$$ will remain in $$\mathbf{G}$$ with given dynamic of the system.

Using the definition of **invariant set**, when $$\dot{V}(\mathbf{x})$$ is **negative semi-definite**, we let $$Q$$ be the set inside of $$r$$ such that $$\dot{V}(\mathbf{x}) = 0$$. And $$M$$ be the largest **invariant set** in $$Q$$ given the system dynamic. We have that the system will converge to $$M$$ when $$t \rightarrow \infty$$. "The largest" are in term of set. Basically if there exists several separate sets that $$\dot{V}(\mathbf{x}) = 0$$, then $$M$$ is the union of all.

For our pendulum example, we can see that the only invariant set in $$\dot{V}(\mathbf{x}) = 0$$ is the equilibrium. Therefore the system converge to the equilibrium.
