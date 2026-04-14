# Prompts — LTI ATS Design

## Assistant used
**GitHub Copilot (Claude Opus 4.6)** — VS Code integrated agent

---

## Prompt 

```
You are a Senior Product Manager and Software Architect. Your task is to design the first version of "LTI", a next-generation Applicant Tracking System (ATS) for a startup entering the HR tech market.

Output everything in a SINGLE markdown file. Use professional, concise language. Every section must include both written explanation AND diagrams (Mermaid syntax inside ```mermaid code blocks).

Follow these steps IN ORDER. Do not skip any step. Do not summarize or abbreviate.

---

## STEP 1 — Product Definition

### 1.1 Software Description
Write a 2-paragraph description of LTI. Explain what it is, what problem it solves, and how it differs from traditional ATS platforms. Position it as an "AI-native recruitment copilot".

### 1.2 Value Proposition
Create a markdown table with 5 rows. Columns: "Aspect" | "Value LTI Delivers". Cover: Speed, Quality, Collaboration, Candidate Experience, Actionable Data. Each row must include a specific measurable claim (e.g., "Reduces time-to-hire by 60%").

### 1.3 Competitive Advantages
Analyze LTI's positioning against THREE competitor tiers:
1. Market leaders (Greenhouse, Lever) — explain 3 advantages
2. Enterprise incumbents (Workday, iCIMS) — explain 3 advantages
3. Emerging players (Ashby, Teamtailor) — explain 3 advantages

### 1.4 Core Features
List exactly 6 core features. For each feature, use an emoji header, a title, and 4 bullet points describing specific capabilities. Features MUST cover:
- Multichannel job posting with AI-assisted descriptions
- AI-powered candidate screening (semantic, not keyword-based)
- Real-time collaboration between recruiters and hiring managers
- No-code workflow automation (drag & drop pipeline builder)
- Analytics and reporting dashboard
- Candidate communication and experience (portal + chatbot)

### 1.5 Lean Canvas
Create a Lean Canvas diagram using ASCII art (monospaced box drawing). It MUST include ALL 9 blocks: Problem (3 items), Solution (3 items), Unique Value Proposition, Unfair Advantage, Customer Segments, Key Metrics, Channels, Cost Structure, Revenue Streams. Include specific pricing tiers (Free/Pro/Enterprise with prices).

---

## STEP 2 — Use Cases

Define exactly 3 use cases. For EACH use case, provide ALL of the following:

- **Title** (descriptive)
- **Primary actor** and **secondary actors**
- **Precondition** and **postcondition**
- **Main flow**: numbered steps (minimum 8 steps per use case)
- **Alternative flows**: at least 3 per use case (numbered as extensions, e.g., "3a.", "7a.")
- **Mermaid diagram**: a `flowchart TB` diagram showing the flow with actors as external nodes, system steps inside a subgraph, and dotted lines to external systems (AI, calendars, job boards, etc.)

The 3 use cases MUST be:
1. **AI-Assisted Job Posting** — recruiter creates a position, AI generates optimized description, bias check, multichannel publishing
2. **Collaborative Candidate Evaluation** — AI pre-screens CVs with scoring, team evaluates via shared real-time scorecards, collaborative decision
3. **Automated Pipeline & Interview Scheduling** — visual pipeline builder, automation rules, calendar integration, AI suggests time slots, candidate self-schedules

---

## STEP 3 — Data Model

### 3.1 Entity Definitions
Define a minimum of 10 entities. For EACH entity, create a markdown table with columns: "Attribute" | "Type" | "Description".
- Use standard SQL types: UUID, VARCHAR(n), TEXT, INTEGER, DECIMAL(p,s), BOOLEAN, TIMESTAMP, ENUM, JSONB, TEXT[]
- Every entity must have: id (UUID PK), created_at (TIMESTAMP)
- Foreign keys must be explicitly marked as (FK) with the referenced entity clear from context
- ENUM fields must list all possible values

Required entities (minimum): Company, User, JobPosition, Pipeline, PipelineStage, Candidate, Application, Interview, InterviewParticipant, Evaluation, AIRecommendation, Notification, PublishingChannel.

