[🏠 Home (System-Design)](../README.md) > **System Design Bibles**

# 🏛️ Software Architecture & System Design Bibles

> Masterworks on data-intensive systems, clean software architecture, reliability, and enterprise engineering patterns.

---

## 📌 Foundational Architecture Literature

Building reliable, scalable, and maintainable systems requires timeless engineering principles. This directory archives the definitive industry bibles for software architects and systems engineers:

### 1. *Designing Data-Intensive Applications (DDIA)* by Martin Kleppmann
- **Key Concepts:**
  - Reliable, Scalable, and Maintainable Systems (SLIs, SLOs, MTBF).
  - Data Models & Query Languages (Relational vs. Document vs. Graph).
  - Storage & Retrieval Engines (SSTables, LSM-Trees, B-Trees).
  - Encoding & Evolution (Thrift, Protocol Buffers, Avro).
  - Distributed Data: Replication (Single-leader, Multi-leader, Leaderless), Partitioning, and Sharding.
  - Transactions: ACID properties, isolation levels (Read Committed, Snapshot, Serializable), and concurrency bugs (Dirty reads, Non-repeatable reads, Phantom reads).
  - Distributed Consensus: Two-phase commit (2PC), Paxos, Raft, and linearizability.

### 2. *Clean Architecture: A Craftsman's Guide to Software Structure and Design* by Robert C. Martin ("Uncle Bob")
- **Key Concepts:**
  - SOLID Design Principles (Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).
  - Component Cohesion & Coupling (REP, CCP, CRP, ADP, SDP, SAP).
  - The Dependency Rule: Source code dependencies must only point inward toward higher-level policies.
  - Entities, Use Cases, Interface Adapters, and Frameworks.
  - Boundaries: Decoupling business logic from databases, user interfaces, and frameworks.

---

## 📚 Included Reference Books

- **`Designing Data-Intensive Applications The Big Ideas Behind Reliable, Scalable, and Maintainable Systems ( PDFDrive ).pdf`**
- **`Clean Architecture A Craftsman's Guide to Software Structure and Design.pdf`**

---

## 🔗 Related Resources

- [Distributed Caching Architecture](../Caching/README.md)
- [Enterprise Node.js Microservices](../Node%20JS/README.md)
- [Real-Time Notification Systems](../Notification%20Systems/notes.md)
- [Agentic AI Learning Pathway](../Agentic%20AI/README.md)
