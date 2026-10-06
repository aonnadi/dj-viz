# Mac loopback setup (BlackHole)

Send the music playing on your Mac straight into dj-viz. You don't need extra hardware or a mic. It's a free way to test at home before moving to the hardware split (see the README).

**How it works:** the audio goes to a *Multi-Output Device*, which plays it through your speakers and copies it into **BlackHole**, a virtual audio cable. dj-viz then listens to BlackHole.

```
Rekordbox / Spotify ──► Multi-Output Device ──┬──► speakers / headphones (you hear it)
                                              └──► BlackHole 2ch ──► dj-viz (it sees it)
```

## 1. Install BlackHole (once)

Pick one:
- **Homebrew:** `brew install blackhole-2ch`
- **Installer:** download *BlackHole 2ch* from existential.audio and run it.

Restart your Mac (or at least quit and reopen any audio apps) afterwards.

## 2. Create a Multi-Output Device (once)

1. Open **Audio MIDI Setup** (Spotlight → "Audio MIDI Setup").
2. Click **+** at the bottom left and choose **Create Multi-Output Device**.
3. Tick both **BlackHole 2ch** and your speakers or headphones (for example, *MacBook Pro Speakers*).
4. Set **Primary Device** to your speakers, and tick **Drift Correction** next to BlackHole 2ch.
5. Optional: double-click the name and rename it to `DJ Viz Out`.

> macOS can't change the volume of a Multi-Output Device with the volume keys. Set the level in your DJ software or on the speakers instead.

## 3. Send audio to it

**Quick test with Spotify, Apple Music or YouTube:** go to System Settings → Sound → Output and pick the Multi-Output Device.

**Rekordbox:** go to Preferences → Audio → Audio, and pick the Multi-Output Device as the output.
- The FLX4's jog wheels, faders and pads keep working over MIDI. The sound now comes out of the Mac instead of the FLX4's master RCA, and **headphone cueing through the FLX4 won't work** in this mode. That's fine for testing visuals, but it's the main reason the hardware split is the real live setup.
- If your Rekordbox version doesn't let you choose another output while the FLX4 is connected, use a Spotify or YouTube test or the mic option for now.

**Serato:** Serato normally locks audio output to supported hardware like the FLX4, so loopback usually isn't possible. Use Rekordbox for loopback testing, or the hardware split.

## 4. Pick it in dj-viz

1. Open `index.html` in Chrome.
2. In the HUD dropdown, choose **BlackHole 2ch**. Allow microphone access when Chrome asks; that's how browsers label any audio input.
3. Play a track. The **bass / mid / high / kick** meters should move, and the visuals should pulse with the music.

dj-viz remembers the input, so next time it starts listening automatically. Press `M` to toggle audio on and off.

## When you're done

Switch your Mac's output (and Rekordbox's) back to your normal speakers or the FLX4.

## Troubleshooting

| Problem | Fix |
|---|---|
| Meters don't move | Check that the source app is outputting to the Multi-Output Device, not directly to the speakers. |
| No sound, but meters move | Your speakers aren't ticked in the Multi-Output Device. |
| Dropdown shows "Audio input" with no names | Pick any entry once and allow access. The real names appear after that. |
| Dropdown only shows "Audio: off" and "System default input" | The browser isn't listing inputs. Use Chrome (not Safari, and turn off Brave Shields if using Brave), then reload. Picking "System default input" just uses the Mac's default input, which is usually the built-in mic. |
| BlackHole isn't in the list, but other inputs are | Fully quit Chrome (⌘Q) and reopen it; if that doesn't help, restart the Mac. Check Audio MIDI Setup shows "BlackHole 2ch" as a device. |
| Quick workaround | System Settings → Sound → **Input** → BlackHole 2ch, then pick "System default input" in dj-viz. |
| "Click anywhere to start audio" | Chrome needs one click or keypress before audio can start. |
| Audio crackles or drifts out of sync | Make sure Drift Correction is ticked for BlackHole 2ch. |
