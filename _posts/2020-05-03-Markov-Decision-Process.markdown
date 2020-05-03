---
layout: post
title:  "Markov decision process"
date:   '2020-05-03'
categories: Machine Learning
---
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
This post was written as a summary of the [2nd Lecture on RL of David Silver](https://www.youtube.com/watch?v=lfHX2hHRMVQ&list=PLzuuYNsE1EZAXYR4FJ75jcJseBmo4KQ9-&index=2).

In the post, I will try to summarize the key idea in the Markov Decision Process (MDP). The post will starts from Markov Process, then Markov Reward Process, in the end Markov Decision Process.

## Markov Process
A Markov Process consists of two components $$\langle S, P \rangle$$:
- **State**: $$S$$
- **State Transition**: $$P$$

A **State** $$S$$ in Markov Process fully describe the system at the current instance. This is called a Markov property: *The future is independent from the history giving present*.

**State Transition**: $$P$$ give the probability of transition from the current state $$s$$ to the next state $$s\prime$$.

For a system with $$N$$ state, we would expect a $$N \times N$$ State Transition Matrix.

## Markov Reward Process
A Markov Reward Process is a Markov Process + reward function + a discount factor $$\langle S, P, R, \gamma \rangle$$:
- **State**: $$S$$
- **State Transition**: $$P$$
- **Reward Function**: $$R$$
- **Discount Factor**: $$\gamma \in [0, 1]$$

The reward can be defined as some score associated with the state: once exit the state, the agent receives the reward associated with the state.

The discount factor is there for discounting the future reward, it can be set to $$1$$, which indicates no discount on the future reward. Often is set to be a value less than $$1$$ for:
- avoid infinite reward,
- future reward could more uncertain,
- humans tend to prefer instant reward than later reward.

The goal of the Markov Reward Process setting is to find an optimal state transition that gives the highest reward. We define the expected reward we get at the $$k$$ instance as $$v(s_k)$$. We refer to $$v$$ as the value function. This bring us to the so-called *Bellman equation*:
\\[
  v(s_k) = r_k + \gamma v(s_{k + 1})
\\]

The expected reward at the current instance ($$k$$ instance) equals the immediate reward (at $$k$$ instance) + the expected reward at the next instance ($$k + 1$$ instance) times the discount factor $$\gamma$$. This is also an essential idea in dynamic programming.

## Markov Decision Process
To be continued.
