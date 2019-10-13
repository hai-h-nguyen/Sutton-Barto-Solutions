Ex 2.1 In "epsilon-greedy action selection, for the case of two actions and " =0.5, what is the probability that the greedy action is selected? 

As when taking random actions, we might actually select optimal action as well. Therefore, the probability is 0.5 + 0.5 * 0.5  = 0.75

Ex 2.2 Consider a k-armed bandit problem with k = 4 actions, denoted 1, 2, 3, and 4. Consider applying to this problem a bandit algorithm using "epsilon-greedy action selection, sample-average action-value estimates, and initial estimates of Q1(a) = 0, for all a. Suppose the initial sequence of actions and rewards is A1 = 1, R1 = -1, A2 = 2, R2 = 1, A3 = 2, R3 = -2, A4 = 2, R4 = 2, A5 = 3, R5 = 0. On some of these time steps the " case may have occurred, causing an action to be selected at random. On which time steps did this definitely occur? On which time steps could this possibly have occurred?

Step 1: A1 = 1, R1 = -1: Random selection/greedy with breaking ties among (1, 2, 3, 4). Greedy action is (2,3,4). (Maybe)
Step 2: A2 = 2, R2 = 1:  Possible greedy/ random selection among (2, 3, 4). Greedy aciton is (2) (Maybe)
Step 3: A3 = 2, R3 = -2: Possible greedy/random. Greedy action is (2) (Maybe)
Step 4: A4 = 2, R4 = 2: Possible greedy/random. Greedy action is (2) (Maybe)
Step 5: A5 = 3, R5 = 0: Random because greedy action is (2) (Yes)

Ex 2.3 In the comparison shown in Figure 2.2, which method will perform best in the long run in terms of cumulative reward and probability of selecting the best action? How much better will it be? Express your answer quantitatively.

epsilon-greedy with epsilon = 0.01 will perform best.
Best cumulative reward = (1-epsilon + epsilon/number_of_possible_action)*(q*) + epsilon/ number_of_possible_action * average of other non-optimal actions

Best probability of selecting the best action: 1 - epsilon + epsilon / (number of possible action)

Ex 2.4 If the step-size parameters, alpha_n, are not constant, then the estimate Qn is a weighted average of previously received rewards with a weighting different from that given by (2.6). What is the weighting on each prior reward for the general case, analogous to (2.6), in terms of the sequence of step-size parameters?

Q_{n+1} = Q_1 \prod_{i=1}^{n}(1-alpha_i) + \sum_{i=1}^n R_i \alpha_i \prod_{j=i}^{n-1}(1-\alpha_{j+1})
Weighting for R_i: \alpha_i \prod_{j=i}^{n-1}(1 - \alpha_{j+1}) with i \leq n - 1
Weighting for R_n: \alpha_n
