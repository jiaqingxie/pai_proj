## Task 4 Implementing a policy gradient algorithm (GAME: Lunar Lander)
MLP blocks are composed of linear layers, activation layers, and dropout layers. The param size determines the depth of the full MLP. The output does not include dropout. Dropout rate is 0.03. A Categorical distribution is the output of the MLP over actions in the Actor class. In torch distribution methods, log_prob provides the log probability of a given distribution. Based on given observations, we produce action distributions, and compute the log-likelihood of given actions. We construct seven buffers in the VPGBuffer class and assign observation, action, reward, value, and log probability to each buffer in the store function. For the end_traj function, we first compute TD residual, which is reward + value* - value. It is combined with gamma * lambda into the cummulative sum. It is stored in the TD residual buffer when TD residual is computed. Secondly, we compute rewards-to-go function by feeding reward and gamma into the cumulative sum. In the Agent class, we implement step function where gradient computation is ignored. Based on the categorical distribution of actions and a sample action, a log probability can be computed. The value function could be achieved by critic given a state. In the training session, we change the epochs to 65, max_ex_len to 298. The policy gradient is updated by the loss function -TD-residual * logp. The value gradient is updated by the MSELoss given ret and the output of vnet. Final mean reward is around 226. 