# Continual Learning on MNIST Dataset 


This repository demonstrates the implementation of continual learning techniques on the MNIST dataset. The project is divided into several stages, starting with a simple Naive Bayes classifier and advancing through more sophisticated methods like **EWC Regularization**, **Replay**, and **Hybrid** approaches. The results show that the Naive Bayes classifier performs poorly, leading to significant forgetting of previous classes, while more advanced techniques like EWC, Replay, and Hybrid provide significant improvements in retaining learned knowledge.

This project leverages the **Avalanche** library, a comprehensive framework for continual learning, which simplifies the implementation of these techniques and provides utilities for evaluating performance across sequential tasks.

- [Techniques Implemented](#techniques-implemented)
  - [Naive Bayes](#naive-bayes)
  - [EWC Regularization](#ewc-regularization)
  - [Replay](#replay)
  - [Hybrid Approach](#hybrid-approach)
  - [Avalanche Library](#avalanche-library)

## Project Overview

The goal of this project is to explore continual learning techniques in a classification task using the MNIST dataset, which contains handwritten digits. Continual learning aims to prevent catastrophic forgetting when models are trained on sequential data, ensuring that previously learned tasks are retained while learning new ones. The project implements the following techniques:

1. **Naive Bayes** - A baseline model to compare the performance of more complex continual learning methods. However, it performs very poorly and suffers from significant forgetting of previously learned classes, often dropping its top accuracy to 0 for older classes.
2. **EWC Regularization** - Elastic Weight Consolidation, a technique to regularize the learning process to prevent catastrophic forgetting.
3. **Replay** - The method of replaying past data while learning new tasks to maintain memory of old tasks.
4. **Hybrid Approach** - A combination of EWC and Replay methods to enhance performance.

## Techniques Implemented

### Naive Bayes
The simplest model in this project, the Naive Bayes classifier is implemented as a baseline for comparing subsequent techniques. However, Naive Bayes performs very poorly in the continual learning setup. It suffers from severe catastrophic forgetting when trained sequentially on different subsets of the MNIST dataset. As new tasks are learned, the accuracy on older classes often drops to 0, and the model is unable to retain any useful information from previous tasks. This makes it unsuitable for continual learning, where memory retention is key.

### EWC Regularization
Elastic Weight Consolidation (EWC) is a technique designed to prevent catastrophic forgetting. It works by adding a regularization term to the loss function that penalizes large changes in important model parameters, which were learned on previous tasks. In this project, EWC significantly improves performance by retaining important model parameters, leading to a more stable performance across tasks and minimizing the forgetting of older classes.

### Replay
In the replay method, the model stores a subset of data from previous tasks and reuses it while training on new tasks. This helps the model retain knowledge from previous tasks, preventing forgetting of older classes while learning new ones. The replay method shows a notable improvement over Naive Bayes by preserving past knowledge, resulting in better overall accuracy.

### Hybrid Approach
The Hybrid approach combines the EWC regularization with the replay method. This method leverages both the advantages of preserving important model parameters (via EWC) and retaining data from previous tasks (via Replay). The Hybrid approach shows the best results in this project, offering enhanced performance in terms of both retaining knowledge from previous tasks and improving accuracy when learning new tasks. It effectively addresses catastrophic forgetting and outperforms Naive Bayes and other individual methods.

### Avalanche Library
For implementing the continual learning techniques, this project uses the **Avalanche** library. Avalanche is a popular framework for continual learning that provides utilities to manage tasks, track performance over time, and implement various continual learning strategies like **Replay**, **EWC**, and **Hybrid**. It simplifies the creation of experiments, handling of data streams, and evaluation, making it easier to focus on experimenting with different continual learning methods.

By using Avalanche, this project benefits from built-in tools to:
- Manage sequential tasks and datasets.
- Evaluate performance with appropriate metrics across different tasks.
- Implement advanced continual learning strategies with minimal boilerplate code.

