# AI Multi-Search Agent 🌐🤖

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/LangGraph-Multi--Agent-blueviolet?style=for-the-badge" />
  <img src="https://img.shields.io/badge/LangChain-Orchestration-1C3C3C?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Streamlit-UI-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

**AI Multi-Search Agent** is a multi-source retrieval and synthesis pipeline built with **LangGraph** and **LangChain**. It dispatches parallel search queries across **Google Search**, **Bing Search**, and **Reddit Communities** (via BrightData SERP & Dataset APIs), extracts top Reddit post discussions, analyzes each source independently, and synthesizes a unified answer.

---

## 🏗️ Retrieval & Synthesis Graph (`main.py`)

```mermaid
flowchart TD
    START([User Question]) --> Google[google_search]
    START --> Bing[bing_search]
    START --> Reddit[reddit_search]
    Google --> SelectReddit[analyze_reddit_posts]
    Bing --> SelectReddit
    Reddit --> SelectReddit
    SelectReddit --> FetchComments[retrieve_reddit_posts]
    FetchComments --> AnalyzeGoogle[analyze_google_results]
    FetchComments --> AnalyzeBing[analyze_bing_results]
    FetchComments --> AnalyzeReddit[analyze_reddit_results]
    AnalyzeGoogle --> Synthesize[synthesize_analyses]
    AnalyzeBing --> Synthesize
    AnalyzeReddit --> Synthesize
    Synthesize --> END([Final Synthesized Answer])
```

---

## 🛠️ Project Structure

```
ai-multi-search-agent/
├── main.py                    # 9-node LangGraph workflow & CLI runner
├── streamlit.py               # Interactive Streamlit dashboard
├── web_operations.py          # Google, Bing, and Reddit search API connectors
├── snapshot_operations.py     # Async dataset snapshot polling & downloader
├── prompts.py                 # Source-specific analysis & synthesis prompt templates
├── pyproject.toml             # Package metadata & dependencies
├── requirements.txt           # Production dependencies
├── .env.example               # Environment variables template
└── README.md                  # Project documentation
```

---

## 📦 Quick Start Guide

### 1. Clone Repository

```bash
git clone https://github.com/alhaj-ai/ai-multi-search-agent.git
cd ai-multi-search-agent
```

### 2. Environment Setup

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

### 3. API Configuration

Copy `.env.example` to `.env` and configure your keys:

```ini
OPENAI_API_KEY=your_openai_api_key_here
BRIGHTDATA_API_KEY=your_brightdata_api_key_here
```

### 4. Run Application

#### Streamlit Dashboard:
```bash
streamlit run streamlit.py
```

#### CLI Mode:
```bash
python main.py
```

---

## 👨‍💻 Author

Developed by **[Mohammed Al-Haj](https://github.com/alhaj-ai)**
- 📧 Email: `ai.mohammed.alhaj@gmail.com`
- 🐙 GitHub: [@alhaj-ai](https://github.com/alhaj-ai)
