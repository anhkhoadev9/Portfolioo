# Huynh Anh Khoa
**Backend .NET Developer & Technical Business Analyst**  
Ho Chi Minh City, Vietnam | [Live Dossier](https://anhkhoadev9.github.io/Portfolioo/) | [GitHub](https://github.com/anhkhoadev9) | [Email](mailto:huynhankhoa30042019@gmail.com)

---

> [!NOTE]
> ### Executive Summary
> Systems-oriented Software Engineer specializing in the **.NET 8 ecosystem** (`C# 12`, `ASP.NET Core`, `Clean Architecture`, `CQRS`) combined with rigorous **Technical Business Analysis (Tech BA)** competency. Bridges the gap between complex enterprise workflows and high-throughput backend implementations through deterministic domain modeling, structured requirements engineering (`BPMN 2.0`, `SRS/BRD`), and low-latency distributed I/O systems.

---

## Strategic Engineering Stack

| Engineering Layer | Core Technologies & Protocols | Architectural Capabilities |
| :--- | :--- | :--- |
| **Runtime & Framework** | `.NET 8 LTS`, `C# 12`, `ASP.NET Core Web API`, `Minimal APIs` | Asynchronous non-blocking I/O, dependency injection container, strongly typed options pattern |
| **System Architecture** | `Clean Architecture`, `CQRS (MediatR)`, `DDD Tactical Patterns`, `SOLID` | Strict 4-layer isolation, decoupled command/query dispatching, zero domain leakage |
| **Real-Time & Media** | `SignalR (WebSockets)`, `WebRTC Peer-to-Peer`, `Signed URLs (TTL)` | Sub-50ms bidirectional state dispatching, zero-server media relays, ephemeral authorization tokens |
| **Persistence & Cache** | `PostgreSQL`, `Microsoft SQL Server`, `Entity Framework Core`, `Redis` | Optimized execution plans, composite index tuning, in-memory sliding window caching |
| **Security & Compliance** | `PostgreSQL Row Level Security (RLS)`, `JWT / Bearer Auth`, `Audit Logs` | Database-enforced tenant isolation, zero-trust perimeter, cryptographically signed URL invalidation |
| **Infrastructure & CI** | `Docker`, `Docker Compose`, `Git`, `GitHub Actions`, `Vitest` | Multi-stage image minimization, isolated testing environments, automated pipeline integration |

---

## Systems Architecture Topology

```text
+-----------------------------------------------------------------------------+
|                          BUSINESS DOMAIN LAYER                              |
|   Stakeholder Requirements  -->  BPMN 2.0 Flowchart  -->  SRS & User Stories |
+-----------------------------------------------------------------------------+
                                      |
                                      v
+-----------------------------------------------------------------------------+
|                         APPLICATION CONTRACT LAYER                          |
|         OpenAPI / Swagger 3.0 Specs  <--->  Client DTO Definitions          |
+-----------------------------------------------------------------------------+
                                      |
                                      v
+-----------------------------------------------------------------------------+
|                      CORE ARCHITECTURE & BACKEND (.NET 8)                   |
|   [ Controllers / Minimal APIs ]                                            |
|                 |                                                           |
|                 v                                                           |
|   [ MediatR Pipeline ] ---> ( Validation / Authorization / Logging )        |
|                 |                                                           |
|       +---------+---------+                                                 |
|       |                   |                                                 |
|       v                   v                                                 |
|  [ Commands ]        [ Queries ]                                            |
|  (State Mutation)    (Read-Optimized Projections)                           |
|       |                   |                                                 |
+-------+-------------------+-------------------------------------------------+
        |                   |
        +---------+---------+
                  |
                  v
+-----------------------------------------------------------------------------+
|                    INFRASTRUCTURE & PERSISTENCE LAYER                       |
|   EF Core / Dapper  -->  PostgreSQL / MS SQL Server  -->  Redis Cache       |
|   SignalR Hubs      -->  Real-Time Bidirectional Event Broadcast            |
|   Storage Engine    -->  Private Cloud Buckets + Signed URLs (TTL 60s)      |
+-----------------------------------------------------------------------------+
```

---

> [!TIP]
> ### Technical Business Analysis & Systems Elicitation
> - **Domain Process Modeling**: Translating ambiguous business rules into formalized `BPMN 2.0` process definitions, swimlane operational workflows, and `UML Sequence Diagrams`.
> - **Contract-First API Governance**: Engineering unified `OpenAPI 3.0 (Swagger)` interface contracts prior to implementation, unlocking parallel frontend/backend sprint cadence and eliminating schema drift.
> - **Requirements Determinism**: Formulating unambiguous Software Requirements Specifications (`SRS`), Business Requirements Documents (`BRD`), and User Stories backed by Gherkin-aligned Acceptance Criteria (`Given-When-Then`).

---

## Featured Engineering Case Studies

### 1. Queue Management System
*High-concurrency ticket dispatching and real-time counter orchestration*

- **Business Problem**: In-person service counters and clinical registration environments suffer severe operational bottlenecks, customer friction, and scheduling blindspots when ticket assignment relies on manual dispatching.
- **System Solution**: Engineered an event-driven queue orchestration engine. Counter operators trigger atomic ticket-call events, instantly propagating state updates to distributed public display terminals via bidirectional WebSocket channels without polling.
- **Architectural Blueprint**:
  - Structured strictly around **Clean Architecture**, enforcing inversion of control across Domain, Application, Infrastructure, and API boundaries.
  - Implemented **CQRS via MediatR**, decoupling state-mutation commands (`CreateTicketCommand`, `CallNextTicketCommand`) from high-frequency projection queries.
  - Deployed `SignalR` hub infrastructure to broadcast real-time state mutations with sub-50ms operational latency.
  - Backed by **PostgreSQL** with indexed state transitions (`Queued` -> `Calling` -> `Servicing` -> `Resolved`).
  - Packaged via multi-stage **Docker** containerization for reproducible zero-drift deployment.

---

### 2. Project M: Memeries Vault
*Zero-leak private media storage and real-time encrypted communication space*

> [!WARNING]
> **Zero-Trust Storage Constraint**: Media assets within private vaults must strictly prohibit persistent direct URLs, public cloud bucket traversal, and cross-tenant enumeration attacks (`IDOR`).

- **Business Problem**: Private multi-user platforms require absolute cryptographic and architectural data isolation. Media assets, telemetry, and private messages must remain completely inaccessible to unauthenticated third parties, even if asset URLs are leaked.
- **System Solution**: Architected an end-to-end secured data vault utilizing a **Feature-Driven Architecture** underpinned by database-enforced row policies, ephemeral signed access tokens, and peer-to-peer real-time media streams.
- **Architectural Blueprint**:
  - **Database-Enforced Access Control**: Enforced PostgreSQL `Row Level Security (RLS)` across all entity tables, mandating `auth.uid() = partner_id` at the database kernel level to eliminate `IDOR` vulnerabilities.
  - **Ephemeral Token Streaming**: Media assets reside inside private cloud buckets; clients receive cryptographically signed URLs with a short Time-to-Live ($\text{TTL} = 60\text{s}$ to $300\text{s}$), rendering captured links inert.
  - **Sliding Window Rate Limiter**: Formulated an in-memory sliding window rate limiter operating at $\mathcal{O}(1)$ map lookup time, safeguarding signaling and dispatch endpoints from abuse.
  - **WebRTC Peer-to-Peer Encryption**: Integrated direct WebRTC audio/video signaling over secure peer connections, ensuring media streams bypass intermediate servers and remain end-to-end encrypted.
  - **Security Telemetry Engine**: Constructed an immutable `security_logs` audit pipeline capturing actor IP, identity signature, endpoint, and severity level for continuous intrusion detection.

---

### 3. Blazor Enterprise Management App
*Internal enterprise portal with unified C# full-stack validation and data orchestration*

- **Business Problem**: Enterprise operations demand centralized catalog and workforce management tools that guarantee uniform validation, deterministic state synchronization, and low operational overhead.
- **System Solution**: Constructed a full-stack enterprise portal utilizing **Blazor Web App (.NET 8)**, leveraging Server-Side Rendering (`SSR`) for instantaneous baseline rendering and WebAssembly (`WASM`) for reactive data grids.
- **Architectural Blueprint**:
  - Leveraged unified C# domain models across both browser execution context and backend services, eliminating serialization discrepancies.
  - Engineered an **Entity Framework Core** persistence layer featuring composite indexing, server-side pagination, and deferred `IQueryable` evaluation.
  - Standardized domain input validation using `FluentValidation` pipelines integrated into the component lifecycle.

---

> [!IMPORTANT]
> ### Engineering Philosophy & Governance
> 1. **Determinism Precedes Code**: Eliminating ambiguity in domain specifications and data contracts prior to writing code prevents costly structural redesigns at later delivery stages.
> 2. **Maintainability Over Obscurity**: Production code is maintained and audited far more frequently than it is written. Explicit variable naming, clear layer boundaries, and documented design rationale supersede short-sighted algorithmic shortcuts.
> 3. **Systematic Root-Cause Remediation**: Operational defects and architectural bottlenecks must be analyzed to their fundamental origin rather than concealed with transient patches.

---

## Education & Academic Background

- **Dong Thap University** — Bachelor of Science in Software Engineering
  - **Core Academic Focus**: Design and Analysis of Algorithms, Data Structures, Relational Database Management Systems, Object-Oriented Software Design, Distributed Systems Principles, Software Quality Assurance.

---

## Professional Registry

- **Full Name**: Huynh Anh Khoa
- **Primary Specialization**: Backend .NET Developer & Technical Business Analyst
- **Physical Location**: Ho Chi Minh City, Vietnam
- **Direct Mail**: [huynhankhoa30042019@gmail.com](mailto:huynhankhoa30042019@gmail.com)
- **Source Repository**: [github.com/anhkhoadev9](https://github.com/anhkhoadev9)
- **Interactive Portfolio**: [anhkhoadev9.github.io/Portfolioo](https://anhkhoadev9.github.io/Portfolioo/)
