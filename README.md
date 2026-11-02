# Huynh Anh Khoa
### Backend .NET Developer & Technical Business Analyst

[Live Portfolio](https://anhkhoadev9.github.io/Portfolioo/) • [GitHub](https://github.com/anhkhoadev9) • [Email](mailto:huynhankhoa30042019@gmail.com) • Ho Chi Minh City, Vietnam

---

## Overview

Software Engineer with a primary focus on the **.NET ecosystem** (.NET 8, C# 12) and modern backend architectures (**Clean Architecture, CQRS, Real-time WebSockets**). Combines strong programming practices with **Technical Business Analysis (Tech BA)** skills to translate business logic, domain constraints, and workflow requirements into robust, maintainable, and scalable systems.

---

## Core Competencies

### Backend Engineering & Architecture
- **Platforms & Languages**: C# 12, .NET 8 (LTS), ASP.NET Core Web API, Minimal API, Blazor (SSR & Interactive WASM).
- **Design Patterns & Architecture**: Clean Architecture (4-layer isolation), CQRS (MediatR), Repository & Unit of Work, Dependency Injection, SOLID principles.
- **Real-Time Communication**: SignalR WebSockets for high-throughput, low-latency client-server event dispatching.
- **Testing & Quality Assurance**: Vitest, automated unit testing, error handling pipeline behaviors.

### Data Management & Security
- **Relational Databases**: PostgreSQL, Microsoft SQL Server, Entity Framework Core, Dapper.
- **Access Control & Privacy**: PostgreSQL Row Level Security (RLS) for tenant/user isolation, Signed URLs with Time-to-Live (TTL) tokens.
- **Traffic & Rate Management**: In-Memory Sliding Window Rate Limiter algorithms (O(1) lookup).
- **DevOps & Containers**: Docker, Docker Compose, Git, GitHub Actions.

### Technical Business Analysis
- **Process & Workflow Modeling**: BPMN 2.0 flowcharts, UML Sequence Diagrams, Use Case modeling.
- **Requirements Engineering**: Software Requirements Specifications (SRS), Business Requirements Documents (BRD), User Stories with structured Acceptance Criteria.
- **Interface Contracts**: OpenAPI / Swagger design-first specifications, Postman collection testing & API mocking.

---

## Featured Projects

### 1. Queue Management System
*High-concurrency ticket dispatching and real-time counter orchestration*

- **Problem**: In-person service congestion and disorganized ticketing in branch offices and service counters.
- **Solution**: Automated ticket distribution system where counter staff trigger next-in-line calls, instantly broadcasting real-time display board updates via WebSockets without page reload.
- **Technical Highlights**:
  - Structured using **Clean Architecture** to eliminate domain logic leaks.
  - Implemented **CQRS with MediatR** to cleanly separate write commands from read-heavy dashboard queries.
  - State tracking backed by **PostgreSQL** (`Waiting`, `In-Service`, `Completed`).
  - Containerized with **Docker** for standardized deployment environments.

### 2. Project M: Memeries Vault
*Private media storage and real-time communication space*

- **Problem**: Zero-leak private social and photo vault requiring strict data privacy, prevention of direct link scraping, and absolute protection against Insecure Direct Object References (IDOR).
- **Solution**: Feature-driven architecture built on top of Supabase (PostgreSQL with RLS), WebRTC, and time-restricted token streaming.
- **Technical Highlights**:
  - **PostgreSQL Row Level Security (RLS)**: Enforced database-level policies ensuring only verified paired accounts can query or mutate corresponding records.
  - **Signed URLs (TTL)**: Media assets stored in private buckets; delivered via cryptographically signed temporary URLs expiring within minutes to prevent unauthorized sharing.
  - **In-Memory Sliding Window Rate Limiter**: Custom sliding window implementation with O(1) map operations to protect sensitive endpoints from brute-force and request abuse.
  - **WebRTC Peer-to-Peer Calling**: Direct audio/video calling using end-to-end encrypted peer connections with near-zero latency.
  - **Security Audit Logs (`security_logs`)**: Real-time logging of actor IPs, endpoints, and severity levels for anomaly detection.

### 3. Blazor Enterprise Management App
*Internal enterprise portal with unified C# full-stack components*

- **Problem**: Need for a maintainable, high-performance administrative dashboard with unified validation rules across client and server.
- **Solution**: Built using **Blazor Web App (.NET 8)** combining Server-Side Rendering (SSR) for initial load speed and WebAssembly (WASM) for rich dashboard interactions.
- **Technical Highlights**:
  - Unified data models and business rules across both frontend and backend using pure C#.
  - Integrated **Entity Framework Core** with optimized query indexes, dynamic filtering, and pagination.
  - Server-side data validation utilizing FluentValidation.

---

## Engineering Principles

1. **Clarity Before Code**: Solving the wrong problem efficiently is still wasted effort. Clarifying domain logic, user stories, and acceptance criteria upfront prevents database re-architecting later.
2. **Readability Over Cleverness**: Code is written once but read hundreds of times by teammates. Naming conventions, explicit intent, and clean modular boundaries take precedence over cryptic one-liners.
3. **Accountability & Root-Cause Analysis**: Approaching defects and code reviews objectively by identifying fundamental root causes rather than applying surface-level patches.

---

## Education

- **Dong Thap University** — Bachelor of Science in Software Engineering
  - Strong foundation in Algorithms, Data Structures, OOP, Database Systems, and Distributed Computing.

---

## Contact

- **Email**: [huynhankhoa30042019@gmail.com](mailto:huynhankhoa30042019@gmail.com)
- **GitHub**: [github.com/anhkhoadev9](https://github.com/anhkhoadev9)
- **Location**: Ho Chi Minh City, Vietnam
