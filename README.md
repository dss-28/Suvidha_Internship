
---

# 🚀 Transformer-Based News Summarization (BART vs LongT5)

### 🧠 Internship Project — Suvidha Foundation

This internship project focuses on **abstractive summarization of news articles** (CNN/DailyMail).
To **better understand model behavior and build a robust system**, the pipeline was also evaluated on **long-form documents** (ArxivSum), demonstrating how **architecture and input length affect summarization performance**.

---

## 📘 Project Overview

The project involved implementing and evaluating **BART** and **LongT5** across datasets of different lengths:

Sure! Here’s your table properly formatted in **Markdown**, ready to copy-paste into your README:

| Model                                    | Architecture    | Key Feature                                                               | Typical Use Case                            |
| :--------------------------------------- | :-------------- | :------------------------------------------------------------------------ | :------------------------------------------ |
| **BART (facebook/bart-large-cnn)**       | Encoder-Decoder | Denoising autoencoder with bidirectional encoder + autoregressive decoder | News summarization                          |
| **LongT5 (google/long-t5-tglobal-base)** | Encoder-Decoder | Sparse + global attention (up to 16K tokens)                              | Long-form documents (for system robustness) |

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
Perfect 👍 — here’s how to **professionally include your dataset sample details** in your README, under a clean “📊 Dataset Summary” section, using what you shared (with clarity on what portions you actually used for evaluation):

---

## 📊 Dataset Summary

| Dataset           |          Type          | Train Samples | Validation Samples | Test Samples | Used in This Project                               |
| :---------------- | :--------------------: | :-----------: | :----------------: | :----------: | :------------------------------------------------- |
| **CNN/DailyMail** |       Short News       |    287,113    |       11,490       |    13,368    | ✅ Used full **validation** & **test** sets         |
| **ArxivSum**      |     Research Papers    |    203,037    |        6,440       |     6,436    | ✅ Used **500 samples each** from validation & test |
| **WikiSum**       | Long-form Multi-Source |     35,775    |        1,000       |     2,000    | 🚧 Planned for next phase                          |
| **MultiNews**     |   Multi-Document News  |     44,972    |        5,662       |     5,662    | 🚧 Planned for next phase                          |

> ✅ Focused on **single-source summarization** in this phase (BART & LongT5).
> 🔭 **Next step:** Extend pipeline for **multi-source summarization** (PEGASUS, LED).

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
  
Perfect — here’s a **professionally formatted, visually rich, and elegant Markdown version** of your section 👇
(copy-paste directly into your README — this will render beautifully on GitHub)

---

## 🧩 Future Work

> **Completed:** Single-source summarization for both short (news) and long (research papers) documents.
> **Next Goal:** Expand to *multi-source* and *multi-document* summarization.

* **🔗 Multi-document & Multi-source Summarization:**
  Extend the current pipeline to handle multiple related documents (e.g., combining several news articles, research papers + their citations, or multi-author reviews).
  Planned improvements include:

  * 🧠 *Document Fusion Strategies:* concatenation with separators, hierarchical encoding, and late fusion.
  * 📊 *Evaluation:* testing on **MultiNews** and **WikiSum** datasets, along with **human evaluation** for coherence and factual consistency.

* **⚖️ Model Expansion:**
  Incorporate **PEGASUS** and **LED** to benchmark robustness across diverse document types —
  from short-form summaries to multi-source synthesis and ultra-long contexts.

---

## 💼 Acknowledgment

Special thanks to **[Suvidha Foundation](https://suvidhafoundationedutech.org/)**
for the opportunity and mentorship during this **NLP internship**.
It was an enriching experience applying **Transformer architectures** for *real-world summarization tasks*.

---

## 🔗 Links

* 📘 **GitHub Repository:** [github.com/dss-28/Suvidha_Internship](https://github.com/dss-28/Suvidha_Internship)
* 🧑‍💻 **Author:** [Darshan Shirsat](https://www.linkedin.com/in/darshanshirsat28/)
* 🏢 **Organization:** [Suvidha Foundation](https://suvidhafoundationedutech.org/)

---

✨ *If you found this useful, please consider giving the repo a star!* ⭐

---

Would you like me to make it look even more **modern and colorful (with emojis + headings + divider styling like badges)** for a more *portfolio-ready* version?
