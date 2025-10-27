# Lab 4 - Reinforcement Learning Theory

## Task 1.1 - Optimal Policy π∗

In the Gridworld, the optimal policy is to reach the goal state (4,3) with +1 reward while avoiding the -1 penalty at (2,3) and the black wall at (2,2).  
Assuming deterministic transitions, the optimal policy π∗ for each white cell is as follows:

- From (1,1): right
- From (2,1): right
- From (3,1): right
- From (4,1): up
- From (1,2): down
- From (3,2): right
- From (4,2): up
- From (1,3): down
- From (3,3): right

## Task 1.2 - Value Function with γ = 0.9, H = 100, and deterministic transitions

- V\*(4,3) ≈ 1 / (1 - 0.9) = 10
- V\*(3,3) ≈ 1 / (1 - 0.9) = 10
- V\*(2,3) ≈ 0.9 * 10 = 9 (2 steps to goal)
- V\*(3,1) ≈ 0.81 × 10 = 8.1 (3 steps to goal)
- V\*(1,1) ≈ 0.9⁵ × 10 ≈ 5.9 (5 steps to goal)

## Task 1.3 - Value Function with γ = 0.7, H = 100, P = 0.8

- V\*(4,3) ≈ 1 / (1 - 0.7) = 3.33 (goal)
- V\*(3,3) ≈ 0.8 × 1/(1 - 0.2 * 0.7) × 3.33 ≈ 3.101 (1-step)


# Task 2 - Short Questions

## Task 2.1 - Exploration vs. Exploitation

This refers to the trade-off between choosing known actions with high reward (exploitation) versus trying new actions that might lead to better rewards (exploration). Balancing both is essential for learning a good policy.

## Task 2.2 - Credit Assignment Problem

This is the problem of determining which actions were responsible for a reward, especially when the reward is delayed. It’s key in learning long-term strategies. This problem can be trickey due to temporal delays and also the evaluation of impact of actions on longer term outcomes.

## Task 2.3 - What is the Markov Property?

The Markov Property states that the future state depends only on the current state and action, not on the sequence of previous states. The current state contains all necessary information.

## Task 2.4 - Does Chess satisfy the Markov Property?

No, there are moves such as castling that depends on previous states e.g. the king and rook must not have moved previously, the king cannot be moved into check

## Task 2.5 - Q-learning vs. Deep Q-learning

Q-learning uses a table to store Q-values for each state-action pair, which becomes inefficient in large state spaces. Deep Q-learning replaces the table with a neural network that approximates the Q-function, allowing it to scale to complex environments like video games.

