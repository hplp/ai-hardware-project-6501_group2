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

In our project, we propose implementing on-device training of machine learning models on a microcontroller using federated learning. To overcome the resource constraints on the microcontroller, we plan to survey algorithms and architectures that require fewer resources than conventional machine learning implementation approaches.

## Key Objectives
1. Literature Review of Resource-Constrained FL
2. Adaptation of FL techniques to leverage multiple MCUs in training
3. Observe sources of greatest resource usage (SRAM, Flash, Compute)
4. Optimize technique to leverage the fewest possible resources

## Technology Stack
1. Algorithms: Federated Learning (Approach adapted from reference papers)
2. Compiler: GNU Compiler Collection (GCC)
3. Architecture: Multiple MCU/CPU Federated Learning Edge Devices
4. VLSI: Arduino Nano 33/STM32 Microcontrollers (Choice pending availability)

## Expected Outcomes
Implementation demo of federated learning for edge AI to showcase working prototype for inference application (TBD), and Extrapolate findings for consideration of adopting techniques to more limited MCUs and beyond.

## Timeline
(Done): Literature Review of Resource-Constrained FL
11/20/24: Finalize target application, and neural network model, and prepare for hardware implementation.
11/27/24: Iterate on implementations, and focus on getting the demo for targeted application working.

## Report
For More detailed report, see Report.md

## Project Files
The project files are under the milestone1 section, under the name of TinyML-FederatedLearning-main (2).zip


