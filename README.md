# WatooM Traktor Pro 4 + padKONTROL Performance Mapping

A custom **Korg padKONTROL performance mapping for Traktor Pro 4**, designed to complement a **Native Instruments Traktor Kontrol S3** rather than replace it.

The S3 remains the main DJ controller for standard deck, transport and mixer duties. The padKONTROL adds a second performance layer for:

- FX control
- Loop Recorder
- Freeze / stutter performance
- Remix Deck sample triggering
- Live loop capture
- Layer muting and retriggering
- Latch and Gate sample performance
- Live remixing and arrangement

The current documented release is **v18**.

## Current Files

| File | Purpose |
|---|---|
| `WatooM-padKONTROL-S3-v18-SCENE8-LATCH-GATE-DW.tsi` | Current Traktor Pro 4 Generic MIDI mapping |
| `WatooM-S3-padKONTROL-Traktor-Pro-4-v18-Complete-User-Manual.pdf` | Full beginner-to-performance user manual |
| `WatooM-S3-padKONTROL-Traktor-Pro-4-v18-Complete-User-Manual.docx` | Editable version of the full user manual |

> The Traktor-exported TSI should be treated as the authoritative mapping. Keep a known-good copy before changing controller mappings.

---

## Hardware and Software

### Required

- **Traktor Pro 4**
- **Native Instruments Traktor Kontrol S3**
- **Korg padKONTROL**
- USB connections for both controllers

### Controller Roles

#### Traktor Kontrol S3

Use the S3 for the normal DJ workflow:

- Deck transport
- Play / Pause
- Cue / CUP
- Jog wheels
- Beat Sync
- Tempo
- Track loading and browsing
- Mixer channel volume
- Crossfader
- EQ
- Gain
- Headphone Cue
- Standard Hotcues
- Normal track loops

#### Korg padKONTROL

Use the padKONTROL for the additional performance layer:

- FX Units 1 and 2
- Loop Recorder
- Freeze slices
- Remix Deck sample cells
- Live sample capture
- Remix Deck layer control
- Latch / Gate performance

This separation deliberately avoids duplicating controls already available on the S3.

---

## Scene Layout

Each padKONTROL scene uses its own MIDI channel.

| Scene | MIDI Channel | Function |
|---:|---:|---|
| 1 | 10 | FX Unit 1 |
| 2 | 11 | FX Unit 2 |
| 3 | 12 | Loop Recorder |
| 4 | 13 | Freeze / Stutter |
| 5 | 14 | Remix / Sample Bank A |
| 6 | 15 | Remix / Sample Bank B |
| 7 | 16 | Remix Deck Layer Mixer |
| 8 | 1 | Capture / Latch / Gate Performance |

These channels must be **saved into the padKONTROL scene memory**. If a scene later reverts to Channel 10, the scene was probably edited but not written back to the Korg's internal memory.

---

# Installation

## 1. Connect the Hardware

Connect both controllers before starting Traktor:

- Traktor Kontrol S3
- Korg padKONTROL

## 2. Import the Mapping

In Traktor Pro 4:

1. Open **Preferences**.
2. Open **Controller Manager**.
3. Import `WatooM-padKONTROL-S3-v18-SCENE8-LATCH-GATE-DW.tsi`.
4. Select the imported **Generic MIDI** device.
5. Set its **In-Port** specifically to the Korg padKONTROL MIDI input.
6. Do **not** leave the mapping on `All Ports`.
7. Disable or remove old duplicate padKONTROL mappings.

Using the specific Korg MIDI port prevents unrelated MIDI devices from triggering padKONTROL commands.

## 3. Leave the S3 Mapping Alone

The S3 should continue using its normal Native Instruments mapping.

The custom TSI is for the **padKONTROL** and is not a replacement S3 mapping.

## 4. Restart Traktor

After importing or replacing the TSI, restart Traktor before troubleshooting an apparently inactive scene.

During development, some newly imported mappings only behaved correctly after restarting Traktor.

---

# Quick Soundcheck

Before using the setup, check these four things:

1. **S3**
   - Load a track.
   - Play / Pause works.
   - Cue works.
   - Mixer and headphones work.

2. **Scene 1**
   - Select Scene 1.
   - Pad 1 should operate FX Unit 1 Button 1.

3. **Scene 3**
   - Select Scene 3.
   - Pad 1 should operate the Loop Recorder Record control.

4. **Scene 8**
   - Select Scene 8.
   - Knob 2 should control Loop Recorder Dry/Wet.

