# dj-viz

Live projected visuals driven by a **Pioneer DDJ-FLX4**. Scratching, the crossfader, EQs, filters and pads each trigger visuals that match the action, so the audience gets a visual show on top of the audio one.

## Run it
1. Plug in the DDJ-FLX4.
2. Open `index.html` in **Chrome or Edge** (Safari and Firefox don't support Web MIDI).
3. Allow MIDI access. The HUD should list the controller.
4. `F` = fullscreen on the projector, `H` = hide HUD, `M` = audio input on/off.

No controller? Drag to scratch, `1`–`8` for pads, `Z`/`X` for the crossfader.

## What reacts to what
| Control | Visual |
|---|---|
| Deck 1 / Deck 2 | Warm tunnel / cool neon grid |
| Crossfader + channel faders | Blend between the two worlds |
| Jog wheel (scratch) | Twist / tilt + RGB smear, follows hand direction |
| Low EQ | Line weight (bass cut thins it, drop slams it back) |
| Mid / High EQ | Spoke sharpness / sparkle |
| Filter knob | Low-pass closes in, high-pass washes out |
| Pads (all modes) | Colored shockwaves |
| Cue | White flash |

## How it works
`MIDI → controller map → performance state → WebGL fragment shader`. The controller map at the top of the script turns raw FLX4 messages into named events. Unmapped messages show up red in the HUD; add a `bind()` line to map them.

## Roadmap
- [ ] Audio input picker (BlackHole / interface) + bass/mid/high band detection
- [ ] Ableton Link bridge for beat-locked visuals (BPM + bar position from Rekordbox/Serato)
- [ ] Now-playing track info → per-track scenes
- [ ] More scenes per deck
