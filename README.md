# Contextual Bandits Simple Example

This code represents the idea of contextual bandits (= associative search). The basic idea is that we have n machines which have k different actions. All machines have different reward probabilities for different actions. The idea is to learn to predict the right action when we know what state we are in. In this example we get state as a color of slot machine. For example when we have green machine it might be better to pull lever 2 and when we have yellow machine it might be better to pull lever 5. This mean that we can't just say that one leaver is better for are machines but we need to find the best lever for every machine. Environment I'm using this example is stationary which mean that some action is better than others.

There is a class called SlotMachine which have own number of actions and also color to make it easier to identify these machines. First when we initialize the class we set standard_deviation to 1 for all action reward probabilities and mean randomly some number between 0 and 1. Q is our estimation of reward we will get when we make action a and N is how many times we have tried that action. Q and N are machine specific and these could have been stored out side of the machine but for simplicity these are attached to some machine. Function pull will give us reward using normal distribution where standard deviation and mean is numbers we initialized earlier.

Then we have choose_action function. This choose maximum action with probability of 1-epsilon and random action with probability of epsilon.

We start by creating four machines which have 10 actions except red have 4.

We define number of steps we want our model to go through. Every step it will get a random machine. First it use chooses an action when epsilon is 0.01. Then it take action and get back reward. These rewards are stored for plots. Finally it will add one to that action and calulate a new reward estimation for that action.

In the end there is plots. First show us how different machines gave different rewards through loops. We can see that red finds right away the highest action because there was only 4 different actions to choose from. Others start by taking worst action before finding the best. Second plot show us how average reward increases which also tell us that we have found better actions than beginning.
