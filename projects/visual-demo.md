# Showcase — Visual Demo Layer (Flutter)

> **Signal:** product sense. Backend is invisible; this project makes a non-technical person *see* the systems working live. The "UI that a CEO could understand" test.

## The one-liner
A Flutter dashboard that **streams the Go processor's live telemetry over WebSockets** at 60fps, plus a polished chat interface into the RAG engine — **web + mobile from one codebase**.

## Why this project exists (the story)
The Event Processor and RAG Engine are invisible. A hiring manager can't *see* throughput. This layer is the proof UI: a real-time executive dashboard showing events flowing in, with a working chat box for document Q&A. It also proves the full microservice ecosystem talks to each other.

## What's shown (architecture — the depth lives in the paid curriculum)

```
[Go Event Processor ──WebSocket──► [Flutter Dashboard (60fps)]
[Python RAG API ──────HTTPS──────► [Flutter Chat UI]
            one Flutter codebase ──► web + iOS + Android
```

- **Realtime:** WebSockets + `StreamBuilder` for live rows streaming onto the screen.
- **State:** Riverpod providers above a clean UI layer.
- **Resilience:** reconnect/backoff when the socket drops (mobiles lose connections constantly).

## The metrics used to sell it
- **60fps** rendering while streaming live updates.
- **One codebase, three platforms** — the recurring-cost argument for a client.
- **Automatic reconnection** under flaky network — because mobile networks drop.

## The interview answer (why it's hard)
"WebSockets die constantly on mobile. How does your UI handle a user driving through a tunnel?" — the full graded answer (backoff, lifecycle handling, state recovery) is in the paid curriculum's Flutter project chapters.

> **Not public:** the source, the state architecture, the reconnect strategy, the golden tests. Inside the 180-day curriculum → **[UPGRADE.md](../UPGRADE.md)**.