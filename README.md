# 🚀 RAG PDF Analyzer

> Upload PDFs and ask questions using AI - powered by local embeddings and Google Gemini

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## ✨ Features

- 🔥 **Local Embeddings** - No API quota issues for PDF uploads
- 🤖 **Google Gemini AI** - Intelligent question answering
- ⚡ **Fast Processing** - No network delays for document processing
- 💾 **Offline Mode** - Process PDFs completely offline
- 📊 **Multi-Document Support** - Upload and query multiple PDFs simultaneously

## 🎯 Why This Project?

Traditional RAG systems hit API rate limits quickly because they call the API for every chunk during PDF upload. This project solves that by:

- Using **local sentence-transformers** for embeddings (runs on your PC)
- Only calling Gemini API for **question answering** (1 call per question)
- Reducing API usage by **90%+**

| Task | Traditional RAG | This Project |
|------|----------------|--------------|
| Upload 10-page PDF | 20-30 API calls ❌ | 0 API calls ✅ |
| Ask a question | 1 API call ✅ | 1 API call ✅ |

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- Google Gemini API key ([Get one free](https://aistudio.google.com/app/apikey))

### Installation

```bash
pip install sentence-transformers langchain langchain-community langchain-google-genai langchain-classic google-generativeai faiss-cpu PyPDF2 langchain-text-splitters langchain-core torch
```

Or use the requirements file:

```bash
pip install -r requirements.txt
```

### Usage

1. **Open the notebook**

   ```bash
   jupyter notebook RAG_PDF_Analyzer.ipynb
   ```

   Or use [Google Colab](https://colab.research.google.com/)

2. **Set your API key** (Step 2 in notebook)

   ```python
   os.environ['GOOGLE_API_KEY'] = 'YOUR_API_KEY_HERE'
   ```

3. **Upload a PDF** (Step 7)

   ```python
   rag = RAGEngine()
   doc_id = rag.add_document("your_file.pdf", "My Document")
   ```

4. **Ask questions** (Step 8)

   ```python
   result = rag.query("What is the main topic?")
   print(result['answer'])
   ```

## 📖 How It Works

```mermaid
graph LR
    A[PDF Upload] --> B[Extract Text]
    B --> C[Split into Chunks]
    C --> D[Local Embeddings]
    D --> E[FAISS Vector Store]
    E --> F[Ask Question]
    F --> G[Search Locally]
    G --> H[Send to Gemini]
    H --> I[Get Answer]
```

1. **PDF Upload** → Extracts text and splits into chunks
2. **Local Embeddings** → Converts chunks to vectors using sentence-transformers (runs on your PC)
3. **FAISS Storage** → Stores vectors in memory for fast similarity search
4. **Question Answering** → Searches locally, sends relevant chunks to Gemini (1 API call)

## 🛠️ Technical Stack

- **Embeddings**: `sentence-transformers` (all-MiniLM-L6-v2)
- **Vector Store**: FAISS (Facebook AI Similarity Search)
- **LLM**: Google Gemini 2.5 Flash
- **PDF Processing**: PyPDF2
- **Framework**: LangChain

## 📊 Performance

- **Upload Speed**: ~2 seconds for 10-page PDF
- **Query Speed**: ~3-5 seconds per question
- **API Usage**: 0 calls for upload, 1 call per question
- **Model Size**: ~90MB (one-time download)

## ⚠️ Troubleshooting

### "429 RESOURCE_EXHAUSTED" error

This only affects Q&A, not uploads. Solutions:
- Wait 24 hours for quota reset
- Use a different API key
- Upgrade to paid tier

### Model download fails

First-time setup downloads ~100MB embedding model. Ensure:
- Stable internet connection
- Sufficient disk space
- No firewall blocking downloads

### PDF has no extractable text

Your PDF might be:
- Scanned images (needs OCR)
- Password protected
- Corrupted

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest features
- Submit pull requests



## 🙏 Acknowledgments

- [LangChain](https://github.com/langchain-ai/langchain) for the RAG framework
- [Sentence Transformers](https://www.sbert.net/) for local embeddings
- [Google Gemini](https://ai.google.dev/) for the LLM API
- [FAISS](https://github.com/facebookresearch/faiss) for vector similarity search

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

**Made with ❤️ using Local Embeddings + Google Gemini**
