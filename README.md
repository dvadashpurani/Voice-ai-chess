# ♟️ AI Chess Engine with Voice Control (Python)

**Demo video and write-up:** [dvadash-portfolio.vercel.app](https://dvadash-portfolio.vercel.app/#projects)

<img width="474" alt="ai chess" src="https://github.com/user-attachments/assets/4ba42662-01c1-443d-b21e-214c26657479">

## 📌 What is this project?
This project is a complete Chess game where a human can play against an AI opponent.  
The AI does not use machine learning models or training data. Instead, it **thinks ahead**, evaluates future moves, and chooses the best possible move based on logic and strategy — similar to how humans think while playing chess.

Along with AI gameplay, the project also supports:
- Graphical user interface
- Drag & drop movement
- Voice-controlled moves (speech to chess moves)

---

## 🧠 How does the AI actually work? (Simple Explanation)

The AI follows **three main steps** every time it makes a move:

1. **Look at all possible moves**
2. **Imagine future game positions**
3. **Score each position and choose the best one**

This process repeats for multiple future moves.

---

## ♟️ Step 1: Board & Game State Representation

The chess board is stored as a **2D list**, where each cell contains:
- `Pw` → White Pawn
- `Qb` → Black Queen
- `0` → Empty square

A separate `GamePosition` class stores:
- Current board
- Player turn
- Castling rights
- En-passant rules
- Move history

This allows the AI to **copy the board and simulate future moves** safely.

---

## 🔍 Step 2: Generating All Legal Moves

Before the AI can think, it must know:
> “What moves are even allowed?”

The engine:
- Checks chess rules
- Prevents illegal moves
- Ensures the king is never left in check
- Handles special rules (castling, en passant, promotion)

This creates a **search space** of valid moves.

---

## 🤖 Step 3: AI Decision Making (Minimax / Negamax)

The AI uses a **Negamax algorithm**, which is a simplified version of Minimax.

### Simple idea:
- The AI assumes the opponent will always play the best move.
- It tries to maximize its advantage and minimize the opponent’s.

The AI looks ahead several moves (depth-based search) and evaluates each possible outcome.

---

## ⚡ Speed Optimization Techniques

To make the AI fast and practical, several optimizations are used:

### Alpha-Beta Pruning
Stops searching branches that cannot give a better result than an already known move.

### Transposition Table
If the AI sees the **same board position again**, it reuses the stored result instead of recalculating.

### Opening Book
For early game moves, the AI plays pre-recorded opening moves instead of calculating from scratch.

---

## 📊 Position Evaluation (How the AI Scores the Board)

Since chess has no training dataset, the AI uses **rule-based evaluation**.

The score is based on:

### 1. Material Value
- Queen = 9
- Rook = 5
- Bishop / Knight = 3
- Pawn = 1

### 2. Piece Positioning
Some squares are better than others.  
Each piece has a table that rewards strong positions like center control.

### 3. Pawn Structure
The AI penalizes:
- Doubled pawns
- Isolated pawns
- Blocked pawns

### 4. Game Phase Awareness
The AI changes strategy between:
- Opening
- Endgame (king activity becomes important)

---

## 🎙️ Voice-Controlled Chess (Extra Feature)

Players can speak moves like:
"E2 to E4"
"Knight to F3"

Speech is converted into board coordinates and validated before making the move.

---

## 🧩 Technologies Used
- Python
- Pygame (GUI)
- SpeechRecognition (voice input)
- Multithreading (AI thinking in background)
- Data Structures & Algorithms

---

## 📈 What I Learned from this Project
- How game-playing AI works internally
- How to optimize recursive search algorithms
- How to represent complex game states
- How to build AI without machine learning models
- How humans strategies are translated into logic

---

## 🚀 Future Improvements
- Neural network based evaluation
- Reinforcement learning (AlphaZero style)
- Online multiplayer
- Performance benchmarking with Stockfish

---

## 👤 Author
Built by **Dvadash Purani**  
Computer Science Graduate | AI & ML Enthusiast

---

## ▶️ How to run

Python 3.10–3.12. Voice mode needs a microphone and an internet connection (Google speech recognition).

```bash
pip install -r requirements.txt
python CHESS.py
```

It starts from any folder: the game loads `Media/`, `newMedia/`, `Voice/` and `openingTable.txt` from its own folder.
