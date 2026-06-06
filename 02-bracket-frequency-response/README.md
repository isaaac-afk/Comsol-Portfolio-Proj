# Project 02: Bracket Frequency Response (Guided Study)

**Date:** 2026-06-05
**COMSOL:** 6.4
**Module:** Structural Mechanics (Solid Mechanics)
**Study:** Frequency Domain

**What this is:** One of COMSOL's bracket tutorials from the Structural Mechanics Module, the frequency response analysis. The geometry and setup are COMSOL's (tutorial series, model 10314); I ran the analysis and wrote this up so I'd understand what it's doing rather than just looking at a colored plot. Drafted with Claude (Opus 4.8) and read through and edited by me.

## The question

A static analysis tells you what happens when you push on a part once and hold it. But real parts get shaken, by motors, road vibration, whatever is bolted nearby. This analysis asks a different question: if you vibrate the bracket with a load that oscillates at different frequencies, how hard does it shake back, and where does the stress pile up?

## How it works

Instead of one steady load, the bracket gets a harmonic load, a force that swings back and forth at a set frequency. COMSOL solves for the steady vibration that settles in, then sweeps that frequency across a range and records the response at each step.

The point of doing this is resonance. Every structure has natural frequencies it "likes" to vibrate at (its eigenfrequencies). Drive it near one of those and the response blows up: small push, big shake. Drive it far from one and almost nothing happens. The frequency sweep is how you find those danger zones before they find you.

*(If your version is the prestressed one, with Study 1 stationary and Study 2 frequency, it first applies a static preload and then computes the vibration on top of that loaded state. Being under load shifts the natural frequencies, the same way tightening a guitar string raises its pitch. Delete this paragraph if your model isn't the prestressed variant.)*

## What it shows

The plot is the Von Mises stress at 114 Hz, one frequency out of the sweep. The stress isn't spread evenly. It bunches up at the fillets where the bracket's arms meet the central body, which are the geometric pinch points. Those would be the first places to crack under repeated vibration.

*Add your own numbers here: peak stress was about ___ MPa at 114 Hz, and the largest overall response in the sweep happened at ___ Hz.*

*(Screenshot in `images/`: Von Mises stress at 114 Hz.)*

## Why it matters

Resonance is how things fail without an obviously huge load. A part rated for far more than its working stress can still crack if it gets vibrated near a natural frequency long enough, because the stress quietly amplifies every cycle and fatigue does the rest. So before you trust a bracket, or a robot arm, or a device housing, in service, you check where its resonances are and make sure nothing it'll actually experience lands on top of them.

## What I took from it

- The difference between a static analysis and a frequency response.
- What an eigenfrequency is, and why driving near one amplifies stress.
- Reading where stress concentrates on a real 3D part (fillets and corners, not flat faces).
- Why a preload can shift a structure's natural frequencies.

## Making it mine (next)

- Run an eigenfrequency study on its own and match the resonance peaks to specific mode shapes.
- Move the load or switch the material and watch the resonant frequencies shift.
- Plot a real response curve (stress or displacement against frequency) instead of a single snapshot.

## Opening it

Open in COMSOL 6.4 with the Structural Mechanics Module. The stored solution was cleared to keep the file small, so press **Compute** (F8) to regenerate the results; a frequency sweep takes a little while. The frequency range and the applied load are the obvious things to change.
