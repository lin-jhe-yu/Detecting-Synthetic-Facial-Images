<img width="1090" height="293" alt="Image" src="https://github.com/user-attachments/assets/681a95cf-a784-43e2-aea9-61bf8bf2c880" />

# Detecting Synthetic Facial Images

## Executive Summary

As the line between real and AI-generated imagery blurs, the ability to reliably detect synthetic faces has become critical for maintaining trust in digital identity. This project demonstrates that lightweight machine learning models can effectively distinguish between real and fake facial images using high-dimensional visual representations.

---

## Key Findings

- **High Detection Accuracy:**  
  Supervised models, specifically SVM and XGBoost, achieved over 75% accuracy in detecting synthetic faces.

- **Efficient Feature Representation:**  
  By reducing the facial embedding space from 512 to 141 features, we preserved model performance while reducing data volume by approximately 72%.

- **Latent Contextual Signals:**  
  Unsupervised clustering revealed that embeddings capture specific recurring visual characteristics, such as hats, glasses, and microphones, which can drive detection performance.

- **Scalable Deployment:**  
  Traditional, "lightweight" models performed competitively with complex neural networks, making them ideal for scalable authenticity screening on everyday digital platforms.

---

## Business & Strategic Impact

This project provides a foundational framework for organizations and platforms to:

- **Enhance Digital Trust:**  
  Implement automated screening tools to deter fraud and identity-based scams.

- **Optimize Resource Allocation:**  
  Use feature reduction to build high-performing models that require less computational power and storage.

- **Adaptive Security:**  
  Balance "Security" (catching more fakes) versus "Usability" (avoiding blocking real users) through customizable model thresholds.

---

## Solution Overview

We developed an end-to-end machine learning pipeline that:

1. **Extracts Embeddings:**  
   Utilizes a ResNet18 model pre-trained on ImageNet to convert facial images into 512-dimensional vectors.

2. **Reduces Dimensions:**  
   Employs TruncatedSVD and RFECV (Recursive Feature Elimination) to identify the most impactful features for classification.

3. **Classifies Authenticity:**  
   Compares a suite of candidate models—from Linear Models (SVM, Logistic Regression) to Ensemble Trees (Random Forest, XGBoost).

4. **Optimizes Performance:**  
   Implements a Weighted Ensemble (SVM + AdaBoost + XGBoost) to blend complementary learners for flexible error control.

---

## Business Problem

Synthetic media is evolving rapidly, often used by bad actors for misinformation or fraud. Current detection systems often face a "sophistication gap." We address three core questions:

1. Can lightweight models reliably identify synthetic images in peer-to-peer contexts?  
2. What specific image characteristics or "latent features" drive detection performance?  
3. How can we minimize data dimensionality without sacrificing predictive accuracy?  

---

## Data Overview

- **Scale:** 10,000 total image samples.  
- **Real Images:** 5,000 samples from the Flickr-Faces-HQ (FFHQ) dataset.  
- **Fake Images:** 5,000 samples from the Real vs AI Generated Faces dataset, including Faceswap, Stable Diffusion, and ThisPersonDoesNotExist.  
- **Feature Engineering:** High-dimensional images are converted to semantic embeddings where similar facial structures have closer vector representations.

---

## Methodology

- **Core Technologies:**  
  Python (Scikit-Learn, XGBoost), ResNet18 (Feature Extraction), TruncatedSVD (Dimensionality Reduction), t-SNE/UMAP (Clustering Visualization).

- **Modeling Strategy:**  
  An exhaustive comparison across linear, tree-based, and probabilistic models to find the optimal balance of speed and accuracy.

---

## Full Presentation

Please find the complete technical deep-dive including confusion matrices, ROC curves, and top-ranking "Red Flag" features here:

- [Full Final Presentation: Detecting Synthetic Facial Images](https://github.com/lin-jhe-yu/Detecting-Synthetic-Facial-Images/blob/main/ML1%20Final%20Presentation.pdf)
