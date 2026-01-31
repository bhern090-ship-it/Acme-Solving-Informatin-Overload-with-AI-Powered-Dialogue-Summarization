# Acme – Solving Information Overload with AI-Powered Dialogue Summarization

## Problem Statement and Business Context

Modern messaging platforms generate large volumes of conversational data, making it difficult for users to quickly understand key information from long group chats. This information overload reduces productivity and engagement.

This project presents an AI-powered dialogue summarization system developed as a proof of concept for Acme Communications. The goal is to automatically condense multi-speaker chat conversations into concise, readable summaries using transformer-based large language models.

---

## Project Overview

This project builds an end-to-end machine learning pipeline for abstractive text summarization using the SAMSum dataset and a transformer-based encoder-decoder architecture.

The system:
- Processes raw conversational text
- Fine-tunes a pretrained transformer model
- Generates concise summaries of dialogues
- Evaluates performance using ROUGE metrics
- Saves the trained model for future inference

---

## Dataset

- Dataset: SAMSum Corpus
- Description: Messenger-style conversations with human-written summaries
- Splits:
  - Training: ~14,700 examples
  - Validation: ~800 examples
  - Test: ~800 examples

The dataset is loaded and managed using the Hugging Face `datasets` library.

---

## Technical Approach

### Model Architecture

- Model: facebook/bart-base
- Architecture: Encoder–Decoder Transformer
- Purpose:
  - Encoder learns contextual representations of dialogue
  - Decoder generates fluent abstractive summaries

BART is well-suited for summarization tasks due to its sequence-to-sequence pretraining objectives.

---

### Data Processing

- Tokenization using Hugging Face AutoTokenizer
- Truncation and padding for consistent batch sizes
- Label masking to ignore padded tokens during loss calculation

---

### Training Strategy

- Framework: Hugging Face Trainer
- Training epochs: 1 (CPU-only constraint)
- Gradient accumulation to simulate larger batch sizes
- Periodic evaluation during training

---

## Evaluation and Results

### Quantitative Evaluation

Model performance is evaluated using ROUGE metrics:
- ROUGE-1: Unigram overlap
- ROUGE-2: Bigram overlap
- ROUGE-L: Longest common subsequence

These metrics compare model-generated summaries with reference summaries written by humans.

---

### Qualitative Evaluation

Manual inspection of sample outputs shows that the model:
- Produces shorter, more concise summaries
- Captures the main intent of conversations
- Performs abstractive summarization rather than copying text

Some inaccuracies remain due to limited training time and computational constraints.

---

## Visualization and Analysis

The notebook includes visualizations for:
- Dataset split distribution
- Summary length comparison between reference and generated summaries
- Qualitative example outputs

These visual analyses confirm that the model learns meaningful summarization behavior.

---

## Limitations

- Training performed on CPU only
- Single training epoch
- Limited hyperparameter tuning
- ROUGE metrics do not fully capture semantic quality

Despite these limitations, the model demonstrates effective summarization capabilities.

---

## Future Improvements

Possible extensions include:
- GPU-based training
- Additional training epochs
- Hyperparameter optimization
- Larger pretrained models (e.g., bart-large-cnn)
- Semantic evaluation metrics such as BERTScore
- Deployment as a web or API-based service

---

## Business Impact

This solution helps address information overload by enabling users to quickly understand long conversations. It demonstrates how transformer-based language models can be applied to real-world business problems involving large-scale textual data.

---

## Reproducibility Instructions

### Install Dependencies
```bash
pip install transformers datasets evaluate torch matplotlib seaborn

