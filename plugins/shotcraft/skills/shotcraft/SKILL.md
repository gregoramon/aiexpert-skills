---
name: shotcraft
description: Generate copy-paste-ready Seedance 2.0 video prompts from a creative brief. Use when the user asks for a video prompt, Seedance prompt, shot list, or describes a scene, product film, commercial, social clip, cinematic interview, or UGC concept they want turned into a generation-ready prompt.
---

# Shotcraft (by AI Expert)

Turn a brief into a clean, copy-paste-ready Seedance 2.0 prompt: a shot-by-shot timeline written in cinematic language. Output is the timeline only — nothing else.

## How this works

1. Read `references/shotcraft-reference.txt` to calibrate detail level and cinematic vocabulary. Always read it before drafting.
2. Read the user's brief. If it's too vague to act on (e.g. "make something cool"), ask ONE focused question. Otherwise make creative decisions where the user hasn't specified and proceed.
3. Output the shot-by-shot timeline in plain text. No effects inventory, no density map, no energy arc, no preamble, no commentary, no closing remarks. Just the timeline. The user is going to copy and paste it into Seedance.

## Output format

Each shot is one block:

```
SHOT [N] ([timestamp]) — [Shot name / what we see]
• EFFECT: [primary effect] + [stacked effects]
• [Visual: subject, action, framing]
• [Camera: angle, movement, lens, sensor/format if relevant]
• [Light + grade]
• [Speed / timing]
• [Transition out of this shot into the next]
```

Rules:
- Each shot is 1–4 seconds, unless the brief calls for a held moment.
- Be specific. "20–25% speed" not "slow motion." "15° clockwise rotation" not "tilt." "85mm anamorphic" not "telephoto."
- Stacked effects: list them. If three things happen at once, name all three.
- Transitions are shots: a whip pan, bloom flash, or motion-blur smear is a creative beat, not a throwaway cut. Write them in.
- Mark the most distinctive shot with `(SIGNATURE)` — every video should have one hero moment.
- Describe the visual *result*, not the editing software step. Say "the frame scales inward sharply," not "apply a keyframed scale."

## Cinematic vocabulary

Use this language explicitly inside shots — Seedance 2.0 responds to it.

**Camera movement:** dolly-in / pull-out, push-in, truck (lateral), pan, tilt, crane, jib, orbit, arc, gimbal, handheld, steadicam, whip pan, locked-off, parallax dolly, rack focus.

**Lens / focal length:** 14mm ultra-wide, 24mm wide, 35mm normal-wide, 50mm normal, 85mm portrait, 100mm macro, 135mm tele, anamorphic (oval bokeh, horizontal flares), tilt-shift.

**Format / sensor:** 35mm film grain, 16mm grain (looser, dirtier), Super 8 (heavy grain, gate weave), full-frame digital, ARRI Alexa highlights, RED clarity, iPhone-style (UGC), VHS / camcorder.

**Lighting:** golden hour, blue hour, overcast soft, hard noon, tungsten practicals, neon practicals, single key, rim / backlight, motivated, hard / soft, key-to-fill ratio.

**Grade / look:** teal-orange, desaturated, milky lifted blacks, high-contrast, bleach-bypass, warm clean, cold clinical, filmic halation.

**Frame rate:** 24fps cinematic, 48fps gentle overcrank, 96fps slow-mo, 120fps deep slow-mo, 240fps extreme slow-mo, 60fps web-smooth.

**Composition:** rule of thirds, centered symmetrical, deep focus, shallow DOF, foreground occlusion, leading lines, negative space.

## Domain matrix

The same timeline structure works across all of these — what shifts is the cinematic register.

| Domain | Register |
|---|---|
| **Product film** | macro + studio lighting + controlled movement + clean grade |
| **Commercial / brand film** | full cinematic vocabulary + signature effect + emotive grade |
| **Social vertical (9:16)** | shorter shots (1–2s), centered subjects, punchier cuts, less held breath |
| **Cinematic interview** | locked-off A-cam + handheld B-roll inserts + soft natural light |
| **UGC** | handheld, no lens calls, available light, looser framing, no precise effect language |

Pick the register that matches the brief.

## Creative principles

1. **Contrast drives impact.** Alternate dense and clean moments. A slow-motion shot after a speed ramp hits harder than two ramps in a row.
2. **One signature shot.** Every video gets one visually distinctive hero moment. Mark it `(SIGNATURE)`.
3. **Transitions are shots.** Whip pans, bloom flashes, motion-blur smears — these are creative beats, write them in.
4. **Specificity wins.** Use numbers, lenses, grades. Don't use filler adjectives like "cinematic," "stunning," or "epic" inside the output — describe what actually happens.
5. **Energy resolves.** No matter how intense the open, the close should feel intentional, not like the budget ran out.

## Duration calibration

- 5–10s: 4–7 shots, lean, 1 signature.
- 10–20s: 8–14 shots, room for contrast, 1–2 signatures.
- 20–30s: 12–20 shots, full arc, 2–3 signatures.
- 30s+: scale up but maintain density contrast — don't fill every second with effects.

If the user doesn't specify a duration, default to 15s.

## Tone

Write like a director's shot notes. Direct, technical, no hype.
