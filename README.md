# Big Five Personality Classification Based on Essay Text Using VGCN-BERT

This repository contains the implementation of Big Five Personality Classification from Essay Texts using VGCN-BERT, a hybrid model that combines contextual language representations from BERT with global semantic information captured through a Vocabulary Graph Convolutional Network (VGCN).

The project is developed as part of an undergraduate thesis (Tugas Akhir) in Informatics and focuses on multi-label personality prediction based on the OCEAN (Big Five) personality model.


## Project Overview

Personality prediction from text is an important task in computational psychology and human-centered AI. Traditional approaches often rely on local textual representations and fail to capture global semantic relationships between words.


## Personality Model

The classification task is based on the Big Five Personality Traits (OCEAN): Openness to Experience, Conscientiousness, Extraversion, Agreeableness, Neuroticism. Each essay may be associated with multiple traits simultaneously, making this a multi-label classification problem.


## Dataset

- Dataset: Essays-Big5

- Source: [Publicly available personality essay dataset](https://huggingface.co/datasets/jingjietan/essays-big5)

- Size: 2,467 English essays

- Labels: Binary labels for each of the five Big Five traits

The dataset is relatively balanced across traits and is widely used as a benchmark for personality prediction from text.


## Methodology

### 1. Text Preprocessing

Two preprocessing pipelines are applied:

- BERT pipeline: minimal preprocessing to preserve linguistic context

- Graph pipeline: stopword removal and lemmatization for vocabulary graph construction

### 2. Vocabulary Graph Construction

- A Vocabulary Graph (VGraph) is built using word co-occurrence statistics

- Edge weights are computed using Normalized Pointwise Mutual Information (NPMI)

- Sliding window technique is used to capture word associations

- NPMI thresholding is applied to reduce graph sparsity

### 3. Feature Extraction

- Each vocabulary node is represented using DistilBERT embeddings

- Mean pooling is applied for subword token aggregation

- Node embeddings serve as input features for the GCN

### 4. Model Architecture (VGCN-BERT)

The model integrates:

- BERT for contextual document representation

- VGCN for global semantic representation from the vocabulary graph

- Graph-enriched embeddings are fused with BERT outputs

- Final classification uses a sigmoid-activated multi-label head

### 5. Training & Evaluation

- Loss function: Binary Cross-Entropy with Logits

- Optimizer: AdamW

- Validation: 5-fold stratified multi-label cross-validation

- Early stopping based on macro F1-score

- Threshold tuning applied on out-of-fold (OOF) predictions to optimize F1-score


## Evaluation Metrics

The model is evaluated using:

- Precision

- Recall

- F1-score (per trait)

- Macro F1-score (primary metric)

- Weighted F1-score

- Subset accuracy (for reference)

Threshold tuning is shown to significantly improve F1-score compared to the default threshold of 0.5.


## Best Configuration (Summary)

- Learning rate: 1e-5

- Dropout: 0.2

- Max sequence length: 200

- NPMI threshold: 0.2

- GCN hidden dimension: 128

- GCN layers: 1

- Graph scale: 1.0

Best performance:

- Macro F1-score ≈ 0.68

- Weighted F1-score ≈ 0.68


## Notes

- This repository is intended for academic and research purposes

- The notebook includes preprocessing, training, evaluation, and analysis in a single pipeline

- Threshold tuning is performed after model training and does not affect learned parameters

# License

This project is released for educational and research use only.

Please cite appropriately if used as a reference.
