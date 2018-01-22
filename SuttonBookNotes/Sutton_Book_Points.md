# RL by Sutton & Barto

## 1. Introduction
  * Reinforcement learning is learning what to do---how to map situations to actions---so as to maximize a numerical reward signal.
  
  * These two characteristics，**trial-and-error search** and **delayed reward**--are the two most important distinguishing features of reinforcement learning.
  
  * One of the challenges that arises in reinforcement learning and not in other kinds of learning is the **tradeoff between exploration and exploitation**.

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
![](https://github.com/yanyangbaobeiIsEmma/CS-234-RL/blob/master/math/exploratoryMoves.png)
* *temporal-difference* learning (Value funciton method)

  ![](https://github.com/yanyangbaobeiIsEmma/CS-234-RL/blob/master/math/TD.gif)
  
    - iteract with environment (opponent player)
    - clear goal, require planning or foresight to take in account delayed effects of choices.

### History of RL
There are two main threads.
1. trial and error
      - Edward Thorndike first expressed the essence of trial-and-error: Law of Effect (it describes the effect of reinforcing events n the tendency to select actions)
      A combination of *selection* and *memory*
         * selectional 
         * associative: alternatives found by selection are associated with particular situations.
      - Minsky's paper *Step Toward Aritifical Intelligence*(1961), discussed *credit-assignment problem*.

 
2. Optimal control, using value functions and DP.
      - from Richard Bellman (mid-1950s), use dynamic system's state and a value funtion, define a functional equation - Bellman equation. Bellman also introduced the discrete stochastic version of optimal control problem known as MDPs.
       - Ron Howard(1960) devised policy iteration method for MDPs. DP suffers from *the curse of dimensionality*, meaning the computations grow exponentially with the number of states.
       - DP is widely considered the only feasible way to solve general stochastic optimal control problem, but it suffers from what Bellman called "the curse of dimensionality", meaning that its computational requirements grow exponentially with the number of state variables.

3. Temporal-difference methods.
      - Klopf (1972) brought trial-and-error learning together with an important component of temporal-difference learning.
      - Sutton and Barto (1978) developed Klopf's ideas and developed a psychological model of classical condistions based on temporal-difference learning. A key step was taken by Sutton in 1988 by separating temporal-difference learning from control, treating it as a general prediction method. That paper introduced TD($\lambda$) algorithm.
      - Sutton and Barto finalized work on actor-critic architecture in 1981.
      - 1989 Chris Watkin developed Q-learning.


## 2. Multi-armed Bandits
### k-armed bandit problem
You are faced repeatedly with a choice among k different options,
or actions. After each choice you receive a numerical reward chosen from a stationary probability
distribution that depends on the action you selected. Your objective is to maximize the expected total
reward over some time period, for example, over 1000 action selections, or time steps.

### Solutions:
1. Action-value Methods:
* greedy method: choose action which has highest estimated value in the history.
* alternative: epsilon-greedy
  - pros: allow epsilon chance to explore, si the probability of selecyiong the optinal action converges to greater than 1 - epsilon
  - cons: not practical. Also worst actions also get explored equally with best actions.

2. Use incremental update on estimation of value

*NewEstimate <- OldEstimate + StepSize[Target - OldEstimate]*

step-size as 1/n results in sample-average method, which guranteed to converge to the true action values of LLN. 

A well-known result in stochastic approximation theory gives us the conditions required to assure convergence with probability 1:

  ![](https://github.com/yanyangbaobeiIsEmma/CS-234-RL/blob/master/math/convergenceCondition.png)

The first condition is required to guarantee that the steps are large enough to eventually overcome any initial conditions or random fluctuations. The second condition guarantees that eventually the steps become small enough to assure convergence.


3. Optimistic Initial Values

By setting inital values for actions, we encourage action-value methods to explore since these methods are biased by their initial estimates.

  ![](https://github.com/yanyangbaobeiIsEmma/CS-234-RL/blob/master/math/optimisticInitialValues.png)

Cons: Only help to explore for stationary problem, any method that focuses on the initial conditions in any special way is unlikely to help with the general nonstationary case.

4. UCB Action Selection

![](https://github.com/yanyangbaobeiIsEmma/CS-234-RL/blob/master/math/UCB.png)
c controls the degree of exploration.

The idea of this upper confidence bound (UCB) action selection is that the square-root term is a measure of the uncertainty or variance in the estimate of a’s value. 















