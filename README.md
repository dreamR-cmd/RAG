# Simple RAG Assistant

基于 LangChain 的简易 RAG（检索增强生成）助手，支持多模型接入。

## 功能

- 支持 PDF 文档加载与向量化存储（Chroma）
- 嵌入模型：OpenAI / Qwen (DashScope) / BGE-small-zh 本地模型
- 对话模型：Qwen / DeepSeek / OpenAI / Zhipu (GLM)
- Streamlit Web 交互界面

## 快速开始

```bash
pip install -r requirements.txt
```

配置 `.env` 文件：

```
QWEN_API_KEY=your_api_key
QWEN_BASE_URL=your_base_url
DASHSCOPE_API_KEY=your_api_key
```

```bash
streamlit run app.py
```

## 项目结构

```
simple_rag_assistant/
├── models/
│   ├── custom_dashscope_embedding.py  # DashScope 嵌入模型封装
│   ├── langchain_embedding.py         # 嵌入模型统一入口
│   └── langchain_llm.py              # LLM 模型统一入口
└── requirements.txt                   # 项目依赖
```
