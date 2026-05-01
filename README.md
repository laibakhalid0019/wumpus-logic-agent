# perceptron-from-scratch
# 🧠 Single-Layer Perceptron from Scratch

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![NumPy](https://img.shields.io/badge/NumPy-only-green?style=flat-square&logo=numpy)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

A clean, minimal implementation of a **single-layer Perceptron** built entirely from scratch using only NumPy — no sklearn, no TensorFlow, no shortcuts.

---

## 📌 Overview

This project implements the classical **Perceptron Learning Algorithm** as originally proposed by Frank Rosenblatt (1958). The model learns a linear decision boundary by iteratively adjusting weights based on prediction errors.

The implementation includes:
- Weight initialization
- Step activation function
- Training loop with Perceptron update rule
- Prediction function
- Evaluation on a dummy dataset (AND gate)

---

## 📁 Project Structure

```
perceptron-from-scratch/
│
├── perceptron.py        # Core implementation
├── README.md            # Project documentation
└── requirements.txt     # Dependencies (numpy only)
```

---

## ⚙️ How It Works

### Algorithm

The Perceptron update rule is:

```
w ← w + η · (y - ŷ) · x
b ← b + η · (y - ŷ)
```

Where:
- `w` = weight vector
- `η` = learning rate
- `y` = true label
- `ŷ` = predicted label
- `x` = input feature vector

### Activation Function

A **step function** is used:

```
f(z) = 1  if z ≥ 0
f(z) = 0  otherwise
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install numpy
```

### Run

```bash
python perceptron.py
```

### Expected Output

```
=== Single-Layer Perceptron Training (AND Gate) ===

Epoch 01 | Errors: 2 | Accuracy: 50.0%
Epoch 02 | Errors: 1 | Accuracy: 75.0%
Epoch 03 | Errors: 0 | Accuracy: 100.0%
...
Epoch 20 | Errors: 0 | Accuracy: 100.0%

Learned Weights: [0.1 0.1] | Bias: -0.10

=== Evaluation ===
Final Test Accuracy: 100.0%
  Sample 1: Input=[0 0] | True=0 | Pred=0 | ✓
  Sample 2: Input=[0 1] | True=0 | Pred=0 | ✓
  Sample 3: Input=[1 0] | True=0 | Pred=0 | ✓
  Sample 4: Input=[1 1] | True=1 | Pred=1 | ✓
```

---

## 🧪 Dataset

The model is trained on the classic **AND gate** truth table — a linearly separable binary classification problem:

| Input X1 | Input X2 | Output (AND) |
|----------|----------|--------------|
| 0        | 0        | 0            |
| 0        | 1        | 0            |
| 1        | 0        | 0            |
| 1        | 1        | 1            |

> ⚠️ Note: The Perceptron cannot solve non-linearly separable problems like XOR. For those, a multi-layer network is required.

---

## 📊 Hyperparameters

| Parameter     | Default | Description                        |
|---------------|---------|------------------------------------|
| learning_rate | 0.1     | Step size for weight updates       |
| epochs        | 20      | Number of full training passes     |

These can be adjusted directly when calling `train_perceptron()`.

---

## 🧩 Key Functions

| Function              | Description                                      |
|-----------------------|--------------------------------------------------|
| `initialize_weights`  | Returns zero-initialized weight vector and bias  |
| `step_activation`     | Binary threshold activation function             |
| `predict`             | Runs forward pass on input array                 |
| `train_perceptron`    | Full training loop with weight updates           |
| `evaluate`            | Prints per-sample predictions and accuracy       |

---

## 📚 Concepts Demonstrated

- **Supervised Learning** — learning from labeled examples
- **Linear Classification** — the Perceptron finds a hyperplane separator
- **Online Learning** — weights are updated after every single sample
- **Convergence** — guaranteed to converge if the data is linearly separable (Perceptron Convergence Theorem)

---

## 🛠️ Extending This Project

You can extend this implementation to:
- Try different datasets (OR gate, custom binary data)
- Plot the decision boundary using matplotlib
- Implement a multi-layer Perceptron (MLP) for non-linear problems
- Add sigmoid activation for probabilistic output

---

## 📄 License

This project is licensed under the MIT License.

---

## 👤 Author

Built as part of **AI 2002 – Artificial Intelligence (Spring 2026)**  
National University of Computer & Emerging Sciences — Chiniot-Faisalabad Campus