If these tests pass, the basic routing is correct.

---

# Scene 1 - FX Unit 1

Scene 1 is the primary FX performance scene.

| Control | Function |
|---|---|
| Pads 1-3 | FX Buttons 1-3 Toggle |
| Pad 4 | Toggle FX Buttons 1-3 together |
| Pads 5-7 + Knob 1 | Select/control FX Knobs 1-3 |
| Pad 13 | Route Deck A to FX Unit 1 |
| Pad 14 | Route Deck B to FX Unit 1 |
| Knob 2 | FX Unit 1 Dry/Wet |
| X | FX Knob 1 |
| Y | FX Knob 2 |

### Pad 4 caveat

Pad 4 sends three independent Toggle commands. If FX Buttons 1-3 begin in mixed states, Pad 4 inverts each state; it does not guarantee a single all-on or all-off result.

### Example FX transition

1. Play Track A using the S3.
2. Select Scene 1.
3. Route Deck A to FX Unit 1.
4. Enable an FX button.
5. Increase Dry/Wet with Knob 2.
6. Manipulate the selected FX parameter.
7. Reduce Dry/Wet.
8. Disable the FX.

Use the S3 for the actual track, EQ and mixer transition throughout.

---

# Scene 2 - FX Unit 2

Scene 2 mirrors the FX workflow for FX Unit 2.

| Control | Function |
|---|---|
| Pads 1-3 | FX Buttons 1-3 Toggle |
| Pad 4 | FX Unit 2 On/Off |
| Pads 5-7 + Knob 1 | Select/control FX Knobs 1-3 |
| Pad 13 | Route Deck A |
| Pad 14 | Route Deck B |
| Knob 2 | FX Unit 2 Dry/Wet |
| X | FX Knob 1 |
| Y | Unused |

---

# Scene 3 - Loop Recorder

Scene 3 provides dedicated Loop Recorder control.

Typical controls include:

- Record / Stop / Overdub
- Play / Pause
- Undo / Redo
- Delete
- Dry/Wet
- Loop size

## Important Loop Recorder behaviour

When you finish the initial recording, Traktor may immediately play the newly recorded Loop Recorder buffer.

A practical workflow is:

1. Record.
2. Stop recording.
3. The loop begins playing.
4. Capture it into a Remix Deck if desired.
5. Stop or delete the Loop Recorder buffer when it is no longer needed.

If the previous recording is not cleared before recording again, Traktor can treat the next pass as an **overdub** rather than a new independent loop.

---

# Scene 4 - Freeze / Stutter

Scene 4 turns the padKONTROL into a Freeze performance surface.

| Control | Function |
|---|---|
| Pads 1-15 | Freeze Slices 1-15 |
| Pad 16 | Freeze Mode Toggle |
| Knob 1 | Slice Size |
| Knob 2 | Slice Count |

Slice 16 is intentionally not mapped because Pad 16 is reserved for Freeze Mode.

### Example Freeze fill

1. Play a track normally on the S3.
2. Select Scene 4.
3. Enable Freeze Mode using Pad 16.
4. Trigger several pads rhythmically.
5. Adjust Slice Size if required.
6. Return to the normal track.
7. Disable Freeze Mode.

---

# Scene 5 - Remix / Sample Bank A

Scene 5 uses MIDI Channel 14 and provides a Remix Deck / sample performance grid.

A useful sample organization is:

| Row | Pads | Suggested Content |
|---|---|---|
| Cell 1 | 1-4 | Kick, bass or primary groove loops |
| Cell 2 | 5-8 | Snare, clap, vocals or secondary hits |
| Cell 3 | 9-12 | Hats, fills, textures or FX |
| Looper | 13-16 | Record / Play / Undo / Delete |

Scene 5 Pad 1 was live-confirmed during development after correcting the Korg scene channel to Channel 14. The remainder of the grid follows the Traktor Direct Mapping command pattern and should be tested before relying on it in a live set.

---

# Scene 6 - Remix / Sample Bank B

Scene 6 mirrors the Scene 5 sample-bank approach on MIDI Channel 15.

Use it for a second bank of:

- drums,
- percussion,
- vocals,
- transition sounds,
- textures,
- loops,
- or alternate Remix Deck content.

Test the complete bank before live use.

---

# Scene 7 - Remix Deck Layer Mixer

Scene 7 is designed for performing with captured layers in Deck C.

