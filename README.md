# Decisio

*A Final Project for the AI-Enabled Python Web Development Bootcamp at Devscale Indonesia.*

Decisio is an advanced, AI-driven decision-intelligence platform designed to ingest multi-source data (PDFs, CSVs, documents), build intelligent knowledge vectors, run interactive analytical chats, and generate automated decision briefs and visualizations.

👉 **[View the Pitch Deck: Transforming Data into Decisions](https://pitch.com/v/ai-ai-workspace-transforming-data-into-decisions-85759b)**

---

## Architecture & Tech Stack

### Backend (`apps/api`)
* **Framework:** Python / FastAPI with SQLAlchemy & Alembic migrations
* **Vector Store & RAG:** ChromaDB with custom chunking, indexing, and retrieval pipelines
* **AI & Agents:** Modular agent definitions (Consultant, Decision Brief, Extraction), Prompt Registry, and OpenAI client integration
* **Async Workers:** Celery + Redis for background source processing and OCR pipeline execution
* **Protocol Support:** Model Context Protocol (MCP) server implementation

### Frontend (`apps/web`)
* **Framework:** React / TypeScript built with Vite
* **Routing & State:** TanStack Router and TanStack React Query
* **Styling & Components:** Tailwind CSS with accessible UI primitives
* **Features:** Real-time streaming chat, interactive evidence chips, data visualization dashboards, and workspace management

---

## Project Structure

```text
decisio/
├── apps/
│   ├── api/                 # FastAPI Python Backend
│   │   ├── alembic/         # Database migrations
│   │   ├── app/
│   │   │   ├── agents/      # Consultant, Extraction, & Decision Brief agents
│   │   │   ├── core/        # Configuration, security, exceptions
│   │   │   ├── knowledge/   # ChromaDB integration, chunking & retrieval
│   │   │   ├── mcp/         # Model Context Protocol server
│   │   │   ├── models/      # SQLAlchemy ORM models
│   │   │   ├── routes/      # API endpoints (chat, sources, visualizations)
│   │   │   ├── schemas/     # Pydantic validation schemas
│   │   │   └── services/    # Business logic & artifact processing
│   │   └── tests/           # Pytest suite
│   │
│   └── web/                 # React Frontend
│       └── src/
│           ├── components/  # UI primitives & layout
│           ├── features/    # Modular feature logic (chat, briefs, sources)
│           └── routes/      # TanStack file-based routes
├── docs/                    # PRD, Architecture specs, and ADRs (0001–0007)
└── docker-compose.yml       # Local container orchestration
```

---

## Getting Started

### Prerequisites
* Python 3.10+ & `uv` / pip
* Node.js 18+ & `pnpm`
* Docker & Docker Compose (optional, for local services)

### Environment Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/SkandarEverest/decisio.git
   cd decisio
   ```
2. Configure environment variables in `apps/api/.env` (reference `apps/api/.env.example`).

### Running Locally

* **Backend Development:**
  ```bash
  cd apps/api
  uvicorn app.main:app --reload
  ```

* **Frontend Development:**
  ```bash
  cd apps/web
  pnpm dev
  ```

* **Docker Compose:**
  ```bash
  docker compose up --build
  ```

---

## Testing

* **Backend Tests:**
  ```bash
  cd apps/api
  pytest
  ```

* **Frontend Tests:**
  ```bash
  cd apps/web
  pnpm test
  ```

---

## Documentation & ADRs
Detailed architectural decisions, technical specs, and design systems are located in the [`docs/`](./docs/) directory, including:
* [Pitch Deck](https://pitch.com/v/ai-ai-workspace-transforming-data-into-decisions-85759b)
* [Architecture Guide](./docs/architecture.md)
* [Product Requirements Document](./docs/prd.md)
* [Architectural Decision Records (ADRs)](./docs/adr/)
