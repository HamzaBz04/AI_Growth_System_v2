# AI Growth Automation System

> **Agentic Marketing Team — Multi-Agent AI System for Marketing Automation**

The **AI Growth Automation System** is a multi-agent AI platform designed to automate the marketing funnel from lead acquisition and qualification to nurturing, conversion, appointment booking, and performance optimisation.

The system is designed as a **white-label, modular and API-driven architecture**, where each specialized agent has a clearly defined responsibility and communicates with the other agents through controlled interfaces.

The development brief defines a phased approach based on a **confirm-then-expand** principle: first validate a minimal working version, then progressively introduce LLM-based intelligence, real integrations, automation and observability.

---

## 🎯 Objectives

The main objectives of the system are to:

- Automate repetitive marketing and lead-management tasks.
- Qualify incoming leads using a structured scoring model.
- Centralize and maintain reliable CRM data.
- Automate lead nurturing and appointment booking.
- Monitor advertising performance and detect campaign issues.
- Provide traceability and observability for AI executions.
- Build a modular architecture that can be adapted to different clients and industries.
- Progressively introduce autonomous decision-making while maintaining human escalation when required.

---

## 🧩 Multi-Agent Architecture

The complete system is organized around specialized agents:

| Agent | Role | Layer |
|---|---|---|
| **Commander** | Orchestration, routing and coordination | Orchestration |
| **CRM Keeper** | Lead data management and CRM synchronization | Intelligence |
| **Qualifier** | Lead intake, scoring and MQL/SQL classification | Conversion |
| **Media Buyer** | Paid advertising monitoring and optimisation | Acquisition |
| **Content & Conversion Strategist** | Ad creatives, landing-page content and CRO | Acquisition |
| **Closer** | Lead nurturing, WhatsApp communication and appointment booking | Conversion |
| **Analyst** | KPI analysis, ROI/ROAS tracking and optimisation signals | Intelligence |

The development brief defines the **Commander** as the orchestrator above the other agents, while the **CRM Keeper** acts as the central data backbone. fileciteturn0file0L28-L54

### Agent responsibilities

#### Commander
Routes events and tasks to the appropriate specialist agent, monitors agent status, resolves conflicts and escalates situations to the human operator.

#### CRM Keeper
Acts as the system's data backbone. It creates, retrieves and updates lead records, validates data, manages pipeline stages and prevents direct CRM access from other agents.

#### Qualifier
Collects lead information, calculates a score from **0 to 100**, and classifies leads as **Disqualified, MQL or SQL** using five scoring dimensions.

#### Media Buyer
Manages paid advertising activities across Meta and Google, monitors campaign KPIs, manages budgets and identifies underperforming campaigns.

#### Content & Conversion Strategist
Generates advertising content, landing-page copy and creative briefs while supporting conversion-rate optimisation and A/B testing.

#### Closer
Handles post-qualification communication through WhatsApp and email, manages nurturing sequences and supports appointment booking.

#### Analyst
Aggregates performance data, calculates KPIs, analyses conversion patterns and provides optimisation signals to the other agents.

The roles, responsibilities and phased capabilities of these agents are defined in the project development brief. fileciteturn0file0L354-L386

---

## 🔄 Lead Conversion Flow

A simplified end-to-end flow is:

```text
                    ┌───────────────────┐
                    │  Lead Acquisition │
                    │ Meta / Google /   │
                    │ External Sources  │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Commander      │
                    │ Routing / Control │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │     Qualifier     │
                    │ Intake + Scoring  │
                    └─────────┬─────────┘
                              │
                 ┌────────────┼────────────┐
                 │            │            │
                 ▼            ▼            ▼
          Disqualified       MQL          SQL
                 │            │            │
                 └────────────┴────────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Closer         │
                    │ Nurturing /       │
                    │ WhatsApp / Email  │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │ Appointment / CRM  │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │      Analyst      │
                    │ KPI / ROI / ROAS  │
                    └─────────┬─────────┘
                              │
                              ▼
                    Optimisation Signals
                    → Commander
                    → Media Buyer
                    → Content Strategist
```

The architecture is designed so that external events enter through HTTP interfaces, while the agent framework handles agent coordination and business logic. fileciteturn0file0L118-L138

---

## 🏗️ Repository Structure

This GitHub repository focuses on the implemented agent code:

