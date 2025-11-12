# 🚀 Transformer-Based Text Summarization (BART vs LongT5)

### 🧠 Internship Project — Suvidha Foundation
Exploring and comparing transformer architectures for **abstractive text summarization**, focusing on how **model design** and **input length** affect summarization quality across domains — from short news to long-form research papers.

---

## 📘 Project Overview

This project was completed as part of my internship at **Suvidha Foundation**.  
The objective was to **implement and evaluate** transformer-based summarization models — **BART** and **LongT5** — on two datasets of different nature and length.

| Model | Architecture | Key Feature | Typical Use Case |
|:------|:--------------|:-------------|:-----------------|
| **BART (facebook/bart-large-cnn)** | Encoder-Decoder | Denoising autoencoder with bidirectional encoder + autoregressive decoder | News summarization |
| **LongT5 (google/long-t5-tglobal-base)** | Encoder-Decoder | Sparse + global attention mechanism for longer sequences (up to 16K tokens) | Long-form summarization |

---

## 🧩 Objectives

- Implement transformer-based abstractive summarization models using Hugging Face Transformers.
- Evaluate how input length and architecture affect model performance.
- Compare results between short-text (news) and long-text (research) summarization.
- Handle GPU and runtime constraints effectively on Google Colab.

---

## 📚 Datasets Used

### 1. **CNN/DailyMail**
- Short news articles (~800 words avg.)
- Preprocessed dataset available via Hugging Face.
- Used for **BART** evaluation.

### 2. **ArxivSum**
- Research paper dataset with long scientific documents (up to 10K–16K tokens).
- Used for **LongT5** evaluation.

---

## ⚙️ Experimental Setup

| Parameter | BART | LongT5 |
|:-----------|:------|:--------|
| Dataset | CNN/DailyMail | ArxivSum |
| Max Input Tokens | 1024 | 16384 |
| Batch Size | 10 | 1 |
| Evaluation Metric | ROUGE (1/2/L) + Precision | ROUGE (1/2/L) + Precision |
| Platform | Google Colab (T4 GPU) | Google Colab (T4 GPU) |

---

Perfect — you’ve structured it well. To make this **README section more accurate, polished, and publication-ready**, here’s the refined version that clearly distinguishes between validation and test performance, improves metric presentation, and gives concise yet professional insights:

---

## 📊 Results

### 🔹 **BART (facebook/bart-large-cnn)** — *Short Text Summarization (News)*

**Dataset:** CNN/DailyMail

| Metric             | Validation |  Test  |
| :----------------- | :--------: | :----: |
| **ROUGE-1**        |    38.69   |  37.68 |
| **ROUGE-2**        |    16.90   |  16.29 |
| **ROUGE-L**        |    23.90   |  23.33 |
| **Avg. Precision** |    32.7%   | 31.49% |

> ✅ **BART** achieves the highest ROUGE scores across short news datasets.
> 🧠 Excels at generating concise, fluent, and well-structured summaries, showing strong generalization across validation and test sets.

---

### 🔹 **LongT5 (google/long-t5-tglobal-base)** — *Long Document Summarization (Research Papers)*

**Dataset:** ArxivSum

| Metric             | Validation |  Test  |
| :----------------- | :--------: | :----: |
| **ROUGE-1**        |    23.24   |  22.94 |
| **ROUGE-2**        |    5.59    |  5.29  |
| **ROUGE-L**        |    13.69   |  13.75 |
| **Avg. Precision** |   31.34%   | 33.45% |

> ✅ **LongT5** demonstrates strong precision for long-context inputs using global attention.
> 📘 Ideal for summarizing lengthy research or technical documents, trading off some ROUGE recall for better factual consistency and coverage.

---

---

## 🧠 Key Insights

- **Model Architecture Matters:** BART’s encoder-decoder design is highly effective for short, cohesive text, while LongT5’s sparse attention enables better long-text understanding.
- **Input Length Impacts Quality:** Truncation severely affects summary quality for research texts — LongT5 mitigates this by extending the input length limit.
- **Compute Constraints:** Efficient GPU utilization (smaller batches, chunked summaries, checkpointing) was key to running large transformer models within Colab limits.

---

## 🧰 Tech Stack

- **Language:** Python  
- **Frameworks:** PyTorch, Hugging Face Transformers  
- **Libraries:** Datasets, Evaluate, ROUGE, NumPy, Pandas  
- **Environment:** Google Colab  
- **Version Control:** Git + GitHub

---

## 🧾 Project Workflow

1. **Dataset Loading & Preprocessing**
   - Tokenization and truncation handled by the respective tokenizer (BART/LongT5).
2. **Model Setup**
   - Loaded pre-trained models from Hugging Face (`facebook/bart-large-cnn`, `google/long-t5-tglobal-base`).
3. **Inference**
   - Inferred articles using models ; monitored ROUGE metrics during validation.
4. **Evaluation**
   - Summaries generated on validation split and scored using ROUGE and precision metrics.
5. **Optimization**
   - Reduced batch size, used gradient accumulation, and saved summaries in chunks to handle Colab runtime limits.

---
Suvidha_Internship/
├── data/
│   ├── cnn_dailymail/
│   └── arxivsum/
├── notebooks/
│   ├── bart_summarization.ipynb
│   └── longt5_summarization.ipynb
├── outputs/
│   ├── bart_summaries.csv
│   ├── longt5_summaries.csv
│   └── rouge_scores.json
├── requirements.txt
├── README.md
└── LICENSE

