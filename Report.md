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
Federated learning has gained significant interest within the research community by enabling machine learning model training on distributed devices without requiring local data sharing. Instead of relying on a centralized dataset to train a single model, federated learning involves training separate models on local datasets and combining them into a unified global model. Although each device operates with a limited dataset, the overall capacity of the global model compensates for this limitation. Federated learning also addresses privacy concerns, making it feasible to train models on sensitive data, like medical records, without transferring them to the cloud.

In our project, we propose implementing on-device training of machine learning models on a microcontroller using federated learning. To overcome the resource constraints on the microcontroller, we implement federated learning across multiple devices to aggregate overall training before the inference stage.

## Key Objectives
1. Literature Review of Resource-Constrained FL
2. Adaptation of FL techniques to leverage multiple MCUs in training
4. Achieve successful ML classification leveraging multiple devices in an FL configuration

## Literature Review
![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Literature_Survey.jpg)


## Technology Stack
1. Algorithms: Federated Learning (Approach adapted from reference [1])
2. Compiler: GNU Compiler Collection (GCC)
3. Architecture: Multiple MCU/CPU Federated Learning Edge Devices
4. VLSI: Arduino Nano 33 BLE (Cortex M4 Core)
![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Platform.jpg)

## Application Development

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Application_Development.jpg)

## Demo

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/AIHardwareFLDemo-ezgif.com-optimize.gif)

## Results
### Single Device

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Results_Sing.jpg)

### Multi-Device

![alt text](https://github.com/hplp/ai-hardware-project-6501_group2/blob/main/Results_Double.jpg)

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


