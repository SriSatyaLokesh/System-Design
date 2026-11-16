[🏠 Home (System-Design)](../README.md) > **Distributed Caching**

# 🚀 Distributed Caching at Scale

> High-performance caching strategies, distributed Redis topologies, cache consistency patterns, and concurrency mitigation for scalable backend systems.

---

## 📌 Overview

Caching is the primary architectural mechanism used to reduce data access latency, minimize relational database load, and prevent downstream network bottlenecks in high-throughput applications.

### Core Caching Topologies & Patterns

1. **Cache-Aside (Lazy Loading):**
   - Application queries cache first. On cache miss, reads from primary database, writes entry into cache with TTL, and returns response.
   - *Best for:* Read-heavy workloads with tolerable eventual consistency.

2. **Write-Through:**
   - Application writes to cache; cache immediately writes synchronously to the database before acknowledging.
   - *Best for:* Strict data consistency between cache and DB; slightly higher write latency.

3. **Write-Behind (Write-Back):**
   - Application writes to cache; cache asynchronously persists batches to the primary database.
   - *Best for:* High-frequency write scenarios (e.g. telemetry, vote counting). Requires persistence guarantees.

4. **Cache Stampede / Thundering Herd Prevention:**
   - Multiple concurrent processes experience a simultaneous cache miss on an expired hot key.
   - *Mitigation:* Mutex locks (single re-computation), probabilistic early expiration (**XFetch algorithm**), or asynchronous background refresh.

---

## 📚 Included Reference Books

This directory contains foundational industry literature for mastering Redis and caching at scale:

- **`caching-at-scale-with-redis-updated-2021-12-04.pdf`** — Architectural patterns for deploying Redis across clustered enterprise environments, persistence configurations (RDB/AOF), and multi-region replication.
- **`Redis_For_Dummies_Limited_Edition.pdf`** — Rapid onboarding reference for Redis data structures (Strings, Hashes, Lists, Sets, Sorted Sets, Bitmaps, and HyperLogLogs).

---

## 🔗 Related Resources

- [System Design Foundations](../README.md#-system-design--distributed-architecture-foundations)
- [Real-Time Notification Systems](../Notification%20Systems/notes.md)
- [Agentic AI Learning Pathway](../Agentic%20AI/README.md)
