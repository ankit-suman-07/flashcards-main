# Research Approach

## 🔍 1. Competitor Analysis

**Goal:** See what existing apps offer, what they lack, and how you can differentiate.

**How to do it:**

* **Direct testing:**

  * Sign up for popular flashcard apps (Quizlet, Anki, Brainscape, Tinycards, RemNote).
  * Note their core flows: card creation, study modes, collaboration, pricing.
* **App store reviews:**

  * Read reviews on **Google Play Store / Apple App Store**.
  * Look for recurring complaints (“UI too cluttered,” “AI features missing,” “not good for teams”).
* **Feature comparison matrix:**

  * Create a simple table in Excel/Notion comparing:

    * Onboarding speed
    * AI support
    * Collaboration/team usage
    * Offline access
    * Pricing
* **Online write-ups:**

  * Search “Best flashcard apps 2025” blogs and YouTube reviews.
  * Extract patterns of what people highlight vs dislike.

---

## 👥 2. Target Users

**Goal:** Understand who might actually use your tool and what’s painful for them.

**How to do it:**

* **Surveys / Polls:**

  * Use **Google Forms** or **Typeform** to ask:

    * “How do you currently revise or study?”
    * “What frustrates you about your current tool?”
    * “Would you use flashcards collaboratively in your team/class?”
  * Share on Reddit (subreddits: r/learnprogramming, r/startups, r/college, r/productivity).
* **Interviews:**

  * Ask 3–5 friends, peers, or LinkedIn contacts:

    * “Do you use flashcards?”
    * “Would AI-generated cards help you?”
* **Startup focus:**

  * Talk to small founders you know (or via IndieHackers, Slack communities).
  * Ask if they’d use a lightweight knowledge retention tool for onboarding/training.

---

## ✅ 3. Feature Validation

**Goal:** Avoid overbuilding — confirm which features are “must-haves” vs “nice-to-haves.”

**How to do it:**

* **Surveys with ranking:**

  * List potential features (AI card gen, image support, spaced repetition, team sharing).
  * Ask people to rank Top 3.
* **Reddit/Twitter polls:**

  * Quick informal validation. Example: “If you used flashcards, what’s more important — AI card creation vs spaced repetition?”
* **Observe existing usage:**

  * Look at **feature requests** on GitHub issues of open-source flashcard apps (like Anki add-ons).
  * See what users are already asking for.

---

## ⚙️ 4. Tech Validation

**Goal:** Show that your chosen stack (PostgreSQL + Node/Express + React) is deliberate.

**How to do it:**

* **Compare alternatives:**

  * Firebase / Supabase (faster to start, but vendor lock-in).
  * PostgreSQL (strong relational structure, reporting).
  * MongoDB (flexible but less structured for financial data).
* **Search startup case studies:**

  * E.g., “Why startups choose PostgreSQL” → performance, cost, reliability.
* **Write small prototypes:**

  * Quick tests: e.g., insert 1M flashcard records in PostgreSQL vs Mongo to measure speed.
* **Cloud pricing comparison:**

  * Compare AWS RDS vs Firebase pricing. Show reasoning for your budget-friendly choice.

---

## 💰 5. Monetization Potential (Optional but powerful)

**Goal:** Show that the project could scale into a startup if needed.

**How to do it:**

* **Competitor pricing research:**

  * Quizlet Plus: \~\$7.99/month.
  * Brainscape Pro: \~\$9.99/month.
  * Note: None are tailored for small startup teams.
* **Business model brainstorming:**

  * Free basic features → Paid tier for AI-generated cards + team dashboards.
* **SaaS community feedback:**

  * IndieHackers / ProductHunt → share your idea, ask if they’d pay.
* **Landing page experiment (optional):**

  * Use Carrd/Framer to create a landing page describing your app + “Sign up for early access” button.
  * See if people actually drop emails.

---

## 🎯 How Recruiters See It

If you include even a **3–5 page research report** in your portfolio, it signals:

* You think like a **product-minded engineer**, not just a coder.
* You can **prioritize features based on evidence**, valuable for startups/founding engineer roles.
* You understand **users, market, and technical tradeoffs** — very rare for freshers.

---

