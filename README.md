# 👩‍🏫👨‍🏫 ExamFlux
ExamFlux is an AI-powered exam authoring and review platform that combines LLM-based question generation, validation guardrails, semantic similarity detection, and human approval into a unified workflow.

## 🎥 Video Walkthrough

https://youtu.be/R-jLH7xjr88

## 📖 Overview

ExamFlux demonstrates how **AI + backend orchestration + workflow automation** can support exam content creation and review.

- Generate exam items from `.docx` files or text prompts using OpenAI GPT-4.1

- Validate generated item structure and enforce guardrails

- Compute semantic embeddings for similarity and duplicate detection

- Allow human reviewers to approve or reject generated items

- Commit approved items to the database

## ✨ Features

| Category | Description |

|---|---|

| **AI Generation** | Generates structured exam items in JSON format from `.docx` files or text prompts |

| **Validation Guardrails** | Enforces choice-length limits and validates generated item structure |

| **Duplicate Detection** | Uses Hugging Face Sentence Transformers for semantic similarity |

| **Human Review Workflow** | Supports approve, reject, and commit actions |

| **Frontend** | React interface for item review and similarity display |

| **Persistence** | SQLite and SQLAlchemy |

## 💻 Tech Stack

| Layer | Technologies |

|---|---|

| **Backend** | Python, FastAPI, SQLAlchemy, SQLite |

| **AI** | OpenAI API / GPT-4.1 |

| **NLP** | Hugging Face Sentence Transformers, Embeddings, Semantic Similarity |

| **Frontend** | React, JavaScript, HTML, CSS |

| **Validation** | Pydantic, JSON Validation |

| **DevOps** | Docker |

## 👤 Author

**Naomi (Yu-Shan) Cheng**  

Master of Computer Science (AI Specialization)  

University of Illinois Urbana–Champaign

"""

# If this is the v2 file, create a clean current-state README instead.

if "MCP Integration" in text or "RAG-based Standards Review" in text:

    text = """# 👩‍🏫👨‍🏫 ExamFlux

ExamFlux is an AI-powered exam authoring and review platform that combines LLM-based question generation, validation guardrails, semantic similarity detection, and human approval into a unified workflow.

---

## 🎥 Video Walkthrough

https://youtu.be/R-jLH7xjr88

---

## 📖 Overview

ExamFlux demonstrates how **AI + backend orchestration + workflow automation** can transform exam content creation.

It provides a complete pipeline:

- Generate exam items from `.docx` files or text prompts using OpenAI GPT-4.1

- Validate structure and enforce guardrails

- Compute semantic embeddings for similarity detection

- Enable human reviewers to approve or reject items

- Commit approved items to the database

Rather than replacing human reviewers, ExamFlux uses AI to accelerate item creation while keeping humans in control of final review and approval.

---

## ✨ Features

| Category | Description |

|-----------|-------------|

| **AI Generation** | Uses the OpenAI API to generate exam items in JSON format from `.docx` files or text prompts |

| **Validation Guardrails** | Enforces choice-length limits and ensures valid item structure |

| **Duplicate Detection** | Embeds each item using Hugging Face Sentence Transformers for semantic similarity search |

| **Review Workflow** | Supports `approve`, `reject`, and `commit` actions |

| **Frontend** | React-based interface for item viewing, approval, and similarity display |

| **Persistence** | Stores item and review data using SQLite and SQLAlchemy |

---

## 🏗️ Architecture

```text

+------------------------------------------------------+

|                    Frontend (React)                  |

|  - Reviewer Interface                               |

|  - Approve / Reject / Commit Workflow               |

|  - Similarity Display                               |

+---------------------------▲--------------------------+

                            |

                            ▼

+---------------------------+--------------------------+

|             FastAPI Backend (Python)                 |

|  - /api/items CRUD routes                            |

|  - /api/items/generate                               |

|  - /api/items/similar                                |

|  - /api/items/approve, /reject, /commit              |

|  - SQLite via SQLAlchemy ORM                         |

+---------------------------▲--------------------------+

                            |

                            ▼

+---------------------------+--------------------------+

|                AI & Embedding Services               |

|  - OpenAI GPT-4.1 for generation                     |

|  - Hugging Face Sentence Transformers embeddings     |

+------------------------------------------------------+

```

---

## 🚀 Setup Instructions

### 1. Clone the repository

```bash

git clone https://github.com/ysc06/AI-powered-exam-item-reviewer.git

cd AI-powered-exam-item-reviewer

```

### 2. Create and activate a virtual environment

```bash

python3 -m venv .venv

source .venv/bin/activate

pip install -r requirements.txt

```

### 3. Add your API key in `.env`

```text

OPENAI_API_KEY=your_api_key_here

```

### 4. Initialize the database

```bash

python -m backend.app.db_init

```

### 5. Run the backend server

```bash

uvicorn backend.app.main:app --reload

```

FastAPI docs:

```text

http://127.0.0.1:8000/docs

```

### 6. Optional: Run with Docker Compose

```bash

docker-compose up --build

```

---

## 📡 API Endpoints

| Method | Endpoint | Description |

|--------|----------|-------------|

| `POST` | `/api/items/` | Create new item |

| `GET` | `/api/items/` | List all items |

| `POST` | `/api/items/generate` | Generate item from OpenAI prompt |

| `GET` | `/api/items/{id}/similar` | Find top-K similar items |

| `POST` | `/api/items/{id}/approve` | Approve item |

| `POST` | `/api/items/{id}/reject` | Reject item |

| `POST` | `/api/items/commit` | Commit approved items |

| `GET` | `/api/export` | Export items to CSV |

---

## 📄 Example JSON Output

```json

{

  "stimulus": "Company memo: meeting on Friday at 10 a.m.",

  "stem": "What is announced in the memo?",

  "choices": [

    "A staff lunch",

    "A budget review",

    "A quarterly meeting",

    "An office relocation"

  ],

  "answer": "C",

  "metadata": {

    "topic": "Business Communication",

    "difficulty": "Medium"

  }

}

```

---

## 💻 Tech Stack

| Layer | Technologies |

|--------|--------------|

| **Backend** | Python, FastAPI, SQLAlchemy, SQLite |

| **AI** | OpenAI API, GPT-4.1 |

| **NLP** | Hugging Face Sentence Transformers, Embeddings, Semantic Similarity |

| **Frontend** | React, JavaScript, HTML, CSS |

| **Utilities** | Docker, dotenv, Pydantic, JSON Validation |

---

## ✅ Current Capabilities

- [x] FastAPI backend with SQLite ORM

- [x] React frontend integration

- [x] AI-powered exam item generation

- [x] Generation from `.docx` files and text prompts

- [x] Validation guardrails

- [x] Embedding-based semantic similarity detection

- [x] Human approve / reject / commit workflow

- [x] Persistent item storage

- [x] Docker support

---

## 🎯 Project Goal

ExamFlux explores how generative AI can shift exam authoring from a primarily manual creation process toward an **AI-assisted, human-reviewed workflow**.

AI accelerates initial item generation and supports duplicate detection, while human reviewers retain control over quality decisions and final approval.

---

## 👤 Author

**Naomi (Yu-Shan) Cheng**  

Master of Computer Science (AI Specialization)  

University of Illinois Urbana–Champaign

"""
