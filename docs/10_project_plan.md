# 📌 Project Plan — Flashcard Learning App

## 1. 🎯 Project Overview

The goal is to build a **research-backed flashcard learning platform** that applies principles of active recall, spaced repetition, and multimedia learning. The app will be developed in **phases**, starting with an MVP and progressively adding enhancements like multimedia, social features, and AI-based card generation.

The plan balances **research validation**, **technical implementation**, and **deployment readiness** for portfolio and career value.

---

## 2. 🛠️ Tools & Stack

* **Frontend**: React (Next.js optional), TypeScript
* **Backend**: Node.js + Express (Nest.js optional)
* **Database**: PostgreSQL
* **Authentication**: JWT + Passport.js
* **File Storage**: Cloudinary (or AWS S3)
* **AI Integration**: OpenAI API, pdf-parse
* **Containerization**: Docker
* **CI/CD**: GitHub Actions
* **Hosting**: Vercel/Netlify (frontend), Render/Heroku (backend)
* **Optional Scaling**: Redis for caching, Chart.js for analytics

---

## 3. 📅 Development Phases & Milestones

### **Phase 0 – Research & Planning (✅ Completed / Ongoing)**

* ✅  Literature review on flashcards and learning effectiveness
* ✅  Idea validation & competitor analysis
* ⏳ Target user identification
* ✅  Feature roadmap (Phase 1 → Phase 4)
* ✅  Database schema design
* ✅  API contract design
* ✅  Tools & stack finalized

**Deliverables**:

* Research documents (`idea_validation.md`, `literature_review.md`, `research_approach.md`)
* Entity definitions (`entities.md`)
* DB schema (`db_tables.md`)
* Endpoints (`endpoints.md`)
* Phase 1 API contracts (`phase1_api_contracts.md`)

---

### **Phase 1 – MVP (Core Flashcard System)**

**Goal**: Launch a single-user app with core CRUD and revision mode.

**Features**:

* User authentication (signup/login)
* Create, update, delete **Decks** and **Cards**
* Revision mode with **Got It / Almost / Again** tracking
* Track per-user progress with **CardProgress** table
* Basic UI for decks & revision

**Deliverables**:

* Backend API (controllers, services, models)
* Postgres schema migration files
* Minimal React frontend (deck & card CRUD, revision mode)
* Deployed MVP (Heroku/Render + Vercel/Netlify)

**Timeline**: \~3–4 weeks

---

### **Phase 2 – Multimedia & Analytics Enhancements**

**Goal**: Improve engagement with media support and progress insights.

**Features**:

* Add images/audio to cards
* View progress dashboard (charts: % confident/doubtful/again, streaks)
* Onboarding flow that teaches effective flashcard use (Flashcards-Plus method)

**Deliverables**:

* Image upload integration (Cloudinary/S3)
* Progress stats API + UI (Chart.js/D3.js)
* Onboarding/tutorial screens

**Timeline**: \~3 weeks

---

### **Phase 3 – Social & Collaboration Features**

**Goal**: Enable users to organize, share, and collaborate.

**Features**:

* Playlists/Collections of decks
* Deck sharing with permissions (view/edit)
* Collaborative editing (multi-user updates)
* Public/private visibility settings

**Deliverables**:

* Playlist & sharing endpoints
* Collaborative editing logic (real-time optional for later)
* UI for sharing & managing visibility

**Timeline**: \~4–5 weeks

---

### **Phase 4 – AI & Smart Learning**

**Goal**: Add advanced research-backed and AI-powered features.

**Features**:

* Smart spaced repetition scheduling (SM-2 or simplified)
* AI-generated cards from PDFs/text (OpenAI + pdf-parse)
* AI hints/explanations for tough cards
* Gamification (streaks, XP, badges)

**Deliverables**:

* AI job queue + API endpoints
* Spaced repetition engine
* Gamification system (XP, badges, streaks)
* AI-enhanced UI (card generation, hints)

**Timeline**: \~4–6 weeks

---

## 4. 📊 Project Tracking

| Phase   | Features                                   | Status        | Target Completion | Actual Completion |
| ------- | ------------------------------------------ | ------------- | ----------------- | ----------------- |
| Phase 0 | Research, schema, endpoints, planning      | ✅ Done        | Aug 2025          | Sep 2025          |
| Phase 1 | Core decks, cards, revision, auth          | ⏳ In Progress | Oct 2025          | -                 |
| Phase 2 | Multimedia, progress dashboard, onboarding | ⏳ Pending     | Nov 2025          | -                 |
| Phase 3 | Sharing, collaboration, collections        | ⏳ Pending     | Dec 2025          | -                 |
| Phase 4 | AI generation, SRS, gamification           | ⏳ Pending     | Jan 2026          | -                 |

---

## 5. 🚀 Success Criteria

* ✅ MVP deployed and usable with CRUD + revision
* ✅ Research-backed features (retrieval, spacing, multimedia) implemented
* ✅ Social and collaboration features added to support real-world learning scenarios
* ✅ AI + gamification make app competitive and portfolio-worthy
* ✅ Well-documented repo (README, project plan, research, API contracts)

---

## 6. 📌 Next Steps

* [ ] Finish **Phase 1 backend API implementation**
* [ ] Implement DB migrations with PostgreSQL
* [ ] Build minimal React frontend for deck & revision flows
* [ ] Deploy MVP to cloud platforms
* [ ] Collect feedback and refine for Phase 2