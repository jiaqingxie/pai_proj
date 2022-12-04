## Task 0: Dummy Task (Exact Posterior)
Task 0 involves calculating the exact posterior for each of the priors. To avoid underflow, we use the logsumexp trick. The log posterior is calculated by multiplying the log prior by the log likelihood. As a result, the log posterior is calculated by dividing the logsumexp of the log likelihood. It is the exact solution that yields a result of 1.