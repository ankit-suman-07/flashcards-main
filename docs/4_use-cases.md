# 📘 App Use-Cases

---

## **Phase 1 – MVP (Core Flashcard System)**

### Use-Case 1: Create Deck and Cards

* **Actor**: User (John)
* **Precondition**: User is logged in.
* **Flow**:

  1. John clicks **Create Deck**.
  2. He enters deck name and description.
  3. John adds 15 cards by typing the topic/question and answer/explanation.
  4. John saves the deck.
* **Outcome**: Deck with cards is stored and visible in his dashboard.

---

### Use-Case 2: Revise Cards in Deck (Active Recall Enforced)

* **Actor**: User
* **Precondition**: Deck with cards exists.
* **Flow**:

  1. User selects a deck and clicks **Start Revision**.
  2. The first card is shown with the **question/topic side up**.
  3. User attempts to recall answer mentally before tapping **Flip**.
  4. The card shows the **answer side**.
  5. User selects:

     * **Got It** → card goes to the back of the deck.
     * **Almost** → card goes to the middle of the deck.
     * **Again** → card is placed near the top.
* **Outcome**: User practices retrieval with adaptive sequencing for stronger retention.

---

### Use-Case 3: Track Card Status

* **Actor**: User
* **Precondition**: Cards exist.
* **Flow**:

  1. During revision, John taps on **Got It**, **Almost**, or **Again**.
  2. Card status is saved (`Confident`, `Doubtful`, `Read Again`).
  3. Status is used in future sessions to influence card scheduling.
* **Outcome**: User sees progress status and system optimizes future review order.

---

### Use-Case 4: Basic Login/Signup

* **Actor**: User
* **Precondition**: None.
* **Flow**:

  1. John signs up using email, username, and password.
  2. He logs in next time with credentials.
* **Outcome**: User has a secure account to manage personal decks.

---

### Use-Case 5: Guided Onboarding

* **Actor**: User
* **Precondition**: First-time login.
* **Flow**:

  1. App explains how flashcards work (retrieval, spacing, reflection).
  2. John practices with a demo deck.
* **Outcome**: User is trained in effective flashcard usage from start.

---

## **Phase 2 – Enhancements (Multimedia + Stats + Notifications)**

### Use-Case 6: Add Multimedia & Bidirectional Cards

* **Actor**: User
* **Precondition**: Deck exists.
* **Flow**:

  1. John edits a card.
  2. He uploads an **image** or adds an **audio clip/link**.
  3. App enables **bidirectional testing** (definition → term and vice versa).
* **Outcome**: Richer, research-backed encoding and recall.

---

### Use-Case 7: View Progress Statistics

* **Actor**: User
* **Precondition**: User has revised at least one deck.
* **Flow**:

  1. John opens **Progress Section**.
  2. App shows stats like:

     * % of cards marked Confident, Doubtful, Read Again
     * Total sessions completed
     * Weakest cards/decks
  3. App suggests “Review Doubtful Cards First.”
* **Outcome**: User tracks improvement and gets actionable study tips.

---

### Use-Case 8: Review Reminders

* **Actor**: User
* **Precondition**: User has pending cards based on schedule.
* **Flow**:

  1. App sends push/email notification: “10 cards are due today.”
  2. John taps notification → takes him directly to review mode.
* **Outcome**: Consistent spaced learning habit.

---

## **Phase 3 – Social & Organization Features**

### Use-Case 9: Create Playlist/Group of Decks

* **Actor**: User
* **Precondition**: At least two decks exist.
* **Flow**:

  1. John creates a playlist called “Biology Prep.”
  2. He adds decks (e.g., Botany, Zoology).
* **Outcome**: Easier organization of related decks.

---

### Use-Case 10: Share Deck with Others

* **Actor**: User A & User B
* **Precondition**: Deck exists, both users have accounts.
* **Flow**:

  1. John clicks **Share Deck**.
  2. He enters friend’s username/email.
  3. Friend accepts invite.
* **Outcome**: Shared deck appears in both accounts.

---

### Use-Case 11: Structured Collaborative Editing

* **Actor**: Multiple Users
* **Precondition**: Shared deck exists.
* **Flow**:

  1. John and Mary enter collaborative mode.
  2. They take turns editing/adding cards.
  3. App provides prompts like “Explain your reasoning” or “Rate this card’s clarity.”
* **Outcome**: Decks are co-created with structured, research-backed collaboration.

---

### Use-Case 12: Deck Insights

* **Actor**: User
* **Precondition**: Multiple decks exist.
* **Flow**:

  1. John opens **Deck Insights**.
  2. App compares performance across decks (e.g., Biology vs Chemistry).
* **Outcome**: User identifies weak subjects faster.

---

## **Phase 4 – Advanced (Smart, Gamified & AI Features)**

### Use-Case 13: Smart Spaced Repetition

* **Actor**: User
* **Precondition**: User has revised multiple sessions.
* **Flow**:

  1. App calculates card difficulty from past answers.
  2. Cards follow spaced repetition (e.g., SM-2 algorithm).
* **Outcome**: Long-term memory retention optimized.

---

### Use-Case 14: Gamification with Streaks & XP

* **Actor**: User
* **Precondition**: User revises regularly.
* **Flow**:

  1. John revises daily for 5 days.
  2. He earns a streak badge + XP points.
  3. Extra XP is awarded for reviewing tough cards.
* **Outcome**: Motivation sustained through learning-focused gamification.

---

### Use-Case 15: AI-Generated Hints

* **Actor**: User
* **Precondition**: Deck exists with text-based cards.
* **Flow**:

  1. John clicks **Generate Hint** for a tough card.
  2. AI generates simplified explanations/examples.
  3. Hint is saved with the card.
* **Outcome**: Supportive scaffolding for tough concepts.

---

### Use-Case 16: AI-Generated Cards from Documents

* **Actor**: User
* **Precondition**: User uploads text/PDF.
* **Flow**:

  1. John uploads lecture slides or a textbook chapter.
  2. AI suggests a set of cards (Q/A).
  3. John edits and approves before saving.
* **Outcome**: Faster deck creation with AI assistance.