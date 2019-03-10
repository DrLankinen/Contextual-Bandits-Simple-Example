# Contextual Bandits Simple Example

This code represents the idea of **contextual bandits** (= associative search). The basic idea is that we have n machines which have k different actions. All machines have different reward probabilities for different actions. The idea is to learn to predict the right action when we know what state we are in. In this example, we get the state as the color of a slot machine. For example, when we have a green machine it might be better to pull lever 2 and when we have a yellow machine it might be better to pull lever 5. This means that we can't just say that one lever is better for all machines but we need to find the best lever for every machine. The environment I'm using in this example is **stationary** which means that the true value of an action is always the same. The method I'm using to approximate action values is called **sample-average**.

There is a class called SlotMachine which have an own number of actions and also color to make it easier to identify these machines. First, when we initialize the class we set standard_deviation to 0.01 for all action reward probabilities and mean randomly some number between 0 and 1. Function **pull** will give a reward using a normal distribution where standard deviation and mean are numbers we initialized earlier.

Then we have **choose_action** function. This chooses maximum action with the probability of **1-epsilon** and random action with the probability of **epsilon**.

We start by creating four machines which have 10 actions.

Then we map each machine to index to make it easier to get the action. We create two matrices which are **Q** and **N**. Shapes of these are (len(machine) X number of actions). This means that each row is for each machine and each column is for each action. **Q** is the value estimation and **N** is the number of times we have selected that action.

We define a number of steps we want our model to go through. Every step will get a random machine. First, it chooses an action when epsilon is 0.01. Then it takes the action and gets back a reward. These rewards are stored for plots. Finally, it will add one to that action and calculate a new reward estimation for that action.

In the end, there are plots. The first shows us how different machines gave different rewards during training. We can see that yellow finds fast the best action and for red it takes more time to find it. The second plot shows us how the average reward increases over time.
