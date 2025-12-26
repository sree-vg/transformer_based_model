# My Zoom: A Transformer-Based Model for Contextual Feedback Validation

## 📌 Project Overview

**My Zoom** is a transformer-based NLP project designed to validate whether user feedback text aligns with a selected dropdown reason. The solution fine-tunes a BERT-based model on paired **text–reason inputs** to perform **binary classification**, ensuring that only relevant and meaningful feedback is recorded.

**Domain:** EdTech (Educational Technology)

---

## 🎯 Problem Statement

In EdTech platforms, users often submit feedback along with a predefined reason. However, mismatched or irrelevant feedback reduces the quality of insights and decision-making.

### Objective

Build a machine learning model that determines whether:

* `1 → Aligned feedback` (feedback matches the selected reason)
* `0 → Not aligned feedback` (feedback does not match the reason)

This improves feedback quality, analytics reliability, and overall user experience.

---

## 💼 Business Use Cases

* **Enhanced Feedback Systems:** Validate feedback before saving it to databases
* **Automated Moderation:** Filter irrelevant or misleading feedback
* **Survey Quality Control:** Maintain meaningful survey responses
* **EdTech Analytics:** Generate accurate insights for course and product improvement

---

## 🧠 Skills Gained

* Text Preprocessing & Data Augmentation
* Transformer Models (BERT)
* Binary Classification in NLP
* Model Evaluation & Error Analysis
* Deployment using Gradio
* Hugging Face ecosystem

---

## 🗂️ Dataset Description

**Format:** Tabular (Excel)

### Columns

* `text` → User feedback
* `reason` → Dropdown-selected reason
* `label` → Target (1 = aligned, 0 = not aligned)

### Data Preparation

* Removed missing values
* Renamed columns for consistency
* Augmented **negative samples** by shuffling reasons to create mismatched text–reason pairs
* Balanced the dataset to avoid class bias

---

## ⚙️ Approach & Methodology

### 1️⃣ Text Preprocessing

* Cleaned feedback and reason text
* Tokenized **paired sequences** using BERT tokenizer
* Applied truncation and padding (max length = 128)

### 2️⃣ Model Development

* Model: `bert-base-uncased`
* Task: Binary sequence-pair classification
* Input: *(feedback, reason)*
* Output: Aligned / Not Aligned

### 3️⃣ Training Configuration

* Optimizer: AdamW (Hugging Face Trainer default)
* Learning Rate: `2e-5`
* Batch Size: `32`
* Epochs: `3`
* Mixed Precision Training (fp16)
* Best model selected using **F1-score**

### 4️⃣ Evaluation Metrics

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

---

## 📊 Results & Performance

**Expected Accuracy:** > 85%

The trained model effectively distinguishes aligned and non-aligned feedback, with balanced performance across both classes.

### Confusion Matrix

The confusion matrix visualizes:

* True Positives
* False Positives
* True Negatives
* False Negatives

This enables detailed error analysis and model reliability assessment.

---

## 🧪 Sample Inputs & Outputs

### Example 1

* **User Feedback:** The instructor explained concepts clearly
* **Selected Reason:** Teaching quality
* **Prediction:** Aligned ✅
* **Confidence:** 0.92

### Example 2

* **User Feedback:** The session had audio issues
* **Selected Reason:** Content relevance
* **Prediction:** Not Aligned ❌
* **Confidence:** 0.88

### Example 3 (Low Confidence Case)

* **User Feedback:** The class was okay
* **Selected Reason:** Overall experience
* **Prediction:** Uncertain ⚠️
* **Confidence:** 0.54

> ⚠️ Predictions with confidence below **0.6** are flagged as *Uncertain* to avoid overconfident decisions.

---

## 🧠 Model Architecture Overview

The project uses a **Transformer-based sequence pair classification architecture** built on BERT.

### Architecture Flow

1. **Input Layer**

   * Two inputs: **User Feedback** and **Selected Reason**
   * Tokenized jointly as:

     ```
     [CLS] feedback text [SEP] reason text [SEP]
     ```

2. **Encoder**

   * Pre-trained `bert-base-uncased`
   * 12 Transformer layers
   * Generates contextual embeddings capturing semantic alignment

3. **Classification Head**

   * Fully connected layer on the `[CLS]` token
   * Outputs probabilities for:

     * `1 → Aligned`
     * `0 → Not Aligned`

4. **Training Strategy**

   * Cross-entropy loss
   * Dataset balanced using synthetic negative samples
   * Best checkpoint selected using **F1-score**

5. **Inference Logic**

   * Softmax probability computation
   * Confidence thresholding to flag uncertain predictions

---

## 🚀 Deployment

* Built an interactive **Gradio UI** for real-time feedback validation
* **Inputs:**

  * User Feedback (Text)
  * Dropdown Reason (Text)
* **Outputs:**

  * Prediction (Aligned / Not Aligned / Uncertain)
  * Confidence Score

The trained model and tokenizer are saved locally and reloaded for inference.

---

## 🧪 Inference Logic

* Uses softmax probabilities
* Confidence score extracted for predicted class
* Returns **"Uncertain ⚠️"** when confidence < `0.6`

---

## 🧾 Project Deliverables

* ✔ Jupyter Notebook (Training & Evaluation)
* ✔ Fine-tuned Transformer Model
* ✔ Gradio Application
* ✔ Confusion Matrix & Evaluation Metrics
* ✔ README Documentation

---

## 🧩 Technical Stack

* Python
* PyTorch
* Hugging Face Transformers
* Datasets
* Scikit-learn
* Gradio
* Google Colab

---

## 📌 Best Practices Followed

* Modular and readable code structure
* PEP 8–compliant Python code
* Proper evaluation on unseen data
* Handling class imbalance
* Reproducible training setup

---

## 🗓️ Timeline

**Project Duration:** 1 Week

---

## 🔗 References

* Hugging Face Transformers Documentation
* Hugging Face Course
* Gradio Documentation
* Pre-trained Transformer Models

---

## 👩‍💻 Author & Approval

**Created By:** Sree V G
---

✨ *This project demonstrates the practical application of transformer-based NLP models for real-world contextual feedback validation systems.*

---
