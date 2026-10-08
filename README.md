# 🧠 Deep Learning PR 1 — Breast Cancer Classification

## 📌 Project Overview

This project is part of **Deep Learning PR 1** and focuses on building and comparing different neural network models for **Breast Cancer Classification**.

The main goal is to understand how different neural network architectures, activation functions, data preprocessing techniques, and Early Stopping affect model performance.

---

## 🎯 Objective

The objective of this project is to:

- Understand and perform **data preprocessing** for neural networks.
- Apply **Data Scaling** using StandardScaler.
- Build a **Single-Layer Perceptron (SLP)** as a baseline model.
- Build a **Multi-Layer Perceptron (MLP)** with hidden layers.
- Compare different **activation functions**.
- Understand the effect of **Early Stopping**.
- Compare training and validation performance.
- Evaluate the models using accuracy and classification reports.

---

## 📊 Dataset

The project uses the **Breast Cancer Wisconsin (Diagnostic)** dataset available through Scikit-learn.

### Dataset Details

- 👥 Total Samples: **569**
- 🔢 Features: **30 numerical features**
- 🎯 Target Classes:
  - `0` → Malignant
  - `1` → Benign
- 🩺 Malignant Cases: **212**
- 🩺 Benign Cases: **357**

The dataset contains no missing values and consists of numerical features describing characteristics of breast cell nuclei.

---

## 🛠️ Technologies & Libraries

The project uses:

- 🐍 Python
- 🤖 TensorFlow / Keras
- 📊 Pandas
- 🔢 Scikit-learn
- 📈 Matplotlib
- 📉 Seaborn
- 📓 Jupyter Notebook

---

# 🔹 Task 1 — Data Loading, EDA & Preprocessing

## 📥 Dataset Loading

The Breast Cancer dataset is loaded using Scikit-learn.

The input features are stored in `X`, while the target values are stored in `y`.

The dataset shape, target class counts, and descriptive statistics are checked.

---

## 📊 Class Distribution

The target class distribution is visualized using a count plot.

The dataset contains:

- **357 Benign cases**
- **212 Malignant cases**

There is a mild class imbalance because the number of Benign cases is higher than the number of Malignant cases.

However, the imbalance is not severe for this dataset size, so special handling is not required.

---

## 🔗 Feature Correlation

A correlation heatmap is used to understand relationships between selected features.

Some features show high correlation with each other.

Highly correlated features are not considered a major problem for neural networks because neural networks can learn non-linear patterns using their weights and biases.

---

## ✂️ Train-Test Split

The dataset is divided into:

- 🏋️ Training data → **80%**
- 🧪 Testing data → **20%**

A fixed random state is used to make the split reproducible, and stratification is applied to maintain the class distribution.

---

## ⚖️ Data Scaling

StandardScaler is applied to the input features.

The scaler is:

- Fitted only on the training data.
- Used to transform the training data.
- Used to transform the test data using the same scaling information.

StandardScaler brings features to a similar scale by making their mean approximately **0** and standard deviation approximately **1**.

This prevents large-value features from dominating the model and helps the neural network train faster and more stably.

---

# 🔹 Task 2 — Single-Layer Perceptron (SLP)

## 🧠 SLP Model

A Single-Layer Perceptron is used as the **baseline model**.

### Architecture

**30 Input Features → 1 Output Neuron**

The output neuron uses the **Sigmoid activation function** because this is a binary classification problem.

---

## ⚙️ Model Training

The SLP is trained using:

- Optimizer → **Adam**
- Loss Function → **Binary Crossentropy**
- Metric → **Accuracy**
- Epochs → **50**
- Batch Size → **32**
- Validation Split → **10%**

---

## 📈 SLP Training Results

Training and validation loss decrease over the epochs, while accuracy increases.

The training and validation performance remain close, showing that the SLP is learning well with no major overfitting.

---

## 🧪 SLP Evaluation

The trained SLP is evaluated using the test dataset.

The evaluation includes:

- Test Accuracy
- Classification Report
- Model Predictions

The model predictions are converted into binary classes using a **0.5 probability threshold**.

---

# 🔹 Task 3 — Multi-Layer Perceptron (MLP) & Activation Functions

## 🧠 MLP Model

A Multi-Layer Perceptron is built with hidden layers to learn more complex relationships between features.

