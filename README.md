# 👩‍🏫👨‍🏫 ExamFlux

> **AI-powered Exam Authoring Platform** for intelligent question
> generation, AI-assisted quality assurance, retrieval-augmented
> standards validation, and human-in-the-loop assessment development.

ExamFlux is an AI-powered exam authoring platform that streamlines the
entire assessment development lifecycle. Instead of focusing only on AI
question generation, ExamFlux integrates generation, AI-assisted review,
retrieval-augmented standards validation, revision workflows, and human
approval into a unified authoring experience.

------------------------------------------------------------------------

# 🎥 Video Walkthrough

https://youtu.be/R-jLH7xjr88

------------------------------------------------------------------------

# 📖 Overview

Modern assessment development requires significantly more than
generating exam questions.

Every exam item should be reviewed for:

-   Writing quality
-   Learning objective alignment
-   Distractor effectiveness
-   Difficulty consistency
-   Internal authoring standards
-   Fairness and sensitivity
-   Publication readiness

ExamFlux demonstrates how modern AI engineering techniques---including
**Prompt Orchestration**, **Retrieval-Augmented Generation (RAG)**, and
**Human-in-the-Loop workflows**---can improve the quality, consistency,
and maintainability of assessment content.

------------------------------------------------------------------------

# ✨ Features

  -----------------------------------------------------------------------
  Category                         Description
  -------------------------------- --------------------------------------
  **AI Question Generation**       Generate structured exam items from
                                   `.docx` documents or text prompts
                                   using OpenAI GPT models

  **Validation Guardrails**        Validate generated items, enforce JSON
                                   schema, and ensure structural
                                   consistency

  **Semantic Similarity            Detect semantically similar items
  Detection**                      using Hugging Face Sentence
                                   Transformers embeddings

  **Human Review Workflow**        Review, approve, reject, and commit
                                   exam items before publication

  **React Frontend**               Interactive reviewer dashboard with
                                   similarity visualization and review
                                   workflow

  **Prompt Orchestration** *(In    Separate generation, review, revision,
  Progress)*                       and retrieval into independent AI
                                   workflows

  **AI Quality Reviewer** *(In     Automatically evaluate grammar,
  Progress)*                       ambiguity, distractor quality,
                                   learning objective alignment, and item
                                   quality

  **AI Revision Assistant** *(In   Revise generated items while
  Progress)*                       preserving learning objectives and
                                   target difficulty

  **RAG-based Standards Review**   Retrieve internal authoring guidelines
  *(In Progress)*                  to validate generated items against
                                   organization-specific standards

  **Human Review Comments** *(In   Reviewer feedback becomes part of the
  Progress)*                       AI revision workflow

  **Version History** *(In         Track AI-generated, AI-revised, and
  Progress)*                       human-edited versions throughout the
                                   authoring lifecycle

  **MCP Integration** *(Planned)*  Expose exam authoring capabilities as
                                   Model Context Protocol (MCP) tools for
                                   AI assistants
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 🏗️ System Architecture

``` text
                           User
                             │
                             ▼
                    Prompt Orchestrator
                             │
        ┌────────────────────┼────────────────────┐
        ▼                    ▼                    ▼
 Question Generation    AI Quality Review    AI Revision
                             │
                             ▼
                RAG Standards Retrieval
                             │
                             ▼
                  Human Review Workflow
                             │
                             ▼
                     Version History
                             │
                             ▼
                  SQLite / Item Database
```

------------------------------------------------------------------------

# 🤖 AI Workflow

``` text
Generate Exam Item
        │
        ▼
AI Quality Review
        │
        ▼
Retrieve Internal Standards (RAG)
        │
        ▼
Human Review
        │
        ▼
AI Revision (if needed)
        │
        ▼
Version History
        │
        ▼
Approve / Reject
```

------------------------------------------------------------------------

# 🚀 Setup Instructions

## 1. Clone the repository

``` bash
git clone https://github.com/<your-username>/exam-item-reviewer.git
cd exam-item-reviewer
```

## 2. Create and activate a virtual environment

