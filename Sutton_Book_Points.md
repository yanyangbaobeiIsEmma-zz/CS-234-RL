# RL by Sutton

## 1. Introduction
  * Reinforcement learning is learning what to do---how to map situations to actions---so as to maximize a numerical reward signal.
  
  * These two characteristics---trial-and-error search and delayed reward---are the two most important distinguishing features of reinforcement learning.
  
  * One of the challenges that arises in reinforcement learning and not in other kinds of learning is the tradeoff between exploration and exploitation.

### Elements of RL
* state
* action
* policy
* reward function (immediate, intrinsic desirability)
* value function (long-term desirability)
   - N.B. evolutionary methods are not necessarily to do value estimation, like genetic algorithms, genetic programming, simulated annealing.
* model of environment 
    given a state and action, models are used to predict next state and reward. Models are used for *planning*.

### Exmaple: Tic-Tac-Toe
  | X | O | O |
  | :----:|:----:| :-----:|
  | O | X | X |
  |   | X |   |
   
#### Classical solutions:
* minimax
* evolutionary approach:
        estimate winning probability by playing some games against opponent.

#### RL and approximate value function
* *temporal-difference* learning (Value funciton method)

  ![](https://github.com/yanyangbaobeiIsEmma/CS-234-RL/blob/master/math/TD.gif)
  
    - iteract with environment (opponent player)
    - clear goal, require planning or foresight to take in account delayed effects of choices.

### History of RL
There are two main threads.
1. trial and error
      - Edward Thorndike first expressed the essence of trial-and-error: Law of Effect (it describes the effect of reinforcing events n the tendency to select actions)
      A combination of *selecction* and *memory*
         * selectional 
         * associative: alternatives found by selection are associated with particular situations.
      - Minsky's paper *Step Toward Aritifical Intelligence*(1961), discussed *credit-assignment problem*.

 
2. Optimal control, using value functions and DP.
      - from Richard Bellman (mid-1950s), use dynamic system's state and a value funtion, define a functional equation - Bellman equation. Bellman also introduced the discrete stochastic version of optimal control problem known as MDPs.
       - Ron Howard(1960) devised policy iteration method for MDPs. DP suffers from *the curse of dimensionality*, meaning the computations grow exponentially with the number of states.

3. Temporal-difference methods.
      - Klopf (1972) brought trial-and-error learning together with an important component of temporal-difference learning.
      - Sutton and Barto (1978) developed Klopf's ideas and developed a psychological model of classical condistions based on temporal-difference learning. A key step was taken by Sutton in 1988 by separating temporal-difference learning from control, treating it as a general prediction method. That paper introduced TD($\lambda$) algorithm.
      - Sutton and Barto finalized work on actor-critic architecture in 1981.
      - 1989 Chris Watkin developed Q-learning.


