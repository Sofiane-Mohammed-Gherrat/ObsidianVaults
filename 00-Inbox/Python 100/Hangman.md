
> Building a Hangman game in Python is a classic way to practice string manipulation, loops, and conditional logic. At its core, the game is a "state machine" that tracks the hidden word, the letters guessed, and the number of lives remaining.

---

## The Core Concept

The game loop follows a simple cycle:

1. **Display** the current progress (e.g., `p _ t h _ n`).

2. **Get input** from the player (a single letter).

3. **Validate** the input (Is it a letter? Was it already guessed?).

4. **Update** the game state (Is the letter in the secret word?).

5. **Check win/loss** conditions.


---

## Code Structure: Primary Functions

To keep your code "DRY" (Don't Repeat Yourself), you should break the logic into functional blocks.

### 1. `get_valid_word()`

This function handles the setup. It usually picks a random word from a list and ensures it doesn't contain spaces or hyphens that might break your logic.

- **Input:** A list of words.
- **Output:** A single uppercase string.

### 2. `display_board(word, guessed_letters)`

This is your "UI" function. It iterates through the secret word and prints the letter if it has been guessed, or an underscore if it hasn't.

- **Logic:** `[letter if letter in guessed_letters else '_' for letter in word]`

### 3. `play_hangman()`

This is your **Main Controller**. It contains the `while` loop that keeps the game running as long as the player has lives and hasn't guessed the word yet.

---

## Secondary (Helper) Functions

These functions aren't strictly necessary for a "MVP" (Minimum Viable Product), but they make your code professional and readable.

### 1. `get_visual(lives)`

Instead of just printing "You have 5 lives left," this function returns a string of ASCII art representing the gallows. As `lives` decreases, the drawing "evolves."

### 2. `validate_input(user_input, guessed_letters)`

Instead of cluttering your main loop, use this to check if the input is:

- A single character.
- An alphabetical letter (not a number/symbol).
- Something that hasn't been guessed already.

### 3. `play_again()`

A simple boolean function at the end of the script that asks the user if they want to restart, resetting the variables without exiting the program.

---

## Suggested Data Architecture

|**Variable**|**Type**|**Purpose**|
|---|---|---|
|`word`|**String**|The secret word to be guessed.|
|`alphabet`|**Set**|All uppercase English letters (for validation).|
|`used_letters`|**Set**|Stores every unique guess the player makes.|
|`lives`|**Integer**|The countdown to "Game Over."|

---
## Hangman in Python – Concept & Structure

### Core Concept

Hangman is a word-guessing game where:

1. A secret word is chosen randomly
2. The player sees blanks representing each letter
3. They guess one letter at a time
4. Wrong guesses cost "lives" (usually 6, representing the hangman drawing)
5. Win = reveal all letters before running out of lives

---

### Code Structure Overview

```lua
hangman/
├── main.py          # Entry point, game loop
├── game.py          # Core game logic
├── words.py         # Word bank / word selection
└── display.py       # Visual output (hangman art, board)
```

---

### Essential Functions (Primary)

These are the **core** functions the game cannot work without:

```python
# words.py
def get_random_word(word_list: list) -> str:
    """Picks a random secret word from the word bank."""

# game.py
def initialize_game(word: str) -> dict:
    """Sets up game state: blanks, lives, guessed letters."""

def process_guess(letter: str, game_state: dict) -> dict:
    """Checks if the guessed letter is in the word,
       updates blanks or deducts a life."""

def check_win(game_state: dict) -> bool:
    """Returns True if all letters have been revealed."""

def check_loss(game_state: dict) -> bool:
    """Returns True if lives have hit zero."""

# main.py
def game_loop(game_state: dict) -> None:
    """The main loop — keeps asking for guesses until win/loss."""
```

---

### Secondary / Supporting Functions

These **enhance** the game but aren't strictly required:

```python
# display.py
def display_hangman(lives: int) -> None:
    """Prints the ASCII art stage based on wrong guesses."""

def display_board(game_state: dict) -> None:
    """Prints the current blanks, guessed letters, and lives."""

# game.py
def validate_input(letter: str, guessed: set) -> bool:
    """Ensures input is a single, new, alphabetic character."""

def get_hint(word: str, blanks: list) -> str:
    """Optional: reveals one random unrevealed letter."""

def calculate_score(lives: int, word: str) -> int:
    """Optional: score based on lives remaining and word length."""

# main.py
def play_again() -> bool:
    """Asks the player if they want another round."""

def load_word_bank(filepath: str) -> list:
    """Loads words from an external .txt file instead of hardcoding."""

def choose_difficulty() -> list:
    """Filters words by length — short (easy), long (hard)."""
```

---

### Game State Dictionary

A clean way to track everything in one place:

```python
game_state = {
    "word":          "python",
    "blanks":        ["_", "_", "_", "_", "_", "_"],
    "lives":         6,
    "guessed":       set(),       # letters already tried
    "wrong_guesses": [],          # for displaying hangman stages
    "score":         0
}
```

---

### Execution Flow

```lua
main.py
  │
  ├── load_word_bank()       → words list
  ├── choose_difficulty()    → filtered words
  ├── get_random_word()      → secret word
  ├── initialize_game()      → game_state
  │
  └── game_loop()
        ├── display_board()
        ├── display_hangman()
        ├── [get input]
        ├── validate_input()
        ├── process_guess()
        ├── check_win() / check_loss()
        └── play_again()
```

---

### Quick Priority Guide

|Priority|Function|Why|
|---|---|---|
|🔴 Must have|`get_random_word`, `process_guess`, `game_loop`, `check_win/loss`|Game won't run without these|
|🟡 Should have|`display_hangman`, `display_board`, `validate_input`|Needed for good UX|
|🟢 Nice to have|`get_hint`, `calculate_score`, `choose_difficulty`, `load_word_bank`|Adds depth and replayability|
### Set() problem with duplicate letters in the word

## Handling Duplicate Letters in Hangman

The `guessed` set is actually **fine as-is** — it's the `blanks` update logic inside `process_guess()` that needs to handle duplicates correctly.

---

### The Problem

```python
word   = "python"  →  no duplicates, easy
word   = "letter"  →  't' appears at index 2 AND 3
                       'e' appears at index 1 AND 4
```

If you only reveal the **first** occurrence of a letter, the player is stuck — they've already guessed it but the other slots stay blank.

---

### The Fix — Loop Through ALL positions

Instead of finding one index, scan the **entire word** and reveal every matching position:

```python
def process_guess(letter: str, game_state: dict) -> dict:
    word    = game_state["word"]
    blanks  = game_state["blanks"]
    guessed = game_state["guessed"]

    guessed.add(letter)  # mark as tried regardless of hit/miss

    if letter in word:
        # ✅ Loop through ALL positions, not just the first
        for index, char in enumerate(word):
            if char == letter:
                blanks[index] = letter   # reveal every occurrence

    else:
        game_state["lives"] -= 1         # only penalise if truly absent

    return game_state
```

#### Trace through `"letter"` with guess `"t"`:

```lua
index 0 → 'l'  ≠ 't'   skip
index 1 → 'e'  ≠ 't'   skip
index 2 → 't'  = 't' ✅ blanks[2] = 't'
index 3 → 't'  = 't' ✅ blanks[3] = 't'
index 4 → 'e'  ≠ 't'   skip
index 5 → 'r'  ≠ 't'   skip

blanks before: ['_', '_', '_', '_', '_', '_']
blanks after:  ['_', '_', 't', 't', '_', '_']
```

---

### Why the `guessed` set still works perfectly

The set tracks **whether a letter was tried**, not how many times or where. Duplicate positions in the word are irrelevant to it — it just prevents the player from guessing the same letter twice:

```python
guessed = {'t', 'e'}

# Player tries 't' again:
if letter in guessed:
    print("You already guessed that!")   # caught cleanly
```

---

### The only extra edge case — `check_win()`

Make sure your win condition checks the `blanks` list, **not** the guessed set:

```python
# ✅ Correct — checks if any blank remains
def check_win(game_state: dict) -> bool:
    return "_" not in game_state["blanks"]

# ❌ Wrong — guessed letters don't guarantee full coverage
def check_win(game_state: dict) -> bool:
    return set(game_state["word"]) == game_state["guessed"]
    # "letter" → {'l','e','t','r'} — this actually works for unique chars
    # but the blanks approach is simpler and always correct
```

---

### Summary

|Component|Role|Duplicate-safe?|
|---|---|---|
|`guessed` set|Tracks tried letters|✅ Yes, no changes needed|
|`blanks` list|Reveals positions|⚠️ Only if you loop all positions|
|`check_win()`|Detects full reveal|✅ Use `"_" not in blanks`|

The key insight: **one letter can map to many positions**, so your reveal logic must always iterate the full word.

