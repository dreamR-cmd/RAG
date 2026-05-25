# Simple RAG Assistant

基于 LangChain + Streamlit 的简易 RAG（检索增强生成）助手，支持多模型接入、检索重排与流式对话。

## 功能

- 文档上传与解析：PDF / DOCX / TXT / MD
- 向量化存储：Chroma
- 嵌入模型：OpenAI / Qwen (DashScope) / BGE-small-zh (HuggingFace 本地)
- 对话模型：Qwen / DeepSeek / OpenAI / Zhipu (GLM)
- 检索重排：BGE-Reranker (CrossEncoder)，提升检索精度
- 对话记忆：滑动窗口，保留最近 50 轮对话
- 流式输出：逐 token 实时生成回答
- Streamlit Web 交互界面

## 快速开始

```bash
pip install -r requirements.txt
```

配置 `.env` 文件：

```
# 千问（必填）
QWEN_API_KEY=your_api_key
QWEN_BASE_URL=your_base_url
DASHSCOPE_API_KEY=your_api_key

# 以下按需配置
DEEPSEEK_API_KEY=your_api_key
DEEPSEEK_BASE_URL=your_base_url
OPENAI_API_KEY=your_api_key
OPENAI_BASE_URL=your_base_url
ZHIPU_API_KEY=your_api_key
ZHIPU_BASE_URL=your_base_url
```

启动应用：

```bash
streamlit run models/main.py
```

## 项目结构

```
simple_rag_assistant/
├── models/
│   ├── main.py                          # Streamlit 入口
│   ├── rag_service_stream.py            # RAG 核心服务（文档处理、检索、流式问答）
│   ├── langchain_embedding.py           # 嵌入模型统一入口
│   ├── langchain_llm.py                 # LLM 模型统一入口（qwen/deepseek/openai/zhipu）
│   ├── custom_dashscope_embedding.py    # DashScope 嵌入模型封装
│   └── reranker_model.py               # 重排模型（CrossEncoder），对检索结果语义重排
├── models_data/                         # 本地模型文件（如 BGE-small-zh）
├── chroma_db/                           # Chroma 向量数据库持久化目录
├── requirements.txt                     # 项目依赖
└── .env                                 # 环境变量配置
```
