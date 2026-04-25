# VGG-style CNN with Multiple Training Strategies (CIFAR-10)

---

## 📌 Overview

This project focuses on understanding how **different data exposure strategies** affect the performance of a **VGG-style Convolutional Neural Network (CNN)**.

Instead of changing the model architecture, we keep the **same VGG network** and vary **how data is fed during training**.

The three strategies explored are:

1. Full Dataset Training
2. Progressive Dataset Revelation
3. Curriculum Learning (Easy → Hard)

This allows us to isolate and study the **impact of training strategy alone**.

---

## 🧠 VGG-style CNN Architecture

The model used in all experiments is a **VGG-style CNN**, known for its simplicity and effectiveness in image classification tasks.

### 🔧 Architecture Details

* Input: 32 × 32 RGB images
* 3 Convolutional Blocks:

  * Block 1: 64 filters
  * Block 2: 128 filters
  * Block 3: 256 filters
* Each block contains:

  * Conv → BatchNorm → Conv → BatchNorm → MaxPooling
* Fully Connected Layer:

  * Dense (512) → Dropout
* Output Layer:

  * 10 classes (Softmax)

### 🎯 Why VGG?

* Simple and uniform design
* Strong feature extraction capability
* Ideal baseline for comparative experiments

---

## 📊 Dataset

* CIFAR-10 dataset
* 50,000 training images
* 10,000 test images
* 10 classes

All three strategies use the **same dataset and preprocessing**, ensuring fair comparison.

---

## ⚙️ Training Strategies

---

### 🔵 1. Full Dataset Training

#### 📌 Description

The model is trained using the **entire dataset from the beginning**.

#### ⚙️ Behavior

* Learns quickly due to full data exposure
* Stable training process
* May start overfitting early

#### 📈 Observations

* Smooth increase in accuracy
* Consistent decrease in loss
* Strong final performance (~75–80%)

---

### 🟡 2. Progressive Dataset Revelation

#### 📌 Description

The model is trained by **gradually increasing the dataset size**.

#### 📊 Stages

| Stage   | Data Used |
| ------- | --------- |
| Stage 1 | 10%       |
| Stage 2 | 25%       |
| Stage 3 | 50%       |
| Stage 4 | 75%       |
| Stage 5 | 100%      |

Each stage is trained for equal epochs.

#### ⚙️ Behavior

* Starts with limited data
* Gradually refines learned features
* Learning becomes more stable over time

#### 📈 Observations

* Gradual accuracy improvement
* Reduced overfitting compared to full training
* Smoother convergence

---

### 🔴 3. Curriculum Learning (Easy → Hard)

#### 📌 Description

The model is trained using samples ordered by **difficulty**, from easiest to hardest.

#### ⚙️ Workflow

1. Train a scorer model
2. Compute per-sample loss (difficulty)
3. Sort data from easy → hard
4. Train progressively with increasing difficulty

#### ⚙️ Behavior

* Learns simple patterns first
* Struggles initially on validation data
* Improves as harder samples are introduced

#### 📈 Observations

* High training accuracy early
* High validation loss at the beginning
* Strong generalization in later stages

---

## 📊 Comparative Analysis

| Strategy     | Convergence Speed | Stability | Generalization |
| ------------ | ----------------- | --------- | -------------- |
| Full Dataset | Fast              | Moderate  | Good           |
| Progressive  | Moderate          | High      | Very Good      |
| Curriculum   | Slow (initial)    | Adaptive  | Strong (later) |

---

## 🧠 Key Insights

* The **same VGG model behaves differently** depending on data exposure
* Full dataset training is efficient but less controlled
* Progressive training improves stability and learning flow
* Curriculum learning enhances generalization by structured learning

---

## 🎯 Conclusion

This study shows that:

> Training strategy plays a crucial role in deep learning performance, even when the model architecture remains unchanged.

Using a VGG-style CNN:

* Progressive and curriculum strategies provide **better learning control**
* Curriculum learning mimics human learning behavior
* Structured data exposure can improve generalization

---

## 🚀 Future Improvements

* Apply strategies to deeper architectures (ResNet, EfficientNet)
* Use adaptive curriculum instead of fixed stages
* Combine progressive and curriculum learning
* Experiment with larger datasets

---
