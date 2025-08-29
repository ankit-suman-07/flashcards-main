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

### Use-Case 2: Revise Cards in Deck

* **Actor**: User
* **Precondition**: Deck with cards exists.
* **Flow**:

  1. User selects a deck and clicks **Start Revision**.
  2. The first card is shown with the **question/topic side up**.
  3. User recalls the answer and taps **Flip**.
  4. The card shows the **answer side**.
  5. User selects:

     * **Got It** → card goes to the back of the deck.
     * **Almost** → card goes to the middle of the deck.
     * **Again** → card is placed near the top.
* **Outcome**: User can revise all cards with custom progress handling.

---

### Use-Case 3: Track Card Status

* **Actor**: User
* **Precondition**: Cards exist.
* **Flow**:

  1. During revision, John taps on **Got It**, **Almost**, or **Again**.
  2. Card status is saved (`Confident`, `Doubtful`, `Read Again`).
  3. Next time John reopens the deck, status is shown on cards.
* **Outcome**: User sees progress status and can filter/revise based on it.

---

### Use-Case 4: Basic Login/Signup

* **Actor**: User
* **Precondition**: None.
* **Flow**:

  1. John signs up using email, username, and password.
  2. He logs in next time with credentials.
* **Outcome**: User has a secure account to manage personal decks.

---

## **Phase 2 – Enhancements (Multimedia + Stats)**

### Use-Case 5: Add Multimedia to Cards

* **Actor**: User
* **Precondition**: Deck exists.
* **Flow**:

  1. John edits a card.
  2. He uploads an **image** or adds a **link** for explanation.
  3. The card now contains text + media.
* **Outcome**: Richer learning experience.

---

### Use-Case 6: View Progress Statistics

* **Actor**: User
* **Precondition**: User has revised at least one deck.
* **Flow**:

  1. John opens **Progress Section**.
  2. App shows stats like:

     * % of cards marked Confident
     * % Doubtful
     * % Read Again
     * Total revision sessions completed
  3. John filters decks by confidence level.
* **Outcome**: User can track improvement visually.

---

## **Phase 3 – Social & Organization Features**

### Use-Case 7: Create Playlist/Group of Decks

* **Actor**: User
* **Precondition**: At least two decks exist.
* **Flow**:

  1. John creates a playlist/group called “Biology Prep”.
  2. He adds multiple decks (like “Botany”, “Zoology”).
  3. Playlist is shown as a single collection.
* **Outcome**: Easier organization of related decks.

---

### Use-Case 8: Share Deck with Others

* **Actor**: User A & User B
* **Precondition**: Deck exists, both users have accounts.
* **Flow**:

  1. John clicks **Share Deck**.
  2. He enters friend’s username/email.
  3. Friend receives invite and accepts.
* **Outcome**: Shared deck appears in both accounts.

---

### Use-Case 9: Collaboratively Edit Deck

* **Actor**: Multiple Users
* **Precondition**: Shared deck exists.
* **Flow**:

  1. John and Mary edit the same deck.
  2. Changes are synced (new cards, edits).
  3. Each user sees updated deck.
* **Outcome**: Decks can be co-created and improved.

---

## **Phase 4 – Advanced (Smart & Gamified Features)**

### Use-Case 10: Smart Spaced Repetition

* **Actor**: User
* **Precondition**: User has used revision mode multiple times.
* **Flow**:

  1. The app calculates difficulty of cards based on past answers.
  2. Cards are shown automatically in a spaced repetition schedule (like Anki/SM2 algorithm).
  3. Easy cards show up less frequently, tough cards show up more often.
* **Outcome**: Efficient memory retention.

---

### Use-Case 11: Gamification with Streaks

* **Actor**: User
* **Precondition**: User logs in regularly.
* **Flow**:

  1. John completes revision for 5 days in a row.
  2. He earns a **streak badge** and points.
  3. App notifies him of streak progress.
* **Outcome**: Higher motivation to study consistently.

---

### Use-Case 12: AI-Generated Hints

* **Actor**: User
* **Precondition**: Deck exists with text-based cards.
* **Flow**:

  1. John clicks **Generate Hint** for a tough card.
  2. The system generates a simplified explanation or example.
  3. Hint is stored with the card.
* **Outcome**: Easier learning with supportive content.

---
