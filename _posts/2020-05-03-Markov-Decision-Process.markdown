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

**State Transition**: $$P$$ give the probability of transition from the current state $$s$$ to the next state $$s^\prime$$.

For a system with $$N$$ state, we would expect a $$N \times N$$ State Transition Matrix.

## Markov Reward Process
A Markov Reward Process is a Markov Process + reward function + a discount factor, $$\langle S, P, R, \gamma \rangle$$:
- **State**: $$S$$
- **State Transition**: $$P$$
- **Reward Function**: $$R$$
- **Discount Factor**: $$\gamma \in [0, 1]$$

The reward can be defined as some score associated with the state: once exit the state, the agent receives the reward associated with the state.

The discount factor is there for discounting the future reward, it can be set to $$1$$, which indicates no discount on the future reward. Often is set to be a value less than $$1$$ for:
- avoid infinite reward,
- future reward could more uncertain,
- humans tend to prefer instant reward than later reward.

The goal of the Markov Reward Process setting is to find an optimal state transition that gives the highest reward. We define the expected reward we get at the $$k$$ instance as $$v(s_k)$$. We refer to $$v$$ as the value function.
<!-- This bring us to the so-called *Bellman equation*:
\\[
  v(s_k) = r_k + \gamma v(s_{k + 1})
\\] -->

The expected reward at the current instance ($$k$$ instance) equals the immediate reward (at $$k$$ instance) + the expected reward at the next instance ($$k + 1$$ instance) times the discount factor $$\gamma$$. This is also an essential idea in dynamic programming.

In a MRP, there is no notion of action, the agent passively move to one state to another given the **State Transition**: $$P$$. We then extend the MRP by consider the agent is able to take **_action_** ($$A$$) in the process instead of simply follows the **State Transition**: $$P$$. This gives us the MDP.

## Markov Decision Process
A Markov Decision Process is a Markov Reward Process + Action, $$\langle S, P, R, A, \gamma \rangle$$
- **State**: $$S$$
- **State Transition**: $$P$$
- **Reward Function**: $$R$$
- **Discount Factor**: $$\gamma \in [0, 1]$$
- **Action**: $$A$$

Instead of passively relying on **State Transition** $$P$$ for moving along the process, now the agent can actively take action.

Lets now look at the comparison between passively moving and actively taking action:

### Passively moving (MRP)
When passively moving, the state value function can be written as:
\\[
  v(s_k) = r_k + \gamma \sum_{i = 1}^n p_i(s_{k + 1}(i)) v_i(s_{k + 1}(i))
\\]
Basically, assume we have $$n$$ possible next states $$s_{k + 1}$$ for current state $$s_k$$. The expected reward at the next state ($$k + 1$$) can be expressed by the sum of probability of transit to that state $$p_i(s_{k + 1}(i))$$ times the expected reward at the state ($$v_i(s_{k + 1}(i))$$).

In the figure, we show the case for $$n = 2$$.

### Taking action
When the agent is able to take actions, this give rise to another function called **action value function**: which indicates the expected reward taking each different action.

Instead of directly transit from current to the next state, now we consider an intermediate action step. The state value function can be re-written into:
\\[
  v(s_k) = \sum_{i = 1}^m p_i(a_k(i)) q(a_k(i))
\\]
This is simply replace the expected reward at the next state using the expected reward taking the actions. The probability $$p_i(a_k(i))$$ gives the probability taking the action $$a_k(i)$$, and $$q(a_k(i))$$ is the **action value function** we mentioned earlier.

Then the question is how to compute $$v(a_k(i))$$: the **action value function**?

After taking a certain action, we are going to end up in some new state $$s_{k + 1}$$, therefore:
\\[
  q(a_k) = r_k + \gamma \sum_{i = 1}^n p_i(s_{k + 1}(i)) v_i(s_{k + 1}(i))
\\]

This is the expected reward at $$s_{k + 1}$$ times the discount factor + the immediate reward of leaving current state $$s_k$$.

By combining the two equation above, we are able to write Bellman expectation equation for both state and action value function.

Bellman expectation equation for state value function: Taking $$q(a_k)$$ into $$v(s_k)$$,
\\[
  v(s_k) = r_k + \gamma \sum_{j = 1}^m p_j(a_k(j)) \sum_{i = 1}^n p_i(s_{k + 1}(i)) v_i(s_{k + 1}(i))
\\]

Bellman expectation equation for action value function: Taking $$v(a_k)$$ into $$q(s_k)$$,
\\[
  q(a_k) = r_k + \gamma \sum_{j = 1}^n p_j(s_{k + 1}(j)) \sum_{i = 1}^m p_i(a_k(i)) q(a_k(i))
\\]
