# Coffee Vending Machine - Mealy vs Moore FSM Implementation

A comprehensive study comparing Mealy and Moore finite state machines for designing a coin-operated coffee vending system.

## 📋 Project Overview

This project implements a coffee vending machine that accepts ₹5 and ₹10 coins and dispenses coffee at ₹15. The system is modeled using both **Mealy** and **Moore** machine architectures to compare their efficiency, state complexity, and practical applications.

## 👥 Team Members

- **Shivamani G**
- **Koushik Reddy G**
- **Chiranjeevi M**

## 🎯 Problem Statement

Design and model a coffee dispenser machine that:
- Accepts ₹5 and ₹10 coins as input
- Dispenses coffee when ₹15 is collected
- Returns ₹5 change when applicable
- Implements both Mealy and Moore machine models
- Compares efficiency between the two approaches

## 🔧 System Specifications

### Input Alphabet (Σ)
- `5` → ₹5 coin
- `10` → ₹10 coin

### Output Alphabet (Δ)
- `(D, R5)` where:
  - `D = 1` → Dispense coffee
  - `R5 = 1` → Return ₹5 change

## 🤖 Machine Implementations

### Mealy Machine

**States:** 3 states (`q₀`, `q₅`, `q₁₀`)

**State Transition Table:**

| Current State | Input | Next State | Output (D, R5) |
|---------------|-------|------------|----------------|
| q₀            | 5     | q₅         | (0,0)          |
| q₀            | 10    | q₁₀        | (0,0)          |
| q₅            | 5     | q₁₀        | (0,0)          |
| q₅            | 10    | q₀         | (1,0)          |
| q₁₀           | 5     | q₀         | (1,0)          |
| q₁₀           | 10    | q₀         | (1,1)          |

**Formal Definition:**
```
M = (Q, Σ, Δ, δ, λ, q₀)

Q = {q₀, q₅, q₁₀}
Σ = {5, 10}
Δ = {(D, R5) | D ∈ {0,1}, R5 ∈ {0,1}}
δ: Q × Σ → Q (state transition function)
λ: Q × Σ → Δ (output function - depends on state AND input)
q₀ = initial state (₹0 collected)
```

### Moore Machine

**States:** 5 states (`q₀`, `q₅`, `q₁₀`, `q₁₅`, `q₂₀`)

**State Transition Table:**

| Current State | Input | Next State | Output (D, R5) |
|---------------|-------|------------|----------------|
| q₀            | 5     | q₅         | (0,0)          |
| q₀            | 10    | q₁₀        | (0,0)          |
| q₅            | 5     | q₁₀        | (0,0)          |
| q₅            | 10    | q₁₅        | (0,0)          |
| q₁₀           | 5     | q₁₅        | (0,0)          |
| q₁₀           | 10    | q₂₀        | (0,0)          |
| q₁₅           | -     | q₀         | (1,0)          |
| q₂₀           | -     | q₀         | (1,1)          |

**Formal Definition:**
```
M = (Q, Σ, Δ, δ, λ, q₀)

Q = {q₀, q₅, q₁₀, q₁₅, q₂₀}
Σ = {5, 10}
Δ = {(D, R5) | D ∈ {0,1}, R5 ∈ {0,1}}
δ: Q × Σ → Q (state transition function)
λ: Q → Δ (output function - depends on state ONLY)
q₀ = initial state (₹0 collected)
```

## ⚖️ Comparison: Mealy vs Moore

| Feature              | Mealy Machine          | Moore Machine            |
|----------------------|------------------------|--------------------------|
| **Output depends on**| Current state & input  | Current state only       |
| **Reaction speed**   | Immediate              | One cycle delayed        |
| **Number of states** | Fewer (3)              | More (5)                 |
| **Output stability** | May glitch on bounces  | Very stable              |
| **Implementation**   | Compact and efficient  | Easier to debug          |
| **Best suited for**  | Real-time quick response | Reliable timing systems |

## ✅ Advantages & Disadvantages

### Mealy Machine

**Advantages:**
- Fewer states required
- Immediate output response
- More compact design
- Efficient for real-time systems

**Disadvantages:**
- Sensitive to input glitches
- Outputs may be unstable with noisy inputs
- Harder to synchronize with clock cycles

**Use Cases:**
- Compact digital circuit designs
- Quick response applications
- Resource-constrained systems

### Moore Machine

**Advantages:**
- Stable, predictable outputs
- Easy hardware implementation
- Less sensitive to input noise
- Simpler debugging process

**Disadvantages:**
- Requires more states
- One clock cycle output delay
- Larger state space

**Use Cases:**
- Safety-critical systems
- Synchronized/clocked systems
- Systems requiring stable outputs

## 💡 Recommendations

### For Theoretical Study
Both models should be demonstrated to highlight their fundamental distinctions in FSM design.

### For Real-World Implementation
A **Mealy-based design** with input debouncing or a **counter-based hybrid FSM** is recommended for:
- Better efficiency
- Faster responsiveness
- Compact implementation

For systems prone to signal noise, a **Moore machine** provides more reliable operation.

## 📚 References

1. **Theory of Automata and Computation** - Hopcroft & Ullman
2. Lecture notes on Finite State Machines - University resources
3. Internal slides: TOA External Presentation (Coffee Vending Machine Design)

## 📁 Repository Structure

```
├── README.md
├── Report/
│   └── TOA_Mealy_vs_Moore_CoffeeMachine_Report.pdf
├── Presentation/
│   └── TOA_EXTERNAL_PRESENTATION.pdf
└── Diagrams/
    ├── mealy_state_diagram.png
    └── moore_state_diagram.png
```

## 🚀 Getting Started

### Theoretical Implementation
The state machines can be analyzed using the transition tables and state diagrams provided in the documentation.

### Simulation
State machines can be simulated using:
- Hardware description languages (Verilog/VHDL)
- Digital logic simulation tools
- Python/Java FSM libraries

## 📝 License

This project is for educational purposes as part of the Theory of Automata coursework.

## 🤝 Contributing

This is an academic project. For suggestions or improvements, please contact the team members.

---

**Course:** Theory of Automata  
**Institution:** [Your Institution Name]  
**Academic Year:** [Year]