``` bash
python3 -m venv .venv
source .venv/bin/activate

pip install -r requirements.txt
```

## 3. Add your API key

Create a `.env` file:

``` text
OPENAI_API_KEY=your_api_key_here
```

## 4. Initialize the database

``` bash
python -m backend.app.db_init
```

## 5. Start the backend

``` bash
uvicorn backend.app.main:app --reload
```

Open:

``` text
http://127.0.0.1:8000/docs
```

## 6. (Optional) Run with Docker Compose

``` bash
docker-compose up --build
```

------------------------------------------------------------------------

# 📡 API Endpoints

  Method   Endpoint                    Description
  -------- --------------------------- ----------------------------------
  `POST`   `/api/items/`               Create new item
  `GET`    `/api/items/`               List all items
  `POST`   `/api/items/generate`       Generate exam items using OpenAI
  `GET`    `/api/items/{id}/similar`   Find semantically similar items
  `POST`   `/api/items/{id}/approve`   Approve item
  `POST`   `/api/items/{id}/reject`    Reject item
  `POST`   `/api/items/commit`         Commit approved items
  `GET`    `/api/export`               Export items to CSV

### Planned APIs

  Method   Endpoint                     Description
  -------- ---------------------------- --------------------------
  `POST`   `/api/items/review`          AI quality review
  `POST`   `/api/items/revise`          AI revision
  `POST`   `/api/items/comments`        Human review comments
  `GET`    `/api/items/{id}/versions`   Retrieve version history

------------------------------------------------------------------------

# 📄 Example JSON Output

``` json
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

------------------------------------------------------------------------

# 🗺️ Roadmap

## ✅ Completed

-   AI-powered exam item generation
-   React + FastAPI full-stack application
-   Semantic similarity detection
-   Human review workflow
-   SQLite persistence
-   OpenAI-powered generation from `.docx` and prompt input

## 🚧 In Progress

-   Prompt Orchestration
-   AI Quality Reviewer
-   AI Revision Assistant
-   RAG-based Standards Review
-   Human Review Comments
-   Version History
-   Structured Review Workflow

## 🔮 Planned

-   MCP Tool Server
-   External Developer API
-   Team Collaboration
-   Analytics Dashboard
-   Sensitive Topic Detection
-   Bias & Fairness Review

------------------------------------------------------------------------

# 💻 Tech Stack

  -----------------------------------------------------------------------
  Layer                     Technologies
  ------------------------- ---------------------------------------------
  **Backend**               FastAPI, Python, SQLAlchemy, SQLite

  **Frontend**              React, JavaScript, HTML, CSS

  **AI**                    OpenAI GPT-4.1 / GPT-4o, Prompt Orchestration
                            *(planned)*

  **NLP**                   Hugging Face Sentence Transformers

  **Retrieval**             Embedding-based Semantic Similarity,
                            Retrieval-Augmented Generation (RAG)
                            *(planned)*

  **AI Protocol**           Model Context Protocol (MCP) *(planned)*

  **Utilities**             Docker, dotenv, Pydantic, JSON Validation
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 📂 Project Structure

``` text
ExamFlux/

├── frontend/
├── backend/
│   ├── api/
│   ├── services/
│   ├── prompts/
│   ├── review/
│   ├── revision/
│   ├── rag/
│   ├── models/
│   └── db/
├── docs/
└── README.md
```

------------------------------------------------------------------------

# 🎯 Vision

ExamFlux aims to evolve beyond an AI question generator into a complete
**AI-powered exam authoring platform**.

By combining:

-   AI-powered question generation
-   AI-assisted quality review
-   Retrieval-Augmented Standards Validation (RAG)
-   Human-in-the-loop review
-   AI-assisted revision
-   Version history
-   Prompt orchestration
-   MCP tool integration

the platform supports a scalable, transparent, and trustworthy workflow
for modern educational and enterprise assessment development.

------------------------------------------------------------------------

# 👤 Author

**Naomi (Yu-Shan) Cheng**

Master of Computer Science (Artificial Intelligence Specialization)\
University of Illinois Urbana--Champaign
