# **The Bandit Problem**

To understand the RL, we need to understand the Bandit problems.Imagine there is a sloth machine in a casino and when you pull a lever it give you a reward.Now lets say there are multiple slot machines, then how would to find the arm or the lever that gives you the maximum reward ??
Well to answer this question we have 3 solution by parts :
  1) Asymptotic correctness : As $t \rightarrow \infty$, We will eventually find the arm with max reward.There are older literature which shows some ways that does this and asymptotically reaches the appropriate arm.
  2) Regret optimality : The solution means that while exploring for the correct arm, how to minimize the reward lost if we already had known the right arm. ![Alt text](Regret Optimality.PNG)
  3) PAC optimality (Probably approximately correct) : This answers the problem of how close I can get to the solution.

# **Value Based Function Methods**

Lets say we have to estimate a function called Q*(a) which gives the value of an action.Now how to estimate this function at any given point of time t.A simple method would be to average the rewards that the action has provided me till time t.Mathematically, it can be represented as:

$$Q_t(a) = \frac{\sum_{i = 1 \rightarrow t} 1_{a_t = a} R_i} {\sum_{i = 1 \rightarrow t} 1_{a_t = a}}$$

where $1_{a_t = a}$ is an indicator function representing if action at time t is action a.

**Exploration-Exploitation Policies**
  1) Espilon Greedy policy : This policy simply states that for $(1-\epsilon)$ probablity, the action choosen shall be $argmax_a Q_t(a)$.And with $\epsilon$ probablity, the other actions actions will be choosen with equal probablity.
  2) Softmax exploration policy : This is better than Epsilon Greedy in a cases which we want to bias exploration to the good actions.In Espilon greedy, at exploration phase all the actions have equal probability of being choosen i.e $\frac{\epsilon}{n_a-1}$, where $n_a$ is the number of unique actions possible and the is subtracted by 1 beacause in exploration we do not take the action which was suppose to be choosen by exploitation.
     Mathematically, we can program the probablity of choosing an action as :
     
$$Pr(a_t = a) = \frac{e^{Q_t(a)}}{\sum_{b =1 \rightarrow n} e^{Q_t(b)}}$$