| Pads | Function |
|---|---|
| 1-4 | Slot Mute / Unmute |
| 5-8 | Slot Retrigger |
| 9-12 | Slot FX On |
| 13 | Loop Recorder Record / Stop / Overdub |
| 14 | Loop Recorder Play / Pause |
| 15 | Undo / Redo |
| 16 | Delete |

## Example four-layer build

Assume Deck C contains:

- Slot 1 = drums
- Slot 2 = bass
- Slot 3 = percussion
- Slot 4 = synth / texture

Start with Slot 1 audible, then:

1. Bring in Slot 2.
2. Add Slot 3 after another phrase.
3. Add Slot 4.
4. Retrigger a layer for emphasis.
5. Momentarily route a layer through FX.
6. Remove layers one at a time for the breakdown.

The S3 remains responsible for the main Deck A/B mix while Scene 7 performs the Remix Deck layers.

---

# Scene 8 - Capture / Latch / Gate

Scene 8 is the live loop-building scene.

## Pad layout

```text
[ CAP S1    ][ CAP S2    ][ CAP S3    ][ CAP S4    ]
[ LATCH S1  ][ LATCH S2  ][ LATCH S3  ][ LATCH S4  ]
[ GATE S1   ][ GATE S2   ][ GATE S3   ][ GATE S4   ]
[ RECORD    ][ CLEAR     ][ UNDO      ][ SPARE     ]
```

Additional control:

- **Knob 2 = Loop Recorder Dry/Wet**

## Independent-layer capture workflow

1. Press **Record**.
2. Perform the sound or phrase you want to capture.
3. Press **Record** again to finish.
4. Capture the Loop Recorder into the desired Remix Deck slot.
5. Press **Clear** before recording the next independent layer.
6. Repeat for Slots 2-4.

Clearing between recordings is important. Otherwise the next recording may overdub the previous Loop Recorder buffer.

---

# Latch and Gate

Traktor Remix Deck Sample Cells have their own Trigger Type.

## Latch

A latched sample keeps playing after you release the trigger.

Use it for:

- drum loops,
- bass loops,
- repeating percussion,
- background textures,
- continuous layers.

## Gate

A gated sample plays only while the trigger is held.

Use it for:

- stabs,
- vocal chops,
- drum hits,
- temporary fills,
- rhythmic chopping,
- performance effects.

## Scene 8 design

Scene 8 provides separate rows for both behaviours:

- Pads 5-8 trigger the **Cell 1 / Latch** version.
- Pads 9-12 trigger the **Cell 2 / Gate** version.

To use the same source material both ways:

1. Put the sample in Cell 1.
2. Duplicate/copy it to Cell 2.
3. Set Cell 1 to **Latch**.
4. Set Cell 2 to **Gate**.

The MIDI mapping alone does not convert a latched sample into a gated sample; the Sample Cell Trigger Type controls that behaviour.

---

# Example Combined S3 + padKONTROL Performance

## Phase 1 - Start the track

On the S3:

1. Load Track A.
2. Cue it in headphones.
3. Start playback.
4. Set gain and EQ.

## Phase 2 - Add FX

On Scene 1:

1. Enable FX Unit 1.
2. Route Deck A.
3. Bring up Dry/Wet with Knob 2.
4. Manipulate FX parameters.
5. Back off Dry/Wet.

## Phase 3 - Create loop layers

On Scene 8:

1. Record a phrase into the Loop Recorder.
2. Stop recording.
3. Capture it into Slot 1.
4. Clear the Loop Recorder.
5. Repeat for additional layers.

## Phase 4 - Perform the layers

Switch to Scene 7:

1. Bring slots in and out.
2. Retrigger layers.
3. Send selected layers to FX.
4. Build or strip down the groove.

## Phase 5 - Add a fill

Switch to Scene 4:

1. Enable Freeze.
2. Trigger a quick slice pattern.
3. Disable Freeze.

## Phase 6 - Mix the next track

Return attention to the S3:

1. Load Track B.
2. Cue it.
3. Sync or beatmatch.
4. EQ the transition.
5. Bring Track B into the mix.
6. Remove Remix Deck layers as required.

The goal is for the padKONTROL to add performance capability while the S3 remains the reliable centre of the DJ mix.

---

# Recommended Beginner Practice Order

Do not try to learn all eight scenes at once.

1. **S3 fundamentals** — Load, Cue, Play, Sync, EQ, mixer and headphones.
2. **Scene 1** — FX buttons, Dry/Wet and FX parameters.
3. **Scene 3** — Record, Stop, Play, Delete and Undo.
4. **Scene 4** — Freeze toggle and slice triggering.
5. **Scene 5** — Sample triggering.
6. **Scene 7** — Layer mute, retrigger and FX.
7. **Scene 8** — Record, capture, clear, Latch and Gate.