```text
AI-Growth-System-Agents/
│
├── crm_keeper/
│   ├── ...
│   └── README.md
│
├── qualifier/
│   ├── ...
│   └── README.md
│
├── media_buyer/
│   ├── ...
│   └── README.md
│
├── closer/
│   ├── ...
│   └── README.md
│
├── .gitignore
└── README.md
```

The complete PFE project also contains documentation, research material, presentation files and the project report. These materials are intentionally kept outside this GitHub code repository.

---

## 🛠️ Technology Stack

| Category | Technologies |
|---|---|
| Programming language | Python |
| API / Web framework | FastAPI |
| Agent framework | LangChain |
| LLMs | OpenAI / DeepSeek / local SLMs depending on the task |
| Package management | UV |
| CRM | HubSpot through an adapter architecture |
| Advertising | Meta Ads API / Google Ads API |
| Messaging | WhatsApp Business API / Brevo |
| Appointment booking | Cal.com |
| Observability | Langfuse |
| Data validation | Pydantic |
| API documentation | FastAPI / OpenAPI / Swagger |
| Deployment | Linux VPS + Nginx / Cloud infrastructure |

The development brief specifies FastAPI as the HTTP/webhook layer, LangChain for the initial agent framework, UV for Python dependency management and Langfuse for LLM observability. fileciteturn0file0L55-L87

---

## 🤖 Implemented Agents in This Repository

### 1. CRM Keeper

The CRM Keeper provides the central interface for lead data.

Main responsibilities include:

- Creating lead records.
- Retrieving lead information.
- Updating lead information.
- Validating incoming data.
- Maintaining lead pipeline stages.
- Preventing duplicate records.
- Providing structured data to other agents.
- Acting as the single access layer to the CRM.



---

### 2. Qualifier

The Qualifier is responsible for evaluating incoming leads.

The scoring model uses five dimensions:

1. Budget fit
2. Timeline urgency
3. Decision authority
4. Problem-solution fit
5. Engagement quality

Each dimension contributes up to **20 points**, giving a total score between **0 and 100**.

Classification:

```text
0 – 30   → Disqualified
31 – 60  → MQL
61 – 100 → SQL
```

The scoring model and classification thresholds are defined in the development brief. fileciteturn0file0L561-L592


---

### 3. Media Buyer

The Media Buyer is responsible for advertising monitoring and optimisation.

Current responsibilities include:

- Monitoring campaign performance.
- Tracking advertising KPIs.
- Budget pacing.
- CPL monitoring.
- Campaign optimisation.
- Meta Ads integration.
- Performance alert handling.
- Langfuse traceability for important operations.



The development brief defines the Media Buyer around Meta Ads and Google Ads management, including campaign structure, targeting, budget allocation and KPI monitoring. fileciteturn0file0L730-L754

---

### 4. Closer

The Closer manages communication with qualified leads and supports conversion.

Main responsibilities include:

- Lead nurturing.
- WhatsApp communication.
- Email sequences.
- Appointment booking.
- CRM updates after communication.
- Handling incoming WhatsApp events.
- Personalised message generation.
- Lead follow-up.



The development brief specifies WhatsApp, email and calendar integrations as the main communication and booking channels for the Closer. fileciteturn0file0L812-L846

---

## 🧠 Lead Scoring

The Qualifier uses a five-dimensional scoring model:

```text
                    Lead
                      │
                      ▼
          ┌───────────────────────┐
          │    Lead Information   │
          └───────────┬───────────┘
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
    Budget         Timeline       Authority
       │              │              │
       └──────────────┼──────────────┘
                      │
             ┌────────┴────────┐
             ▼                 ▼
       Problem-Solution     Engagement
             Fit              Quality
             └────────┬────────┘
                      ▼
                 Score 0–100
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
   Disqualified      MQL           SQL
     0–30           31–60         61–100
```

The weights and thresholds are configurable per client in the planned architecture. fileciteturn0file0L574-L592

---

## 🔌 API Architecture

Each agent that receives external events exposes a FastAPI application.

Examples of webhook endpoints defined by the architecture include:

```text
Commander
POST /event

Qualifier
POST /form-submission

CRM Keeper
POST /crm/update

Media Buyer
POST /ads/alert

Closer
POST /whatsapp/incoming
```

Incoming payloads are validated before reaching agent logic, and FastAPI automatically exposes OpenAPI documentation through `/docs`. fileciteturn0file0L118-L142

---

## 📊 Observability with Langfuse

Langfuse is used to provide observability over AI executions.

The system tracks information such as:

