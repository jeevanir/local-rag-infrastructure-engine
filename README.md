# Local Enterprise RAG Infrastructure Engine 🤖

A secure, 100% local, zero-cost Retrieval-Augmentation Generation (RAG) system running entirely within an isolated environment. This prototype allows teams to query proprietary documentation with natural language without leaking sensitive corporate data to external third-party cloud APIs.

## 🛠️ System Architecture & Workflow
1. **Data Ingestion:** Documents inside `./knowledge_base/` are chunked into 500-character segments using LangChain's Recursive Character Text Splitter.
2. **Vectorization Matix:** Text chunks are transformed into 384-dimensional mathematical coordinates via a local Hugging Face model (`all-MiniLM-L6-v2`).
3. **Storage Layer:** Structural coordinates are saved into an on-device local instance of `Chroma DB`.
4. **Context Retrieval:** User queries are matched against the database using semantic similarity metrics to extract the top 2 factual context chunks.
5. **Orchestration & Guardrails:** Injected context is wrapped inside native ChatML token formatting (`<|im_start|>`/`<|im_end|>`) to control model boundaries.
6. **Local Inference:** A local LLM pipeline (`Qwen2.5-0.5B-Instruct`) synthesizes answers in-memory, protected by an explicit regex post-processing cleanup filter.

## 🚀 Key Features
- 🔒 **100% Data Localization:** Zero external cloud network calls—guaranteeing data privacy.
- 💰 **Zero-Cost Compute:** Operates fully on-device without cloud API key usage overhead.
- 📊 **Telemetry Dashboard:** Dual-panel Streamlit layout showing a Live Chat window alongside a real-time Vector Store Inspector.

## 📦 Installation & Execution
1. Clone the repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/local-rag-infrastructure-engine.git](https://github.com/YOUR_USERNAME/local-rag-infrastructure-engine.git)