Once those workflows are comfortable, begin combining them.

---

# Troubleshooting

## Nothing responds

Check:

- The correct Generic MIDI device is selected.
- In-Port is the Korg padKONTROL, not `All Ports`.
- The padKONTROL is connected before starting Traktor.
- The correct Korg scene is selected.

## Wrong scene runs commands

Verify the saved scene channels:

```text
Scene 1 = Ch10
Scene 2 = Ch11
Scene 3 = Ch12
Scene 4 = Ch13
Scene 5 = Ch14
Scene 6 = Ch15
Scene 7 = Ch16
Scene 8 = Ch1
```

Make sure each MIDI channel change was actually written into the padKONTROL scene memory.

## Scene changes revert to Channel 10

The scene was probably edited but not saved. Perform a Scene Write on the padKONTROL after changing the MIDI channel.

## One pad performs multiple actions

An older padKONTROL mapping may still be active. Disable or remove duplicate Generic MIDI mappings.

## Scene 8 recordings overdub the previous loop

Clear/Delete the Loop Recorder buffer after capturing it into a Remix Deck slot.

## A captured loop starts playing immediately

That can be normal Loop Recorder behaviour. Use Play/Pause or clear the buffer after capture.

## Hold does not stop a Remix sample

The Remix Deck cell is probably set to **Latch**. Set the Sample Cell Trigger Type to **Gate** if you want it to play only while held.

## Freeze pads do nothing

Enable Freeze Mode first.

## Scene 8 Knob 2 does nothing

Check:

- Scene 8 is saved on Channel 1.
- The v18 TSI is loaded.
- `Ch01 CC073` reaches the Traktor mapping.
- Loop Recorder is available in the Global Section.

---

# Mapping Validation Status

Not every part of the project has the same level of live testing.

| Area | Status |
|---|---|
| Scene 1 | Core FX behaviour live-confirmed |
| Scene 2 | Core layout follows Scene 1; FX2 routing changed to Toggle |
| Scene 3 | Loop Recorder commands based on Traktor-exported learned mappings |
| Scene 4 | Freeze commands based on Traktor-exported learned mappings |
| Scene 5 | Pad 1 live-confirmed; remaining cell grid should be tested |
| Scene 6 | Mirrors Scene 5; test full bank before live use |
| Scene 7 | Slot Mute row live-confirmed; Retrigger and Slot FX derived from Traktor-generated mappings |
| Scene 8 | Direct capture based on Traktor export; Latch/Gate behaviour also depends on Sample Cell configuration; Knob 2 controls Loop Recorder D/W |

Perform a complete soundcheck before using the mapping in a public performance.

---

# Documentation

The complete manual contains:

- scene diagrams,
- pad layouts,
- step-by-step examples,
- beginner exercises,
- Loop Recorder workflows,
- S3 integration,
- FX examples,
- Freeze examples,
- Remix Deck examples,
- song-building examples,
- troubleshooting,
- and performance preparation.

See:

- `WatooM-S3-padKONTROL-Traktor-Pro-4-v18-Complete-User-Manual.pdf`
- `WatooM-S3-padKONTROL-Traktor-Pro-4-v18-Complete-User-Manual.docx`

---

# Suggested Repository Layout

```text
.
├── README.md
├── mappings/
│   └── WatooM-padKONTROL-S3-v18-SCENE8-LATCH-GATE-DW.tsi
├── docs/
│   ├── WatooM-S3-padKONTROL-Traktor-Pro-4-v18-Complete-User-Manual.pdf
│   └── WatooM-S3-padKONTROL-Traktor-Pro-4-v18-Complete-User-Manual.docx
└── images/
    └── ...
```

---

# Versioning

Current documented release: **v18**

When changing the mapping:

1. Export the mapping from Traktor.
2. Keep the previous known-good TSI.
3. Increment the version.
4. Update the user manual.
5. Update this README.
6. Test every modified scene.
7. Perform a complete pre-performance soundcheck.

---

# Project Goal

This project turns the Korg padKONTROL into a dedicated **live-performance companion to the Traktor Kontrol S3**.

The S3 handles the dependable DJ fundamentals.

The padKONTROL adds the creative layer:

**FX + Freeze + Loop Recorder + Samples + Live Capture + Remix Layers + Latch/Gate Performance.**
