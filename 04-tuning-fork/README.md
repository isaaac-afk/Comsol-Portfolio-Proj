# Project 04: Tuning Fork Eigenfrequency Analysis (Guided Study)

**Date:** 2026-06-07
**COMSOL:** 6.4
**Module:** Structural Mechanics (Solid Mechanics)
**Study:** Eigenfrequency (parametric in prong length)

**What this is:** COMSOL's tuning fork tutorial application. The model is COMSOL's; I ran it and wrote this up so I'd understand what the eigenfrequency study is actually doing. Drafted with Claude (Opus 4.8) and read through and edited by me. Source: COMSOL Application Libraries.

## The question

Why does a tuning fork ring at one clean note, and what sets that note? The model computes the fork's natural vibration frequencies and shows that the fundamental one, the pitch you actually hear, is fixed by the length of the prongs.

## How it works

Strike a tuning fork and it doesn't vibrate randomly. It settles into specific natural shapes called eigenmodes, each with its own frequency. An eigenfrequency analysis finds those with no applied load at all. The frequencies are a property of the shape and the material alone, so the study is really asking "what frequencies does this object want to vibrate at?"

The fundamental mode is the one that makes the sound: the two prongs swing in and out together, and that motion is the note you hear. The model computes that frequency and sweeps the prong length to show how the two are connected.

## What it shows

At a prong length of 0.0791 m, the fundamental eigenfrequency comes out to 440.16 Hz, which is A4, the concert pitch an orchestra tunes to. The mode shape shows the displacement growing from almost nothing at the base to a maximum at the prong tips. That's exactly why you hold a fork at the base: it's the still point, so your fingers barely damp the ring.

Because the study sweeps the prong length, the trend reads straight off the results: longer prongs ring lower, shorter prongs ring higher.

## Why it matters

This is the same resonance idea as the bracket in project 02, but turned on its head. There, resonance was a hazard to design away from. Here it's the entire point. The fork is shaped so that one clean eigenfrequency dominates, which is what makes it useful as a pitch reference.

The inverse version of the problem is the interesting engineering part. Instead of asking "what frequency does this length give," you ask "what length gives me 440 Hz," and solve it backwards. The COMSOL app does this with a secant-method root finder, which is a small taste of design optimization: choosing geometry to hit a target. (It's also the principle behind resonant medical tools like ultrasonic surgical tips, which are tuned to vibrate hard at one specific frequency.)

## What I took from it

- What an eigenfrequency analysis computes, and that it needs no applied load.
- Why the fundamental mode sets the pitch while the higher modes shape the timbre.
- How geometry (prong length) maps to frequency, and what it means to solve that backwards.
- The contrast with project 02: resonance as a feature here, resonance as a failure risk there.

## Making it mine (next)

This model is already parametric, so it's an easy one to take further:
- Pick a target note and find the prong length that produces it.
- Plot the fundamental frequency against prong length across the whole sweep.
- Switch the material (steel versus aluminum) and see how the pitch shifts at the same length.

## Opening it

Open in COMSOL 6.4 with the Structural Mechanics Module. Press **Compute** (F8) to run the eigenfrequency study. The prong length parameter is the thing to vary.
