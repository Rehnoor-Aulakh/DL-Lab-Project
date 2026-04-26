# CIFAR-10 Image Classification using CNN

This project implements a **Deep Convolutional Neural Network (CNN)** for image classification on the CIFAR-10 dataset using TensorFlow/Keras.

## 📌 Overview
The CIFAR-10 dataset consists of **60,000 color images (32x32)** across 10 classes:
- Airplane, Automobile, Bird, Cat, Deer  
- Dog, Frog, Horse, Ship, Truck  

The model is trained to classify images into these categories with high accuracy.

---

## 🧠 Model Architecture
The CNN consists of:
- 3 Convolutional Blocks:
  - Conv2D → Batch Normalization → MaxPooling
- Fully Connected Layers:
  - Dense (256) + Dropout (0.5)
  - Dense (128) + Dropout (0.3)
- Output Layer:
  - Dense (10) with Softmax activation

---

## ⚙️ Training Details
- **Optimizer:** Adam  
- **Loss Function:** Sparse Categorical Crossentropy  
- **Batch Size:** 64  
- **Epochs:** 25  
- **Activation:** ReLU (hidden), Softmax (output)  

### Data Preprocessing
- Normalization (pixel values scaled to [0,1])
- Data Augmentation:
  - Rotation (±15°)
  - Horizontal Flip
  - Zoom & Shear
  - Width/Height Shift

---

## 🔬 Training Strategies Compared
Three different training approaches were evaluated:

1. **Standard Training**
   - Full dataset used for all epochs  

2. **Progressive Dataset Revelation**
   - Data introduced gradually (10% → 100%)

3. **Curriculum Learning**
   - Training from easiest to hardest samples  

---

## 📊 Results

| Strategy                     | Test Accuracy | Test Loss |
|----------------------------|--------------|-----------|
| Standard Training          | **75.88%**   | **0.6819** |
| Progressive Revelation     | 74.00%       | 0.7597    |
| Curriculum Learning        | 71.38%       | 0.8304    |

---

## 📈 Key Insights
- Standard training achieved the best performance.
- Progressive learning improved gradually but had limited full-data training time.
- Curriculum learning underperformed due to noisy difficulty estimation and reduced data diversity early in training.

---

## 🚀 Conclusion
The **standard full-data training approach** provided the best results, achieving the highest accuracy and lowest loss. Alternative strategies like progressive and curriculum learning may improve with better tuning and data sampling methods.

---

## 🛠️ Technologies Used
- Python
- TensorFlow / Keras
- NumPy
- Matplotlib

---

## 📂 Project Structure
