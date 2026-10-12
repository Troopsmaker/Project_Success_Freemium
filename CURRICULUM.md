# The 180-Day Map — as Designed (Public Preview)

> This is the **structure** of the full curriculum: six tracks, an 180-day parallel cadence, and time-boxed lessons. It is published so you can see exactly how the journey is built — and where the free line sits. **The chapters themselves are the paid curriculum.** The rows below are gate markers, not links to free content.

---

## How the engine runs (free to read)

```
Every day, in a fixed order, six tracks advance together:
  Applications → Interview Prep → SQL → Python → Go → Flutter → CS → DSA → Project → Revision → Review
```

- **Time labels:** early days are short (20–40 min), senior weeks run longer (45–60 min).
- **One day covers all six tracks** — you never fall into single-track boredom.
- **Sections end where the plan ends, not at 180** — Python runs 175 days, Flutter 154, Go 163, SQL 182, CS 180, DSA 180. The map is the plan, not a magic number.

---

## Track 1 — Python & FastAPI + AI (175 days)

| Block | What you become able to do | Where |
|---|---|---|
| Core language | variables → generators → decorators → dataclasses | in course |
| Concurrency & runtime | threading, multiprocessing, GIL, asyncio event loop | in course |
| FastAPI | routing, Pydantic, dependency injection, middleware, CORS | in course |
| Auth & DB | JWT, OAuth2, bcrypt, RBAC, SQLAlchemy, Alembic | in course |
| Redis & Celery | caching, pub/sub, distributed queues, cron | in course |
| Testing | pytest, fixtures, TestClient | in course |
| AI & LLMs | OpenAI, LangChain, embeddings, **pgvector, RAG**, HyDE | [free sample](free-sample/python-fastapi.md) for the first step |
| Agents | ReAct, custom tools, **LangGraph**, multi-agent | in course |
| DevOps & deploy | Docker, CI/CD, Nginx, SSL, Prometheus/Grafana | in course |
| System design (Python) | URL shortener, chat, notifications, cron | in course |
| Mock interviews | GIL, memory leaks, WSGI/ASGI, CAP, JWT vs sessions… | in course |

## Track 2 — Flutter / Dart (154 days)

| Block | What you become able to do | Where |
|---|---|---|
| Dart language | null safety, streams, isolates, mixins | in course |
| Widgets & layout | widget tree, rows/columns, slivers, responsive | [free sample](free-sample/flutter-dart.md) for the first step |
| State | setState → Provider → **Riverpod** | in course |
| Networking & data | dio, JSON, freezed, Hive, sqflite | in course |
| The AI chat build | WebSockets, TTS/STT, camera, file upload | in course |
| Animation | implicit/explicit, Hero, Lottie, CustomPainter | in course |
| Testing | unit, widget, golden, integration, Mocktail | in course |
| Production | Firebase, push, method channels, profiling, ASO, stores | in course |

## Track 3 — Go (163 days)

| Block | What you become able to do | Where |
|---|---|---|
| Core language | slices, structs, pointers, interfaces | in course |
| **Concurrency** | goroutines, channels, select, worker pools, mutexes, atomics | [free sample](free-sample/go-concurrency.md) for the first step |
| Web | net/http, Gin, middleware, validation | in course |
| DB | pgx/database/sql, **sqlc**, Redis | in course |
| Architecture | clean architecture: domain → repository → usecase → delivery | in course |
| Distributed | **gRPC**, WebSockets, Kafka, RabbitMQ, tracing | in course |
| Quality | testing, benchmarks, pprof, race detector, fuzz, AST | in course |
| Design (Go) | URL shortener, chat server, image pipeline, payments | in course |

## Track 4 — SQL & PostgreSQL (182 days)

| Block | What you become able to do | Where |
|---|---|---|
| Core & CRUD | tables, keys, joins (all kinds), aggregation | in course |
| Advanced SQL | CTEs, recursive CTEs, **window functions**, LAG/RANK | [free sample](free-sample/sql-postgres.md) for indexing |
| Performance | **EXPLAIN ANALYZE**, B-Tree/hash/GIN indexes, vacuuming | in course |
| Transactions | ACID, isolation levels, locks, deadlocks | in course |
| Vector & search | **pgvector**, HNSW, full-text | in course |
| Admin & scale | RLS, replication, PITR, partitioning, caching | in course |
| SQL system design | e-commerce schema, event sourcing, multi-tenant | in course |
| 14 mock OAs | the classic → the final comprehensive exam | in course |

## Track 5 — CS Fundamentals (180 days)

| Block | What you become able to do | Where |
|---|---|---|
| OS | processes, threads, scheduling, IPC, deadlock, virtual memory | in course |
| Networking | OSI/TCP-IP, DNS, HTTP/1·2·3, TLS | in course |
| Security | encryption, JWT, OAuth2, CORS, XSS/CSRF/SQLi | in course |
| System design | CAP, sharding, caching, message queues, microservices | in course |
| 16+ full designs | URL shortener → Uber → Ticketmaster | in course |
| Behavioral | 10 STAR scripts | in course |

## Track 6 — DSA (180 days)

| Block | What you become able to do | Where |
|---|---|---|
| Foundations | Big O, hash maps, arrays | in course |
| The 150 grind | two pointers → sliding window → trees → graphs → DP | [free sample](free-sample/dsa-patterns.md) for the unlock pattern |
| Advanced graphs | Dijkstra, Kruskal, union-find, topo | in course |
| Mock OA patterns | monotonic stack/queue, sweep line, greedy intervals | in course |
| 6 timed OA mocks | the gauntlet | in course |

---

## Where the free line sits

| Kind | Status |
|---|---|
| The **method** (how the engine runs) | **Free** — see [README](README.md) |
| One **beginner lesson** per track | **Free** — see `free-sample/` |
| The **curriculum shape** (this map) | **Free** — designed to show the journey |
| Project **showcases** (shape only) | **Free** — see `projects/` |
| Every **chapter**, insight, solution, and build | **Paid** — [UPGRADE.md](UPGRADE.md) |

> This map is deliberately asymmetric: you can see **where the journey goes** and **experience its first step**, but the substance is earned through the curriculum. Don't try to reconstruct the hidden chapters from this preview — the full depth is the product.