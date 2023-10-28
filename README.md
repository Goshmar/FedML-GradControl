## FedML-GradControl

The article titled ["Federated Learning with Unbiased Gradient Aggregation and Controllable Meta Updating"](https://arxiv.org/pdf/1910.08234.pdf) addresses the challenges and limitations of federated learning (FL), a decentralized machine learning approach that leverages smart edge devices for training models.

<strong>Last Update: October, 28th, 2023</strong>.	

 - _add: UGA, FedMeta reproducing_
 - _add: report 1 about testing UGA, FedMeta_
 - _add: comparison plots using UGA and FedMeta_
 - _add: folder's structure and release_

---

## Contents
 - **main/**: Contains 

 - **experiments/**: Contains the main code for reproducing the results and working on the project.

 - **reports/**: Contains supplementary documentation, including reports related to the project.

 - **results**/: Stores the results of experiments and simulations conducted during the research.

## Problem Statement:
The article focuses on two key issues in federated learning:

 - **Gradient Biases:** The multiple steps of local model updating on edge devices can lead to gradient biases, affecting the quality of the aggregated global model.

 - **Inconsistent Optimization Objectives:** Selecting a subset of clients for computation in each round may result in an inconsistency between the optimization objectives and the real target data distribution, particularly problematic in non-IID (non-identically distributed) FL settings.

<p align="center">
  <img src="/images/FedMeta_round.png" width="900" height="450">
</p>

_Importance: Federated learning is crucial for privacy preservation and reducing communication costs in distributed systems, making it a hot research topic. Addressing gradient biases and inconsistent optimization objectives is essential for improving the convergence and accuracy of federated models._

## Examples of Occurrence:
The problems discussed in the paper occur in scenarios where federated learning is employed, such as mobile devices, IoT devices, and distributed edge computing environments. The authors propose two main techniques to address the identified problems:

 - **Unbiased Gradient Aggregation (UGA):** This technique leverages a keep-trace gradient descent and gradient evaluation strategy to calculate gradients against the initial global model parameters, effectively reducing gradient biases.

<p align="center">
  <img src="/images/UGA_algo.png" width="650" height="350">
</p>

 - **Controllable Meta Updating (FedMeta):** This approach introduces an additional meta updating procedure using a small set of data samples (Dmeta) after model aggregation in each round. It aims to provide a clear and consistent optimization objective by optimizing for performance on Dmeta.

<p align="center">
  <img src="/images/FedMeta_algo.png" width="650" height="350">
</p>

The authors build their approach on the foundation of FedAvg, which is a fundamental FL algorithm. They extend FedAvg by introducing UGA and FedMeta to mitigate gradient biases and improve optimization objectives.

## Key Features of Proposed Methods:
UGA reduces gradient biases by calculating gradients against the initial global model parameters, rather than the locally updated ones.
FedMeta introduces a controllable meta updating step, optimizing models for a specific meta training set (Dmeta). Both UGA and FedMeta are model- and task-agnostic, making them versatile for various FL settings.

**Intuition for Effectiveness:** UGA reduces gradient biases by ensuring that gradients are computed against the same model parameters across all clients. FedMeta provides a consistent optimization objective by optimizing models for a specific dataset (Dmeta), improving convergence and model quality.

**Improvements Over Prior Literature:** The proposed methods, UGA and FedMeta, improve upon prior FL techniques by addressing gradient biases and offering a controllable meta updating process. These improvements are shown to enhance convergence speed and model accuracy, especially in non-IID FL scenarios.

On the practical side, the article demonstrates the problems of federated learning. To solve them, various options for using UGA and FedMeta are proposed, their effectiveness is demonstrated by experimenting with various network architectures in various FL settings. These methods are aimed at making federated learning more reliable and efficient, especially in scenarios where the distribution of data across peripherals is not the same.

---
