# 📌 Flashcard App – Feature List

### ✅ Core Features (MVP – Phase 1)

1. **Deck Management** – Create, edit, and organize decks for any subject or topic.
2. **Smart Cards** – Add cards with **questions and answers** (supports bidirectional mode).
3. **Revision Mode** – Study decks with interactive flashcards that simulate real exam prep.
4. **Confidence Tracking** – Mark cards as *Got It*, *Almost*, or *Again* for personalized learning.
5. **Progress Tracking** – Each user’s performance is tracked separately, with session history.

---

### 🖼️ Phase 2: Multimedia Support

6. **Image-based Flashcards** – Attach images to cards (e.g., diagrams, charts, formulas).
7. **Future-ready Media** – Extendable to audio/video flashcards for language and medical study.

---

### 👥 Phase 3: Collaboration & Sharing

8. **Playlists / Collections** – Group multiple decks into playlists for structured revision (e.g., “Final Exam Prep”).
9. **Deck Sharing** – Share decks or playlists with friends, classmates, or teams.
10. **Visibility Controls** – Choose between private, shared, or public decks.
11. **Multi-User Accounts** – Support for multiple users, roles, and collaborative learning.

---

### 🤖 Phase 4: AI-Powered Learning

12. **AI-Generated Cards** – Upload PDFs, notes, or text, and automatically generate flashcards.
13. **Smart Hints** – Get AI-suggested hints and explanations for tough cards.
14. **Spaced Repetition (SM-2 Algorithm)** – Automatic scheduling for maximum retention.
15. **Gamification** – Streaks, XP points, and leaderboards to make learning fun and motivating.

---

✨ **Why it stands out?**

* Backed by **cognitive psychology research** (retrieval practice + spaced repetition).
* Designed to grow from a **personal study tool** into a **collaborative, AI-powered learning platform**.
* Built for **students, professionals, and lifelong learners**.


# 📂 Backend Folder Structure (Node.js + Express + PostgreSQL)

```
flashcard-app-backend/
│── src/
│   ├── config/
│   │   ├── db.ts                 # PostgreSQL connection (using Prisma/TypeORM/Knex)
│   │   ├── redis.ts              # Redis client config (optional caching/session)
│   │   ├── cloudinary.ts         # Cloudinary setup for image uploads
│   │   ├── passport.ts           # JWT + Passport.js strategies
│   │   └── env.ts                # Centralized environment variables
│   │
│   ├── controllers/              # Route handlers (API endpoints)
│   │   ├── user.controller.ts
│   │   ├── deck.controller.ts
│   │   ├── card.controller.ts
│   │   ├── revision.controller.ts
│   │   ├── playlist.controller.ts
│   │   └── ai.controller.ts      # For OpenAI integration (Phase 4)
│   │
│   ├── services/                 # Business logic (separate from controllers)
│   │   ├── user.service.ts
│   │   ├── deck.service.ts
│   │   ├── card.service.ts
│   │   ├── revision.service.ts
│   │   ├── playlist.service.ts
│   │   └── ai.service.ts
│   │
│   ├── models/                   # Database models/entities
│   │   ├── user.model.ts
│   │   ├── deck.model.ts
│   │   ├── card.model.ts
│   │   ├── cardProgress.model.ts
│   │   ├── playlist.model.ts
│   │   └── aiJob.model.ts
│   │
│   ├── routes/                   # API route definitions
│   │   ├── user.routes.ts
│   │   ├── deck.routes.ts
│   │   ├── card.routes.ts
│   │   ├── revision.routes.ts
│   │   ├── playlist.routes.ts
│   │   └── ai.routes.ts
│   │
│   ├── middleware/               # Middlewares for auth, errors, validation
│   │   ├── auth.middleware.ts
│   │   ├── error.middleware.ts
│   │   └── validate.middleware.ts
│   │
│   ├── utils/                    # Helper functions (non-business logic)
│   │   ├── logger.ts
│   │   ├── response.ts           # Standardized API responses
│   │   ├── pdfParser.ts          # pdf-parse integration for AI features
│   │   └── spacedRepetition.ts   # Scheduling algorithm
│   │
│   ├── tests/                    # Unit + integration tests
│   │   ├── user.test.ts
│   │   ├── deck.test.ts
│   │   ├── card.test.ts
│   │   ├── revision.test.ts
│   │   └── playlist.test.ts
│   │
│   ├── app.ts                    # Express app setup (middleware, routes)
│   └── server.ts                 # Entry point (start server)
│
├── prisma/ or migrations/        # DB schema (Prisma schema or Knex migrations)
│
├── .env                          # Environment variables
├── Dockerfile                    # Backend Docker config
├── docker-compose.yml            # DB + Redis + Backend container setup
├── package.json
└── tsconfig.json
```

---

## 🔑 Folder/File Explanations

* **`config/`** → Setup files for PostgreSQL, Redis, Cloudinary, JWT/Passport, environment configs. Keeps app clean.
* **`controllers/`** → Each file = API endpoints (thin layer). Just takes request → calls `service` → sends response.
* **`services/`** → Actual business logic. E.g., spaced repetition, deck ownership checks, card creation.
* **`models/`** → Database schema (if using ORM like Prisma/TypeORM). Represents **tables** like `User`, `Deck`, `Card`.
* **`routes/`** → Maps URLs (`/api/decks/:id`) to controller functions. Keeps routing clean.
* **`middleware/`** → Authentication (JWT), validation, error handling (centralized).
* **`utils/`** → Helper modules like logger, PDF parsing, spaced repetition algorithm.
* **`tests/`** → Jest/Mocha tests for controllers/services. Keeps things production-grade.
* **`app.ts`** → Builds the Express app (middleware, routes).
* **`server.ts`** → Starts the server (reads `PORT`, connects DB).
* **`prisma/` or `migrations/`** → DB schema + migration history.

---

## ✅ Why This Works for Your Tools

* Fits **Express + PostgreSQL** workflow (with Prisma/Knex).
* Scales easily → new features = add new service/controller/model/route.
* Clean separation (controllers = API, services = logic, models = DB).
* Supports **AI, Redis, Cloudinary, JWT** naturally.
* Docker + GitHub Actions ready.