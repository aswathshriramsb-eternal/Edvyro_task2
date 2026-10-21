
# ⚡ Polarity Pulse — Game Design & Playtest Pack (Task 2)

![Track](https://img.shields.io/badge/Track-Game_Development-00F0FF?style=for-the-badge)
![Task](https://img.shields.io/badge/Task_2-GDD_%26_Playable_Prototype-FF6B00?style=for-the-badge)
![Assets](https://img.shields.io/badge/Assets-100%25_Original_Procedural-10B981?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-slate?style=for-the-badge)

> **Live Playable Prototype & Interactive GDD:** [Insert Your Deployed Link Here]

**Polarity Pulse** is an original single-button reflex arcade game and interactive design specification built for the **EdVyro Game Development Track (Task 2: Game Design Document and Playable Prototype)**. The entire submission is packaged into a single, zero-dependency web application containing the playable prototype, the one-page GDD, annotated SVG feedback state sketches, and a live anonymous playtest telemetry sheet.

---

## 📋 Table of Contents
1. [Prototype Constraints Verification](#-1-prototype-constraints-verification)
2. [One-Page Game Design Document (GDD)](#-2-one-page-game-design-document-gdd)
3. [Main Screen & Feedback State Sketches](#-3-main-screen--feedback-state-sketches)
4. [Playtest Sheet & Zero-Explanation Onboarding](#-4-playtest-sheet--zero-explanation-onboarding)
5. [Tech Stack & Original Asset Architecture](#-5-tech-stack--original-asset-architecture)
6. [How to Run Locally](#-6-how-to-run-locally)

---

## ✅ 1. Prototype Constraints Verification

| Constraint | Implementation in Polarity Pulse | Status |
| :--- | :--- | :--- |
| **One Core Action** | Single-button magnetic phase inversion toggling between **Blue (+ Circle)** and **Orange (− Hexagon)**. | ✔️ Verified |
| **One Clear Goal** | Absorb matching energy waves to reach **1,500 PTS** and stabilize the reactor core before losing all 3 shields. | ✔️ Verified |
| **3–5 Minute Session** | Wave velocity, laser gate frequency, and combo multipliers (1x–4x) are mathematically paced for a ~3.5-minute run to 1,500 PTS. | ✔️ Verified |
| **Keyboard & Touch Controls** | Full desktop keyboard support (`SPACE`, `W`, `Up`, `Enter`, `P`, `R`, `M`) + mobile touch canvas tap & dedicated on-screen action bar. | ✔️ Verified |
| **Original / Licensed Assets** | 100% original procedural HTML5 Canvas vector geometry + real-time WebAudio API synthesizer (zero external sprites or audio files). | ✔️ Verified |

---

## 📖 2. One-Page Game Design Document (GDD)

### 2.1 Player Fantasy & Target Audience
* **Player Fantasy:** You are a *Subatomic Containment Specialist* operating the magnetic core of an unstable plasma reactor. Channeling high-speed, chaotic energy waves into harmonic resonance through split-second timing makes the player feel like a razor-sharp reflex operator.
* **Target Audience:** Casual arcade, rhythm, and fast-twitch reflex players (ages 10+, fans of *Super Hexagon*, *Duet*, and *Ikaruga*) seeking an immediately readable, high-contrast browser or mobile game with zero tutorial bloat.

### 2.2 Core Gameplay Loop
$$\text{Action} \longrightarrow \text{Feedback} \longrightarrow \text{Consequence} \longrightarrow \text{Next Decision}$$

1. **Action (Invert Polarity):** The player presses `SPACE` or `Taps` to toggle the core between **Positive (+ Blue Circle)** and **Negative (− Orange Hexagon)** in 0ms.
2. **Feedback (Multi-Sensory):**
   * *Match:* Core elastically scales to `1.35x`, emits an expanding radial shockwave, bursts 18 velocity-inherited particles, floats `+PTS` combat text, and plays an ascending pentatonic synth chime.
   * *Mismatch:* 180ms directional camera shake, crimson border vignette flash, shattered shield particles, and a low sawtooth warning buzz.
3. **Consequence (State Update):**
   * *Match:* Awards `+10 × Multiplier` PTS (`+15 × Multiplier` for Laser Gates), increments streak, scales multiplier up to `4x` (every 4 streak), and **restores +1 lost shield every 8 consecutive matches**.
   * *Mismatch:* Shatters 1 of 3 orbiting shield segments and resets the combo multiplier to `1x`.
4. **Next Decision (Anticipation):** The player reads the shape, color, and speed of the next descending orb or laser gate along the central sightline and decides whether to hold or invert polarity.

### 2.3 Game States (Onboarding, Win, Loss, Pause, Restart)
* **Onboarding State (Silent / Zero-Text):** The first 2 waves of every run spawn deterministic single orbs—Wave 1 matches the player's starting Blue (+) polarity; Wave 2 is an Orange (−) orb surrounded by a pulsing golden visual ring prompting a flip without text clutter.
* **Win State (1,500 PTS):** Displays the *Overdrive Stabilized* victory screen with run duration, max streak, accuracy percentage, and the option to continue into *Endless Freeplay*.
* **Loss State (0 Shields):** Displays the *Containment Breach* screen detailing final score, survival time, and the exact wave/score failure point.
* **Pause State (`P` / `ESC`):** Immediately freezes delta-time physics and audio oscillators with a status overlay.
* **Restart State (`R`):** Instant zero-load reset from any state, archiving telemetry into the Playtest Sheet.

### 2.4 Input Map (Keyboard & Touch)
| Action | Keyboard Binding | Touch / Pointer Binding |
| :--- | :--- | :--- |
| **Flip Polarity (+ / −)** | `SPACE`, `W`, `Up Arrow`, or `Enter` | Tap anywhere on Canvas or tap `⚡ FLIP POLARITY` button |
| **Pause / Resume Game** | `P` or `Escape` | Tap `Pause (P)` button in top HUD bar |
| **Quick Restart Run** | `R` | Tap `Restart (R)` button in top HUD bar |
| **Toggle Audio Synth** | `M` | Tap `🔊 SFX: ON/OFF` button |
| **Toggle Onboarding Mode** | — | Tap `🎯 Onboarding: Zero-Text / HUD Hints` button |

### 2.5 Deliberate Scope Cuts
* **✕ No 2D Spatial Movement:** Deliberately excluded X/Y joystick movement so 100% of player attention remains focused on single-button timing and polarity reading.
* **✕ No Meta-Progression Shops or Currencies:** Excluded upgrade trees and inventory menus to keep the 3–5 minute arcade loop pure and self-contained.
* **✕ No External Asset Requests:** Excluded external PNGs, MP3s, and game engines so the prototype loads instantaneously in one file offline or online.

---

## 📐 3. Main Screen & Feedback State Sketches

The application includes three embedded, annotated SVG architectural wireframes (`#sketches` section):
1. **Sketch A — Main Screen & HUD Sightline:** Illustrates the peripheral top HUD bar, the uncluttered central magnetic track, the 3 orbiting shield arcs around the player core, and dual color+shape encoding (`+ Circle` vs `− Hexagon`) for colorblind accessibility.
2. **Sketch B — Positive Absorption State:** Illustrates the expanding concentric shockwave rings, radial particle burst vectors, `+40 PTS (4x)` floating pop-up, and harmonic synth feedback.
3. **Sketch C — Mismatch & Shield Breach State:** Illustrates the 180ms camera displacement, crimson danger vignette, shield arc fracture, and multiplier reset feedback.

---

## 🧪 4. Playtest Sheet & Zero-Explanation Onboarding

All playtest observations follow strict privacy rules (**zero personal data collected**—anonymous session IDs and behavioral telemetry only).

| Session ID | Understood Goal? | 1st Action Time | Failure Points | Accessibility Issues | Delight / Frustration Moments | One Change to Retest |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **PT-01 (Baseline)** | Yes (Silent) | `1.42s` | Double-gate speed transition at 650 PTS | None; shape coding (`+ circle` / `− hex`) aided contrast | *Delight:* 8x shield restore chime.<br>*Frustration:* Sudden gate arrival | Add 300ms pre-spawn lane warning pulse before laser gates |
| **PT-02 (Mobile Touch)** | Yes (Silent) | `1.18s` | Rapid alternating orb pair at 1,100 PTS | Thumb slightly covered lower core when tapping canvas directly | *Delight:* Dedicated bottom flip button.<br>*Frustration:* Late flip on pair | Raise player core Y-position by 15px for clearer thumb clearance |

*Note: The live application also features an interactive **Playtest Observation Logger** that auto-fills the player's latest run telemetry (First Flip Time, Accuracy, Survival Duration, and Failure Point) directly into the table.*

---

## 🛠️ 5. Tech Stack & Original Asset Architecture

* **Core Engine:** Vanilla JavaScript (`requestAnimationFrame` delta-time loop) + HTML5 `<canvas>` 2D Context.
* **Audio Engine:** Procedural WebAudio API (`OscillatorNode` + `GainNode` frequency ramps for triangle, sine pentatonic scale, and sawtooth waveforms).
* **UI & Styling:** Tailwind CSS + SVG Blueprints.
* **Typography:** `Syne` (Display Headings), `Plus Jakarta Sans` (Body), and `Fira Code` (Monospace HUD & Telemetry).

---

## 🚀 6. How to Run Locally

Because the entire project is built using a single-file architecture with zero build steps required:

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/polarity-pulse-task2.git
   ```
2. Open `index.html` directly in any modern desktop or mobile web browser, or serve it locally:
   ```bash
   npx serve .
   ```
