# Information Retrieval & Text Mining Engine

##  Project Overview
This project was developed as a comprehensive course and team project for **Data Mining** I got 19.5/20. The primary objective was to build an end-to-end Text Mining and Document Classification pipeline capable of processing unstructured textual data, indexing information for precise retrieval, and applying machine learning architectures for both supervised classification and unsupervised clustering.

The system features a live processing engine integrated with a **FastAPI** backend to expose real-time analysis capabilities externally.

---

##  Technical Architecture & Pipeline

The implementation is divided into distinct operational blocks, moving from raw data ingestion to production-level model evaluations:

### 1. Data Ingestion & API Integration
*   **FastAPI Backend:** Built a lightweight, asynchronous API engine to receive and process real-time text inputs dynamically.
*   **Secure Tunneling:** Leveraged `pyngrok` to establish external endpoints for the backend environment.
*   **File Management:** Automated the extraction and parsing of zipped document corpora into structured Pandas DataFrames.

### 2. Natural Language Processing (NLP) Preprocessing
To clean and prepare raw documents for vector space modeling, a modular preprocessing pipeline was engineered using **NLTK**:
*   **Tokenization & Case Normalization:** Segmented texts into individual word tokens while converting all characters to lowercase.
*   **Noise Reduction:** Stripped out all punctuation and numeric characters.
*   **Stopword Filtering:** Removed standard English stopwords to isolate high-value content words.
*   **Lemmatization:** Applied the `WordNetLemmatizer` to reduce words to their base vocabulary forms (lemmas) for consistency.

### 3. Vector Space Modeling & Indexing (TF-IDF)
*   Transformed clean textual content into a high-dimensional continuous numerical matrix using **TF-IDF (Term Frequency-Inverse Document Frequency)** vectorization via `scikit-learn`.
*   Generated a Term-Document matrix representing the relative statistical weight of unique terms across the entire 30-document corpus.

### 4. Information Retrieval (IR) System
*   Developed a custom search engine implementing **Cosine Similarity** to measure the distance between vectorized user queries and the indexed document corpus.
*   **Evaluation Metrics:** Validated system performance by analyzing **Precision @ 5** and **Recall @ 5** profiles across distinct query categories (Medical vs. Non-Medical).

### 5. Supervised Machine Learning (Classification)
Trained and compared two alternative classification algorithms to predict document labels based on their TF-IDF feature vectors (split into 60% training and 40% testing):
*   **Multinomial Naive Bayes (NB):** Utilized as a probabilistic benchmark classifier.
*   **Decision Tree Classifier (DT):** Used as an alternative deterministic model.
*   **Performance Tracking:** Evaluated both models using overall accuracy scores, detailed classification reports ($Precision$, $Recall$, $F_1\text{-score}$), and visual **Confusion Matrices**.

### 6. Unsupervised Machine Learning (Clustering)
*   **Dimensionality Reduction:** Implemented **Truncated SVD** and **PCA** to compress the high-dimensional sparse TF-IDF space down to dense components.
*   **K-means Clustering:** Partitioned documents into distinct groups without utilizing their true labels, mapping internal patterns directly.
*   **Visual Boundaries:** Plotted document clusters on a 2D coordinate plane with calculated elliptical class boundaries using `matplotlib`.

---

## 💻 Tech Stack & Tools
*   **Core Language:** Python
*   **Web Framework:** FastAPI, Uvicorn, Threading, Pyngrok
*   **Data Analysis:** Pandas, NumPy, Regex
*   **NLP Suite:** NLTK
*   **Machine Learning Library:** Scikit-Learn
*   **Visualization:** Matplotlib
