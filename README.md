# ✦ Celestial Instrument

A browser-based musical instrument controlled entirely by hand gestures — no keyboard, no MIDI controller, just your webcam.

**[▶ Try it live](https://SelenaJiangSR.github.io/celestial-instrument/)**

<video src="demo.mp4" controls width="100%"></video>

---

## What it does

Point your hands at the two wheels on screen to play chords in real time:

- **Left hand** — selects the root note (C, D, E, F, G, A, B)
- **Right hand** — selects the chord type (maj, m, m7, sus4, dim, aug, 7)
- **Center circle (either hand)** — stops all sound immediately
- Music only plays while your hand is actively on a section — move away and it stops

---

## Tech stack

| Tool | Purpose |
|------|---------|
| [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) | Real-time hand tracking via webcam |
| [Tone.js](https://tonejs.github.io/) | Web audio synthesis and scheduling |
| HTML5 Canvas | Radial wheel UI rendering |
| Salamander Grand Piano samples | Real piano recordings via Tone.Sampler |

Everything runs in a **single HTML file** — no install, no dependencies, no server needed.

---

## Sound design

Two instrument presets:

**Piano** — Real recorded samples from the Salamander Grand Piano library, loaded via Tone.Sampler. Short reverb tail for a natural, dry sound.

**Soul** — A custom RnB-style synth built with:
- 3 detuned sine waves (`fatsine`, spread: 22 cents) for warmth and body
- `Tone.Chorus` for a lush, silky texture
- Low-pass filter at 2400 Hz to smooth out harsh harmonics
- Moderate reverb (decay: 2.8s) for space without muddiness

Signal chain: `PolySynth → Filter → Chorus → Reverb → Compressor → Limiter → Output`

---

## How to use

1. Open the [live link](https://SelenaJiangSR.github.io/celestial-instrument/) in Chrome or Edge
2. Allow camera access when prompted
3. Wait for `GESTURE CAM ACTIVE ✦` to appear
4. Hold your **left hand** in front of the left wheel — point your palm at a note segment
5. Hold your **right hand** in front of the right wheel — point at a chord type
6. Switch timbre using the **piano / soul** buttons at the bottom

**Tips:**
- Works best in a well-lit room
- Keep hands roughly at chest height, facing the camera
- One hand controls note, the other controls chord — use both together for full chords

---

## Run locally

No setup required. Just download `index.html` and open it in a browser:

```bash
# Option 1: just open the file
open index.html

# Option 2: serve locally (avoids some camera permission issues)
python3 -m http.server 8000
# then open http://localhost:8000
```

---

## Project background

Built as a personal project to explore gesture-based human-computer interaction. The idea was to make something where your body is the interface — no device between you and the music.

All audio synthesis and hand tracking run entirely in the browser, making it zero-install and shareable via a simple link.

---

*Made by [Selena J.](https://github.com/SelenaJiangSR)*
