# Neural Architecture Search using Regularized Evolution

## Instructions

Download the API and save it in the ```API/``` directory: [API](https://drive.google.com/file/d/16Y0UwGisiouVRxW-W5hEtbxmcHw_0hF_/view)


## Introduction to Neural Architecture Search

***Neural Architecture Search (NAS)*** is the process of automating the design of neural network architectures to optimize their performance for a given task. Instead of relying on manual trial-and-error by human experts, NAS leverages algorithms to explore a vast space of potential architectures, identifying those that achieve the best balance between accuracy, efficiency, and resource usage. This approach has become increasingly important as deep learning models grow in complexity and are applied to a wide range of applications, from image recognition to natural language processing.

## Problem with NAS

The first basic strategy in neural architecture search is to randomly select and train architectures from the search space, then compare their performance. However, the challenge lies in the fact that these architecture spaces can be immense. Training every possible architecture to convergence becomes computationally impractical. Therefore, more efficient strategies must be employed. One such approach involves defining a ***search strategy*** that navigates the space effectively, aiming to identify the optimal architecture without the need to exhaustively explore the entire space. The second approach leverages metrics to compare architectures without requiring full training. For instance, ***training-free metrics*** enable the evaluation of architectures based on their potential performance, allowing comparisons without the computational cost of training each model.

## NAS-Bench 201

**NAS-Bench-201** is a predefined search space designed to enable fair and consistent comparisons among different NAS methods. The search space consists of 15,625 convolutional neural network architectures for image classification, with each model pre-trained on CIFAR-10, CIFAR-100, and ImageNet datasets. 

Researchers can query the performance of any architecture directly using its string-based representation, such as:  
`|skip_connect~0|+|nor_conv_3x3~0|skip_connect~1|+|nor_conv_3x3~0|avg_pool_3x3~1|skip_connect~2|`.  

In this search space, architectures are represented as directed acyclic graphs (DAGs), where nodes correspond to intermediate states, and edges denote operations applied between nodes.

For more information, refer to the [NAS-Bench-201 paper](https://openreview.net/forum?id=HJxyZkBKDr) and the [official API](https://github.com/D-X-Y/NAS-Bench-201).

## Work

In this work, we employ the search strategy [Regularized Evolution](https://arxiv.org/abs/1802.01548) to efficiently traverse the search space only for CIFAR10. Regularized Evolution is designed to balance exploration and exploitation, making it well-suited for navigating large and complex search spaces. 

We will compare this approach with Random Search, which selects architectures randomly from the search space without considering any optimization strategy.

Results can be observed in the notebool ```nas.ipynb```