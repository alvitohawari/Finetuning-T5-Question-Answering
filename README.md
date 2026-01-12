# Fine-tuning T5 for Question Answering

## 👥 Team Information
**Course**: Deep Learning  
**Institution**: Telkom University  

| Name | NIM |
|------|-----|
| Alvito Kiflan Hawari | 1103220235 |
| Nafal Rifky Atsilah Maulana | 1103223106 |

---

## 🎯 Purpose
This repository contains the implementation of a project focused on **Question Answering (QA)**.

The objective of this project is to fine-tune a pre-trained **T5 (Text-to-Text Transfer Transformer)** model to perform **extractive question answering**.  
Given a context paragraph and a question, the model learns to generate the correct answer span from the text.

---

## 🔍 Project Overview

### The Task: Question Answering
We utilize the **SQuAD (Stanford Question Answering Dataset)**, a reading comprehension dataset consisting of questions posed by crowdworkers on a collection of Wikipedia articles.

### The Model: Google T5-base with Prefix-Tuning
- **Architecture**: Encoder-Decoder Transformer (Seq2Seq)
- **Approach**: Question Answering is treated as a **text-generation task**, where:
  - **Input**:  
    ```
    question: <question> context: <context>
    ```
  - **Output**:  
    ```
    <answer>
    ```
- **Fine-tuning Strategy**: This project employs **Prefix-Tuning**, which adapts the model by training only a small set of prefix tokens while keeping the base T5 model frozen. This approach is parameter-efficient and reduces training cost.

### The Dataset: SQuAD
- **Input**: Context paragraph and corresponding question
- **Output**: Exact answer span extracted from the context
- **Dataset Size Used**:
  - 10,000 training samples
  - 1,000 validation samples

---

## 📊 Technical Approach

### Model Configuration
- **Base Model**: `google/t5-base`
- **Tokenizer**: `T5TokenizerFast` (SentencePiece-based)
- **Framework**: PyTorch & Hugging Face Transformers
- **Fine-tuning Method**: Prefix-Tuning (only prefix tokens are trainable)

### Training Configuration
- **Batch Size**: 8
- **Learning Rate**: 5e-4
- **Epochs**: 5
- **Optimizer**: AdamW
- **Scheduler**: Linear learning rate schedule with warmup
- **Gradient Clipping**: Maximum norm of 1.0

---

## 📁 Repository Structure

