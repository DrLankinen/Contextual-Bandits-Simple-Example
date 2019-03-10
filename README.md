# Contextual Bandits Simple Example

This code represents the idea of **contextual bandits** (= associative search). The basic idea is that we have n machines which have k different actions. All machines have different reward probabilities for different actions. The idea is to learn to predict the right action when we know what state we are in. In this example we get state as a color of slot machine. For example when we have green machine it might be better to pull lever 2 and when we have yellow machine it might be better to pull lever 5. This mean that we can't just say that one lever is better for all machines but we need to find the best lever for every machine. Environment I'm using in this example is **stationary** which mean that true value of action is always the same. The method I'm using to approximate action values is called **sample-average**.

There is a class called SlotMachine which have own number of actions and also color to make it easier to identify these machines. First when we initialize the class we set standard_deviation to 1 for all action reward probabilities and mean randomly some number between 0 and 1. Function pull will give us a reward using normal distribution where standard deviation and mean is numbers we initialized earlier.

Then we have choose_action function. This choose maximum action with probability of **1-epsilon** and random action with probability of **epsilon**.

We start by creating four machines which have 10 actions.

Then we map each machine to index to make it easier to get the action. We create two matricies which are **Q** and **N**. Shapes of these are (len(machine) X number of actions). This mean that each row is for each machine and each column is for each action. **Q** is the value estimation and **N** is number of times we have selected that action.

We define number of steps we want our model to go through. Every step it will get a random machine. First it chooses an action when epsilon is 0.01. Then it take action and get back reward. These rewards are stored for plots. Finally it will add one to that action and calulate a new reward estimation for that action.

In the end there is plots. First shows us how different machines gave different rewards durring training. We can see that yellow finds fast the best action and for red it takes more time to find it. The second plot shows us how average reward increases over time.