- Agent name
- Client ID
- Lead ID when applicable
- Model used
- Input/output context
- Latency
- Cost
- Agent traces
- Evaluation information

Langfuse becomes particularly important when agents use real LLM calls and is mandatory for the production-oriented phase defined in the development brief. fileciteturn0file0L109-L117

---

## 🛡️ Error Handling

The architecture follows a centralized error-handling approach:

```text
Agent Error
    │
    ▼
Log error
    │
    ▼
Notify Commander
    │
    ▼
Commander decides
    │
    ├── Retry
    ├── Reassign
    └── Escalate to operator
```

Agents should explicitly handle errors, log failures and avoid exposing raw API errors directly to the operator. External API calls should also use appropriate retry and backoff mechanisms. fileciteturn0file0L1016-L1026

---

## 📋 Logging Standard

The project defines a structured logging format for agent actions:

```json
{
  "agent_name": "qualifier",
  "action_type": "score_lead",
  "input_summary": "Lead qualification data received",
  "output_summary": "Lead classified as SQL",
  "lead_id": "UUID",
  "client_id": "client_id",
  "model_used": "rule-based",
  "latency_ms": 120,
  "timestamp": "2026-01-01T00:00:00Z"
}
```

This structure provides a common format for monitoring and later analysis. fileciteturn0file0L999-L1015

---

## 🚀 Installation

### Prerequisites

Recommended environment:

- Python 3.10+
- UV
- Git
- API credentials for the services required by each agent

Install UV:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```


## 🔐 Environment Variables

Each agent should provide a `.env.example` file containing the required configuration variables.

Example:

```env
OPENAI_API_KEY=
LANGFUSE_PUBLIC_KEY=
LANGFUSE_SECRET_KEY=
LANGFUSE_HOST=

CRM_API_URL=
CRM_API_TOKEN=

WHATSAPP_API_TOKEN=
BREVO_API_KEY=

META_ACCESS_TOKEN=
META_AD_ACCOUNT_ID=
```

> **Never commit `.env` files, API keys, access tokens, passwords or other secrets to GitHub.**

---

## ▶️ Running an Agent

From an agent directory:

```bash
uv run uvicorn api:app --host 0.0.0.0 --port 8000
```

For local development:

```bash
uv run uvicorn api:app --reload
```

FastAPI automatically exposes the Swagger interface at:

```text
http://localhost:8000/docs
```

The exact port and startup command can differ between agents depending on their deployment configuration.

---

## 🧪 Testing

Run the tests of an agent with:

```bash
uv run pytest tests/
```

The project development brief requires tests for public functions before phase validation. fileciteturn0file0L1038-L1048

---

## 📈 Development Methodology

The system follows three development phases:

### Phase A — Proof of Concept

Focus:

- Minimal working functionality.
- Basic integrations.
- Hardcoded logic where appropriate.
- Telegram-based validation.
- Basic logging.
- Payload validation.

### Phase B — Intelligence Layer

Focus:

- Real LLM decisions.
- Real APIs.
- Dynamic workflows.
- Real CRM integration.
- Automated sequences.
- Langfuse tracing.

### Phase C — Production

Focus:

- Multi-client support.
- Adaptive behaviour.
- Autonomous optimisation.
- Full observability.
- Evaluation.
- Production-grade orchestration.

The development brief explicitly defines this **confirm-then-expand** progression and requires validation before moving from one phase to another. fileciteturn0file0L11-L24

---

## 🔒 Security Principles

The project follows these principles:

- Secrets are stored in environment variables.
- External payloads are validated before processing.
- Agents do not directly expose raw API errors.
- CRM access is centralized through the CRM Keeper.
- Agent actions are logged.
- AI executions are observable through Langfuse.
- Human escalation is available for situations outside automated decision authority.

---

## 📚 Documentation

Each agent should contain its own documentation, including:

```text
README.md
.env.example
CHANGELOG.md
tests/
```

The development brief specifies that every agent must have a README explaining its role, responsibilities, setup, environment variables, execution, tests, current phase, validation checklist, limitations and inputs/outputs. fileciteturn0file0L285-L313

---

## 🎓 Academic Context

This project was developed as part of a **Projet de Fin d'Études (PFE)** focused on the design and implementation of an AI-powered multi-agent marketing automation system.

The project combines:

- Artificial Intelligence
- Large Language Models
- Multi-Agent Systems
- Lead Scoring
- CRM Integration
- Marketing Automation
- API Integration
- Observability
- Data and performance analysis

---

