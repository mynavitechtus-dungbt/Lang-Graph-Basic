# LangGraph Tutorial Series

## 📚 Giới Thiệu

Repository này chứa các bài học và ví dụ thực hành về **LangGraph** - một thư viện mạnh mẽ để xây dựng các ứng dụng AI với state machines và graph-based workflows. Từ những khái niệm cơ bản đến các ứng dụng thực tế nâng cao.

> *"Training LangGraph to make salary go to the moon, get the money and give all to my wife."* 💰🌙

## 🎯 Highlights

### Notebook 9: PDF RAG Agent
Một ứng dụng RAG (Retrieval-Augmented Generation) hoàn chỉnh với:
- **Vector Database**: Sử dụng Chroma để lưu trữ và tìm kiếm embeddings từ PDF documents
- **Tool Calling**: Tích hợp Google Gemini với tool calling để tự động retrieve documents
- **LangGraph Workflow**: Quản lý flow: User Query → LLM → Tool Call → Retrieve → Generate Response
- **Interactive Q&A**: Hệ thống hỏi đáp tương tác với healthcare documents

## 🗂️ Cấu Trúc Project

Repository được tổ chức thành 3 phần chính:

```
LangGraph/
├── Basic/                          # 📘 Các bài học cơ bản về LangGraph
│   ├── 1.Your First LangGraph Example — Turning Logic into Flow.ipynb
│   ├── 2.Structured States & Multi-Step Reasoning Explained.ipynb
│   ├── 3.Conditional Routing in LangGraph.ipynb
│   ├── 4.Multi-Branch Decision Flows Explained.ipynb
│   ├── 5.Building Loops & Iterative Logic in LangGraph.ipynb
│   ├── 6.State-Based Conversational AI Tutorial.ipynb
│   ├── 7.LangGraph Tool Nodes Explained.ipynb
│   ├── 8.Build an AI Document Editing Agent (Drafter) with LangGraph.ipynb
│   ├── 9.Build a PDF RAG Agent with LangGraph and Gemini.ipynb
│   ├── data/
│   │   └── Healthcare.pdf          # Sample PDF for RAG example
│   ├── requirements.txt
│   ├── .env.example
│   └── README.md
├── Advanced/                       # 📗 Các bài học nâng cao (sắp có)
│   └── README.md
├── Projects/                       # 📙 Các dự án thực tế (sắp có)
│   └── README.md
├── README.md
└── .gitignore
```

---