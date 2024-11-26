
# Exploring Machine Reading Comprehension with RoBERTa, ChatGPT, and Claude 3.5 Sonnet

# Popular Datasets for MRC
- **[SQuAD (Stanford Question Answering Dataset)](https://rajpurkar.github.io/SQuAD-explorer/):**  
  Extractive QA with human-annotated answers.  
  - GitHub: [stanfordnlp/stanford-question-answering-dataset](https://github.com/stanfordnlp/stanford-question-answering-dataset)
- **[Natural Questions (NQ)](https://ai.google.com/research/NaturalQuestions/):**  
  Real-world questions answered with passages from Wikipedia.  
  - GitHub: [google-research-datasets/natural-questions](https://github.com/google-research-datasets/natural-questions)
- **[MS MARCO](https://microsoft.github.io/msmarco/):**  
  Passage ranking and MRC tasks based on Bing search queries.  
  - GitHub: [microsoft/MSMARCO-Passage-Ranking](https://github.com/microsoft/MSMARCO-Passage-Ranking)
- **[HotpotQA](https://hotpotqa.github.io/):**  
  Multi-hop reasoning questions requiring information from multiple passages.  
  - GitHub: [hotpotqa/hotpot](https://github.com/hotpotqa/hotpot)
- **[TriviaQA](http://nlp.cs.washington.edu/triviaqa/):**  
  QA over trivia-style questions and long documents.  
  - GitHub: [allenai/triviaqa](https://github.com/allenai/triviaqa)

# **Data Preparation**
- **Dataset:** SQuAD 2.0.
- **Steps Taken:**
  - Downloading the dataset using Hugging Face.
  ```py
  ```
  - Selecting 15 question-answer pairs.
   ```py
  ```

  - Extracting basic statistics:
    - Context lengths (max/average/min).
    - Question lengths (max/average/min).
    - Answer lengths (max/average/min).
 ```py
  ```

A **machine reading comprehension (MRC)** task involves teaching a machine to understand and answer questions about a given text or passage. It's a key challenge in natural language processing (NLP) and plays an essential role in applications like question answering systems, chatbots, and search engines.

### Types of MRC Tasks
1. **Extractive Question Answering**
2. **Abstractive Question Answering**
3. **Multiple Choice Question Answering**
4. **Yes/No or Boolean Question Answering**
5. **Cloze-style Tasks**
6. **Open-Domain Question Answering**

### Approaches for MRC
1. **Pre-trained Language Models**
   - Models like **BERT**, **RoBERTa**, **ALBERT**, and **GPT** have transformed MRC by leveraging contextual embeddings.
   - Example: Fine-tune BERT for the SQuAD dataset.
2. **Span Prediction Models**
   - Identify the start and end of the answer span within the passage.
3. **Sequence-to-Sequence Models**
   - Used for abstractive tasks where answers are generated (e.g., T5, BART).
4. **Neural Architecture Enhancements**
   - Techniques like attention mechanisms, multi-hop reasoning, and pointer networks improve comprehension and answer generation.

#### **Using Models for Question Answering**
- **RoBERTa**
  - Brief setup process.
  - Key outputs: start/end indices, predicted tokens, and decoded answers.
- **ChatGPT**
  - Prompt design process.
  - Summary of outputs (answers and reasoning).
- **Claude 3.5 Sonnet**
  - Reusing prompts from ChatGPT.
  - Key differences in outputs (if any).

#### **Results and Analysis**
- **Manual Evaluation:**
  - Correctness scores for each model.
  - Observations on accuracy and performance.

- **Model Comparisons:**
  - Brief discussion on:
    - Which model performed best.
    - Notable strengths and weaknesses.

- **Example Comparisons:**
  - Two sample cases with:
    - Ground truth.
    - Outputs from each model.
    - Observations and insights.

---

#### **Self-Reflection**
- What I learned from this experiment.
- Areas for improvement in the pipeline or methodology.

---

#### **Conclusion**
- Summary of the experiment.
- Key takeaways on MRC with pre-trained and large language models.

---

#### **Appendix (Optional)**
- Code snippets for RoBERTa implementation.
- Example prompts used for ChatGPT and Claude 3.5 Sonnet.
- Links to dataset and resources.

---

Here are some quality-of-life repositories and tools related to machine reading comprehension (MRC) development, including pre-trained models, evaluation utilities, and data loaders:

---

# Quality of Life Repositories for MRC Development

### 1. **Hugging Face Transformers**
   - **Description:** Provides pre-trained models and tokenizers for SQuAD, MS MARCO, and other QA tasks.
   - **GitHub:** [huggingface/transformers](https://github.com/huggingface/transformers)
   - **Why it's useful:**
     - Pre-trained models for fine-tuning (e.g., BERT, RoBERTa, T5).
     - Ready-to-use pipelines for extractive and generative QA.
     - Compatible with PyTorch and TensorFlow.

---

### 2. **Haystack**
   - **Description:** Framework for building search systems and QA pipelines.
   - **GitHub:** [deepset-ai/haystack](https://github.com/deepset-ai/haystack)
   - **Why it's useful:**
     - Easy integration of retriever-reader pipelines.
     - Supports datasets like SQuAD and Natural Questions.
     - Works with Elasticsearch, FAISS, or Weaviate for retrieval tasks.

---

### 3. **jiant**
   - **Description:** An NLP toolkit for multitask and transfer learning.
   - **GitHub:** [nyu-mll/jiant](https://github.com/nyu-mll/jiant)
   - **Why it's useful:**
     - Streamlines model training for multiple NLP tasks, including QA.
     - Includes data pre-processing, tokenization, and evaluation utilities.

---

### 4. **DeepPavlov**
   - **Description:** A conversational AI and MRC library with pre-trained QA models.
   - **GitHub:** [deepmipt/DeepPavlov](https://github.com/deepmipt/DeepPavlov)
   - **Why it's useful:**
     - Ready-to-use pipelines for MRC tasks.
     - Offers tools for building end-to-end dialogue systems.

---

### 5. **Simple Transformers**
   - **Description:** A user-friendly wrapper around Hugging Face Transformers for various NLP tasks.
   - **GitHub:** [ThilinaRajapakse/simpletransformers](https://github.com/ThilinaRajapakse/simpletransformers)
   - **Why it's useful:**
     - Simplifies fine-tuning for SQuAD and other QA datasets.
     - Minimal code required for training and evaluation.

---

### 6. **TextFlint**
   - **Description:** A unified multilingual robustness toolkit for NLP models.
   - **GitHub:** [flint-nlp/textflint](https://github.com/flint-nlp/textflint)
   - **Why it's useful:**
     - Stress-tests QA models by introducing adversarial examples.
     - Enhances robustness evaluation and error analysis.

---

### 7. **SquadRunner**
   - **Description:** A utility to simplify experimentation with the SQuAD dataset.
   - **GitHub:** [robertsdionne/SquadRunner](https://github.com/robertsdionne/SquadRunner)
   - **Why it's useful:**
     - Pre-built scripts for downloading, preparing, and evaluating SQuAD.
     - Supports fine-tuning of models on SQuAD v1.1 and v2.0.

---

### 8. **AllenNLP**
   - **Description:** A research library for deep learning in NLP.
   - **GitHub:** [allenai/allennlp](https://github.com/allenai/allennlp)
   - **Why it's useful:**
     - Built-in modules for extractive QA tasks like SQuAD.
     - Tools for model interpretation, debugging, and visualization.

---

### 9. **Open-Domain Question Answering (ODQA) Benchmark**
   - **Description:** A toolkit for running open-domain QA experiments.
   - **GitHub:** [facebookresearch/DPR](https://github.com/facebookresearch/DPR)
   - **Why it's useful:**
     - Implements Dense Passage Retrieval for QA.
     - Provides training data and scripts for retriever-reader pipelines.

---

### 10. **MRC Utilities**
   - **Description:** Tools for evaluation, data preparation, and benchmarking.
   - **GitHub:** [openai/mrc-tools](https://github.com/openai/mrc-tools)
   - **Why it's useful:**
     - Metrics calculators (e.g., EM, F1).
     - Scripts for converting datasets into MRC formats.

---

Let me know if you'd like help with setting up any of these repositories or integrating them into your workflow!
