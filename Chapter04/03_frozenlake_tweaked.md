### `filter_batch`

- We calculate `disc_rewards` using `filter_fun` with a discounting factor `GAMMA` such that, the more time steps the agent takes to reach the goal, the lesser the reward.

### `__main__`

- As getting valid instances with decent reward is much rarer for FrozenLake, instead of discarding old batch of training data, we keep appending new data on top of the old data.
- Of the entire batch of old and new data, we keep only the 500 most recent instances and discard the rest.
- We use a lower learning rate than earlier.
- Stop when `reward_mean > 0.8`.