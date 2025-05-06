# Course Notes: Creating Databases with AI Coding Tools

*Reference Codebase: [`/live-coding-outputs/2025_04_03_Databases`](../../live-coding-outputs/2025_04_03_Databases/)*

---

## 🔧 Overview

In this module, we explore how to design and implement databases using AI-assisted workflows combined with modern development tools like SQLModel, Prisma, SQLite, and [Supabase](../../tools/infrastructure/Supabase.md). The goal is to reduce friction in full-stack development by using LLMs to help scaffold and manage data infrastructure from both [Python](../../tools/foundational/Python.md) and [Node.js](../../tools/foundational/JavaScript.md) environments.

---

## 🔩 Part 1: The Modern Database Workflow

### 🧱 Traditional Approach

- Requires raw SQL knowledge
- Database setup is often slow and error-prone
- Hard to collaborate between backend/frontend teams

### 🚀 AI-Enhanced Workflow

- Start from natural language prompts
- AI generates schemas, models, ER diagrams, and plans
- Work in code-first ORMs that sync with SQL in the background
- Use built-in validators and type-checkers for reliability
- Easily migrate from local SQLite to hosted Supabase

---

## 📦 Part 2: Tech Stack Breakdown

### 🐍 Python Side (Backend + Modeling)

| Tool     | Role                          | Link                                              | Notes                                             |
| :------- | :---------------------------- | :------------------------------------------------ | :------------------------------------------------ |
| SQLModel | ORM layer for Python          | -                                                 | Combines SQLAlchemy + Pydantic for schema + validation |
| SQLite   | Local embedded database       | -                                                 | Zero setup, great for prototyping                 |
| UV       | Modern Python package manager | [UV Guide](../../tools/foundational_dev/UV.md)    | Faster than pip, useful for virtualenvs           |
| .env     | Environment configuration     | -                                                 | API keys, DB URLs, secrets (e.g., using `python-dotenv` package) |

### 🟩 Node.js Side (Frontend + Integration)

| Tool     | Role                           | Link                                              | Notes                                             |
| :------- | :----------------------------- | :------------------------------------------------ | :------------------------------------------------ |
| Prisma   | ORM for Node.js                | -                                                 | Schema-first development, migrations, type safety  |
| Supabase | Production-ready DB platform   | [Supabase Guide](../../tools/infrastructure/Supabase.md) | Built-in REST/GraphQL, auth, vector embeddings    |
| React    | Frontend framework             | -                                                 | Used to display data from Supabase (often via Next.js) |

---

## 🧠 Part 3: AI-Assisted Prompting Workflow

### 🌱 Core Prompts

Use prompts to generate key architectural artifacts:

- **Product Definition Prompt:**  
  "Define the purpose and user goals of the app. What problems does it solve?"

- **UX Definition Prompt:**  
  "Describe the key user interactions and screens."

- **Solution Architecture Prompt:**  
  "Generate a high-level architecture (frontend/backend/database)."

- **Data Architecture Prompt:**  
  "You're a data architect. Design a scalable relational schema to support both a Python backend using SQLModel and a Node.js backend using Prisma."

- **Project Planner Prompt:**  
  "Break down the implementation into clear, step-by-step tasks with checkboxes and complexity ratings (easy/medium/hard). Output in Markdown."

---

## 🧱 Part 4: From Prompt to Working Database

### 🧪 Step-by-Step Setup (Python)

```bash
# Initialize project with UV
uv init tacoquest 
cd tacoquest
# Create virtual environment (uv does this implicitly with sync/add)
uv venv 
# Add dependencies
uv add sqlmodel sqlite-utils python-dotenv 
```

**Recommended structure:**

```
tacoquest/
├── data/                 # SQLModel schema & mock data
├── plan.md               # Implementation plan in markdown
├── .env                  # Supabase credentials
├── main.py               # Entrypoint
└── requirements.txt
```

**Initialize your schema with SQLModel:**

```python
from sqlmodel import SQLModel, Field

class User(SQLModel, table=True):
    id: int | None = Field(default=None, primary_key=True)
    name: str
    email: str
```

**Create and seed the database:**

```bash
python main.py --seed
```

---

### 🌐 Supabase Integration

Set up your project via the [Supabase UI](https://supabase.com/)

Grab your API keys and DB URL and paste into `.env`:

```dotenv
SUPABASE_URL=https://xyz.supabase.co
SUPABASE_KEY=your_public_key
SUPABASE_SECRET=your_service_role_key
```

Then run the migration:

```bash
python main.py --migrate
```

---

## ⚙️ Part 5: Prisma Integration ([Node.js](../../tools/foundational/JavaScript.md))

```bash
# Example using Next.js
npx create-next-app frontend 
cd frontend
npm install prisma @prisma/client
npx prisma init
```

Edit `prisma/schema.prisma` to match your backend:

```prisma
model User {
  id    Int    @id @default(autoincrement())
  name  String
  email String @unique
}
```

Run Prisma commands:

```bash
npx prisma db push
npx prisma studio
```

---

## 🧪 Part 6: Mock Data & Debugging

Generate and insert realistic mock data using AI.

Include test commands like:

```bash
python main.py --debug
python main.py --demo
```

**Bonus:**

- Implement toggleable logging and verbose debug modes
- Test with tools like DB Browser for SQLite or PostgREST for Supabase

---

## 🔁 Part 7: Frontend Integration

- Use React or another frontend to read data via Supabase APIs
- Build a UI that reflects live database content
- Optional: add filters, charts, or admin views

---

## 📓 Part 8: Best Practices + Tips

### ✅ Development Tips

- Always prototype locally with SQLite first
- Sync environment variables across .env files in Python & Node
- Use markdown output from AI tools to easily copy into docs or code
- Keep schemas versioned with [Git](../../tools/foundational_dev/Git-for-windows.md)

### ❗ Common Pitfalls

| Problem                      | Solution                                  |
|------------------------------|-------------------------------------------|
| Tables missing in Supabase   | Ensure you run schema migration scripts   |
| No data showing in frontend  | Confirm API keys and Supabase row-level security |
| Too many files in Copilot    | Trim the working context window           |

---

## 📍 Summary Flow

```mermaid
graph TD
A[Prompt AI] --> B[Generate Data Schema]
B --> C1[Python SQLModel]
B --> C2[Prisma Schema]
C1 --> D1[SQLite DB]
C1 --> D2[Supabase]
C2 --> D2
D2 --> E[React/Node Frontend]
```

---

Would you like me to export this as a downloadable .md file?

---

*Licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0/)](https://creativecommons.org/licenses/by-nc/4.0/)*
*Visit [ProductFoundry.ai](https://productfoundry.ai)*
