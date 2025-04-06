---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---
# Breaking Neural Network Scaling Laws with Modularity

Neural networks (NNs) have become ubiquitous in machine learning applications due to their incredible flexibility and performance. However, understanding how and why neural networks generalize—especially on complex, high-dimensional tasks—remains an open challenge. Our recent paper provides insights into NN generalization using a novel theoretical model validated by extensive empirical experiments.

## Theoretical Setup: Capturing Generalization with a Simple Model

To begin our investigation, we constructed a theoretical model of NN generalization. In our setup, we consider regression tasks where outputs depend linearly on a large set of random features drawn from a Gaussian distribution. 

We study how a neural network approximates this function using a limited number of parameters (p), focusing on how accurately it generalizes given training data (n samples). Our theoretical analysis reveals a key relationship:

- Generalization error depends crucially on the dimensionality (m), the number of model parameters (p), and the amount of training data (n).
- The complexity of learning scales *exponentially* with task dimensionality.

## Empirical Validation: Matching Theory and Practice

We empirically validated our theoretical model using a modular sine-wave regression task:

<p align="center">
    <img src="imgs/sine_wave_diagram_edited.png" alt="Sine Wave Regression Task" width="600"> 
</p>

*Figure 1: Illustration of a single module in our sine wave regression task, where each target function is composed of multiple sine wave components.*

By varying parameters such as dimensionality (m), number of parameters (p), and number of samples (n), we observed clear patterns of generalization error. Remarkably, our theoretical model accurately predicted key trends such as the invariance of loss with the number of modules, sublinear increase in loss with dimensionality, and double-descent behavior of loss with model parameters and data samples:

<p align="center">
    <img src="imgs/loss_trends.png" alt="Generalization Error Trends" width="600"> 
</p>

*Figure 2: Empirical and theoretical trends of training and test loss, demonstrating strong alignment between theory and practice.*

## Insights into High-dimensional Generalization

Our model also explains why high-dimensional tasks demand exponentially more data for effective generalization. This aligns with previous observations in deep learning literature, highlighting the severe limitations neural networks face when scaling to complex, high-dimensional scenarios:

<p align="center">
    <img src="imgs/theoretical_m_vs_n.png" alt="Sample Complexity vs Dimensionality" width="600"> 
</p>

*Figure 3: The exponential relationship between required samples and input dimensionality, illustrating the challenge of scaling to high-dimensional tasks.*

## Modular Neural Networks: A Path to Efficient Generalization

Motivated by these insights, we proposed a modular neural network architecture designed explicitly for modular tasks. By explicitly constructing modular architectures and training them with a specialized initialization method (based on kernel optimization), we achieved significantly better performance:

<p align="center">
    <img src="imgs/tsne.png" alt="Module Embeddings with t-SNE" width="600"> 
</p>

*Figure 4: t-SNE embeddings show that our modular initialization closely aligns learned modules (right) with the underlying true modules, unlike traditional random initializations (left and center).*

We validated our modular approach on more complex tasks, such as Compositional CIFAR-10, achieving superior accuracy and robustness compared to traditional architectures:

<p align="center">
    <img src="imgs/compositional_cifar.png" alt="Compositional CIFAR-10 Task" width="600"> 
</p>

*Figure 5: An example input for the Compositional CIFAR-10 task, demonstrating a high-dimensional modular classification problem.*

Our modular approach demonstrated robustness even under combinatorial and noisy conditions:

| Method               | Combinatorial OOD Accuracy | Accuracy under Noise |
|----------------------|----------------------------|----------------------|
| Baseline Monolithic  | 42.56%                  | 39.47%              |
| Baseline Modular     | 45.26%                  | 43.07%              |
| **Our Method**       | **49.90%**              | **46.95%**           |

*Table 1: Robustness of our modular neural networks to combinatorial and noisy perturbations.*

## Conclusions and Future Directions

Our work demonstrates that understanding the modular structure inherent in tasks can significantly enhance neural network generalization. By bridging theory with practical architectural innovations, we've shown a promising path forward for tackling high-dimensional machine learning problems efficiently.

We believe that future research should further explore modular architectures, not only as a theoretical construct but also as a practical method for solving real-world complex tasks.


**Citation:**
```
@inproceedings{boopathy2025breaking,
    title={Breaking Neural Network Scaling Laws with Modularity},
    author={Akhilan Boopathy, Sunshine Jiang, William Yue, Jaedong Hwang, Abhiram Iyer, Ila Fiete},
    booktitle={International Conference on Learning Representations (ICLR)},
    year={2025}
}
```

