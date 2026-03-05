# Baby Sounds

A soothing sound mixer for helping babies sleep. No dependencies, no build step — just one HTML file.

## Features

- **9 layered sounds** — White Noise, Pink Noise, Rain, Ocean, Fan, Shushing, Womb, Heartbeat, Lullaby
- **Mix & match** — Per-sound volume faders with a master volume control
- **Presets** — Deep Sleep, Nap Time, Womb, and Clear for quick setups
- **Sleep timer** — 15m, 30m, or 1h with gentle fade-out
- **Screen dimmer** — Adjustable brightness so the screen doesn't light up the room
- **Visualizer** — Real-time frequency display
- **Works on iOS** — Routes audio through the speaker even with the mute switch on

## Usage

Open `index.html` in any modern browser. That's it.

## How It Works

All audio is generated in the browser using the [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API):

- **Noise-based sounds** (white/pink noise, rain, ocean, fan, shushing, womb) use pre-generated 20-second audio buffers shaped with filters and LFOs
- **Oscillator-based sounds** (heartbeat, lullaby) use real-time synthesis with gain envelopes and procedurally generated melodies
- Sounds fade in over 1.5s and fade out over 2s for smooth transitions

## License

MIT
