# 📝 Spanish-OCR

## 📌 Overview
This project focuses on building an OCR (Optical Character Recognition) system capable of transcribing text from **old Spanish manuscripts and scanned documents**. The goal was to develop a model that could handle noisy historical texts, special characters, and poor image quality — all common challenges in real-world archival digitization tasks.

---

## 🚀 Our Approach

### 1️⃣ Baseline: TrOCR-Small
- Started with **TrOCR-small-spanish** on Kaggle (P100 GPU).
- Initial WER (Word Error Rate): **0.78**

---

### 2️⃣ Image Binarization
- Applied **binarization** to enhance text visibility by converting grayscale to black-and-white using a pixel threshold.
- Helped reduce WER to **0.6**

---

### 3️⃣ Upgrade to TrOCR-Large
- Switched to **TrOCR-Large** for better performance.
- Trained with **batch size = 4** due to GPU limits.
- Results:
  - After 2 epochs: **WER = 0.28**
  - After 14 epochs: **WER = 0.234**

---

### 4️⃣ Postprocessing for Common Errors
- Corrected common OCR mistakes (e.g., misrecognized **ã**).
- Postprocessing lowered WER further to **0.202**

---

### 5️⃣ BART as a Refinement Layer
- Fed TrOCR outputs into a **BART model** trained on ground truth.
- Aimed to fix misrecognized words and improve sentence fluency.
- Due to limited compute, BART didn’t outperform TrOCR-Large.

---

## 📊 Results

| Model Stage         | WER     |
|---------------------|---------|
| TrOCR-Small         | 0.780   |
| + Binarization      | 0.600   |
| TrOCR-Large         | 0.234   |
| + Postprocessing    | **0.202** ✅ |

**Final Model WER:** 0.202  

---

## 💡 Challenges & Learnings

- 🧠 **Limited GPU** = smaller batch sizes & slower training  
- 🔣 **Rare characters** were misrecognized due to limited training data  
- 🛠️ **Postprocessing** made a meaningful difference

---

## ✅ Conclusion & Future Work

Despite hardware constraints, we achieved strong results through:
- Careful preprocessing
- Model scaling
- Smart postprocessing

🔮 Next steps:
- Explore **multi-stage refinement**
- Enhance **training data diversity**
- Utilize **stronger GPUs** for larger models

---
