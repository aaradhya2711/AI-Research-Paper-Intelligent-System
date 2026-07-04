# AI Research Paper Intelligent System using NLP, Transformers, and Semantic Search

## Project Overview

Research papers are growing rapidly in every field, making it difficult for researchers and students to find relevant papers and understand them efficiently. The goal of this project is to build an intelligent system that can not only retrieve relevant research papers but also help users understand their content through summarization, keyword extraction, and named entity recognition.

This project combines Natural Language Processing (NLP), Transformer models, and Semantic Search techniques to create an end-to-end research paper analysis system.


## Problem Statement

Finding relevant research papers from thousands of available papers is often time-consuming. Reading long abstracts and identifying important information manually can also be challenging.

This project addresses these challenges by providing:

- Semantic search for finding similar research papers.
- Automatic summarization of research paper abstracts.
- Extraction of important keywords and phrases.
- Identification of technical entities from research papers.


## Dataset

The project uses the **ML-ArXiv Papers Dataset** available on Hugging Face.

The dataset contains:

- Research Paper Titles
- Research Paper Abstracts

Dataset Link: https://huggingface.co/datasets/CShorten/ML-ArXiv-Papers


## Features Implemented

### 1. Data Preprocessing
- Loaded the ML-ArXiv Papers dataset.
- Selected the title and abstract columns.
- Combined both columns into a single `paper_text` field.
- Cleaned the text by removing newline characters and unnecessary spaces.

### 2. Semantic Embeddings using Sentence Transformers
- Used the `all-MiniLM-L6-v2` Sentence Transformer model.
- Converted research papers into dense vector embeddings.
- Generated embeddings for approximately 15,000 research papers.

### 3. Similarity Measurement
- Used Cosine Similarity to measure semantic similarity between research papers.
- Compared embeddings to understand how closely related two papers are.

### 4. Semantic Search using FAISS
- Used FAISS (Facebook AI Similarity Search) for efficient vector search.
- Stored embeddings inside a FAISS index.
- Retrieved the top-k most relevant research papers for a given user query.

Example Query:

```python
search_paper("deep learning for medical image analysis")
```

### 5. Research Paper Summarization
- Implemented abstractive summarization using the `facebook/bart-large-cnn` model.
- Generated concise summaries of research paper abstracts.
- Built a function that searches and summarizes the retrieved papers.

Example:

```python
search_and_summarize("Deep learning in medical imaging", k=5)
```

### 6. Keyword Extraction using KeyBERT
- Used KeyBERT to extract important keywords and key phrases from research papers.
- Generated both single-word and multi-word key phrases.

Example Output:

- tomographic imaging deep
- medical imaging
- deep learning

### 7. Named Entity Recognition (NER)

To make the project more informative, three different approaches for Named Entity Recognition were implemented.

#### Approach 1: Custom Technical NER using spaCy EntityRuler

A rule-based Named Entity Recognition system was developed using spaCy's `EntityRuler`.

This approach identifies technical entities such as:

- Python → PROGRAMMING_LANGUAGE
- FastAPI → FRAMEWORK
- TensorFlow → LIBRARY
- PyTorch → LIBRARY
- BERT → MODEL
- GPT → MODEL
- FAISS → VECTOR_DATABASE
- spaCy → LIBRARY

This approach was useful for recognizing domain-specific technical entities that are usually not detected by traditional NER models.

#### Approach 2: Named Entity Recognition using Zero-Shot Classification and Transformers

A transformer-based approach was implemented using `facebook/bart-large-mnli`.

This approach:

- Extracts entities and noun phrases from text.
- Uses Zero-Shot Classification to automatically assign labels.
- Predicts entity categories without manually defining patterns.

The entities are classified into categories such as:

- PROGRAMMING_LANGUAGE
- FRAMEWORK
- LIBRARY
- MODEL
- METHOD
- APPLICATION
- TASK
- VECTOR_DATABASE

This approach is more flexible than rule-based NER because it can infer categories for previously unseen entities. However, its predictions may sometimes be less accurate for highly technical terms.


#### Approach 3: Hybrid Named Entity Recognition for Technical Entity Extraction

A hybrid NER approach was developed by extending spaCy's `EntityRuler` with a larger set of domain-specific technical patterns.

This approach recognizes:

- Programming Languages
- Frameworks
- Libraries
- Models
- Methods
- Applications
- Tasks
- Vector Databases

Example entities extracted:

- Sentence Transformers → LIBRARY
- KeyBERT → LIBRARY
- semantic similarity search → METHOD
- medical image analysis → APPLICATION
- Named Entity Recognition → METHOD
- The Semantic Research Paper Search Engine → APPLICATION

This approach provided more accurate and domain-specific technical entity extraction by extending rule-based NER with a broader set of technical patterns and entities.

## Technologies Used

- Python
- Pandas
- NumPy
- Sentence Transformers
- FAISS
- Hugging Face Transformers
- KeyBERT
- spaCy
- Scikit-Learn


## Project Workflow

```text
Research Paper Dataset
          ↓
Text Preprocessing
          ↓
Sentence Transformer Embeddings
          ↓
FAISS Semantic Search
          ↓
Top Relevant Papers
          ↓
Research Paper Summarization
          ↓
Keyword Extraction
          ↓
Named Entity Recognition
```


## Project Structure

```text
AI-Research-Paper-Intelligent-System
│
├── AI_Research_Paper_Intelligent_System.ipynb
├── README.md
├── requirements.txt
```


## Note

The `paper_embeddings.npy` and `paper_faiss.index` files have not been uploaded to this repository due to GitHub file size limitations.
These files are automatically generated during the execution of the notebook and can be recreated by running the project from the beginning.


## Key Learnings

This project helped me understand how different NLP techniques can be integrated to build an end-to-end intelligent system. Through this project, I gained practical experience in:

- Sentence Embeddings
- Semantic Search
- Vector Databases using FAISS
- Transformer-based Summarization
- Keyword Extraction
- Rule-based Named Entity Recognition
- Zero-Shot Entity Classification
- Hybrid Technical Entity Extraction
- Building complete NLP pipelines


## Future Scope

- Develop a web application using Streamlit or FastAPI.
- Allow users to upload and analyze their own research papers.
- Implement paper recommendation systems.
- Add paper comparison and citation generation features.
- Improve technical entity extraction using domain-specific transformer models and knowledge graphs.


## Author

**Aaradhya Chauhan**  
B.Tech Computer Science Engineering  
Interested in Machine Learning, Artificial Intelligence, and Data Analytics.


## Acknowledgement

This project was developed as part of my learning journey in Natural Language Processing and helped me understand how modern NLP and Transformer-based techniques can be applied to solve real-world information retrieval problems.
