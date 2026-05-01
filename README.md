# Wumpus Logic Agent

![HTML](https://img.shields.io/badge/HTML5-Canvas-orange?style=flat-square)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow?style=flat-square)
![Logic](https://img.shields.io/badge/AI-Propositional%20Logic-blue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

A browser-based Knowledge-Based Agent that navigates a Wumpus World grid using Propositional Logic and an automated Resolution Refutation engine — built entirely in vanilla HTML, CSS, and JavaScript with no external dependencies.

---

## Overview

The agent operates in a randomly generated grid containing hidden pits and a Wumpus. It receives percepts (Breeze near pits, Stench near Wumpus) and uses a Propositional Logic Knowledge Base to deduce which adjacent cells are safe before moving.

The inference engine implements the full Resolution Refutation algorithm: clauses are added to the KB via TELL, and safety of a cell is queried via ASK by negating the goal and resolving clause pairs until a contradiction (empty clause) is derived.

---

## Features

- Dynamic grid sizing — configure rows and columns before each episode
- Random placement of pits (20% probability per cell) and one Wumpus
- Percept generation — Breeze if adjacent to pit, Stench if adjacent to Wumpus
- Propositional Logic KB updated in real time as the agent moves
- Resolution Refutation engine resolves CNF clauses to prove cell safety
- Real-time metrics dashboard showing inference steps and active percepts
- Color-coded grid: blue (agent), green (visited/safe), red (danger), gray (unknown)
- Step-by-step navigation mode

---

## How It Works

### Knowledge Base

When the agent visits a cell and detects a percept, it adds clauses to the KB:

```
Breeze at (x,y)  →  tell: [~B_x_y, P_nx_ny, P_nx2_ny2, ...]
Stench at (x,y)  →  tell: [~S_x_y, W_nx_ny, W_nx2_ny2, ...]
```

### Resolution Refutation

Before moving to an unvisited neighbor `(nx, ny)`, the agent queries:

```
Is P_nx_ny provable?   (is there a pit here?)
Is W_nx_ny provable?   (is there a Wumpus here?)
```

The engine negates the query, adds it as a unit clause, then resolves clause pairs. If the empty clause is derived, the query is entailed — meaning danger is confirmed. If no new clauses can be produced, the cell is considered safe to enter.

### Resolution Algorithm

```javascript
function resolve(ci, cj) {
  // Find complementary literals between two clauses
  // Return new resolvent clauses with those literals removed
}

function resolution(query) {
  clauses = KB + [negate(query)]
  repeat:
    for each pair (ci, cj):
      resolvents = resolve(ci, cj)
      if empty clause found → return true (query entailed)
    if no new clauses → return false
}
```

---

## Project Structure

```
wumpus-logic-agent/
│
├── wumpus.html      # Complete single-file application
└── README.md        # Project documentation
```

---

## Getting Started

No installation or build step required.

1. Clone the repository
2. Open `wumpus.html` in any modern browser
3. Set grid dimensions (Rows x Cols)
4. Click Start to generate the environment
5. Click Next Step to advance the agent one move at a time

---

## Grid Legend

| Color | Meaning |
|-------|---------|
| Blue | Agent current position |
| Green | Visited and confirmed safe |
| Gray | Unvisited / unknown |
| Red | Confirmed pit or Wumpus |

---

## Metrics Dashboard

The panel below the grid displays:

- **Inference Steps** — total number of clause resolutions performed across all moves
- **Percepts** — current breeze/stench status at the agent's position

---

## Concepts Demonstrated

- Knowledge-Based Agent architecture (TELL / ASK)
- Propositional Logic and CNF clause representation
- Resolution Refutation proof by contradiction
- Online KB construction from sensor percepts
- Entailment checking without enumeration

---

## Limitations

- If a cell could be a pit or a Wumpus, both must be independently refuted before the agent enters
- Fallback to random movement when no safe cell can be proven — the agent may still die in highly constrained environments
- No backtracking or utility-based planning; the agent is purely logic-driven

---

## Built With

- HTML5 Canvas for grid rendering
- Vanilla JavaScript for all logic — no frameworks
- CSS for layout and styling

---

## Author

**Muhammad Shahzain**
AI 2002 — Artificial Intelligence (Spring 2026)
National University of Computer and Emerging Sciences — Chiniot-Faisalabad Campus
