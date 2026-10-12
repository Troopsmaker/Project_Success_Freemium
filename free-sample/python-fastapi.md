# Free Sample — Python & FastAPI: From a Variable to a Live Endpoint

> **Difficulty:** Beginner · **Time:** ~20 minutes · **Level:** The first step of the Python & FastAPI track.
> **Outcome:** you will run a live HTTP API that accepts a name and returns a greeting — with zero framework magic you don't control.

---

## 1. Why this lesson exists

You can learn Python syntax anywhere. What the full curriculum teaches — and what this sample previews — is the **leap from "a script that runs on your laptop" to "an API that servers run"**. FastAPI is the fastest, most opinionated way to make that leap, and it's the backbone of the paid track's AI/RAG build.

This free lesson gets you to a **live endpoint**. The next chapter — the first paid step — takes that endpoint and makes it **production-shaped**: typed models, validation, dependency injection, and tests.

---

## 2. Your first variables (30 seconds)

```python
name = "student"          # str
days_completed = 0        # int
progress = 0.5            # float
is_learning = True        # bool
```

Python infers types at runtime. You'll *feel* the difference when the paid track moves you to Go, where types are strict and checked at compile time.

## 3. A function (30 seconds)

```python
def greet(person: str) -> str:
    return f"Hello, {person}!"
```

Type hints (`: str`, `-> str`) are Python's contract. FastAPI **uses them** to build validation and docs automatically.

## 4. Make it an endpoint (5 minutes)

FastAPI turns a Python function into an HTTP endpoint with a single decorator:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Project Success sample"}

@app.get("/greet/{name}")
def greet_endpoint(name: str):
    return {"greeting": f"Hello, {name}!",
            "track": "Python & FastAPI",
            "chapter": "free sample"}
```

## 5. Run it (2 minutes)

```bash
pip install "fastapi[standard]"
uvicorn main:app --reload
```

Open `http://127.0.0.1:8000/docs` — FastAPI gives you an interactive Swagger UI **for free**, generated from your type hints. Hit `/greet/{name}` in your browser and you have a live API.

## 6. What you just proved

- A Python function ⇄ an HTTP endpoint (one decorator).
- Type hints drive automatic validation + docs.
- You can run a server with one command.

**That's the habit:** small, runnable, verified. Every chapter in the curriculum ends with a running thing, not a lecture.

---

## 🚧 Where the paid curriculum begins (the gate)

| This free step | The paid next step (Python track) |
|---|---|
| Return a dict | **Pydantic models** — typed request/response shapes with validation errors returned as JSON |
| Hardcoded string | **Path + query params**, request bodies, and error handling |
| One endpoint | FastAPI **Dependency Injection**, middleware, CORS, background tasks |
| No database | SQLAlchemy + **Alembic migrations** |
| No auth | **JWT + OAuth2 + bcrypt + RBAC** |
| No AI | OpenAI, LangChain, and the **RAG pipeline with pgvector** |

The full order, every one of the 175 Python-track chapters, and each chapter's **Senior Dev Insight** (the interview payload) are inside the curriculum → **[UPGRADE.md](../UPGRADE.md)**.

---

> **Try this now:** change the greeting string and run it again. That "edit → see it live" loop is the entire method.