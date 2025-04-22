<p align="center"><strong> MohammadAmin M. Shabestari </strong></p>

---

**Date**: 04/17/2025  
[LinkedIn Profile](https://www.linkedin.com/in/mohammadamin-shabestari) | [GitHub Profile](https://github.com/Msh8303)  
✉️ **Email**: shabestari8303p@gmail.com  

---

# 🏗️ Concrete Compressive Strength Prediction  
**A Neural Network Approach with Hyperparameter Optimization**

---

## 📜 Abstract  
This project predicts the compressive strength of concrete using ingredient composition and curing age. We implement Multilayer Perceptrons (MLPs) with PyTorch, compare loss functions (MSE, MAE, Huber), optimizers (Adam, SGD, RMSProp), and architectural configurations. Key findings reveal that an **MLP with 32 hidden units, trained for 100 epochs using MSE loss and RMSProp optimizer**, achieves the best performance (Test MSE: 0.2893, MAE: 0.4369). We demonstrate the impact of hyperparameter tuning and regularization on model generalization.

---

## 📚 Table of Contents  
1. [Dataset Overview](#-dataset-overview)  
2. [Methodology](#-methodology)  
3. [Key Results](#-key-results)  
4. [Critical Analysis](#-critical-analysis)  
5. [Conclusion](#-conclusion)  

---

## 🏗️ Dataset Overview  
### **Source**: [Concrete Compressive Strength Dataset](https://archive.ics.uci.edu/dataset/165/concrete+compressive+strength)  
#### **Features**:  
- **Cement**, **Blast Furnace Slag**, **Fly Ash** (kg/m³)  
- **Water**, **Superplasticizer**, **Aggregates** (kg/m³)  
- **Age** (Days)  
- **Target**: `concrete_compressive_strength` (MPa)  

---

## 🧠 Methodology  
### 1. **Data Preprocessing**  
- **Normalization**: StandardScaler applied to features and target.  
- **Train-Validation-Test Split**: 70%-15%-15% stratified split.  

### 2. **Neural Network Architecture**  
- **MLP Designs**:  
  - *Simple Network*: 1 hidden layer (16–32 units), ReLU activation.  
  - *Output Layer*: 1 neuron for regression.  
- **Loss Functions**: MSE (prioritizes large errors), MAE (robust to outliers), Huber (balanced).  

### 3. **Training Protocol**  
- **Optimizers**: Adam (adaptive learning rate), SGD (vanilla), RMSProp (gradient magnitude adaptation).  
- **Early Stopping**: Patience=5 epochs, min Δ=0.01.  
- **Device Utilization**: CUDA GPU acceleration.  

### 4. **Evaluation Metrics**  
- **Mean Squared Error (MSE)**: Penalizes large prediction errors.  
- **Mean Absolute Error (MAE)**: Robust to outlier values.  

---

## 📊 Key Results  
### **Top Performing Models**  
| Configuration                | Hidden Units | Epochs | Optimizer | Loss  | Test MSE | Test MAE |  
|------------------------------|--------------|--------|-----------|-------|----------|----------|  
| Baseline MLP                 | 32           | 50     | Adam      | MSE   | 0.5904   | 0.6249   |  
| Extended Training            | 32           | 100    | Adam      | MSE   | 0.3762   | 0.5034   |  
| **Optimal Model**            | 32           | 100    | RMSProp   | MSE   | **0.2893** | **0.4369** |  

### **Hyperparameter Impact**  
1. **Hidden Layer Size**:  
   - 32 units reduced MSE by 15.6% compared to 16 units.  
2. **Training Duration**:  
   - 100 epochs improved MSE by 50.4% over 20 epochs.  
3. **Optimizer Choice**:  
   - RMSProp outperformed Adam (MSE ↓23.1%) and SGD (MSE ↓67.6%).  

---

## 🔍 Critical Analysis  
### ❌ **Why MAE Underperformed MSE**  
| Aspect               | MSE Behavior                  | MAE Behavior                  |  
|----------------------|-------------------------------|-------------------------------|  
| **Gradient Dynamics**| Large gradients for big errors| Constant gradients            |  
| **Outlier Handling** | Sensitive to outliers         | Robust to outliers            |  
| **Convergence**      | Faster convergence            | Slower convergence            |  

#### **Explanation**:  
- MSE’s quadratic penalty better captured the nonlinear relationship between concrete ingredients and strength.  
- MAE’s linear penalty struggled with error magnitude differentiation, leading to slower convergence.  

### ✅ **Why RMSProp Outperformed Adam**  
- **Adaptive Learning Rates**: RMSProp’s exponential moving average of squared gradients stabilized updates for small-batch training.  
- **Momentum Lack**: Adam’s momentum term occasionally overshot optimal weights in this low-dimensional regression task.  

---

## 🏆 Conclusion  
- **Best Model**: **MLP (32 hidden units, 100 epochs, MSE loss, RMSProp)** achieves state-of-the-art performance with MSE=0.2893.  
- **Practical Implications**:    
   - MSE is preferred for quality control where large strength deviations are critical.  
 


--- 
