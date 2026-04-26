# MobileNetV2 and EfficientNet with Multiple Training Strategies (CIFAR-10)

---

## Overview

This project investigates how different data exposure strategies influence the performance of deep learning models.

Instead of altering only the architecture, this study focuses on how training data is presented during learning. The same dataset is used across all experiments, while the training strategy is varied.

Two architectures are evaluated:

- MobileNetV2  
- EfficientNet-B0  

The following strategies are explored:

1. Full Dataset Training  
2. Progressive Dataset Revelation  
3. Curriculum Learning (Easy → Hard)  

This enables a systematic analysis of convergence behavior, stability, and generalization.

---

## Models

### MobileNetV2

- Lightweight convolutional neural network  
- Uses depthwise separable convolutions  
- Optimized for efficiency and faster computation  

### EfficientNet-B0

- Scaled convolutional architecture  
- Uses compound scaling (depth, width, resolution)  
- Provides improved feature representation and accuracy  

---

## Dataset

- CIFAR-10 dataset  
- 50,000 training images  
- 10,000 test images  
- 10 classes  

All experiments use identical preprocessing to ensure a fair comparison.

---

## Training Strategies

---

### 1. Full Dataset Training

#### Description

The model is trained using the entire dataset from the beginning.

#### Behavior

- Fast convergence due to full data exposure  
- Stable training process  
- Limited control over learning progression  

#### Results

| Model         | Accuracy |
|--------------|----------|
| MobileNetV2  | 82.68%   |
| EfficientNet | 84.11%   |

#### Observations

- Both models achieve strong performance with stable convergence.  
- EfficientNet outperforms MobileNet due to better feature extraction.  
- Serves as a baseline for comparison with other strategies.  

---

### 2. Progressive Dataset Revelation

#### Description

The model is trained by gradually increasing the dataset size.

#### Stages

| Stage | Data Used |
|------|----------|
| 1    | 10%      |
| 2    | 25%      |
| 3    | 50%      |
| 4    | 75%      |
| 5    | 100%     |

Each stage is trained for equal epochs.

#### Behavior

- Begins with limited data exposure  
- Gradually refines learned representations  
- Improves training stability  

#### Results

| Model         | Accuracy |
|--------------|----------|
| MobileNetV2  | 80.65%   |
| EfficientNet | 83.30%   |

#### Observations

- Gradual improvement in accuracy across stages.  
- Reduced overfitting compared to full dataset training.  
- EfficientNet consistently achieves higher performance.  

---

### 3. Curriculum Learning (Easy → Hard)

#### Description

The model is trained using samples ordered by difficulty, from easiest to hardest.

#### Workflow

1. Perform initial warm-up training  
2. Compute per-sample loss  
3. Sort samples from easy to hard  
4. Train on easy subset followed by full dataset  

#### Behavior

- Learns simple patterns first  
- Gradually adapts to complex samples  
- Improves generalization  

#### Results

| Model         | Accuracy |
|--------------|----------|
| MobileNetV2  | 82.20%   |
| EfficientNet | 84.05%   |

#### Observations

- More structured and stable learning process.  
- Improved generalization compared to progressive training.  
- EfficientNet achieves the highest accuracy overall.  

---

## Comparative Analysis

| Strategy     | MobileNetV2 | EfficientNet-B0 |
|-------------|------------|-----------------|
| Full Dataset | 82.68%     | 84.11%          |
| Progressive  | 80.65%     | 83.30%          |
| Curriculum   | 82.20%     | 84.05%          |

---

## Key Insights

- Training strategy significantly impacts model performance.  
- Full dataset training provides strong baseline performance.  
- Progressive training improves stability but may slightly reduce accuracy.  
- Curriculum learning provides better generalization and structured learning.  
- EfficientNet consistently outperforms MobileNet across all strategies.  
- MobileNet remains competitive with lower computational cost.  

---

## Conclusion

This study demonstrates that:

Training strategy plays a critical role in deep learning performance, even when the architecture remains unchanged.

- Progressive learning enhances training stability  
- Curriculum learning improves generalization  
- EfficientNet achieves the best overall performance  

Structured data exposure leads to more effective and controlled learning.

---