### Architecture

**30 Input Features → 64 ReLU → 32 ReLU → 1 Sigmoid**

Hidden layers allow the model to learn combinations of features instead of relying only on simple relationships.

For example, one feature alone may not be enough to classify a tumor, but a combination of multiple features can provide a stronger prediction.

---

## ⚙️ MLP Training

The MLP is trained using:

- Optimizer → **Adam**
- Loss Function → **Binary Crossentropy**
- Metric → **Accuracy**
- Epochs → **100**
- Batch Size → **32**
- Validation Split → **10%**

---

# 🔄 Activation Function Comparison

Three activation functions are compared in the hidden layers:

### 🔴 ReLU

**64 ReLU → 32 ReLU → 1 Sigmoid**

### 🟢 Tanh

**64 Tanh → 32 Tanh → 1 Sigmoid**

### 🔵 Sigmoid

**64 Sigmoid → 32 Sigmoid → 1 Sigmoid**

The output layer remains Sigmoid because the task is binary classification.

---

## 📊 Activation Function Results

ReLU, Tanh, and Sigmoid all achieve high training accuracy.

ReLU shows the most stable validation performance, while Tanh and Sigmoid show a larger training-validation gap.

Therefore, **ReLU performs better for this MLP** based on the observed validation performance.

---

## 🧪 MLP Evaluation

The ReLU-based MLP is evaluated on the test dataset.

The evaluation includes:

- Test Accuracy
- Classification Report
- Model Predictions

The MLP predictions are converted into binary classes using a **0.5 probability threshold**.

---

# 🔹 Task 4 — Early Stopping

## 🧠 Early Stopping Experiment

A fresh MLP is created to study the effect of Early Stopping.

### Architecture

**30 Input Features → 128 ReLU → 64 ReLU → 1 Sigmoid**

The model is first trained for **300 epochs without Early Stopping**.

This allows the training and validation loss curves to be observed over a longer training period.

---

## ⏹️ Early Stopping

Early Stopping is then applied using:

- Monitor → **Validation Loss**
- Patience → **15 epochs**
- Restore Best Weights → **Yes**

The purpose is to stop training when the validation loss stops improving.

The best-performing weights are restored after training stops.

---

## 📈 Early Stopping Visualization

Training and validation loss are plotted to show when Early Stopping occurs.

A vertical dashed line is used to indicate the epoch at which training stopped.

---

## 🔍 With vs Without Early Stopping

The training results are compared between:

### Without Early Stopping
The model is trained for the full 300 epochs.

### With Early Stopping
The model stops training when validation loss no longer improves for the specified patience period.

This comparison helps understand how Early Stopping can prevent unnecessary training and reduce the risk of overfitting.

---

# 📚 Concepts Covered

This project currently covers the following concepts:

- 📥 Data Loading
- 🔎 Exploratory Data Analysis
- 📊 Class Distribution
- 🔗 Feature Correlation
- ✂️ Train-Test Split
- ⚖️ StandardScaler
- 🧠 Single-Layer Perceptron
- 🧠 Multi-Layer Perceptron
- ⚡ ReLU Activation
- ⚡ Tanh Activation
- ⚡ Sigmoid Activation
- 📈 Training & Validation Curves
- ⏹️ Early Stopping
- 🧪 Model Evaluation
- 📋 Classification Report

---

# 📁 Project Structure

The project contains the following main notebook:

- 📓 `project1_deeplearning.ipynb`

The notebook contains the complete workflow from dataset loading and preprocessing to neural network training and evaluation.

---

# 🏁 Conclusion

This project demonstrates the complete basic workflow of a neural network classification problem.

The project starts with data preprocessing and scaling, then builds an SLP as a baseline model. A more powerful MLP is then created to learn complex relationships between the input features.

Different activation functions are compared, with **ReLU showing more stable validation performance** in the current experiments.

Finally, Early Stopping is introduced to control unnecessary training and study the relationship between training and validation performance.

Overall, the project provides practical understanding of how preprocessing, neural network architecture, activation functions, and training techniques affect a deep learning classification model.

---

## 👨‍💻 Project

**Deep Learning PR 1**

**Dataset:** Breast Cancer Wisconsin (Diagnostic)

**Framework:** TensorFlow / Keras

**Language:** Python

**Environment:** Jupyter Notebook

---
