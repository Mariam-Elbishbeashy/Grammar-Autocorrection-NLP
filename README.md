# A Comparative Study of Machine Learning and Deep Learning Models for Grammar Autocorrection

## 📁 Dataset Overview

**Dataset** used in this project is the **Grammar-Correct Dataset** obtained from [Kaggle](https://www.kaggle.com/datasets).  

It contains slightly more than **2,000 English sentence pairs**, each consisting of:
- An **ungrammatical sentence**
- Its **corrected version**

The dataset covers a wide range of common grammatical errors, such as:
- Spelling and punctuation mistakes
- Verb tense inconsistencies
- Article misuses
- Sentence structure faults .. etc

---

## 📊 Dataset Structure

| Feature | Type | Description |
|--------|------|-------------|
| Serial Number | Numerical | Entry index |
| Error Type | Categorical | Classification of the grammar error |
| Ungrammatical Statement | Text | Raw sentence with grammar errors |
| Standard English | Text | Corrected sentence |

---

## 🙌 Contributions

The full preprocessing pipeline, model training, analysis, and reporting for Dataset were conducted by:

- **[Mariam-Elbishbeashy](https://github.com/Mariam-Elbishbeashy)**
- **[LauraLucasZ](https://github.com/LauraLucasZ)**

This work is part of an **original, research project** on grammatical error correction.

---

## 🛠️ Preprocessing Steps

1. **Cleaning Special Characters**
   - Lowercasing
   - Retained `.`, `,`, `?`, alphanumeric and whitespace  
   - Removed unnecessary symbols

3. **Negation Normalization**  
   - E.g., `can't` → `cannot`, `won't` → `will not`

4. **Tokenization & POS Tagging**  
   - `nltk.word_tokenize` and Averaged Perceptron POS tagger

5. **Feature Engineering**  
   - POS Tag Sequences  
   - POS Embeddings (Word2Vec, 50-dim)  
   - Token Embeddings (Word2Vec, 100-dim)  
   - Bigram & Trigram Embeddings (50-dim each)

---

## 📈 Visualizations

- Top 5 grammatical error types
- Sentence length distributions
- Top 20 unigrams, bigrams, trigrams in ungrammatical data

---

## 🤖 Models Applied

### Machine Learning:
- Naive Bayes  
- SVM  
- KNN  
- Decision Tree  
- XGBoost  
- Random Forest  

### Deep Learning:
- DistilBERT  
- T5-small  
- FLAN-T5-base  
- BART
- LSTM
- DistilBART

---

## 📊 Results Summary

## 📊 Machine Learning Results

### 10-Fold Cross-Validation

| Classifier     | Features   | Accuracy (%) | Precision (%) | Recall (%) | F1 Score (%) |
|----------------|------------|--------------|----------------|-------------|--------------|
| GaussianNB     | POS        | 53.12 ± 2.69 | 52.60 ± 2.17   | 63.62 ± 3.22| 57.57 ± 2.37 |
|                | Unigram    | 51.31 ± 2.45 | 51.65 ± 3.00   | 43.76 ± 4.37| 47.25 ± 3.08 |
|                | Bigram     | 50.42 ± 2.00 | 50.66 ± 3.00   | 31.12 ± 3.91| 38.46 ± 3.58 |
|                | Trigram    | 50.89 ± 2.02 | 51.09 ± 2.62   | 41.03 ± 3.86| 45.45 ± 3.12 |
| SVM            | POS        | 53.47 ± 2.86 | 53.03 ± 2.52   | 61.54 ± 2.90| 56.95 ± 2.46 |
|                | Unigram    | 51.39 ± 2.65 | 51.36 ± 2.58   | 54.81 ± 4.34| 52.95 ± 2.80 |
|                | Bigram     | 50.10 ± 2.13 | 40.12 ± 20.17  | 51.73 ± 44.53| 38.00 ± 30.08 |
|                | Trigram    | 49.41 ± 0.92 | 35.67 ± 18.82  | 30.74 ± 38.17| 25.99 ± 25.98 |
| XGBoost        | POS        | 54.14 ± 2.90 | 53.51 ± 2.50   | 64.57 ± 2.81| 58.48 ± 2.09 |
|                | Unigram    | 51.61 ± 1.50 | 51.90 ± 1.72   | 44.45 ± 6.69| 47.63 ± 3.98 |
|                | Bigram     | 47.57 ± 2.39 | 47.40 ± 2.54   | 42.72 ± 2.66| 44.88 ± 2.13 |
|                | Trigram    | 50.89 ± 2.62 | 51.53 ± 4.33   | 31.57 ± 5.98| 38.85 ± 5.28 |
| KNN            | POS        | 48.71 ± 1.80 | 48.70 ± 1.90   | 46.63 ± 2.74| 47.60 ± 1.84 |
|                | Unigram    | 45.91 ± 2.77 | 45.93 ± 2.74   | 45.98 ± 3.11| 45.94 ± 2.77 |
|                | Bigram     | 39.57 ± 1.83 | 39.22 ± 1.92   | 38.01 ± 2.53| 38.59 ± 2.14 |
|                | Trigram    | 39.40 ± 3.49 | 38.74 ± 3.20   | 36.17 ± 3.99| 37.33 ± 3.30 |
| Random Forest  | POS        | 46.04 ± 2.46 | 45.96 ± 2.48   | 45.84 ± 4.03| 45.88 ± 3.19 |
|                | Unigram    | 41.97 ± 3.13 | 42.13 ± 3.11   | 42.86 ± 3.67| 42.46 ± 3.19 |
|                | Bigram     | 38.95 ± 2.16 | 39.22 ± 2.06   | 40.19 ± 2.36| 39.69 ± 2.13 |
|                | Trigram    | 43.24 ± 2.20 | 43.15 ± 2.18   | 42.57 ± 3.18| 42.82 ± 2.46 |
| Decision Tree  | POS        | 43.58 ± 2.13 | 43.30 ± 2.19   | 41.43 ± 2.48| 42.33 ± 2.20 |
|                | Unigram    | 43.58 ± 2.22 | 43.23 ± 2.38   | 40.93 ± 2.79| 42.03 ± 2.45 |
|                | Bigram     | 47.03 ± 2.17 | 46.96 ± 2.17   | 45.54 ± 2.89| 46.21 ± 2.27 |
|                | Trigram    | 46.93 ± 2.03 | 46.74 ± 2.21   | 45.19 ± 4.14| 45.92 ± 3.15 |


### Train/Test Split (90%–10%)

| Classifier     | Features   | Accuracy (%) | Precision (%) | Recall (%) | F1 Score (%) |
|----------------|------------|--------------|----------------|-------------|--------------|
| GaussianNB     | POS        | 55.45        | 55.60          | 55.45       | 55.13        |
|                | Unigram    | 50.25        | 50.26          | 50.25       | 49.68        |
|                | Bigram     | 50.99        | 51.13          | 50.99       | 49.47        |
|                | Trigram    | 48.02        | 47.98          | 48.02       | 47.77        |
| SVM            | POS        | 55.20        | 55.36          | 55.20       | 54.86        |
|                | Unigram    | 52.48        | 52.48          | 52.48       | 52.45        |
|                | Bigram     | 50.99        | 50.99          | 50.99       | 50.96        |
|                | Trigram    | 50.99        | 50.99          | 50.99       | 50.96        |
| XGBoost        | POS        | 50.74        | 50.75          | 50.74       | 50.63        |
|                | Unigram    | 46.29        | 46.25          | 46.29       | 46.17        |
|                | Bigram     | 43.07        | 43.04          | 43.07       | 43.02        |
|                | Trigram    | 43.56        | 43.56          | 43.56       | 43.55        |
| KNN            | POS        | 51.49        | 51.49          | 51.49       | 51.47        |
|                | Unigram    | 48.02        | 48.01          | 48.02       | 47.97        |
|                | Bigram     | 41.09        | 41.05          | 41.09       | 41.02        |
|                | Trigram    | 40.59        | 39.54          | 40.59       | 39.06        |
| Random Forest  | POS        | 52.23        | 52.26          | 52.23       | 52.04        |
|                | Unigram    | 44.80        | 44.80          | 44.80       | 44.79        |
|                | Bigram     | 37.38        | 37.35          | 37.38       | 37.35        |
|                | Trigram    | 41.83        | 41.68          | 41.83       | 41.57        |
| Decision Tree  | POS        | 44.55        | 44.46          | 44.55       | 44.32        |
|                | Unigram    | 46.04        | 45.97          | 46.04       | 45.82        |
|                | Bigram     | 44.80        | 44.80          | 44.80       | 44.79        |
|                | Trigram    | 42.57        | 42.57          | 42.57       | 42.57        |

---

## 📊 Deep Learning Results

### Evaluation on Full Dataset + 5-Fold Cross Validation

| Model     | BLEU (Full) | Exact Match (%) | BLEU (CV) | Accuracy (%) | Precision (%) | Recall (%) | F1 Score (%) |
|-----------|-------------|------------------|-----------|----------------|----------------|-------------|---------------|
| DistilBERT| -           | -                | -         | 58.67 ± 1.91   | 58.26 ± 2.34   | 63.17 ± 7.01| 60.31 ± 2.33 |
| T5        | 72.71       | 45.39            | 66.86 ± 0.53| 34.59 ± 1.98  | 34.59 ± 1.98  | 34.59 ± 1.98| 34.59 ± 1.98 |
| FLAN-T5   | 83.32       | 59.12            | 74.64 ± 1.58| 48.61 ± 2.20  | 48.61 ± 2.20  | 48.61 ± 2.20| 48.61 ± 2.20 |
| BART      | **94.04**   | **86.87**        | 77.89 ± 1.04| 54.56 ± 2.40  | 54.56 ± 2.40  | 54.56 ± 2.40| 54.56 ± 2.40 |

---

## 🧾 Example Predictions

| Ungrammatical Sentence                       | Reference (Corrected)                      | BART Prediction                             | FLAN-T5 Prediction                          | Match (BART) | Match (FLAN-T5) |
|---------------------------------------------|---------------------------------------------|---------------------------------------------|----------------------------------------------|--------------|-----------------|
| they was playing soccer last night          | they were playing soccer last night         | they were playing soccer last night         | they were playing soccer last night          | ✅ True      | ✅ True          |
| she will goes to the party tonight          | she will go to the party tonight            | she will go to the party tonight            | she will go to the party tonight             | ✅ True      | ✅ True          |
| the kids plays video games after school     | the kids play video games after school      | the kids play video games after school      | the kids play video games after school       | ✅ True      | ✅ True          |
| the computer not working properly           | the computer is not working properly        | the computer is not working properly        | the computer is not working properly         | ✅ True      | ✅ True          |
| i has been to paris three times             | i have been to paris three times            | i have been to paris three times            | i have been to paris three times             | ✅ True      | ✅ True          |
| the cat catch the mouse yesterday           | the cat caught the mouse yesterday          | the cat caught the mouse yesterday          | the cat caught the mouse yesterday           | ✅ True      | ✅ True          |
| she buy a new dress for the party           | she buys a new dress for the party          | she buys a new dress for the party          | she buys a new dress for the party           | ✅ True      | ✅ True          |
| the teacher teach the students in the classroom | the teacher teaches the students in the classroom | the teacher teaches the students in the classroom | the teacher taught the students in the classroom | ✅ True    | ❌ False         |
| the dog was chase the squirrel              | the dog was chasing the squirrel            | the dog was chasing the squirrel                 | the dog chased the squirrel                  | ✅ True    | ❌ False         |
| the manager gives a speech at the meeting   | the manager gave a speech at the meeting    | the manager gives a speech at the meeting   | the manager gave a speech at the meeting     | ❌ False     | ❌ False          |

These examples demonstrate that transformer-based models like **BART** and **FLAN-T5** are capable of performing accurate grammatical corrections, closely matching the target sentences.

---

## ✅ Conclusion

This project demonstrates a comprehensive approach to grammatical error correction using both traditional machine learning and modern deep learning models.  
Key findings include:
- **ML models** achieved moderate performance with POS features showing the best consistency.
- **Transformer-based models**, especially **BART**, significantly outperformed others, achieving high BLEU and exact match scores.
- **FLAN-T5** & **FLAN-T5**  also showed strong generalization capabilities while being lightweight and efficient.

The study reinforces the effectiveness of pretrained transformer architectures for nuanced language correction tasks.

---

## 🚀 Future Work

To further enhance this project, the following directions are proposed:
- **Data Augmentation**: Increase dataset size with synthetic error generation to improve model robustness.
- **Error Type-Specific Models**: Train specialized models for distinct grammar error types (e.g., tense, articles).
- **Deployment**: Wrap the best model into a web-based grammar correction tool for public use.


