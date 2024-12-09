[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/Buol6fpg)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=16987558)

# Group Federated Minds: Federated Learning for Edge AI

## Team member
- Anjali Agrawal: Algorithm Developer
- Aki Tanaka: Architecture Developer
- Charlie Hess: Software Developer

## Project Title
Federated Learning for Edge AI

## Project Description
We all are aware of traditional machine learning where data is collected from several edge devices and the model is trained on this aggregated data. However, this approach requires powerful servers and are not practical for tinyML applications where compute operations are increasingly moving from cloud to the network edge. Here, we want to explore about one such approach which is called Federated Learning. This is a decentralized form of machine learning where models are sent to individual devices where local models are trained with local datasets and then merged into a global model. This is useful particularly in resource constrained edge devices where neural networks are implemented in distributed manner.

Federated learning has gained significant interest within the research community by enabling machine learning model training on distributed devices without requiring local data sharing. Instead of relying on a centralized dataset to train a single model, federated learning involves training separate models on local datasets and combining them into a unified global model. Although each device operates with a limited dataset, the overall capacity of the global model compensates for this limitation. Federated learning also addresses privacy concerns, making it feasible to train models on sensitive data, like medical records, without transferring them to the cloud.

In our project, we propose implementing on-device training of machine learning models on a microcontroller using federated learning. To overcome the resource constraints on the microcontroller, we implement federated learning across multiple devices to aggregate overall training before the inference stage.

## Key Objectives
1. Literature Review of Resource-Constrained FL
2. Adaptation of FL techniques to leverage multiple MCUs in training
4. Achieve successful ML classification leveraging multiple devices in an FL configuration

## Literature Review
We performed literature survey with the goal of finding existing implementations that can help us guide towards decision of selecting application as well as hardware platform. This also helped us identify the key metrics in our application and existing tradeoffs. As can be seen from the plot below, the time to train increases as the RAM capacity per edge node decreases.

Based on literature survey results, we chose the application of keyword spotting to be implemented on Arduino Nano 33 BLE Sense board.
![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Literature_Survey.jpg)


## Technology Stack
1. Algorithms: Federated Learning (Approach adapted from reference [1])
2. Compiler: GNU Compiler Collection (GCC)
3. Architecture: Multiple MCU/CPU Federated Learning Edge Devices
4. VLSI: Arduino Nano 33 BLE (Cortex M4 Core)
![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Platform.jpg)

## Application Development
This section outlines the creation of a keyword spotting application designed to study model training on a microcontroller. The application allows users to select and train the model to recognize up to three distinct keywords. Once the model is trained, users can switch to an inference mode to test the keyword detection functionality. At present, the application indicates the detected keyword by illuminating the corresponding color on the Arduino board's RGB LED.

1. Hardware Setup
The application runs on an Arduino Nano 33 BLE Sense board, which includes many essential components. The board features a built-in microphone for recording keywords, as well as an integrated white LED and an RGB LED. The white LED indicates the application stage (e.g., IDLE, busy), while the RGB LED displays the output class of the keyword spotting model. For training the model with three keywords, three buttons are connected to the board’s digital inputs, each corresponding to one keyword. A fourth button is added for testing the model through inference.

2. Workflow
The application is activated either by flashing the program onto the Arduino board or restarting the board with the program pre-installed. When powered on, a new model is initialized, with its weights and biases set to random values. Users can then train the model by pressing one of three dedicated training buttons, each linked to a specific keyword. Pressing a button causes the RGB LED to light up in a color representing that button (red, green, or blue). After releasing the button, the Arduino's built-in microphone records one second of audio, during which the user should speak the desired keyword. The captured audio is processed into a feature vector, and the model is trained using this vector, with the button press determining the label for the keyword. A fourth button is available for testing the model. This button follows the same process as the training buttons but instead performs inference. Upon recognizing a keyword, the RGB LED lights up in the color corresponding to the detected word.

