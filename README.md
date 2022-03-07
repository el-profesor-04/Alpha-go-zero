# Alpha-go-zero

The Alpha Go and Alpha go zero were developed by google deepmind for the game of go.

This Repo contains data and implementation of Alpha go zero for the game of chess.


Problem: The representation for the Policy for the Algorithm using a Deep Neural Network that outputs the best action (one-hot vector) and expected winner (+1 for player1 and -1 for player2).

Model Architecture: Since the Neural network had to have many layers (to represent an enormous number of states), a ResNet Architecture was used (19 ResNet Blocks). The ResNet model is based on the intuition of skip connections which solve the problem of Exploding/Vanishing gradients in Deep Networks. The network was branched two give 2 different outputs (action vector and expected winner). 

Framework: For building and training the Neural Network, TensorFlow Functional API was used. Along with Custom loss function and update using tf.GradientTape API.

Timeline: The project had 2 parts: a) Representation of the Game: To make the game rules so that randomized agents could play, took 5 days.
b) To build a Custom model, implement Tree Search Algorithm, took 1 week, before finally training on Google Cloud Platform for 3 days (intermittently).

Additional Remarks: The project had a gap in part b) for the following reasons:
The game of chess is different from that of Go (as in the original paper), it is possible that the random agents may never end the game. One solution was to clip the maximum possible moves in the game but that would result in a draw and there won't be any learning. 
Therefore, I decided to use expert-level game records to train the agents (in contrast to the original paper).

Outcome: After 18 hours of training using the Nvidia V100 GPU, the agent showed some improvements in the gameplay but was far from the human gameplay level. I suppose more computing power and weeks of training could result in an expert agent with a superhuman rating. 
