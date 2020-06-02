### `iterate_batches`

- Yields one batch of episodes at a time
- The network takes observations as input, and returns action probabilities as predictions
- At this point, the network is randomly initialized, so the predicted actions are random
- Once we have accumulated `batch_size` episodes, we yield the batch

### `filter_batch`

- Collects all rewards for each episode in batch
- Calculates reward boundary `reward_bound` by taking `PERCENTILE` percentile value of the collected rewards
- Also calculates reward mean
- Filters out episodes that have reward less than `reward_bound` and adds the other episodes to the training data
- We only keep those actions which give good rewards
- By feeding these good action instances to our model, we train our model to predict better actions with each iteration
- Initially, the model will predict random actions, so our loss will be high (difference between predicted action and the action we want)
- But as we propagate the loss backwards and update weights, the predicted actions should improve to be closer to wanted actions


Basically, the `cross-entropy` method helps us create good-quality training data, on which our model then trained