3. Neural Network Model and Training
The model used in our application is a feedforward neural network with a single hidden layer of 16 nodes. The model utilizes an online learning approach, allowing it to adapt dynamically during operation. As noted, the model is re-initialized with random parameters each time the application restarts. When a training button is pressed and released, the board captures a keyword spoken by the user and processes it to generate a feature vector in the form of Mel-Frequency Cepstral Coefficients (MFCCs). This feature vector is then input into the model for forward propagation, producing activation values for the three output nodes. Using these outputs and the expected target values—determined by the pressed button—the mean squared error is computed. Subsequently, the error magnitude (delta) for each neuron is calculated, enabling the backpropagation algorithm to update the model's weights and biases accordingly.

4. Software Implementation
This architecture features a central server and multiple worker nodes. The central server performs model averaging by combining the local models received from the worker nodes after a predefined number of training epochs. This process generates an updated global model, which is then distributed back to the worker nodes. Each worker node subsequently uses the updated global model to continue training its local model with the data available on its node. The server runs on a PC. It
communicates with the worker nodes over serial lines. It sends and receives model data from the worker nodes. 

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Application_Development.jpg)

## Demo

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/AIHardwareFLDemo-ezgif.com-optimize.gif)

## Results
In our project, we experimented two defferent cases; 
1. Federated learning in single device<br>
   Case1: Single word training<br>
   Case2: Two word training<br>
   Case3: Three word training
2. Federated learning in two devices. The host computer perform federated
   Case1: Single word training<br>
   Case2: Two word training<br>
   Case3: Three word training

### Single Device

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Results_Sing.jpg)


The three plots showed the results of the loss and the number of epoch in each case using the single device.<br>
As we demonstrated the operation in the demo, the case in single device with one-word training successfully got the loss wnought to be small after 10 times training. However, when we trained the multiple words in the same device, the loss were not properly saturated near zero. To improve these, we guess setting proper learning rate is important. The defualt learning rate in the reference model [1] is 0.3 and this value is high as they pointed out. This can lead to unstable training process.

### Multi-Device

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Results_Double.jpg)

We expanded our testing to the multi-device training where each device performs their own federated learning. After the local learning, the host comouter gathers the local models and merges the models by federated average learning. After the average learning, the host computer redistribute the update models into local machines.

Even using multiple devices, we could confirmed the successful operation with single word training. However, we still need more investigation for mupltiple keyword recoginition due to the parameter optimization for this application.

## Discussion and Future Work


In this work, we have achieved:​

- a Federated Learning proof of concept using low resource micronctrollers
- Keyword spotting in FL edge system with up to 3 keywords

Limitations include:

- Increase in number of keywords leads to increasing value of loss converged to (worse performance with more keywords)
- Increase in number of devices degrades convergence of loss function during training phase

Based on these limitations, future work may include:

- Refining the training process to improve performance with more keywords
- Improving the process of model aggregation from the various FL nodes to achieve improved performance with multiple devices

## References
[1] Marc Monfort Grau, Roger Pueyo Centelles, and Felix Freitag. 2021. On-Device Training of Machine Learning Models on Microcontrollers With a Look at Federated Learning. In Proceedings of the Conference on Information Technology for Social Good (GoodIT '21). Association for Computing Machinery, New York, NY, USA, 198–203. https://doi.org/10.1145/3462203.3475896<br>
[2] L. Wulfert, C. Wiede and A. Grabmaier, "TinyFL: On-Device Training, Communication and Aggregation on a Microcontroller For Federated Learning," 2023 21st IEEE Interregional NEWCAS Conference (NEWCAS), Edinburgh, United Kingdom, 2023, pp. 1-5, doi: 10.1109/NEWCAS57931.2023.10198040.<br>
[3] K. Kopparapu, E. Lin, J. G. Breslin and B. Sudharsan, "TinyFedTL: Federated Transfer Learning on Ubiquitous Tiny IoT Devices," 2022 IEEE International Conference on Pervasive Computing and Communications Workshops and other Affiliated Events (PerCom Workshops), Pisa, Italy, 2022, pp. 79-81, doi: 10.1109/PerComWorkshops53856.2022.9767250. <br>
[4] M. Ficco, A. Guerriero, E. Milite, F. Palmieri, R. Pietrantuono, S. Russo, Federated learning for IoT devices: Enhancing TinyML with on-board training, Information Fusion, Volume 104, 2024,102189, ISSN 1566-2535, https://doi.org/10.1016/j.inffus.2023.102189. <br>
