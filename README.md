# Klasifikasi Kepribadian Big Five Berdasarkan Teks Esai Menggunakan VGCN-BERT

This repository contains the implementation of Big Five Personality Classification from Essay Texts using VGCN-BERT, a hybrid model that combines contextual language representations from BERT with global semantic information captured through a Vocabulary Graph Convolutional Network (VGCN).

The project is developed as part of an undergraduate thesis (Tugas Akhir) in Informatics and focuses on multi-label personality prediction based on the OCEAN (Big Five) personality model.

## Project Overview
Personality prediction from text is an important task in computational psychology and human-centered AI. Traditional approaches often rely on local textual representations and fail to capture global semantic relationships between words.

## Personality Model
The classification task is based on the Big Five Personality Traits (OCEAN): Openness to Experience, Conscientiousness, Extraversion, Agreeableness, Neuroticism. Each essay may be associated with multiple traits simultaneously, making this a multi-label classification problem.

## Dataset
Dataset: Essays-Big5

Source: Publicly available personality essay dataset

Size: 2,467 English essays

Labels: Binary labels for each of the five Big Five traits

The dataset is relatively balanced across traits and is widely used as a benchmark for personality prediction from text.

## Methodology
