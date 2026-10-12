# Free Sample — Go: Goroutines Without the Fear

> **Difficulty:** Beginner-friendly · **Time:** ~20 minutes · **Level:** Your first taste of Go's superpower.
> **Outcome:** you'll run concurrent code — several things "at the same time" — and understand the one rule that keeps it safe.

---

## 1. Why this lesson exists

Python is the scripting engine, but when the paid curriculum wants **throughput** — 5,000 requests/sec, worker pools, microservices — it uses Go. The entire reason is **goroutines** and **channels**. This free lesson gives you the core idea safely. The paid track turns it into a production event processor.

## 2. Setup (2 minutes)

```bash
go mod init sample
# edit main.go, then:
go run .
```

## 3. A goroutine — the smallest concurrent unit

```go
package main

import (
	"fmt"
	"sync"
)

func worker(id int, wg *sync.WaitGroup) {
	defer wg.Done() // mark done when this returns
	fmt.Println("worker", id, "started")
	fmt.Println("worker", id, "done")
}

func main() {
	var wg sync.WaitGroup
	for i := 0; i < 4; i++ {
		wg.Add(1)      // announce one more task
		go worker(i, &wg) // run it concurrently
	}
	wg.Wait()          // wait for ALL workers
	fmt.Println("all done")
}
```

## 4. The two rules that make it safe

1. **Synchronize with `WaitGroup`** (or channels) — never let the main function finish before its goroutines.
2. **Don't share memory by racing on it.** If two goroutines write the same variable at the same time, you get a **data race**. The paid track teaches the full toolkit: mutexes, channels, the race detector, and worker pools.

Run this and watch the workers interleave in a different order every time — *that's concurrency*.

## 5. What you just proved

- A goroutine is just `go fn()` — a light, concurrent task.
- `sync.WaitGroup` = "wait for everyone before we exit."
- Concurrency is *structure*; parallelism (real simultaneous execution on multi-core) is what Go's scheduler gives you on top.

`go run -race .` — the **race detector** — is a superpower no other mainstream language ships so simply. The paid track uses it on every concurrency chapter.

---

## 🚧 Where the paid curriculum begins (the gate)

| This free step | The paid next step (Go track) |
|---|---|
| One goroutine + WaitGroup | **Channels** (buffered/unbuffered/directional) and `select` |
| Ordered printing | **Worker pools** and the **fan-in/fan-out** pattern |
| Raw ints | Structs, error handling (`if err != nil`), interfaces |
| No server | `net/http`, **Gin**, JSON, CORS |
| No system | **gRPC**, WebSockets, Redis, Kafka, sqlc |
| No build | testing, benchmarks, pprof, race detector, fuzz, AST |

The full 163-chapter Go track, the concurrency deep-dives, and each **Senior Dev Insight** are inside the curriculum → **[UPGRADE.md](../UPGRADE.md)**.

---

> **Try this now:** bump the loop to `i < 40` and rerun. Watch the interleaving pattern shift. That nondeterminism is exactly why synchronization matters — and why the paid track's worker-pool chapters will make sense so fast.