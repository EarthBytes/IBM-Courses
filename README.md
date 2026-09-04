# IBM AI Engineering

Coursework and projects from IBM. This repository showcases the final projects of these courses. 

## Courses

### Machine Learning with Python — IBM (85.95%)

Built a foundation in machine learning using Python and scikit-learn, covering supervised and unsupervised learning, model evaluation, and hyperparameter tuning. Applied these techniques to a rainfall prediction project that walks through the full ML workflow: data loading and exploration, feature preprocessing with pipelines, model training, cross-validation, and performance analysis.

**Project:** [`ML-Python/RainfallPredictionClassifier.ipynb`](ML-Python/RainfallPredictionClassifier.ipynb)

### Generative AI Applications with RAG and LangChain — IBM (88%)

Part of the IBM course where I achieved 88%, building an end-to-end RAG-based question-answering application. Developed document ingestion and chunking pipelines, generated embeddings using IBM watsonx models, stored them in Chroma DB, and implemented retrieval with LangChain's `RetrievalQA` chain. The system is integrated into an interactive Gradio interface for uploading PDFs and asking natural-language questions.

**Project:** [`GenAI-RAG-LangChain/qabot.py`](GenAI-RAG-LangChain/qabot.py)

## RAG QA Bot

The chatbot in `GenAI-RAG-LangChain/` follows a standard RAG pipeline:

1. **Load** — PDF documents via LangChain's `PyPDFLoader`
2. **Split** — text into chunks with `RecursiveCharacterTextSplitter`
3. **Embed** — chunks using IBM watsonx (`ibm/granite-embedding-278m-multilingual`)
4. **Store** — embeddings in a Chroma vector database
5. **Retrieve** — relevant chunks via similarity search
6. **Generate** — answers using `RetrievalQA` with the watsonx LLM (`ibm/granite-4-h-small`)
7. **Serve** — through a Gradio web UI on port 7860

### Running locally

```bash
cd GenAI-RAG-LangChain
python3.11 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python qabot.py
```

Open `http://localhost:7860`, upload a PDF, and ask a question.

> **Note:** The app is designed for the IBM Skills Network Cloud IDE where watsonx credentials are provided automatically. Running locally requires a `WATSONX_APIKEY` environment variable and a watsonx project ID.
