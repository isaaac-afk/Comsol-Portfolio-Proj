# Project 03: Thermal Microactuator (Guided Study)

**Date:** 2026-06-06
**COMSOL:** 6.4
**Modules:** AC/DC (Electric Currents) + Heat Transfer + Structural Mechanics
**Study:** Stationary, fully coupled

**What this is:** COMSOL's two-hot-arm thermal actuator tutorial, the fully coupled `thermal_actuator_tem` version. The model is COMSOL's; I ran it and wrote this up to understand how the three physics fit together rather than just looking at the plot. Drafted with Claude (Opus 4.8) and read through and edited by me. Source: COMSOL Application Libraries.

## The question

This is a MEMS device, a microscopic actuator a fraction of a millimeter across that moves when you run current through it. The question the model answers is simple: send current in, and how far does the tip move, and why?

## How it works

Three physics, each one feeding the next, in a chain.

1. **Electricity.** A voltage drives current through the actuator's arms. The thin arms carry more resistance than the wide one.
2. **Heat.** That current dumps heat into the material (Joule heating, the same effect as the ablation model in project 01). The thin, high-resistance arms get much hotter than the wide arm.
3. **Motion.** Hot metal expands. Because the thin arms heat up and expand more than the cooler arm, the whole device bends to one side, like a bimetallic strip, except the bending is driven by uneven heating instead of two different metals.

What makes this a genuine multiphysics problem is that the three are actually linked. No current, no heat. No heat, no expansion. And the geometry decides how the heating splits between the arms. COMSOL solves all three at once instead of one after another.

## What it shows

The temperature plot runs from 300 K (room temperature, at the anchored pads) up past 500 K along the thin arms. That gradient is the whole story: the arms are the hot, expanding part, and the pads stay cool and fixed. The difference in expansion between the hot arms and the cooler arm is what pushes the tip sideways.

*Add your own number here: tip displacement was about ___ µm at the applied voltage.*

*(Screenshot in `images/`: temperature distribution across the actuator.)*

## Why it matters

This is one of the cleanest examples of turning an electrical signal straight into mechanical motion at the microscale. No motor, no hinges, just heat and expansion. Devices built on this idea drive micro-grippers, optical switches, and micro-positioners. It's also a good lesson in why you can't model these things in isolation: widen an arm and you change its resistance, which changes the heating, which changes the motion. All three effects have to be solved together or the answer is wrong.

## What I took from it

- How COMSOL chains three physics (electric, then thermal, then structural) in a single coupled solve.
- Why the geometry controls the whole effect, through its influence on resistance and heating.
- That thermal expansion can be used as an actuation mechanism, not just treated as a nuisance.
- Reading a temperature field on a real device and connecting it to the motion it produces.

## Making it mine (next)

- Sweep the applied voltage and plot tip displacement against it.
- Change the arm geometry and watch how the motion responds (the parameterized version of this tutorial is built for exactly that).
- Compare against the Joule-heating-only version to see what the structural coupling actually adds.

## Opening it

Open in COMSOL 6.4. The fully coupled version needs the Structural Mechanics Module or the MEMS Module. Press **Compute** (F8) to solve. The applied voltage is the obvious knob to turn.
