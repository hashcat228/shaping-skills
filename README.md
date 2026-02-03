# Shaping Skills

> ⚠️ **Alpha / Experimental** — These skills are under active development. Expect rough edges.

Claude Code skills for collaborative product shaping and system understanding.

---

## Breadboarding

Breadboarding transforms a workflow description into a complete map of affordances and their relationships. The output is a set of tables showing what the product does and how it's wired together — which we can render as a diagram of the shape.

### What Makes Breadboards Different

**Breadboards are a product point of view on the technical system.** They show how the system is wired together from the product and user experience perspective — not from the code organization perspective.

The question it answers: **"What does this product do, and how does it do it?"**

This is what unites everyone — product, design, engineering. At the end of the day, we have to evaluate what the product *does* and *how* it does it in order to:
- **Design changes** — understand current wiring before proposing new wiring
- **Evaluate behavior** — is the product doing the right thing?
- **Debug problems** — when behavior is wrong, trace the wiring to find what to change

Other diagrams organize around technical concerns (components, types, data structures). Breadboards organize around *capability* — what the system lets users do and how that works underneath.

### What Breadboards Uniquely Capture

1. **The product's operational reality** — What can users do? What happens when they do it? Why doesn't it work?

2. **UI and Code in one view** — Other diagrams stay in one layer. Breadboards span from button click (U) through handler (N) to store (S) to display (U).

3. **Two explicit flows** — Control flow (Wires Out) and data flow (Returns To) are separated.

### When to Use What

| Question | Best Tool |
|----------|-----------|
| How do our services communicate? | System Architecture |
| What happens step-by-step when X occurs? | Sequence Diagram |
| What states can this be in? | State Chart |
| What are the branching conditions? | Decision Tree |
| What types exist and how do they relate? | Class Diagram |
| What's the data model? | ER Diagram |
| **What can users do and how does it work?** | **Breadboard** |

Breadboards fill the gap between "high-level architecture" and "read the code." They show the operational structure at the level of *what the product does* — making them useful for product thinking, debugging behavior, and planning changes.

---

## Shaping

Shaping is a formalism for interacting with Claude Code when you want to iterate on both the requirements and different solution options. It provides notation and structure for exploring what to build before committing to implementation.

### Why Use a Formalism?

When you're shaping a feature with Claude, you're often going back and forth — refining what you actually need while sketching how you might build it. Without structure, this gets messy: requirements blur with solutions, trade-offs get lost, and it's hard to compare approaches.

The shaping formalism gives you:
- **Notation** — R0, R1... for requirements; A, B, C... for solution shapes
- **Separation** — requirements define constraints independent of any particular approach
- **Comparison** — fit checks (R × S matrices) reveal which shape best fits your constraints
- **Traceability** — decisions are recorded, not lost in conversation

The question it helps answer: **"What are we solving, and which approach best fits our constraints?"**

### Core Concepts

| Concept | Notation | Meaning |
|---------|----------|---------|
| **Requirements** | R0, R1, R2... | Problem constraints (what we need) |
| **Shapes** | A, B, C... | Solution options (pick one) |
| **Parts** | A1, A2, A3... | Parts of a shape (combine within shape) |
| **Alternatives** | A1-a, A1-b... | Approaches to a part (pick one per part) |
| **Fit Check** | R × S matrix | Decision matrix: ✅ pass, ❌ fail |
| **Spike** | — | Investigation task to learn how the system works |

### Phases

```
Shaping → Slicing → Implementation
```

| Phase | Purpose | Output |
|-------|---------|--------|
| **Shaping** | Explore problem and solution space | Requirements, shapes, fit checks, breadboard |
| **Slicing** | Break down for incremental delivery | Vertical slices with demo-able UI |

### Documents

| Document | Purpose |
|----------|---------|
| **Frame** | The "why" — problem, outcome, source material |
| **Shaping doc** | Ground truth — R, shapes, fit checks, breadboard |
| **Slices doc** | Implementation plan — vertical slices with demos |

### Spikes

A spike is an investigation task to learn how the existing system works and what concrete steps are needed to implement a part. Use spikes when there's uncertainty about mechanics or feasibility.

Spikes answer questions like:
- "Where is the X logic?"
- "What changes are needed to achieve Y?"
- "Which constraints affect this approach?"

The output is understanding — enough to describe the steps needed. Spikes gather information; decisions come afterward based on that information.

### Integration with Breadboarding

Once a shape is selected, use `/breadboarding` to detail it into concrete affordances. The breadboard shows exactly what users can do and how it wires together — making the shape concrete enough to slice and build.
