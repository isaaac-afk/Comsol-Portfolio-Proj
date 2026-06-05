# Project 01: Radiofrequency Tissue Ablation (Guided Study)

**Date:** 2026-06-03
**COMSOL:** 6.2 (solved), opened in 6.4
**Modules:** AC/DC (Electric Currents) + Heat Transfer (Bioheat)
**Study:** Frequency-Transient

**What this is:** A walkthrough of COMSOL's built-in RF Ablation example. I didn't build this model from scratch. It ships with the AC/DC and Heat Transfer modules and is documented in Walter Frei's 2016 COMSOL blog. I ran it and wrote up how it works so I'd actually understand it rather than just click Compute. The write-up was drafted with help from Claude (Opus 4.8) and then read through and edited by me.

## The question

RF ablation kills a tumor by cooking it. A needle electrode goes into the tissue, a 500 kHz current runs through it, and the tissue heats up until the cells die. The model answers one thing: over a couple of minutes of current, how hot does the tissue get, and how big is the region that actually gets destroyed?

## How it works

Two physics problems, solved together.

First the electrical one. Current from the electrode flows through the tissue and dumps heat wherever it runs densest. At 500 kHz the magnetic side of things is negligible (the skin depth works out to about a meter, far bigger than the centimeter-scale region we care about), so COMSOL skips the magnetic fields and just solves for voltage. The heat it produces is plain resistive heating, the same reason a toaster wire glows.

Then the thermal one. That heat feeds into the Pennes bioheat equation, which is ordinary heat conduction plus one extra term for blood. Flowing blood carries heat away, so the tissue doesn't just keep climbing in temperature forever. This matters more than it sounds: tissue sitting next to a big vessel is genuinely hard to ablate, because the blood keeps cooling it. Surgeons call it the heat-sink effect.

The two are linked in a Frequency-Transient study. COMSOL solves the steady 500 kHz electrical field once, hands the heating over to the thermal solver, and steps that forward in time from 0 to 120 seconds.

## Setup at a glance

- 2D axisymmetric geometry. The electrode is round, so you model a flat slice and spin it around the axis. Much cheaper than full 3D.
- Tissue treated electrically like weak saltwater (about 0.5 S/m).
- A Terminal condition sets the electrode voltage; the outer boundaries are insulated.
- Mesh refined near the electrode tip, where the heating is fiercest.
- A damage model tracks which tissue crosses the death threshold, so the ablated zone shows up directly in the results.

## What it shows

The heating piles up at the electrode tip. That is the main thing, and it is not obvious until you see it: the shape of the kill zone comes from where the electric field concentrates, not just from how much power you pour in. Sharpen the tip and that is where the tissue dies first. Temperature then spreads outward, blood perfusion fights back, and over 120 seconds you get a roughly teardrop-shaped region of dead tissue around the exposed part of the needle.

*(Screenshots to add to `images/`: voltage field, heating distribution, final temperature and damage zone.)*

## What I took from it

- How COMSOL bolts a frequency-domain electrical problem onto a transient heat problem.
- Why a high frequency lets you ignore magnetic fields.
- What the blood-perfusion term in the bioheat equation actually does.
- How a damage integral turns a temperature plot into a predicted ablation zone.

## Making it mine (next)

Right now this is COMSOL's model with my explanation on top. To turn it into work that is actually mine:

- Sweep the electrode voltage and treatment time, then plot how the ablated volume responds.
- Change the electrode tip shape and compare the damage zones.
- Put a blood vessel next to the electrode and measure the heat-sink effect.

Each of those becomes its own project (02, 03, and on).

## Opening it

Open `rf_ablation.mph` in COMSOL 6.2 or later with the AC/DC and Heat Transfer modules, then **Study 1 > Compute** (F8). It runs in under ten seconds. The voltage, the frequency, and the time range are the obvious knobs to play with.
