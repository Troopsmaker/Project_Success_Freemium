# Free Sample — DSA: The One Pattern That Unlocks Half of LeetCode

> **Difficulty:** Beginner · **Time:** ~20 minutes · **Level:** The first unlock of the DSA track.
> **Outcome:** you'll understand **Big O** and the **hash map time-space tradeoff** — the exact reasoning that turns "I can't solve it" into "I know which tool to reach for."

---

## 1. Why this lesson exists

The DSA track is 180 chapters: arrays → trees → graphs → DP → mock OA tests. Every single one rests on **one habit of mind**: read the problem, see the pattern, estimate the cost — *before* writing the loop. This free lesson installs that habit.

## 2. Big O in ten seconds

- **O(1)** — constant: a lookup by index, e.g. `list[5]`.
- **O(N)** — linear: search a list of N items, worst case check all N.
- **O(N²)** — nested loop over N items: N×N checks.
- **O(log N)** — halving: binary search.

The question is always the same: **how does the work grow as the input grows?** That growth rate is the complexity.

## 3. The tradeoff that unlocks Everything (the point)

> **Hash map: swap memory for time.**

```python
# O(N²) — for each item, scan all the others
def find_pair_slow(nums, target):
    for i in range(len(nums)):
        for j in range(len(nums)):
            if i != j and nums[i] + nums[j] == target:
                return (i, j)
    return None

# O(N) — remember what you've seen, check in O(1)
def find_pair_fast(nums, target):
    seen = {}              # value -> its index
    for i, v in enumerate(nums):
        need = target - v
        if need in seen:
            return (seen[need], i)
        seen[v] = i
    return None
```

Same answer. **O(N²) → O(N)** — just by using a hash map to remember instead of re-scanning.

## 4. Why this is "half of LeetCode"

- **Two Sum** (the most famous interview question) *is* this pattern.
- "Have I seen X before?" **anywhere** → hash map.
- Counting frequencies, finding duplicates, deduplication, grouping → hash map.
- It's the foundation of the sliding-window and prefix-sum patterns in the paid track.

## 5. The habit to take away

```
1. Read the problem.
2. Ask: what's the naive cost? (usually O(N²) or O(N×M))
3. Ask: is the bottleneck a repeated search? → hash map
4. Ask: is it ordered / contiguous? → two pointers, sliding window, or binary search
5. Write the code, then state the complexity out loud.
```

Stating complexity out loud is exactly what interviewers grade. The paid track makes that automatic — every chapter ends with the pattern + its Big O.

---

## 🚧 Where the paid curriculum begins (the gate)

| This free step | The paid next step (DSA track) |
|---|---|
| The hash-map idea | Full **hash map implementation**: collisions, load factor, when O(1) becomes O(N) |
| Two Sum | The **150-problem grind** in verified order: strings → sliding window → trees → graphs → DP |
| Interactive reasoning | **Monotonic stacks/queues, union-find, Dijkstra, topo sort, sweep line** |
| One pattern | **6 full timed OA tests** and every code answer |
| Complexity instinct | Big O *and* **space** complexity for every chapter |

Each DSA chapter is Go/Python verified against the real runtime — no "trust me" code. The full curriculum → **[UPGRADE.md](../UPGRADE.md)**.

---

> **Try this now:** run both functions on a large list and feel the time difference. That difference IS Big O — you just installed the mental model that the next 179 chapters build on.