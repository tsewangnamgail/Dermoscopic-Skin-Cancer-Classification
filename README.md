# 🧠 Dermoscopic Skin Cancer Classification
### Transfer Learning & Fine-Tuning using EfficientNetB2

---

## 📌 Overview
This project presents a deep learning-based system for binary skin cancer classification using dermoscopic images. The model leverages **EfficientNetB2** with transfer learning and fine-tuning to classify images into:

* 🔴 **Cancer**
* 🟢 **Non-Cancer**

The system is designed to demonstrate the practical application of deep learning techniques in medical image analysis, including handling class imbalance and staged fine-tuning.

---

## 🎯 Objective
To build an accurate and generalizable skin cancer detection model using:
* **Transfer learning** (Pre-trained on ImageNet)
* **Data augmentation** to improve robustness
* **Class weighting** to address label distribution
* **Layer-wise fine-tuning** for feature adaptation

---

## 📂 Dataset
* **Total Images:** 2239
* **Original Classes:** 9 skin lesion categories
* **Final Task:** Binary Classification (Cancer vs. Non-Cancer)

### Binary Grouping Logic:
| Category | Included Lesion Types |
| :--- | :--- |
| **Cancer (1)** | Melanoma, Basal Cell Carcinoma, Squamous Cell Carcinoma, Actinic Keratosis |
| **Non-Cancer (0)** | Nevus, Dermatofibroma, Pigmented Benign Keratosis, Seborrheic Keratosis, Vascular Lesion |

---

## 🏗 Model Architecture
* **Backbone:** EfficientNetB2 (ImageNet Pre-trained)
* **Global Average Pooling**
* **Batch Normalization**
* **Dense Layer:** 256 units, ReLU activation
* **Dropout:** 0.5 (for regularization)
* **Final Output:** 1 Neuron (Sigmoid Activation)

---

## 🔄 Training Strategy

1.  **Warmup Phase:**
    * Base model frozen.
    * Only the custom classifier head is trained.
    * **Learning Rate:** $1 \times 10^{-3}$
2.  **Fine-Tuning Phase:**
    * Last 30 layers unfrozen.
    * **Learning Rate:** $1 \times 10^{-5}$
    * Focuses on adapting high-level features to medical nuances.

---

## 📊 Performance
* **Validation Accuracy:** ~67%
* **Test Accuracy:** ~63%

### Test Classification Report:
| Class | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **Non-Cancer** | 0.56 | 0.83 | 0.67 |
| **Cancer** | 0.76 | 0.45 | 0.57 |

> [!IMPORTANT]  
> **Limitations:** Small dataset size (2239 images), visual similarity between benign and malignant lesions, and limited pre-malignant samples. This model is for **academic demonstration** and is not intended for clinical diagnostic use.

---

## 🛠 Tech Stack
* **Language:** Python
* **Framework:** TensorFlow / Keras
* **Architecture:** EfficientNetB2
* **Tools:** Scikit-learn, Google Colab

---

## 🚀 How to Run
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install tensorflow scikit-learn matplotlib
    ```
3.  **Train the model:** Run the provided Jupyter/Colab notebook.
4.  **Inference:** Use the prediction script to test on new images:

```python
prediction = model.predict(img_array)
if prediction > 0.5:
    print("Result: Cancer")
else:
    print("Result: Non-Cancer")

---

## 📌 Future Improvements
To evolve this project into a more robust tool, the following enhancements are planned:

* **Dataset Expansion:** Integration of the **ISIC (International Skin Imaging Collaboration)** full dataset to improve generalization.
* **Explainability:** Implementation of **Grad-CAM** (Gradient-weighted Class Activation Mapping) to visualize "why" the model predicts cancer by highlighting specific image regions.
* **Metric Optimization:** Fine-tuning the classification **threshold** to prioritize **Recall** for the Cancer class (minimizing false negatives).
* **Deployment:** Building a web-based interface using **Flask** or **FastAPI** for real-time image uploads and predictions.

---

## 🎓 Academic Value
This project serves as a comprehensive demonstration of key competencies in modern AI development:

* **Domain-Specific Transfer Learning:** Adapting ImageNet-trained models to specialized medical imagery.
* **Imbalance Mitigation:** Effectively using **Class Weights** to prevent model bias toward the majority class.
* **Advanced Optimization:** Implementing a two-stage training strategy (Warmup + Layer-wise Fine-tuning).
* **Rigorous Evaluation:** Moving beyond simple accuracy to analyze **Confusion Matrices**, **Precision**, and **F1-scores**.

---

## 👤 Author
**Tsewang Namgail** *Deep Learning & AI Enthusiast* [![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/your-profile) 
[![GitHub](https://img.shields.io/badge/GitHub-Profile-lightgrey?style=flat&logo=github)](https://github.com/your-username)

---
*Disclaimer: This project is for educational purposes only and should not be used as a substitute for professional medical advice or diagnosis.*
