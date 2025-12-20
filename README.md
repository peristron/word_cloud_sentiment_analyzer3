# 🧠 The Unstructured Data Intel Engine
### Multi-File Word Cloud, Network Graph & Bayesian Analyzer

This is a local-first, Streamlit-based application designed to extract context, meaning, and hidden structure from "dirty" unstructured data. It moves beyond simple word counting by employing **Network Graph Theory**, **Bayesian Inference**, and **Generative AI** to turn raw text into qualitative insights.

## 🚀 Key Features

### 1. 📥 Universal Input Support
*   **File Formats:** CSV, Excel (XLSX/XLSM), JSON, PDF, PPTX (PowerPoint), VTT (Transcripts), and TXT.
*   **Web Scraping:** Enter URLs to automatically scrape and process visible text.
*   **Manual Entry:** Paste raw text directly for quick analysis.
*   **Large File Support:** Optimized streaming for processing large datasets.

### 2. 🔍 Bayesian Topic Modeling (LDA & NMF)
Discover hidden themes in your data without reading every line. The app creates a Document-Term Matrix and applies your choice of probabilistic modeling:
*   **LDA (Latent Dirichlet Allocation):** Best for "Mixed" content like essays or assignments. Assumes documents are mixtures of various topics.
*   **NMF (Non-negative Matrix Factorization):** Best for "Distinct" content like chat logs or short feedback. Uses linear algebra to force words into sharp, distinct categories.

### 3. 🕸️ Network Graph & Community Detection
*   **Concept Mapping:** visualizes how words connect (Bigrams). If "Battery" connects to "Drain," a physical link is drawn.
*   **Community Detection:** Algorithms automatically color-code clusters of words that appear together frequently (e.g., separating "Login Issues" from "Billing Issues").
*   **Physics Simulation:** Interactive, drag-and-drop graph to analyze node centrality.

### 4. ⚖️ Bayesian Sentiment Inference
*   **Beyond Averages:** Instead of simply reporting "60% Positive," the app uses a **Beta-Binomial Conjugate Prior** model.
*   **Credible Intervals:** Calculates a 95% High Density Interval (e.g., "We are 95% confident the true sentiment is between 55% and 65%"). This is crucial for small or noisy datasets.

### 5. 🤖 Generative AI Analyst
*   **Synthesized Insights:** Aggregates the statistical data, graph clusters, and frequency lists and sends them to an LLM.
*   **Providers Supported:** OpenAI (GPT-4o) and xAI (Grok).
*   **Output:** Returns a qualitative narrative identifying root causes, themes, and anomalies.

---

## 🛠️ Installation & Setup

1.  **Clone or Download** this repository.
2.  **Install Requirements:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: This installs scientific libraries like `scikit-learn`, `scipy`, and `networkx`)*.
3.  **Run the App:**
    ```bash
    streamlit run app.py
    ```

## ⚙️ Configuration

### AI Access
To use the Generative AI features, you will need an API Key from either **OpenAI** or **xAI**.
*   You can enter these in the Sidebar UI securely.
*   Alternatively, you can pre-configure them in `.streamlit/secrets.toml`:
    ```toml
    [secrets]
    auth_password = "your_admin_password" # Optional: to lock AI features
    openai_api_key = "sk-..."
    xai_api_key = "..."
    ```

### NLP Settings
The app includes a robust cleaning engine configurable via the Sidebar:
*   **Stopwords:** Custom comma-separated list + Toggle for Prepositions.
*   **Cleaning:** Remove HTML, Chat Artifacts (timestamps), URLs, and Integers.
*   **Model Selection:** Toggle between LDA and NMF in the "Performance Options" tab.

---

## 📘 How to choose your Model?

When using the **Bayesian Theme Discovery** feature, use this guide:

| Model | Best For... | Why? |
| :--- | :--- | :--- |
| **LDA** | **Essays, Assignments, Research** | Finds "Mixtures." An essay on History might be 40% Politics, 30% War, 30% Economy. LDA captures this nuance. |
| **NMF** | **Chat Logs, Support Tickets, Feedback** | Finds "Categories." A support ticket is usually about ONE thing (e.g., "Password Reset"). NMF separates these sharply. |

---

## 🔒 Privacy Note
This application processes data locally (or on the server where you deploy it). However, if you use the **AI Analysis** feature, summary statistics (top words, graph clusters) are sent to the chosen AI provider (OpenAI or xAI). **Do not upload PII (Personally Identifiable Information) or sensitive proprietary data if using public API endpoints.**

---

## 📦 Dependencies
*   `streamlit` - UI Framework
*   `pandas` - Data Manipulation
*   `scikit-learn` - LDA & NMF Modeling
*   `scipy` - Bayesian Statistics (Beta Distribution)
*   `networkx` - Graph Theory
*   `nltk` - Sentiment Analysis
*   `beautifulsoup4` - Web Scraping
*   `python-pptx` / `pypdf` - File Parsing
