# Setup the Requirements and Run the First Iteration

## Set up your hardware (if applicable)
Arduino nano 33 BLE x3 for Federated Learning
![IMG_3871](https://github.com/user-attachments/assets/e6b79a45-91d3-497f-99d3-47745fa2a288)

## Identify (or train) your model 
The model used in our application is a feedforward neural network with a single hidden layer of 16 nodes. The input layer has 650 nodes, the same number as the size of the feature vector obtained from the MFCCs algorithm (13*50). The output layer only has 3 nodes, each one representing a keyword. This architecture gives a sum of 10448 weights and 19 biases.

## Program your hardware
The federated learning server is implemented in Python that runs on a PC. It communicates with the worker nodes over serial lines. It sends and receives model data from the worker nodes that are implemented on arduino nano BLE 33.

## Run the first iterations to test the computation module in your system.
After the program in arduino nano BLE 33, we have tried to run the first iteration. We could confirm the hardware is properly setup until the voice recognition. We will try speaking the voice to the microphone embedded with arduino so that the program can train the model on the edge. 
![Screenshot 2024-11-26 103836](https://github.com/user-attachments/assets/6c069bf4-f8f3-4c7f-b42d-5ad64f16ebd1)


## Respond to the feedback in the repo.
