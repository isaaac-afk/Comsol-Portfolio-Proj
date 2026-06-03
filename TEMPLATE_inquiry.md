# Project [NN]: [Project Title]

**Date:** [YYYY-MM-DD]
**COMSOL version:** [e.g. COMSOL 6.2]
**Physics interface(s):** [e.g. Heat Transfer in Solids]
**Study type:** [Stationary / Time-Dependent / Frequency Domain / Parametric Sweep]

**One-line summary:** [In a single sentence, what does this model do?]

---

## 1. Objective

> *What question are you trying to answer, or what phenomenon are you trying to capture?*

[Write 1–3 sentences. Example: "Investigate how the steady-state temperature distribution in a metal fin changes with convective cooling on its surface."]

## 2. Background & Motivation

> *Why does this matter? What's the real-world or engineering context?*

[Even 2–3 sentences is fine. This is the "implication" — connect the model to something concrete: a device, a biological system, a design decision.]

## 3. Physics & Governing Equations

> *Which physics is being solved, and what are the key equations?*

- **Module/interface:** [e.g. Heat Transfer in Solids]
- **Governing equation(s):** [e.g. steady-state heat conduction: ∇·(k∇T) + Q = 0]
- **Key assumptions:** [e.g. constant material properties, no radiation, 2D]

## 4. Model Setup

| Element | Details |
|---|---|
| **Geometry** | [shape and dimensions, 2D/3D] |
| **Materials** | [material(s) and the properties that matter, e.g. k, ρ, Cp] |
| **Boundary conditions** | [e.g. fixed temperature on left edge, convective flux on right edge, insulated elsewhere] |
| **Mesh** | [mesh type and refinement, e.g. physics-controlled, fine] |
| **Solver / study** | [e.g. stationary, default direct solver] |

## 5. Results

> *What did the simulation produce? Add screenshots to the `images/` folder and reference them here.*

![Result plot](images/result.png)

[Describe the key result(s) in words: maximum/minimum values, where they occur, any interesting patterns. Include numbers where you have them.]

## 6. Interpretation & Implications

> *What does the result mean? This is the most important section for a portfolio.*

[Explain what you learned. Did it match your expectation? What would change if you adjusted a parameter? Why would an engineer care about this result?]

## 7. Limitations & Assumptions

[List what the model simplifies or ignores, e.g. "2D approximation ignores edge effects," "constant properties ignore temperature dependence."]

## 8. Next Steps / Extensions

[What would you try next? e.g. "add a time-dependent study," "run a parametric sweep on thermal conductivity," "extend to 3D."]

## 9. How to Open

1. Open `[model].mph` in COMSOL Multiphysics [version].
2. To re-run: **Study > Compute** (or press F8).
3. [Any notes on parameters you can change to explore the model.]
