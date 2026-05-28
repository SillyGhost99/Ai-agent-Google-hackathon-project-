# Ai-agent-Google-hackathon-project

# HAVEN — Survival Intelligence Agent

> *"2.6 billion people live without reliable internet. Every AI assistant ever built forgot about them. HAVEN didn't."*

---

## What is HAVEN?

HAVEN is an AI-powered survival knowledge agent built for low-connectivity and no-connectivity environments. It gives emergency guidance, answers survival questions, and learns from documents you upload — serving communities that mainstream AI has never reached.

Farmers in rural Africa. Trekkers in the Himalayas. Villagers in remote Southeast Asia. Disaster survivors with no signal. These are HAVEN's users.

HAVEN is not a chatbot. It is a multi-step reasoning agent that plans, retrieves, synthesizes, and acts.

---

## The Problem

Every AI assistant built today assumes one thing — that you have internet.

GPT. Gemini. Claude. Alexa. Siri. All of them. Useless without a connection.

- **2.6 billion people** have no internet access
- **1.3 billion more** have access so unreliable it's effectively unusable
- When disasters strike, even connected regions go dark instantly
- Rural communities, remote workers, and field operators face this daily

For these people, AI has never existed. HAVEN changes that.

---

## What HAVEN Does

### Emergency Decision Mode
User types or says `"snake bite"` — HAVEN returns a 5-step action sequence immediately. No fluff. No explanation. Just what to do right now.

### Survival Knowledge Retrieval
Ask any survival question — HAVEN searches its knowledge base using semantic vector search and returns a cited, sourced answer. It tells you exactly which document the answer came from.

### Document Ingestion
Upload any PDF — a first aid manual, a wilderness guide, a medicine reference. HAVEN chunks it, embeds it, stores it, and makes it instantly queryable. Your knowledge base grows with every upload.

### Multi-Step Scenario Planner
Describe a complex situation — *"Power is out, I have rice and beans, I'm 3km from the nearest town, it's getting cold"* — HAVEN breaks it into sub-problems, retrieves relevant protocols for each, and synthesizes a full prioritized action plan.

---

## Architecture

```
User Input (Text)
      │
      ▼
Google Cloud Agent Builder
(Gemini Flash — Reasoning Core)
      │
      ▼
Intent Classifier
      │
   ┌──┴──────────────────┬────────────────────┐
   ▼                     ▼                    ▼
Emergency            Knowledge           Scenario
Decision Mode        Retrieval           Planner
   │                     │                    │
   ▼                     ▼                    ▼
Immediate            MongoDB MCP         Sequential
Action Steps         Vector Search       Tool Calls
                         │
                         ▼
                  Atlas Vector Index
                  (Survival Knowledge Base)
                         │
                         ▼
                  Cited Response
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Agent Orchestration | Google Cloud Agent Builder |
| LLM | Gemini 1.5 Flash |
| Vector Database | MongoDB Atlas |
| Partner Integration | MongoDB MCP Server |
| Embeddings | Gemini text-embedding-004 |
| Backend | FastAPI on Google Cloud Run |
| Document Processing | PyMuPDF + chunking pipeline |
| Frontend | HTML / CSS / JS |

---

## Knowledge Base (Preloaded)

- Wilderness First Aid Manual
- Snake Bite & Poisoning Protocols
- Emergency Shelter & Fire Safety Guide
- Water Purification & Food Safety Reference
- 100+ Emergency Recipes (ingredient-based search)
- Basic Medical Emergency Reference

All content is chunked, embedded, and stored in MongoDB Atlas with full vector search indexing. Users can extend the knowledge base by uploading their own PDFs.

---

## Demo

**Scenario 1 — Emergency Query**
```
User:  "snake bite"
HAVEN: 1. Stay calm. Do not run.
       2. Wash wound with clean water.
       3. Immobilize the affected limb.
       4. Remove tight clothing or jewelry near bite.
       5. Get to a hospital immediately.
       Source: Snake Bite Protocol v2, WHO Emergency Reference
```

**Scenario 2 — Scenario Planning**
```
User:  "Power is out. I have rice, beans, and canned tomatoes.
        No gas stove. What do I do?"
HAVEN: [Plans 3 sub-tasks: food prep, heat source, nutrition]
       [Retrieves protocols for each]
       [Returns full prioritized action plan with sources]
```

**Scenario 3 — Document Upload**
```
User:  [Uploads wilderness_first_aid.pdf]
HAVEN: "Document indexed. 47 chunks stored. Ready to query."
User:  "What does the manual say about hypothermia treatment?"
HAVEN: [Returns answer cited from the uploaded document]
```

---

## Roadmap

This is HAVEN v1 — a proof of concept demonstrating the agent intelligence and knowledge architecture on Google Cloud infrastructure.

| Phase | What | When |
|---|---|---|
| v1 (Now) | Cloud agent — Gemini API + MongoDB Atlas | Hackathon |
| v2 | Android app — Gemini Nano + local ChromaDB | 3-6 months |
| v3 | Fully airgapped — zero connectivity required | 6-12 months |

The transition from cloud to edge requires no architectural changes — only a runtime swap. Gemini Nano replaces the Gemini API. ChromaDB replaces MongoDB Atlas. The agent logic is identical.

---

## Who This Is For

| User | Situation |
|---|---|
| Rural farmer | No internet, needs crop/health guidance |
| Mountain trekker | Remote area, medical emergency |
| Village health worker | Offline medical reference |
| Disaster survivor | Infrastructure collapsed, needs immediate help |
| Remote field operator | No connectivity, needs technical manuals |

---

## Built For

**Google Cloud Rapid Agent Hackathon 2026**
Track: MongoDB
Built with: Google Cloud Agent Builder, Gemini, MongoDB Atlas, MongoDB MCP Server

---

## Setup & Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/haven
cd haven

# Install dependencies
pip install -r requirements.txt

# Set environment variables
cp .env.example .env
# Add your MongoDB connection string and Gemini API key

# Run ingestion pipeline (preload knowledge base)
python ingest.py

# Start the backend
uvicorn main:app --reload

# Open frontend
open index.html
```

---

## License

MIT License — see LICENSE file for details.

---

## Team

Built during the Google Cloud Rapid Agent Hackathon, May–June 2026.
