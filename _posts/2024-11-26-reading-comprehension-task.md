
# Exploring Machine Reading Comprehension with RoBERTa, ChatGPT, and Claude 3.5 Sonnet

A **machine reading comprehension (MRC)** task involves teaching a machine to understand and answer questions about a given text or passage. It's a key challenge in natural language processing (NLP) and plays an essential role in applications like question answering systems, chatbots, and search engines.

### Types of MRC Tasks
1. **Extractive Question Answering**
   - The answer is a substring of the provided text.
   - Example:
     - Passage: "The Eiffel Tower is located in Paris."
     - Question: "Where is the Eiffel Tower located?"
     - Answer: "Paris"

2. **Abstractive Question Answering**
   - The answer is not a direct substring but is generated based on understanding the text.
   - Example:
     - Passage: "The Eiffel Tower stands tall in the heart of Paris, France."
     - Question: "Where is the Eiffel Tower located?"
     - Answer: "The Eiffel Tower is in Paris, France."

3. **Multiple Choice Question Answering**
   - The model selects the correct answer from a set of options.
   - Example:
     - Passage: "Paris is the capital of France."
     - Question: "What is the capital of France?"
     - Options: (A) Berlin, (B) Madrid, (C) Paris, (D) Rome
     - Answer: (C) Paris

4. **Yes/No or Boolean Question Answering**
   - The model answers with a simple "Yes" or "No."
   - Example:
     - Passage: "The Eiffel Tower is located in Paris."
     - Question: "Is the Eiffel Tower in Paris?"
     - Answer: "Yes"

5. **Cloze-style Tasks**
   - Fill-in-the-blank tasks where the answer is missing from the passage.
   - Example:
     - Passage: "The Eiffel Tower is located in _____"
     - Answer: "Paris"

6. **Open-Domain Question Answering**
   - The passage is not given; the model retrieves relevant text from a large corpus and then answers the question.


### Popular Datasets for MRC
- **SQuAD (Stanford Question Answering Dataset):** Extractive QA with human-annotated answers.
- **Natural Questions (NQ):** Real-world questions answered with passages from Wikipedia.
- **MS MARCO:** Passage ranking and MRC tasks based on Bing search queries.
- **HotpotQA:** Multi-hop reasoning questions requiring information from multiple passages.
- **TriviaQA:** QA over trivia-style questions and long documents.


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

#### **Data Preparation**
- **Dataset:** SQuAD 2.0.
- **Steps Taken:**
  - Downloading the dataset using Hugging Face.
  - Selecting 15 question-answer pairs.
  - Extracting basic statistics:
    - Context lengths (max/average/min).
    - Question lengths (max/average/min).
    - Answer lengths (max/average/min).

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

---

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

