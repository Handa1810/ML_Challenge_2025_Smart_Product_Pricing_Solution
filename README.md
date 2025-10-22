# ML Challenge 2025: Smart Product Pricing Solution

[![Leaderboard Rank](https://img.shields.io/badge/Leaderboard-2337%2F6645-blue)](https://www.amazonmlchallenge2025.com/leaderboard) 
[![Mean SMAPE](https://img.shields.io/badge/Mean%20SMAPE-52.77%25-green)]() 
[![Colab Notebook](https://img.shields.io/badge/Colab-Open%20Notebook-orange)](https://colab.research.google.com/drive/14isoBEBADsG-lCxLhK3WSYtx3P9G3TQB?usp=sharing)
[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)]()
[![PyTorch](https://img.shields.io/badge/PyTorch-2.1-red?logo=pytorch&logoColor=white)]()
[![Transformers](https://img.shields.io/badge/Transformers-HuggingFace-orange?logo=huggingface&logoColor=white)]()
[![EfficientNet](https://img.shields.io/badge/EfficientNet-B3-lightgrey)]()

**Team Name:** Algorithmic Minds  
**Team Members:** Yash Handa, Suhani Kumari, Vishakha Gupta  
**Submission Date:** 13/10/2025  

![ML Challenge](images/ML%20challenge.jpg)
---

## 🏆 About the Challenge

The **Amazon ML Challenge 2025** is a two-stage competition for engineering students across India, offering an opportunity to work on real-world datasets from Amazon. Participants build innovative solutions for predicting product prices based on product images and descriptions. Top-performing teams win cash prizes and certificates.

**Competition Structure:**  

1. **Round 1 - ML Hackathon:**  
   - Teams receive the dataset and problem statement on Day 1.  
   - Submission includes code, notebooks, and a 1–2 page solution document.  
   - Live leaderboard tracks team rankings throughout the hackathon.  

2. **Round 2 - Finale:**  
   - Top 10 teams are invited to present their solutions live to Amazon scientists.  
   - Finale hosted virtually on 17th October 2025.  

> Although we did not qualify for the Grand Finale, participating in this challenge was an incredible learning experience. We gained hands-on exposure to **multimodal machine learning, attention-based models, and real-world product pricing prediction**, which will greatly enhance our skills for future projects.

---

## 📄 Executive Summary

We developed a **multimodal deep learning model** that predicts optimal product prices by leveraging both **textual** and **visual** information.  

**Key Highlights:**  
- **Innovation:** Attention-based fusion between image and text embeddings.  
- **Performance:**  
  - **Mean SMAPE:** 52.77% across 5-fold cross-validation  
  - **Best Fold SMAPE:** 53.01%  
- **Robustness:** Low variance across folds (<1%), stable predictions across product categories.  

Our model intelligently decides how much to rely on text versus images for each product, improving overall accuracy and generalization.

---

## 🧠 Methodology Overview

### 1. Problem Analysis
- Framed as a **regression problem** predicting product prices from images and descriptions.  
- **Insights from EDA:**  
  - Text captures brand, category, and quality cues.  
  - Images reflect visual quality, color, texture, and background complexity.  
  - Price distribution is skewed, requiring **log-scaling** for stability.  
  - Luxury items and outliers significantly affect predictions.  
  - Combining modalities outperforms using only text or images.

### 2. Solution Strategy
- **Approach Type:** Hybrid Multimodal Model  
- **Core Innovation:** Attention-gated fusion of **text embeddings** (transformer-based) and **image embeddings** (EfficientNet-B3).  
- **Architecture:** Two-stream network with learnable attention gates that dynamically weight text and image features for optimal price prediction.  

---

## 🏗️ Model Architecture

### Overview
1. **Text Branch:**  
   - Uses `SentenceTransformer` (all-mpnet-base-v2) → 768-dimensional embeddings.  
   - Captures semantic info: brand, material, descriptive cues.  

2. **Image Branch:**  
   - Pretrained `EfficientNet-B3` → 1536-dimensional visual embeddings.  
   - Encodes features: color, texture, shape, context.  

3. **Feature Projection:**  
   - Embeddings projected into a common space via fully connected layers.  

4. **Attention Gate:**  
   - Dynamically assigns weights to text and image features per product.  

5. **Fusion Network & Price Prediction:**  
   - Weighted embeddings concatenated and passed through a **MLP** for final price prediction.  

---

### Components

| Module | Details |
|--------|---------|
| **Text Preprocessing** | Lowercasing, punctuation removal, normalization |
| **Text Model** | SentenceTransformer all-mpnet-base-v2, 768-dim embeddings |
| **Image Preprocessing** | Resize to 300×300, normalization |
| **Image Model** | EfficientNet-B3 (pretrained), 1536-dim embeddings |
| **Fusion Module** | Learnable attention gate + fully connected layers for final prediction |

---

## 📊 Model Performance

**5-Fold Cross-Validation SMAPE:**

| Fold | SMAPE (%) |
|------|-----------|
| 1    | 53.27     |
| 2    | 52.45     |
| 3    | 52.80     |
| 4    | 52.31     |
| 5    | 53.01     |

- **Average SMAPE:** 52.77%  
- **Best Fold:** 52.31%  
- **Stability:** Cross-validation variance <1%  
- **Other Metrics:** RMSE improved ~20% after multimodal fusion; LogHuber loss decreased steadily.  

---

## ✅ Conclusion

Our **attention-gated multimodal model** effectively combines textual and visual features to enhance price prediction.  

**Key Strengths:**  
- Dynamic weighting of text vs. image per product  
- Robust performance across categories and outliers  
- Low cross-validation variance → consistent predictions  

**Future Directions:**  
- Contrastive pretraining for better multimodal alignment  
- Domain-specific fine-tuning for niche product categories  

---

## 📎 Appendix

**Code & Artifacts:**  
- [Colab Notebook & Precomputed Embeddings](https://colab.research.google.com/drive/14isoBEBADsG-lCxLhK3WSYtx3P9G3TQB?usp=sharing)

**Additional Results:**  
- Smooth training convergence around epoch 40  
- Early stopping prevents overfitting  
- Attention mechanism adapts dynamically to modality dominance  

---

## 🌟 Team Contact

**Algorithmic Minds**  
- **Yash Handa** - [GitHub](https://github.com/Handa1810), [LinkedIn](https://www.linkedin.com/in/yashhanda18)
- **Suhani Kumari** - [GitHub](https://github.com/SuhaniSingh-29), [LinkedIn](https://www.linkedin.com/in/suhani-kumari-2b3526306/)
- **Vishakha Gupta** [GitHub](https://github.com/Vishakha), [LinkedIn](https://www.linkedin.com/in/vishakha-gupta-b34650266/)
