# Free Sample — SQL: Why Indexes Make Queries Instant

> **Difficulty:** Beginner · **Time:** ~20 minutes · **Level:** First taste of the PostgreSQL track.
> **Outcome:** you'll see a slow query become instant, understand *why*, and never write an unindexed lookup again.

---

## 1. Why this lesson exists

The paid SQL track runs 182 chapters deep (window functions, EXPLAIN, pgvector, transactions). It powers both portfolio projects. But the **single most valuable idea** in all of it is: **an index turns a full scan into a jump lookup.** Learn it once, here, and you'll instantly understand why databases are fast.

## 2. Setup (2 minutes)

```bash
docker run --name pg -e POSTGRES_PASSWORD=p -d postgres:16-alpine
docker exec -it pg psql -U postgres -c "CREATE DATABASE demo;"
```

## 3. A table, then the pain (5 minutes)

```sql
CREATE TABLE users (
  id BIGSERIAL PRIMARY KEY,
  email TEXT UNIQUE,
  created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);
```

Generate 1 million rows (pg `generate_series` is perfect for this) and then run:

```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'x@y.com';
```

Without an index that's a **sequential scan** — Postgres walks all 1M rows. `EXPLAIN ANALYZE` is how you *see* it: it prints the actual plan and time.

## 4. The fix (2 minutes)

```sql
CREATE INDEX idx_users_email ON users (email);
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'x@y.com';
```

Now it's an **index scan** — milliseconds instead of seconds. The `email` column above already got one from `UNIQUE`, so for a real demonstration create the table without UNIQUE, or index `created_at` and query a range:

```sql
CREATE INDEX idx_users_created ON users (created_at);
EXPLAIN ANALYZE
  SELECT * FROM users WHERE created_at > now() - interval '1 day';
```

## 5. What you just learned

- **Sequential scan** = read everything. **Index scan** = jump straight to the result.
- `EXPLAIN ANALYZE` is the debugger — never guess, look.
- The data structure behind the default index is a **B-Tree** (the paid track + the CS track cover it in depth).

That's the entire "performance thinking" habit: shape the query, verify with `EXPLAIN ANALYZE`, add the index, re-verify.

---

## 🚧 Where the paid curriculum begins (the gate)

| This free step | The paid next step (SQL track) |
|---|---|
| One bare table | Keys, constraints, normalization, all 7 JOIN types |
| SELECT with explain | Window functions (`OVER`/`PARTITION BY`, RANK, LAG), CTEs, recursive CTEs |
| A B-Tree index | Hash/GIN/GiST/partial/expression/composite indexes, `VACUUM`, bloat |
| Running locally | Isolation levels, locks, deadlocks, **ACID** deeply |
| Text search | Full-text (`tsvector`), **pgvector** + HNSW |
| One database | Replication, RLS, partitioning, caching (Redis) |
| — | 14 mock OAs + SQL system-design chapters |

The full 182-chapter SQL track and its **Senior Dev Insights** are inside the curriculum → **[UPGRADE.md](../UPGRADE.md)**.

---

> **Try this now:** run the `EXPLAIN ANALYZE` before and after the index and note both times. That before/after pair is the exact habit the paid track drills into every performance chapter.