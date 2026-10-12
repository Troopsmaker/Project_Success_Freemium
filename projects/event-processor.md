# Showcase — High-Throughput Event Processor (Go)

> **Signal:** Go concurrency at real scale — the "systems" proof. A fresher who demonstrates goroutine worker pools and survivor-grade failure handling reads as a senior in the making.

## The one-liner
A Go ingestion engine that buffers high-velocity events in **Redis**, fans them out to a **goroutine worker pool**, and bulk-inserts into Postgres — sustaining **5,000+ requests/sec** without losing data or locking the database.

## Why this project exists (the story)
How do companies like Uber or Swiggy handle millions of incoming GPS pings without crashing? Answer: a pipeline that *buffers* (so a spike can't hit the DB directly), *fans out* (so many events process concurrently), and *bulk-inserts* (so you don't exhaust database IOPS). This project builds that engine and proves it with a load test.

## What's shown (architecture — the depth lives in the paid curriculum)

```
[Ingest API] --> [Redis buffer] --> [Goroutine worker pool] --> [bulk insert] --> [Postgres]
                                      (bounded concurrency, WAL-backed)
```

- **Concurrency:** goroutines + channels for fan-in/fan-out; a **bounded worker pool** so memory never explodes.
- **Buffering:** Redis holds the burst; workers drain it steadily.
- **Durability & idempotency:** on-conflict upserts so retries can't double-write.

## The metrics used to sell it
- **5,000+ req/s** sustained.
- **Race-detector clean** — `go run -race` with zero data races.
- **No memory leak** under stress (the leak-scan chapters exist for a reason).

## The interview answer (why it's hard)
"Redis is in-memory — what happens if it crashes mid-burst?" and "How do you guarantee no double-writes when a worker dies mid-insert?" — the full graded answers are in the paid curriculum's Go project chapters.

> **Not public:** the source, the worker-pool tuning, the failure-mode analysis (circuit breakers, backoff, idempotency), and the load-test harness. Inside the 180-day curriculum → **[UPGRADE.md](../UPGRADE.md)**.