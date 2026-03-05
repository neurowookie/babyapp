# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Baby Sounds is a single-file web application (`index.html`) that generates soothing audio for babies using the Web Audio API. There is no build system, package manager, or external dependencies.

## Running the App

Open `index.html` directly in a modern browser. No build step or server required.

## Architecture

Everything lives in one `index.html` file (~939 lines) containing inline CSS and JavaScript:

- **CSS** (top): Custom properties for theming, responsive layout with media queries, animations, accessibility support (prefers-reduced-motion)
- **HTML** (middle): UI controls for sound mixer, presets, timer, screen dimmer, and visualization
- **JavaScript** (bottom): Audio engine and UI logic

### Audio Engine (Web Audio API)

The audio pipeline follows this chain: individual sound sources → per-sound gain nodes → master gain node → audio destination.

Sound generation approaches:
- **Noise-based** (white/pink/brown noise, rain, ocean, fan, shushing, womb): Pre-generated audio buffers (20s at 44.1kHz) played in loops, shaped with filters (low-pass, high-pass, band-pass) and LFOs for modulation
- **Oscillator-based** (heartbeat, lullaby): Real-time synthesis with oscillators, gain envelopes, and convolver reverb for the lullaby

Key audio behaviors:
- Sounds fade in over 1.5s and fade out over 2.0s using gain ramping
- Heartbeat BPM range: 40–120; Lullaby BPM range: 30–90
- The lullaby uses a procedurally generated melody with reverb via an impulse response

### UI Features

- Per-sound volume faders with a master volume control
- Presets (Deep Sleep, Nap Time, Womb, Clear) configure multiple sounds at once
- Timer system (15m, 30m, 1h) with fade-out before stopping
- Screen dimmer with adjustable brightness
- Real-time frequency visualization using AnalyserNode
