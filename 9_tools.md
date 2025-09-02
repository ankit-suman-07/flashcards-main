### Tools Table

| Tech/Tool                            | Feature                            | Rationale                                    | Why Not Other Tools                                 |
| ------------------------------------ | ---------------------------------- | -------------------------------------------- | --------------------------------------------------- |
| React (or Next.js)                   | UI framework + optional SSR        | High demand in Canada/remote jobs            | Others less popular or flexible                     |
| TypeScript                           | Static typing                      | Strong industry adoption                     | JS lacks safety and scalability                     |
| Node.js + Express (Nest.js optional) | Backend API                        | Widely used in full-stack remote roles       | More agile than Java/Spring, easier pairing with JS |
| PostgreSQL                           | Relational DB                      | Reliable, structured, widely used            | NoSQL adds unnecessary complexity early             |
| Redis (optional cache)               | Caching/session store              | Standard in larger apps                      | Not needed until scaling                            |
| Cloudinary (or S3)                   | Image uploads                      | Simple, robust image handling                | Firebase overkill                                   |
| JWT + Passport.js                    | Authentication                     | Lightweight, standard for Phase 3            | Auth0 too heavy for MVP                             |
| Docker                               | Containerization                   | Industry standard, simplifies dev and deploy | Overhead but worthwhile early                       |
| GitHub Actions                       | CI/CD                              | Easy integration, free tier                  | Jenkins too complex                                 |
| Vercel/Netlify (frontend)            | Hosting                            | Quick deploy for React/Next.js               | AWS too complex initially                           |
| Heroku/Render                        | Backend hosting                    | Easy PaaS for APIs                           | Kubernetes too early-stage                          |
| OpenAI API                           | AI card generation                 | Fast integration with strong docs            | Self-hosting LLMs complex                           |
| pdf-parse                            | PDF parsing                        | Lightweight extraction                       | Heavy OCR not needed                                |
| Spaced repetition lib                | Review scheduling                  | Proven algorithm available                   | Re-inventing algorithm risky                        |
| Chart.js / D3.js                     | Analytics dashboards               | Lightweight charts for user insights         | BI tools too heavy                                  |
| GitHub (PM)                          | Issue tracking, project management | Common remote collaboration tool             | Jira overkill at start                              |
| Slack/Discord                        | Team communication                 | Widely used in remote teams                  | Microsoft Teams heavier to set up                   |

---
### Frontend

* **React (or Next.js)**
  - **Feature**: UI layer, optional server-side rendering (Next.js)
  - **Rationale**: React is massively popular in Canada, USA, UK job listings—as seen in React-heavy roles on Glassdoor and Reddit job discussions. Next.js adds SEO and performance benefits while being widely adopted.
  - **Why not others**: Angular and Vue are less in-demand and more complex; React's ecosystem and flexibility make it more future-proof.

* **TypeScript**
  - **Feature**: Typed JS for maintainability and scalability
  - **Rationale**: Increasingly a standard requirement (e.g., “TypeScript” mentioned in modern React listings).
  - **Why not plain JS**: Enhances code safety and IDE support; plain JS risks type issues and slower scaling.

---

### Backend

* **Node.js with Express (or optionally NestJS)**
  - **Feature**: API server, handles business logic
  - **Rationale**: Node.js is in high demand for full-stack roles and common in MERN-like stacks, frequently mentioned in job posts.
  - **Why not Django/Spring**: While Django, Java, Spring, .NET are used, Node.js offers faster iteration for MVPs and pairs well with React/TypeScript.

* **PostgreSQL**
  - **Feature**: Relational data storage (cards, decks, users)
  - **Rationale**: Widely used in production systems, preferred for reliability and schema safety; Reddit notes Postgres is fundamental.
  - **Why not NoSQL**: NoSQL like Mongo adds complexity for structured data; PostgreSQL suits the structured relationships in your app.

