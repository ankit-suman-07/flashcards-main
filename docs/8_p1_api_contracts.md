# 📌 API Contracts – Phase 1, MVP

---

## 1. **Users**

> In Phase 1 you can hardcode a single user, but I’m keeping signup/login so you’re future-ready.

### `POST /users/signup`

**Purpose:** Register a new user

**Request:**

```json
{
  "username": "john123",
  "email": "john@example.com",
  "password": "securePass123"
}
```

**Response:**

```json
{
  "id": "u-1",
  "username": "john123",
  "email": "john@example.com",
  "createdAt": "2025-09-02T10:00:00Z"
}
```

---

### `POST /users/login`

**Purpose:** User login and receive token

**Request:**

```json
{
  "email": "john@example.com",
  "password": "securePass123"
}
```

**Response:**

```json
{
  "token": "jwt.token.value",
  "user": {
    "id": "u-1",
    "username": "john123",
    "email": "john@example.com"
  }
}
```

---

## 2. **Decks**

### `POST /decks`

**Purpose:** Create a new deck

**Request:**

```json
{
  "name": "Biology Deck",
  "description": "Basic biology flashcards",
  "tags": ["biology", "science"]
}
```

**Response:**

```json
{
  "id": "d-1",
  "name": "Biology Deck",
  "description": "Basic biology flashcards",
  "tags": ["biology", "science"],
  "createdAt": "2025-09-02T10:00:00Z",
  "updatedAt": "2025-09-02T10:00:00Z"
}
```

---

### `GET /decks`

**Purpose:** List all decks of the logged-in user

**Response:**

```json
[
  { "id": "d-1", "name": "Biology Deck", "description": "Basic biology flashcards", "cardCount": 15 },
  { "id": "d-2", "name": "Math Formulas", "description": "Important formulas", "cardCount": 10 }
]
```

---

### `GET /decks/{deckId}`

**Purpose:** Get details of a deck (with cards if requested via query param)

**Response:**

```json
{
  "id": "d-1",
  "name": "Biology Deck",
  "description": "Basic biology flashcards",
  "tags": ["biology"],
  "cards": [
    { "id": "c-101", "question": "Cell is the ___", "answer": "Basic unit of life", "isBidirectional": true },
    { "id": "c-102", "question": "Mitochondria is the ___", "answer": "Powerhouse of the cell", "isBidirectional": false }
  ]
}
```

---

### `DELETE /decks/{deckId}`

**Response:**

```json
{ "message": "Deck deleted successfully" }
```

---

## 3. **Cards**

### `POST /decks/{deckId}/cards`

**Purpose:** Add a new card to a deck

**Request:**

```json
{
  "question": "What is photosynthesis?",
  "answer": "Process by which green plants make food using sunlight",
  "isBidirectional": true,
  "tags": ["biology", "plants"]
}
```

**Response:**

```json
{
  "id": "c-201",
  "question": "What is photosynthesis?",
  "answer": "Process by which green plants make food using sunlight",
  "isBidirectional": true,
  "tags": ["biology", "plants"]
}
```

---

### `GET /decks/{deckId}/cards/{cardId}`

**Response:**

```json
{
  "id": "c-201",
  "question": "What is photosynthesis?",
  "answer": "Process by which green plants make food using sunlight",
  "isBidirectional": true,
  "tags": ["biology", "plants"]
}
```

---

### `PATCH /decks/{deckId}/cards/{cardId}`

**Request:**

```json
{
  "question": "Photosynthesis occurs in ___?",
  "answer": "Chloroplasts"
}
```

**Response:**

```json
{
  "id": "c-201",
  "question": "Photosynthesis occurs in ___?",
  "answer": "Chloroplasts",
  "isBidirectional": true,
  "tags": ["biology", "plants"]
}
```

---

### `DELETE /decks/{deckId}/cards/{cardId}`

**Response:**

```json
{ "message": "Card deleted successfully" }
```

---

## 4. **Revision Mode**

> Here, **status is tracked in CardProgress** (per user, not in the card itself).

### `POST /decks/{deckId}/revision/start`

**Purpose:** Start a revision session

**Response:**

```json
{
  "sessionId": "rev-abc123",
  "deckId": "d-1",
  "currentCard": {
    "id": "c-101",
    "question": "Cell is the ___",
    "answer": null,
    "status": "new"
  }
}
```

---

### `POST /revision/{sessionId}/answer`

**Purpose:** Submit answer & update **CardProgress**, return next card

**Request:**

```json
{
  "cardId": "c-101",
  "userAnswer": "Basic unit of life",
  "result": "got-it" // got-it | almost | again
}
```

**Response:**

```json
{
  "updatedProgress": {
    "cardId": "c-101",
    "status": "got-it",
    "lastReviewedAt": "2025-09-02T10:05:00Z",
    "nextReviewAt": "2025-09-04T10:05:00Z"
  },
  "nextCard": {
    "id": "c-102",
    "question": "Mitochondria is the ___",
    "answer": null,
    "status": "new"
  }
}
```

---

## 5. **Collections (Optional in Phase 1)**

If you want to allow grouping decks even in MVP (rename of playlists → collections):

### `POST /collections`

**Request:**

```json
{
  "name": "Final Exam Prep",
  "deckIds": ["d-1", "d-2", "d-3"]
}
```

**Response:**

```json
{
  "id": "col-301",
  "name": "Final Exam Prep",
  "deckIds": ["d-1", "d-2", "d-3"]
}
```