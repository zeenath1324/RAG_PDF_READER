# 📄 RAG-Based PDF Reader

An AI-powered PDF question-answering application that allows users to upload PDF documents, ask questions, and receive relevant answers based on the document's content using Retrieval-Augmented Generation (RAG).

## 1. Problem Statement

Reading and understanding lengthy PDF documents such as textbooks, research papers, reports, and study materials can be time-consuming. Finding specific information manually across multiple pages can also be difficult.

The **RAG-Based PDF Reader** solves this problem by allowing users to upload PDF files and ask questions in natural language. The application retrieves relevant information from the document and uses a Large Language Model (LLM) to generate context-based answers.

**Target Users:**
- Students looking for answers in study materials.
- Researchers analyzing research papers.
- Teachers working with educational documents.
- Professionals searching reports and documentation.

## 2. Features

- **PDF Upload:** Upload PDF documents for analysis.
- **Document Ingestion:** Extract text from PDF files and split it into smaller chunks.
- **Semantic Search:** Retrieve relevant information based on the meaning of a user's question.
- **AI-Powered Answers:** Generate natural-language answers using a Large Language Model.
- **Context-Based Responses:** Answer questions using information retrieved from the uploaded document.
- **Answer with Citation:** Identify relevant document sections or page numbers when supported by the implementation.
- **Safe Refusal:** Indicate when the document does not contain sufficient information to answer a question.
- **Interactive Interface:** Provide a simple interface for asking questions and exploring PDF content.

## 3. Tech Stack

- **Programming Language:** Python
- **AI Framework:** LangChain
- **Embeddings:** Hugging Face Sentence Transformers
- **Vector Database:** FAISS or Chroma
- **Language Model:** LLM through the configured model provider
- **User Interface:** Gradio or Streamlit, depending on the implementation
- **PDF Processing:** PyPDF or PyPDF2
- **Deployment:** Hugging Face Spaces

## 4. How to Run Locally

### Prerequisites

- Python 3.10 or later
- Git
- An API key if the selected language model provider requires one

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

### Step 2: Navigate to the Project Folder

```bash
cd YOUR-REPOSITORY
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables

If your application uses an API key, configure it using an environment variable or a local `.env` file. Do not upload API keys or secrets to GitHub.

### Step 5: Run the Application

For a Streamlit application:

```bash
streamlit run app.py
```

For a Gradio application, run the appropriate Python entry-point file, for example:

```bash
python app.py
```

Open the local URL displayed in the terminal to access the application.

## 5. RAG Pipeline

The application follows a Retrieval-Augmented Generation workflow.

**Pipeline:**

Documents → Text Extraction → Text Chunking → Embeddings → Vector Store → Semantic Retrieval → LLM Answer → Source Citation

### How It Works

1. **Document Upload:** The user uploads a PDF document.
2. **Text Extraction:** The application extracts readable text from the PDF.
3. **Chunking:** The extracted text is divided into smaller sections for efficient retrieval.
4. **Embedding Generation:** Each text chunk is converted into a numerical vector using an embedding model.
5. **Vector Storage:** The vectors and associated text are stored in a vector database.
6. **Semantic Retrieval:** The user's question is embedded and compared with stored vectors to retrieve relevant chunks.
7. **Answer Generation:** The LLM generates an answer using the retrieved context.
8. **Citation:** Relevant source sections or page references are presented when available.

## 6. Evaluation

The application can be evaluated using questions that test retrieval accuracy, answer relevance, document grounding, and refusal behaviour.

| No. | Test Question | Expected Behaviour |
|---|---|---|
| 1 | What is the main topic of this document? | Summarizes the central topic using the PDF. |
| 2 | What are the key points discussed? | Identifies the important points in the document. |
| 3 | Explain the main concept in simple words. | Provides a clear explanation based on the retrieved context. |
| 4 | What examples are mentioned in the document? | Retrieves examples that appear in the PDF. |
| 5 | What are the advantages discussed? | Lists advantages supported by the document. |
| 6 | What challenges or limitations are mentioned? | Identifies the stated challenges or limitations. |
| 7 | Which section discusses the main objective? | Retrieves the relevant section or page when available. |
| 8 | Summarize the conclusion. | Summarizes the document's conclusion if present. |
| 9 | What is the publication date? | Returns the date if it is available in the document. |
| 10 | What is the capital of a country unrelated to this document? | Refuses or states that the uploaded document does not provide sufficient information. |

### Evaluation Metrics

- **Retrieval Relevance:** Whether the retrieved chunks contain information relevant to the question.
- **Answer Accuracy:** Whether the generated answer agrees with the source document.
- **Groundedness:** Whether the response is supported by retrieved context.
- **Citation Accuracy:** Whether the cited source actually supports the answer.
- **Refusal Behaviour:** Whether the system avoids unsupported answers when the document lacks the required information.

*Note: These are proposed test cases and expected behaviours, not measured results. Record the observed behaviour after running each question against your application.*

## 7. Limitations and Safety

### Limitations

- Scanned PDFs may require Optical Character Recognition (OCR) to extract text.
- Complex tables, charts, images, and unusual document layouts may not be interpreted correctly.
- Retrieval quality depends on the embedding model, chunk size, and retrieval settings.
- The LLM may produce incorrect or incomplete answers.
- Very large documents may require additional processing time and memory.
- Answers are limited by the quality and content of the uploaded documents.

### Safety Measures

- The application should answer using retrieved document context rather than unsupported assumptions.
- It should indicate when sufficient evidence is unavailable.
- Citations should be checked against the original document.
- Uploaded documents may contain confidential information; users should avoid uploading sensitive files to untrusted deployments.
- If an external LLM provider is used, document content sent to that provider may be subject to its data-handling policies.
- API keys and credentials must be stored securely and never committed to the repository.

## 8. Live App Link

**Hugging Face Spaces:** [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]

Replace this placeholder with the URL of your deployed Hugging Face Space.

## Future Improvements

- Support multiple PDF uploads.
- Display source citations with page numbers.
- Add chat history and follow-up questions.
- Support scanned PDFs using OCR.
- Improve retrieval using hybrid search and reranking.
- Add document summarization and multilingual question answering.

## Conclusion

The RAG-Based PDF Reader demonstrates how Retrieval-Augmented Generation can make document analysis faster and more interactive. By combining semantic search, vector embeddings, and a Large Language Model, it helps users find relevant information and understand PDF documents through natural-language questions.

---

**Developed using Python and Retrieval-Augmented Generation (RAG).**
