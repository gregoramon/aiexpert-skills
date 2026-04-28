---
name: shotcraft
description: Generate copy-paste-ready Seedance 2.0 video prompts from a creative brief. Use when the user asks for a video prompt, Seedance prompt, shot list, or describes a scene, product film, commercial, social clip, cinematic interview, or UGC concept they want turned into a generation-ready prompt.
---

# Shotcraft (by AI Expert)

Turn a brief into a copy-paste-ready Seedance 2.0 prompt: a beat-by-beat timeline written in prose-rich, register-aware language. Every beat carries visual, camera, light, audio, and timing. Output is the timeline only — nothing else.

## How this works

1. Read `references/shotcraft-reference.txt` to calibrate detail level, prose density, and cinematic vocabulary. Always read it before drafting.
2. Read the user's brief. If it's too vague to act on (e.g. "make something cool"), ask ONE focused question. Otherwise make creative decisions where the user hasn't specified, and proceed.
3. Output the beat-by-beat timeline in plain text. No effects inventory, no density map, no energy arc, no preamble, no commentary, no closing remarks. Just the timeline. The user is going to copy-paste it into Seedance.

## Output format

Each beat is one block:

```
BEAT [N] ([timestamp]) — [Story title]
• EFFECT: [primary effect] + [stacked effects]
• VISUAL: [Prose: subject, wardrobe, body language, action, framing, environment. Use negative directives where the wrong default is plausible — "NOT slow," "NOT ceremonial," "NOT showy."]
• CAMERA: [Angle, movement, motivation. Use lens / sensor / format vocabulary when the register calls for it — cinematic = "85mm at f/1.4"; UGC = "phone-POV, constant low-amplitude shake."]
• LIGHT + GRADE: [Atmosphere first, then technical: "cool diffused terminal daylight, slight bloom on glass" → "warm clean grade, lifted blacks."]
• AUDIO: [Music dynamics, voice cues, sound design, mix behaviour. Even silence is a choice — write "room tone only, no score" when that's the intent.]
• TIMING: [Frame rate, speed, holds, beats.]
• EXIT: [How this beat hands off to the next.]
• (SIGNATURE) — flag here when this beat carries a signature moment.
```

Rules:
- Each beat is 1–4 seconds, unless the brief calls for a held moment.
- Write VISUAL as PROSE, not a stripped-down checklist. Wardrobe specifics, body-language nuance ("shoulders relaxed, jaw closed, head scanning"), environmental texture, continuity cues — these prevent generic output.
- Use negative directives where defaults could go wrong. "NOT ceremonial" stops the model drifting into formal-procession choreography. Models drift toward averages; explicit negatives anchor intent.
- Reason about physics and continuity. If a tall subject enters a sedan, note the duck. If a foreground phone occludes the subject, note when it clears. The model doesn't track scale or consistency — you do.
- Audio is part of the prompt. Seedance 2.0 supports audio. Write it explicitly: music dynamics, sound design, mix behaviour, even intentional silence.
- Be specific in the right register. "240fps overcrank" + "85mm anamorphic" is cinematic; "phone-POV handheld jostle" + "auto-exposure hunt" is UGC. Don't mix vocabularies.
- Stacked effects: list them. Three things at once = name all three.
- Transitions are beats. Whip pans, autofocus snaps, crowd cheer swells, focus pulls — write them in.
- Signature moments — 5–10s gets 1, 10–20s gets 1–2, 20–30s gets 2–3. Mark each `(SIGNATURE)` at the end of the block.
- Describe the visual *result*, not the editing software step.

## Cinematic vocabulary

Use this language explicitly inside beats — Seedance 2.0 responds to it.

**Camera movement:** dolly-in / pull-out, push-in, truck (lateral), pan, tilt, crane, jib, orbit, arc, gimbal, handheld, steadicam, whip pan, locked-off, parallax dolly, rack focus, phone-POV.

**Camera behaviour (UGC register):** auto-exposure hunt, autofocus pull (snap-focus), foreground occlusion, micro-zoom (operator pushes phone forward), reframe up/down, bumped-by-crowd jolt, phone held vertically at chest height.

**Lens / focal length:** 14mm ultra-wide, 24mm wide, 35mm normal-wide, 50mm normal, 85mm portrait, 100mm macro, 135mm tele, anamorphic (oval bokeh, horizontal flares), tilt-shift.

**Format / sensor:** 35mm film grain, 16mm grain (looser, dirtier), Super 8 (heavy grain, gate weave), full-frame digital, ARRI Alexa highlights, RED clarity, iPhone-style (UGC), VHS / camcorder.

**Lighting:** golden hour, blue hour, overcast soft, hard noon, tungsten practicals, neon practicals, single key, rim / backlight, motivated, hard / soft, key-to-fill ratio, slight bloom on glass, specular highlight roll.

**Grade / look:** teal-orange, desaturated, milky lifted blacks, high-contrast, bleach-bypass, warm clean, cold clinical, filmic halation.

**Frame rate:** 24fps cinematic, 48fps gentle overcrank, 96fps slow-mo, 120fps deep slow-mo, 240fps extreme slow-mo, 60fps web-smooth.

**Audio:** music swell / drop / sting / score, diegetic vs non-diegetic, voice-over, dialogue, PA announcement (two-tone chime + slight distortion), ambient room tone, foley, sound design, mix duck (one element softens to let another through), audio compression on impact, fade in/out, hard cut, intentional silence, close-mic'd vs distant.

**Composition:** rule of thirds, centered symmetrical, deep focus, shallow DOF, foreground occlusion, leading lines, negative space.

## Domain matrix

The same beat structure works across all of these — what shifts is the register.

| Domain | Register |
|---|---|
| **Product film** | macro + studio lighting + controlled movement + clean grade + light sound design |
| **Commercial / brand film** | full cinematic vocabulary + signature effects + emotive grade + score |
| **Social vertical (9:16)** | shorter beats (1–2s), centered subjects, punchier cuts, less held breath |
| **Cinematic interview** | locked-off A-cam + handheld B-roll inserts + soft natural light + clean dialogue mix + room tone |
| **UGC / phone-POV** | handheld jostle, no lens calls, available light, looser framing, behavioural camera language ("auto-exposure hunt," "operator gets bumped"), diegetic crowd / room sound |

Pick the register that matches the brief.

## Creative principles

1. **Contrast drives impact.** Alternate dense and clean moments. A slow beat after a fast one hits harder than two fast beats in a row.
2. **Signature moments matter.** Every video gets at least one — longer pieces can carry two or three. Mark each `(SIGNATURE)`.
3. **Transitions are beats.** Whip pans, autofocus snaps, crowd cheer swells, focus pulls — write them in.
4. **Specificity in the right register.** Numbers, lenses, grades for cinematic; behavioural camera language for UGC. Don't mix.
5. **Anchor what models drift on.** Detail wardrobe and body language. Use negative directives. Reason about scale and continuity. Write audio. These four are where generic output comes from — leave none to chance.
6. **Energy resolves.** No matter how intense the open, the close should feel intentional, not like the budget ran out.

## Duration calibration

- 5–10s: 4–7 beats, lean, 1 signature.
- 10–20s: 8–14 beats, 1–2 signatures.
- 20–30s: 12–20 beats, 2–3 signatures.
- 30s+: scale up but maintain density contrast — don't fill every second.

If the user doesn't specify a duration, default to 15s.

## Tone

Director's beat notes. Direct, prose-rich, no hype. Trust the reader.
