# dj-viz

Live projected visuals that react to **the music** and to **the DJ's hands**. The audio drives energy, bass, kicks and drops. A **Pioneer DDJ-FLX4** adds gestures: scratching, the crossfader, EQs, filters and pads each trigger visuals that match the action. The audience gets a visual show on top of the audio one.

## Run it
1. Open `index.html` in **Chrome or Edge** (Safari and Firefox don't support Web MIDI).
2. **Audio:** pick an input from the HUD dropdown (mic, BlackHole or an audio interface). The choice is remembered.
3. **Controller (optional):** plug in the DDJ-FLX4 and allow MIDI access.
4. `F` = fullscreen on the projector, `H` = hide HUD, `M` = audio on/off.

No controller? Drag to scratch, `1`–`8` for pads, `Z`/`X` for the crossfader.

## Getting the music in
The page listens to any audio input. Which one you use depends on the setup:

| Setup | Use it for | How |
|---|---|---|
| **Mac mic** | Quick check | Pick the built-in mic. Noisy, but no setup. |
| **Loopback (BlackHole)** | Testing at home on your own laptop | [docs/mac-loopback-setup.md](docs/mac-loopback-setup.md) |
| **Hardware split** | Live shows, any DJ, any gear | Mixer's spare output (booth / rec / master 2), or a Y-split of the FLX4 master RCA → USB audio interface → visuals laptop. Pick the interface in the dropdown. |

Levels are auto-normalised, so a quiet mic and a hot line input both give full-range movement.

## What reacts to what
**From the audio (works with any DJ):**

| Sound | Visual |
|---|---|
| Kick | Camera punch + thick pulse on the rings / grid |
| Bass / mid / high | Line weight / spoke sharpness and grid glow / sparkle |
| Overall energy | Brightness and speed: breakdowns dim and drift, drops glow and rush |

**From the FLX4 (gesture layer):**

| Control | Visual |
|---|---|
| Deck 1 / Deck 2 | Warm tunnel / cool neon grid |
| Crossfader + channel faders | Blend between the two worlds |
| Jog wheel (scratch) | Twist / tilt + RGB smear, follows hand direction |
| Low / Mid / High EQ | Scales how much of that band shows up (an EQ kill kills it visually too) |
| Filter knob | Low-pass closes in, high-pass washes out |
| Pads (all modes) | Colored shockwaves |
| Cue | White flash |

## How it works
```
audio input ──► FFT bands + kick detection ─┐
                                            ├─► performance state ──► WebGL fragment shader
MIDI ──► controller map ──► named events ───┘
```
The controller map at the top of the script turns raw FLX4 messages into named events. Unmapped messages show up red in the HUD; add a `bind()` line to map them.

## Roadmap
- [x] Audio input picker (mic / BlackHole / interface) + bass/mid/high + kick detection
- [ ] Ableton Link bridge for beat-locked visuals (BPM + bar position from Rekordbox/Serato)
- [ ] Pro DJ Link support for CDJ setups
- [ ] Now-playing track info → per-track scenes
- [ ] More scenes per deck
- [ ] Mappings for more controllers
