# Knowledge Base Retrieval and Question-Answering System with Evaluation

## Overview

This project implements a Knowledge Base (KB) Retrieval and Question-Answering (QA) system using a JSON-based dataset and evaluates the generated answers using metrics like **ROUGE-L** and **BERTScore**. The system performs the following:

1. **Knowledge Base Setup**: Loads and preprocesses a JSON dataset containing URLs, titles, and text.
2. **Question Retrieval**: Uses **TF-IDF Vectorization** and **Cosine Similarity** to rank and retrieve top-relevant knowledge base entries for a user-provided question.
3. **Answer Generation**: Employs the **Google Gemini API** to generate answers based on the retrieved entries.
4. **Evaluation**:
   - **ROUGE-L**: Measures sentence-level coherence and structural similarity.
   - **BERTScore**: Evaluates factual consistency by leveraging semantic embeddings.

## Features

- **Efficient Retrieval**: Utilizes TF-IDF and Cosine Similarity to find relevant entries for user queries.
- **Generative Answering**: Integrates Google Gemini API to provide contextually accurate and coherent answers.
- **Evaluation Framework**: Uses advanced metrics (ROUGE-L and BERTScore) to evaluate answer quality.
- **Scalable**: Handles large JSON datasets and supports complex queries.

---

## Prerequisites

### Libraries and Dependencies
Install the required libraries using the following command:
```bash
pip install pandas scikit-learn google-generativeai rouge-score bert-score
```

### Files
Ensure the following files are available:
1. `Clearfeed_kb.json`: JSON file containing the knowledge base.
2. `clearfeed_qa_pairs.csv`: CSV file containing QA pairs for evaluation (optional).

Update the file paths in the script as needed.

---

## Usage

### Step 1: Knowledge Base Preparation
The script:
1. Loads the `Clearfeed_kb.json` dataset.
2. Flattens the JSON data into a pandas DataFrame with columns: `url`, `title`, `text`.
3. Combines `title` and `text` into a `content` column for TF-IDF processing.

### Step 2: Question Retrieval
1. Initialize the **TF-IDF Vectorizer**.
2. Compute similarity scores using **Cosine Similarity**.
3. Retrieve the top 5 most relevant URLs and titles for the user question.

### Step 3: Answer Generation
The **Google Gemini API**:
1. Takes the user question and retrieved entries as input.
2. Constructs a context-based prompt.
3. Generates an answer using the **gemini-1.5-flash** model.

### Step 4: Evaluation
The script evaluates the generated answers using two metrics:
1. **ROUGE-L**: Compares the generated answer with the top-retrieved content.
2. **BERTScore**: Assesses factual consistency between the generated answer and the reference content.

---

## Code Execution
1. Place the required files (`Clearfeed_kb.json` and others) in the appropriate directory.
2. Run the script in a Jupyter Notebook or Python environment.
3. Follow the prompts to input a question and receive generated answers.

---

## Example Execution

### Input
```plaintext
Enter your question: What is the process for integrating Clearfeed with Slack?
```

### Output
```plaintext
Top 5 URLs:
1) https://example.com/integrations/slack
2) https://example.com/docs/slack-setup
3) https://example.com/guides/slack-integration
4) https://example.com/tutorials/slack-clearfeed
5) https://example.com/faq/slack-integration

Generated Answer:
To integrate Clearfeed with Slack, follow these steps: ...
```

### Evaluation
```plaintext
ROUGE-L Score: 0.85
Factual Consistency (BERTScore F1): 0.92
```

---

## Key Concepts and Methodologies

1. **TF-IDF Vectorization**:
   - Converts text into numerical vectors for similarity computation.
   - Emphasizes unique, meaningful terms in documents.

2. **Cosine Similarity**:
   - Measures similarity between vectors, ranking documents by relevance.

3. **Google Gemini API**:
   - Generates contextual, natural language responses from the knowledge base.

4. **ROUGE-L**:
   - Evaluates linguistic and structural similarity.

5. **BERTScore**:
   - Ensures semantic consistency by comparing embeddings.

---

## Configuration

### Google Gemini API Key
Update the API key in the script:
```python
GEMINI_API_KEY = "YOUR_API_KEY"
```

### File Paths
Update paths for input files:
```python
KB_FILE = '/path/to/Clearfeed_kb.json'
EVAL_FILE = '/path/to/clearfeed_qa_pairs.csv'
```

---

## Limitations and Future Improvements

1. **Dependency on Gemini API**: Requires a valid API key for operation.
2. **Knowledge Base Size**: Large datasets may impact retrieval speed.
3. **Evaluation Metrics**: While ROUGE-L and BERTScore are robust, additional metrics could enhance evaluation.

### Future Enhancements
- Incorporate **fine-tuning** of the retrieval system.
- Optimize for **real-time querying** with larger datasets.
- Add support for multi-language queries and datasets.

---

## License
This project is open-source and distributed under the MIT License.

---

## Contact
For questions or issues, please contact the author via [GitHub](https://github.com/yug-sinha).
