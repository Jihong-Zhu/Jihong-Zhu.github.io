---
layout: post
title:  "Solving MDP - Value and Policy Iteration"
date:   '2020-05-14'
categories: Machine Learning
---
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

This post was written as a summary of the [3rd Lecture on RL of David Silver](https://www.youtube.com/watch?v=Nd1-UUMVfz4&list=PLzuuYNsE1EZAXYR4FJ75jcJseBmo4KQ9-&index=3)

In the last post we defined what is MDP, now we would like to know how to solve it.

There are two ways to solve a MDP:
- Policy Iteration
- Value Iteration

Note that to solve MDP means that we need to find the optimal policy that gives the highest reward under the MDP. **The optimal policy is deterministic.** Before we start with solving the MDP, we first introduce how to evaluate a policy.
## Policy Evaluation
**_Given a certain policy, we would like to find the expected reward for each state in the MDP._**

We do policy evaluation by:
1. initialize each state with a random expected reward (all **0s**  for instance)
2. Update the expected reward by Bellman expectation equation for state value function (See [Markov decision process](https://jihong-zhu.github.io/machine/learning/2020/05/03/Markov-Decision-Process.html)).
3. Re-do step 1 and 2 until the reward does not change anymore.

Basically this means we update the current state reward with one step look ahead given the policy. We continue to do this until the reward does not change anymore (converged). We found the expected reward for each state given the policy.
## Policy Iteration
We do policy iteration by:
1. Policy evaluation
2. Act greedy according to the policy evaluation results
3. Re-do step 1 and 2 until there is no change in the policy.
4. Eureka! We find the optimal policy.

# Modification:
Note with policy iteration, we need to act after we finish the whole policy evaluation process which is also iterative.

Instead of wait until policy evaluation converges, do we need to wait for it to converge?

The answer is no. We could simply act greedy after $$k$$ steps (when $$k = 1$$ this is equivalent to value iteration) update of the expected reward in policy evaluation. We continue this until there is no change in the policy. And Eureka! We find the optimal policy.

## Value Iteration
In value iteration, there is no specific policy for evaluation. We simply iterative find the value function of the given MDP based on Bellman optimality equation. Then act according the the final value function.

## Important Note
**_Here solving the MDP means that we know the full dynamics of MDP. This is usually not the case in the real-world problems. Therefore in the next post I will try to explain the method for solving MDP without a model._**
