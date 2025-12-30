# questiongenlp
# NLP_Question_Generation_Pipelines

This repository contains **three distinct NLP pipelines** for processing text and scientific papers, extracting key concepts, and automatically generating questions. Each project explores different approaches, datasets, and evaluation strategies, demonstrating how pipeline design affects performance.

---

## Projects Overview

### **Project 1: NLP-Powered Scientific Paper Summarization & Question Generation**
- **Goal:** Summarize scientific paper abstracts, extract keywords, and generate questions automatically.
- **Dataset:** ArXiv JSON dataset (sampled abstracts)
- **Technologies:** Dask, Pandas, Hugging Face Transformers (`t5-small` for summarization), YAKE, T5 QA-QG (`valhalla/t5-small-qa-qg-hl`)
- **Key Steps:**
  1. Summarization of abstracts.
  2. Keyword extraction using YAKE.
  3. Question generation based on extracted keywords.
  4. Evaluation via ROUGE-L, Precision@5, and keyword coverage.
- **Performance:**
  - Summarization Accuracy (ROUGE-L F1): 41.60%
  - Keyword Extraction Accuracy (Precision@5): 4.00%
  - Question Generation Accuracy: 86.67%
  - Overall Pipeline Accuracy: 43.84%
- **Notes:** Audio or large text noise can reduce keyword extraction accuracy, affecting overall performance.

---

### **Project 2: Multilingual NLP Pipeline for Concept Extraction & Question Generation**
- **Goal:** Process textual datasets, extract concepts using multilingual NER, classify them, and generate questions.
- **Technologies:** Python, NLTK, SpaCy (`xx_ent_wiki_sm`), TF-IDF, RandomForest, T5 QA-QG
- **Key Steps:**
  1. Text preprocessing (lowercasing, stopwords removal, tokenization)
  2. Concept extraction using multilingual NER
  3. TF-IDF feature extraction and RandomForest classification
  4. Question generation highlighting extracted concepts
  5. Evaluation for each step
- **Performance:**
  - Text Preprocessing Accuracy: 100%
  - NER Concept Extraction Accuracy: 92%
  - Classification Accuracy: 30%
  - Question Generation Accuracy: 5%
  - Overall Pipeline Accuracy: 57.60%
- **Notes:** Preprocessing and NER performed well, but low classification and question generation accuracy reduced overall performance.

---

### **Project 3: NLP Pipeline for Computer Science Paper Analysis & Question Generation**
- **Goal:** Analyze Computer Science research papers, extract keywords and entities, and generate questions.
- **Dataset:** ArXiv JSON (CS papers)
- **Technologies:** Dask, Pandas, NLTK, SpaCy (`en_core_web_sm`), YAKE, T5 QA-QG
- **Key Steps:**
  1. Load and filter CS papers from ArXiv dataset.
  2. Preprocess abstracts (lowercasing, punctuation & stopword removal).
  3. Extract top 5 keywords using YAKE.
  4. Named Entity Recognition (SpaCy) for people, organizations, locations.
  5. Generate up to 3 questions per abstract using T5 QA-QG.
  6. Evaluate each step (keywords, entities, question generation).
- **Performance:**
  - Keyword Extraction Accuracy: 100%
  - NER Accuracy: 86%
  - Question Generation Accuracy: 100%
  - Overall Pipeline Accuracy Estimate: 95.80%
- **Notes:** Highest accuracy achieved due to:
  - Structured, clean textual dataset.
  - Optimized pipeline with proper preprocessing and batch processing.
  - Effective keyword selection with YAKE.
  - Question generation directly linked to keywords in context.

---

## **Comparison of Projects**

| Feature / Metric                  | Project 1          | Project 2        | Project 3 (CS Papers) |
|-----------------------------------|-----------------|-----------------|---------------------|
| Input Data Type                    | JSON abstracts  | Text dataset    | JSON abstracts      |
| Summarization                      | Yes             | No              | No                  |
| Keyword / Concept Extraction       | YAKE            | Multilingual NER | YAKE                |
| Classification                     | No              | RandomForest    | No                  |
| Question Generation                | Yes (T5 QA-QG)  | Yes (T5 QA-QG)  | Yes (T5 QA-QG)      |
| Preprocessing Accuracy             | Medium          | 100%            | 100%                |
| NER Accuracy                       | -               | 92%             | 86%                 |
| Keyword Extraction Accuracy        | 4%              | 100%            | 100%                |
| Question Generation Accuracy       | 86.67%          | 5%              | 100%                |
| Overall Pipeline Accuracy          | 43.84%          | 57.60%          | 95.80%              |

**Insights:**
- **Project 1:** Summarization adds complexity; keyword extraction accuracy is low due to noise in the abstracts.
- **Project 2:** Preprocessing and NER are solid, but classification and question generation were weak.
- **Project 3:** Optimized pipeline and structured data led to the **highest overall accuracy**.

## Link to the dataset : 
https://www.kaggle.com/datasets/Cornell-University/arxiv