* **Redis (optional cache/session store)** (Phase 5+)
  - **Feature**: Fast caching for session or metadata
  - **Rationale**: Common in mid-to-large systems; mentioned as cache complement.
  - **Why not required early**: Only needed when scaling or caching becomes important—overkill for MVP.

---

### Storage for Images

* **Cloudinary (or Amazon S3 with a simple wrapper)**
  - **Feature**: Image hosting and delivery
  - **Rationale**: Cloudinary is easy to integrate, handles uploads/resizing, free tier available. S3 is industry-standard and simple.
  - **Why not Firebase Storage**: Overkill for this use; adds more complexity. Cloudinary/S3 are lighter and more flexible.

---

### User Authentication (Phase 3+)

* **JWT + Passport.js (or NextAuth if Next.js)**
  - **Feature**: Secure authentication for multi-user
  - **Rationale**: Popular solutions within Node ecosystem; well-documented and flexible.
  - **Why not Auth0 (idle for MVP)**: Hosted auth providers are heavy and costly; better to start with simpler JWT-based flow.

---

### DevOps / Deployment

* **Docker**
  - **Feature**: Containerization for consistent development/deployment
  - **Rationale**: Expected in remote/full-stack roles.
  - **Why not skip**: Simplifies environment differences; invaluable when scaling or onboarding.

* **GitHub Actions (CI/CD)**
  - **Feature**: Automated testing and deployment workflows
  - **Rationale**: Commonly used in remote teams, plus integrates well with GitHub.
  - **Why not Jenkins**: More complex to setup; Actions are lightweight and free for small projects.

---

### Cloud & Hosting

* **Vercel or Netlify (for frontend)**
  - **Feature**: Easy hosting for React/Next.js apps
  - **Rationale**: Smooth deployments, built-in CI, previews.
  - **Why not AWS initially**: Simpler and faster setup; AWS can come later when scaling.

* **Heroku (or Render/Fly.io) for backend**
  - **Feature**: Simple app deployment, add-ons for DB
  - **Rationale**: Low-friction hosting for MVP.
  - **Why not Kubernetes/EKS**: Overengineered for early stages; use simpler PaaS until needed.

---

### AI Feature (Phase 4+)

* **OpenAI API**
  - **Feature**: Generate question-answer pairs from text/PDF
  - **Rationale**: Industry standard LLM API—quick to integrate with strong documentation.
  - **Why not self-hosted models**: Too heavy and costly initially.

* **PDF parsing library (e.g., pdf-parse)**
  - **Feature**: Extract text for AI processing
  - **Rationale**: Lightweight Node package, simple to integrate.
  - **Why not heavy OCR tools**: Not necessary unless images with text only—overkill for MVP.

---

### Optional Advanced (Phase 5+)

* **Anki-style Spaced Repetition algorithm library (e.g., SM-2)**
  - **Feature**: Smarter review scheduling
  - **Rationale**: Powerful learning enhancement; simple JS implementations exist.
  - **Why not build from scratch**: Better to leverage proven algorithm than risk parity.

* **Analytics: Chart.js or D3.js**
  - **Feature**: Deck progress insights (Phase 5)
  - **Rationale**: Chart.js offers quick visualizations; D3 for deeper control.
  - **Why not heavy BI tools**: Overkill for MVP dashboards.

---

### Communication / Project Management

* **GitHub (Issues, Projects, Discussions)**
  - **Feature**: Manage tasks and collaboration
  - **Rationale**: Standard for remote work; free and integrated.
  - **Why not Jira initially**: Too heavy; GitHub is lean and effective.

* **Slack / Discord (optional for team chat)**
  - **Feature**: Team communication
  - **Rationale**: Common in remote teams.
  - **Why not Microsoft Teams**: Slack/Discord lighter and faster to onboard.

---



### Final Thoughts

* **Phases 1–2**: Focus on React/TypeScript, Node.js, PostgreSQL, basic auth, and image upload infrastructure.
* **Phase 3–4**: Add multi-user auth, AI card generation via OpenAI, PDF parsing.
* **Phase 5+**: Introduce spaced repetition, analytics, caching, and better deployment as needed.

