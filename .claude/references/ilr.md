# Reference: Designing Interactive Learning Resources (ILR)

## 1. Resource Taxonomy

An effective curriculum is divided into two distinct archetypes that balance guided learning with independent problem-solving.

| Feature          | **Tutorials**                          | **Labs**                                  |
| :--------------- | :------------------------------------- | :---------------------------------------- |
| **Primary Goal** | Conceptual acquisition & micro-skills. | Synthesis & practical application.        |
| **Structure**    | Multiple short lessons (Linear).       | Single, comprehensive project.            |
| **New Concepts** | Introduced and explained.              | **Zero** new concepts; only applications. |
| **User Tasks**   | Guided, atomic action items.           | Open-ended User Stories.                  |

---

## 2. Tutorial Architecture (The "2-Minute Rule")

Tutorials are the engine of the curriculum, designed for rapid, high-frequency success to build learner confidence.

- **Time-to-Success:** Each individual lesson must be consumable and solvable within **2 minutes**.
- **Action-Centric Learning:** Every lesson **must** require the learner to perform at least one physical or logical action. Purely passive reading is prohibited.
- **Reinforcement Lessons:** Periodically include lessons that omit the conceptual explanation. These should focus entirely on additional action items that vary the context of a previously taught skill to ensure transferability.
- **Strategic Scaffolding:** Do not force learners to build from first principles on every project. Use "seeded" states—pre-built boilerplates, directory structures, or initial variable states—so the learner focuses exclusively on the specific learning outcome of that lesson.

---

## 3. Lab Architecture (The Synthesis Phase)

Labs act as the "final boss" of a module, testing the learner's ability to combine multiple concepts.

- **User Stories:** Deliver requirements as high-level User Stories (e.g., _"The system should notify the user when the temperature exceeds 100°C"_) rather than step-by-step instructions.
- **Interdependency:** User Stories and their associated evaluations can be **cascading**. Success in one part of the lab may be a prerequisite for the next.
- **Zero-Theory Zone:** If a concept was not explicitly covered in a prior tutorial, it must not appear in a lab.

---

## 4. The Interactivity Hierarchy

The goal is "Game Board" levels of agency. LLMs must prioritize interactivity in the following order:

1.  **Direct Manipulation (Gold Standard):** Interacting with a live environment (e.g., a terminal, a logic board, a 3D model, or a code editor).
2.  **Simulations & Animations:** For abstract or physical topics (e.g., physics, construction, chemistry), provide interactive simulations where the learner adjusts variables (torque, pH, velocity) to observe real-time outcomes.
3.  **Passive Assessment (Last Resort):** Multiple-choice or fill-in-the-blank questions. These are **not** considered fully interactive and should only be used when no physical or logical state can be reasonably manipulated.

---

## 5. Evaluation & Feedback Paradigm

All evaluations are programmatic assertions of the learner's current state within the browser environment.

### Feedback Components:

- **Learner-Facing Requirement:** A clear, static sentence explaining what the system is looking for (e.g., _"The support beam must be able to withstand 500kN of force"_).
- **Technical Assertion Trace:** A dynamic, technical error message provided for debugging purposes (e.g., Assertion failed: expected stress < 450MPa, received 510MPa).
- **Pedagogical Hints:** Optional nudges triggered after failed attempts to guide the learner back to the correct logic without revealing the answer.

---

## 6. Gamification & Engagement

To maintain momentum and provide a sense of progression, the ILR should feature:

- **Stateful Feedback:** Distinct visual cues or animations for successful completions versus failed attempts.
- **Progress Tracking:** Visual indicators of how much of the tutorial or lab remains.
- **Engagement Hooks:** Elements like daily streaks or achievements to reward consistency.
