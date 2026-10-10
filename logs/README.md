```markdown
# MNIST Digit Classification - The Impact of Feature Scaling

This repository demonstrates building, training, and evaluating simple Artificial Neural Networks (ANNs) on the MNIST handwritten digit dataset using TensorFlow and Keras.

Specifically, it highlights a crucial machine learning concept: **the dramatic impact of feature scaling (normalization) on neural network convergence and accuracy**.

## 🚀 Project Overview

- **Dataset:** MNIST (60,000 training images, 10,000 testing images of 28x28 grayscale digits)
- **Frameworks:** TensorFlow, Keras, NumPy, Matplotlib, Seaborn
- **Key Comparison:** Training a neural network using raw pixel values ($[0, 255]$) vs. scaled pixel values ($[0, 1]$).

## 📊 Key Findings

| Experiment | Data Scaling | Epochs | Training Loss | Training Accuracy | Test Accuracy |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **1. Single Layer** | ❌ No | 5 | ~5.48 | ~43.2% | ~42.7% |
| **2. Single Layer** |  Yes | 5 | **~0.26** | **~92.5%** | **~92.4%** |
| **3. Deep Network (3 Layers)** |  Yes | 5 | **~0.05** | **~98.4%** | **~97.5%** |
| **4. Deep Network (4 Layers)** |  Yes | 8 | **~0.09** | **~97.6%** | **~97.6%** |

### Why Scaling Matters
When input features have high ranges (like $0$ to $255$), the gradients during backpropagation can become extremely large or volatile, preventing the optimizer (Adam) from finding the global minimum efficiently. Scaling the dataset to a range of $[0, 1]$ ensures smooth gradient descent, faster training convergence, and significantly higher classification accuracy.

## 📈 Visualizations
Inside the notebook, we generate confusion matrices to analyze which digits the model misclassified the most (e.g., distinguishing between $2$ and $8$, or $4$ and $9$).

```python
# Scaled input evaluation
model.evaluate(X_test_flattened, y_test)
```