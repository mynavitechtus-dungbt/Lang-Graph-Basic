# LangGraph Tutorial Basic Series

## 🔑 Khái Niệm Cơ Bản

- **State**: Dictionary chứa dữ liệu truyền qua các nodes
- **Node**: Function nhận state và trả về state đã cập nhật
- **Edge**: Kết nối giữa các nodes (fixed hoặc conditional)
- **Graph**: Tập hợp nodes và edges được compile thành ứng dụng

## 📖 Các File Notebook

### 1. Your First LangGraph Example — Turning Logic into Flow
   - Giới thiệu cơ bản về LangGraph
   - Tạo graph đơn giản với 1 node
   - Hiểu cách state được truyền qua nodes

### 2. Structured States & Multi-Step Reasoning Explained
   - Làm việc với structured states (TypedDict)
   - Multi-step processing với nhiều nodes tuần tự
   - Quản lý state phức tạp hơn

### 3. Conditional Routing in LangGraph
   - Conditional routing - điều hướng dựa trên điều kiện
   - Sử dụng conditional edges
   - Quyết định động trong graph flow

### 4. Multi-Branch Decision Flows Explained
   - Graph phức tạp với nhiều nhánh
   - Xử lý nhiều luồng xử lý song song
   - Advanced conditional routing patterns

### 5. Building Loops & Iterative Logic in LangGraph
   - Tạo loops và logic lặp lại
   - Xử lý iterative workflows
   - Quản lý state trong vòng lặp

### 6. State-Based Conversational AI Tutorial
   - Xây dựng conversational AI với LangGraph
   - Quản lý conversation state
   - Tích hợp với LLM models

### 7. LangGraph Tool Nodes Explained
   - Sử dụng tool nodes trong LangGraph
   - Tích hợp external tools và APIs
   - Tool calling patterns

### 8. Build an AI Document Editing Agent (Drafter) with LangGraph
   - Xây dựng ứng dụng thực tế: AI Document Editor
   - Tích hợp các concepts từ các bài học trước
   - Xử lý document editing workflow với LangGraph

### 9. Build a PDF RAG Agent with LangGraph and Gemini
   - Xây dựng RAG (Retrieval-Augmented Generation) Agent với PDF documents
   - Tích hợp Chroma vector database để lưu trữ và tìm kiếm documents
   - Sử dụng LangGraph để quản lý workflow: retrieve → tool call → generate response
   - Tích hợp Google Gemini model với tool calling
   - Xử lý PDF documents với PyPDFLoader và text splitting
   - Tạo interactive Q&A system cho healthcare documents

## 🚀 Cài Đặt

### Yêu Cầu
- Python 3.11+
- pip

### Các Bước Cài Đặt

1. **Tạo virtual environment (nếu chưa có):**
   ```bash
   python -m venv venv
   ```

2. **Kích hoạt virtual environment:**
   ```bash
   source venv/bin/activate  # Trên macOS/Linux
   # hoặc
   venv\Scripts\activate  # Trên Windows
   ```

3. **Cài đặt dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Cấu hình environment variables:**
   ```bash
   cp .env.example .env
   # Chỉnh sửa file .env và thêm API keys của bạn
   ```

3. **Khởi chạy Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

### Dependencies

- `jupyter>=1.0.0` - Jupyter notebook environment
- `langgraph>=1.0.0` - LangGraph library
- `ipykernel>=6.0.0` - IPython kernel for Jupyter
- `python-dotenv>=1.0.0` - Environment variable management
- `langchain-google-genai>=1.0.0` - Google GenAI integration for LangChain
- `langchain-community>=0.0.20` - Community integrations (PDF loader, etc.)
- `langchain-chroma>=0.1.0` - Chroma vector database integration
- `langchain-huggingface>=0.0.1` - HuggingFace embeddings integration
- `rich>=13.0.0` - Rich text and beautiful formatting in terminal

## 📝 Cấu Trúc Project

```
Basic/
├── 1.Your First LangGraph Example — Turning Logic into Flow.ipynb
├── 2.Structured States & Multi-Step Reasoning Explained.ipynb
├── 3.Conditional Routing in LangGraph.ipynb
├── 4.Multi-Branch Decision Flows Explained.ipynb
├── 5.Building Loops & Iterative Logic in LangGraph.ipynb
├── 6.State-Based Conversational AI Tutorial.ipynb
├── 7.LangGraph Tool Nodes Explained.ipynb
├── 8.Build an AI Document Editing Agent (Drafter) with LangGraph.ipynb
├── 9.Build a PDF RAG Agent with LangGraph and Gemini.ipynb
├── data/
│   └── Healthcare.pdf                    # Sample PDF document for RAG
├── requirements.txt
├── .env.example
├── README.md
└── venv/                    # Virtual environment (gitignored)
```
