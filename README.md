# Connect-4 AI Agents: Minimax, Expectimax, and Random Strategies 🎮🤖

## **Overview**  
This project implements **Connect-4 AI agents** using three different strategies:  
✅ **Agent A**: **Minimax Algorithm** with **Alpha-Beta Pruning** – Optimal play with guaranteed best moves.  
✅ **Agent B**: **Expectimax Algorithm** – Probabilistic play with varying optimality.  
✅ **Agent C**: **Random Moves** – Baseline strategy for comparison.  

The project evaluates the performance of these agents in various matchups, focusing on **win rates**, **game lengths**, and **pruning efficiency**.  

---

## **Features**  
- 🎲 **Simulates Connect-4 Games** with AI agents.  
- 🧠 **Implements Advanced Algorithms**: Minimax, Expectimax, and Random.  
- 📊 **Analyzes Performance**: Win-to-loss ratios, game lengths, and pruning statistics.  
- 🔄 **Supports Multiple Matchups**: Agent A vs Agent A, Agent A vs Agent B, Agent B vs Agent C, etc.  

---

## **Implementation Details**  

### **Game Setup**  
The Connect-4 game is played on a **6x7 grid**. The initial state is an empty board, and players take turns dropping discs into columns. The game ends when a player forms a line of four discs (horizontally, vertically, or diagonally) or the board is full (resulting in a draw).  

#### **State Representation**  
- The board is represented as a **6x7 matrix**, where:  
  - `0` represents an **empty cell**.  
  - `1` represents a disc placed by **Player 1** (Agent A or B).  
  - `2` represents a disc placed by **Player 2** (Agent B or C).  

#### **Goal Test**  
The game checks for a win by verifying if a player has four consecutive discs in a row, column, or diagonal. If the board is full and no player has won, the game ends in a draw.  

---

## **Agents Overview**  

### 🔵 **Agent A: Minimax with Alpha-Beta Pruning**  
- **Strategy**: Minimax is a decision-making algorithm that aims to minimize the possible loss for a worst-case scenario. It assumes the opponent will always play optimally.  
- **Depth**: The algorithm explores up to **4 moves ahead** to balance computational efficiency and strategic depth.  
- **Alpha-Beta Pruning**: This optimization technique reduces the number of nodes evaluated in the game tree, improving performance.  

#### **Minimax Complexity**  
- **Time Complexity**: `O(b^d)`, where `b` is the branching factor and `d` is the depth.  
- **Space Complexity**: `O(d)` for recursion depth.  

---

### 🔴 **Agent B: Expectimax with Probability**  
- **Strategy**: Expectimax is a variant of Minimax that accounts for probabilistic behavior in the opponent. It assumes the opponent may not always play optimally, introducing randomness.  
- **Probability (p)**: The probability that the opponent will make the optimal move. This project tests different values of `p` (0.25, 0.5, 0.75).  
- **Depth**: Similar to Agent A, it explores up to **4 moves ahead**.  

#### **Expectimax Complexity**  
- **Time Complexity**: `O(b^d)`, but with probabilistic branching.  
- **Space Complexity**: `O(d)` for recursion depth.  

---

### 🟢 **Agent C: Random Moves**  
- **Strategy**: This agent makes random moves, serving as a baseline for comparison. It does not employ any strategic decision-making.  

---

## **Heuristic Function**  
The heuristic function evaluates the quality of a board state by analyzing potential advantages for each player. It scores board positions based on the following criteria:  
- **Four in a row**: +1000 for the agent, -1000 for the opponent.  
- **Three in a row (with one empty)**: +50 for the agent, -50 for the opponent.  
- **Two in a row (with two empty)**: +10 for the agent, -10 for the opponent.  

The heuristic function divides the board into windows of four cells (horizontal, vertical, and diagonal) and evaluates each window to determine the overall score.  

---

## **Installation & Usage**  

### **1. Clone the Repository**  
```bash
git clone https://github.com/YOUR_USERNAME/Connect-4-AI-Agents.git
cd Connect-4-AI-Agents
```

### **2. Install Dependencies**  
```bash
pip install numpy pandas
```

### **3. Run the Simulation**  
To run the simulation with all matchups:  
```bash
python connect4_simulation.py
```

For specific matchups:  
```bash
python agent_a_vs_agent_a.py  # Agent A vs Agent A  
python agent_a_vs_agent_c.py  # Agent A vs Agent C  
python agent_b_vs_agent_c.py  # Agent B vs Agent C  
```

---

## **Results & Performance Metrics**  

The project evaluates the performance of the agents in the following matchups:  
1. **Agent A vs Agent A** (10 games)  
2. **Agent A vs Agent C** (10 games)  
3. **Agent A vs Agent B (p=0.5)** (10 games)  
4. **Agent B (p=0.75) vs Agent C** (10 games)  
5. **Agent B (p=0.5) vs Agent C** (10 games)  
6. **Agent B (p=0.25) vs Agent C** (10 games)  

### **Key Metrics**  
- **Win-to-Loss Ratio**: The number of wins divided by the number of losses.  
- **Game Length**: The number of moves in each game.  
- **Alpha-Beta Pruning**: The number of prunes performed during the search.  

### **Summary of Results**  
| Matchup | Wins | Losses | Draws | Avg Game Length | Avg Alpha Prunes | Avg Beta Prunes |
|---------|------|--------|-------|-----------------|------------------|-----------------|
| Agent A vs Agent A | 4 | 5 | 1 | 26.20 | 685.30 | 1637.60 |
| Agent A vs Agent C | 10 | 0 | 0 | 10.60 | 202.10 | 457.50 |
| Agent A vs Agent B (p=0.5) | 9 | 1 | 0 | 12.10 | 224.70 | 530.10 |
| Agent B (p=0.75) vs Agent C | 8 | 2 | 0 | 13.40 | 0.00 | 0.00 |
| Agent B (p=0.5) vs Agent C | 7 | 3 | 0 | 18.70 | 0.00 | 0.00 |
| Agent B (p=0.25) vs Agent C | 6 | 4 | 0 | 19.60 | 0.00 | 0.00 |

---

## **Observations**  
- **Minimax Dominance**: Agent A (Minimax) consistently outperforms the other agents, especially against random strategies.  
- **Expectimax Performance**: Agent B's performance declines as the probability of making optimal moves decreases. With lower `p` values, Agent B behaves more like a random agent.  
- **Game Lengths**: Games between two Minimax agents are longer, reflecting deeper strategic play, while games involving random agents are shorter.  

---

## **Future Improvements**  
🚀 Implement **Heuristic-Based Strategies** for better performance.  
🚀 Add **Graphical User Interface (GUI)** for interactive gameplay.  
🚀 Optimize **state storage & memory usage**.  

---

## **Contributing**  
Want to improve this project? **Fork, submit pull requests, or suggest enhancements!**  

---

## **License**  
📜 This project is **open-source** and available for academic and research use.  

---

This README provides a **clear and structured overview** of your **Connect-4 AI Agents** project. 🚀 Let me know if you need modifications!