### 3.2 ER Diagram
Create a Mermaid `erDiagram` showing ALL entities and their relationships with proper cardinality notation (||--o{, }o--||, etc.).

### 3.3 Relationships Table
A markdown table listing every relationship with columns: "Relationship" | "Cardinality" | "Description".

---

## STEP 4 — High-Level System Architecture

### 4.1 Architecture Description
Describe a cloud-native microservices architecture organized in 6 layers:
1. **Presentation Layer**: SPA frontend, candidate portal
2. **API Layer**: API Gateway, GraphQL aggregation, WebSocket server
3. **Business Services Layer**: List each microservice (minimum 9) with its responsibility
4. **Data Layer**: PostgreSQL (multi-tenant RLS), Redis, Elasticsearch, S3
5. **Messaging Layer**: Message broker for async communication
6. **Infrastructure Layer**: Container orchestration, observability stack

Also include a section on key architectural decisions (multi-tenancy strategy, event-driven communication, real-time collaboration approach, AI service isolation).

### 4.2 Architecture Diagram
Create a Mermaid `graph TB` diagram showing ALL layers, ALL services, ALL data stores, ALL external integrations, with proper connection lines (solid for sync, dotted for external). Group components using `subgraph` blocks.

---

## STEP 5 — C4 Diagram (AI Service Deep Dive)

Choose the AI Service as the component to decompose. Create THREE C4 levels:

### 5.1 Level 1 — System Context
Mermaid diagram showing LTI as a single box, with 3 user personas and 4+ external systems. Apply C4 color conventions (dark blue for people, blue for system, gray for external).

### 5.2 Level 2 — Container Diagram
Mermaid diagram showing all containers inside LTI: frontend, API gateway, each microservice (with technology stack label), data stores, and message broker. Highlight the AI Service in a distinct color (orange).

### 5.3 Level 3 — Component Diagram (AI Service internals)
Mermaid diagram decomposing the AI Service into components organized in 3 subgroups:
- **Core AI Components** (minimum 5): CV Screening Engine, Candidate Matching Engine, Bias Detection Module, Generative AI Module, Predictive Analytics Engine
- **Infrastructure Components** (minimum 4): Embedding Store, Model Cache, Task Queue Consumer, LLM Gateway
- **MLOps & Governance** (minimum 3): Model Registry, Model Monitor, Explainability Engine

Show external connections: which other microservices call the AI Service (with endpoint labels), connections to data stores, and connections to external LLM providers.

### 5.4 Component Description Table
A markdown table with columns: "Component" | "Technology" | "Responsibility" — one row per component from the Level 3 diagram.

---

## STEP 6 — Summary
Write a 3-paragraph closing summary covering: (1) the three strategic pillars of LTI, (2) why the architecture supports growth from startup to enterprise, (3) why the AI Service design addresses regulatory and ethical concerns (EU AI Act, bias detection, explainability).

---

## FORMAT CONSTRAINTS
- Single markdown file, properly structured with ## and ### headers
- All diagrams in Mermaid syntax (```mermaid blocks)
- The Lean Canvas MUST use ASCII art (not Mermaid)
- Tables must use proper markdown pipe syntax
- Do not use placeholder text like "TBD" or "TODO"
- Do not include a table of contents
- Language: Spanish (technical terms may remain in English)
```

---

## Notes

The full document ([LTI-MDH.md](LTI-MDH.md)) was generated in a single iteration using this prompt with GitHub Copilot (Claude Opus 4.6), producing:
- Competitive analysis against 6 ATS platforms (Greenhouse, Lever, Workday, iCIMS, Ashby, Teamtailor)
- Lean Canvas in ASCII art with SaaS pricing model
- 3 detailed use cases with Mermaid flowcharts
- Data model with 13 entities, typed attributes, and Mermaid ER diagram
- Microservices architecture (9 services) with full Mermaid diagram
- C4 diagram at 3 levels (Context → Containers → Components) for the AI Service, with 13 internal components
