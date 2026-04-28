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

```text
BEAT [N] ([timestamp]) — [Story title]
• EFFECT: [primary effect] + [stacked effects]
• VISUAL: [Prose: subject, wardrobe, body language, action, framing, environment. Use negative directives where the wrong default is plausible — "NOT slow," "NOT ceremonial," "NOT showy."]
• CAMERA: [Angle, movement, motivation. Lens look ("85mm portrait, extremely shallow depth of field"), and where useful, a camera body / aesthetic ("ARRI ALEXA aesthetic," "Sony Venice look," "shot on iPhone," "Bolex 16mm grain"). For UGC: behavioural language ("phone-POV, constant low-amplitude shake," "auto-exposure hunt").]
• LIGHT + GRADE: [Atmosphere first, then technical: "cool diffused terminal daylight, slight bloom on glass" → "warm clean grade, lifted blacks."]
• AUDIO: [Music dynamics, voice cues, sound design, mix behaviour. Even silence is a choice — write "room tone only, no score" when that's the intent.]
• TIMING: [Pacing language ("slow steady push-in," "snap into stillness"), frame rate when it carries a look ("deep slow-motion," "gentle overcrank"). Avoid the unqualified word "fast" — known to degrade Seedance output. Use "rapid," "snap," "sudden" instead.]
• EXIT: [How this beat hands off to the next.]
• (SIGNATURE) — flag here when this beat carries a signature moment.
```

End every prompt with this exact constraints footer. The four stabilizers cover the most common Seedance failure modes — include all four every time, regardless of scene:

```text
CONSTRAINTS: avoid jitter, avoid identity drift, avoid bent limbs, avoid temporal flicker
```

What each stabilizer protects against:
- `avoid jitter` — frame-level shake / unwanted micro-movement on locked-off shots
- `avoid identity drift` — subject's face / wardrobe / build mutating across beats
- `avoid bent limbs` — anatomically broken arms, legs, fingers in motion
- `avoid temporal flicker` — flicker / strobe artefacts across the duration

Rules:
- **Total duration must not exceed 15 seconds.** Seedance 2.0 generates a maximum of 15 seconds per pass. For anything longer, generate multiple ≤15s prompts and stitch them in post.
- Each beat is 1–4 seconds, unless the brief calls for a held moment.
- **Beat timestamps must be monotonically increasing, contiguous, and non-overlapping.** Each beat starts where the previous beat ended (e.g. `00:00-00:01` then `00:01-00:03`, never `00:00-00:01` then `00:00-00:03`). No gaps unless the brief explicitly calls for a held silent moment.
- Write VISUAL as PROSE, not a stripped-down checklist. Wardrobe specifics, body-language nuance ("shoulders relaxed, jaw closed, head scanning"), environmental texture, continuity cues — these prevent generic output.
- Use negative directives where defaults could go wrong. "NOT ceremonial" stops the model drifting into formal-procession choreography. Models drift toward averages; explicit negatives anchor intent.
- Reason about physics and continuity. If a tall subject enters a sedan, note the duck. If a foreground phone occludes the subject, note when it clears. The model doesn't track scale or consistency — you do.
- Audio is part of the prompt. Seedance 2.0 supports audio. Write it explicitly: music dynamics, sound design, mix behaviour, even intentional silence.
- Be specific in the right register. Cinematic = lens look + camera body aesthetic + descriptive pacing ("85mm portrait, ARRI Alexa highlights, slow steady push-in"). UGC = behavioural language ("phone-POV handheld jostle, auto-exposure hunt"). Don't mix vocabularies.
- Avoid photography jargon. Seedance is trained on cinematic descriptions, not technical specs — `f/2.8`, `ISO 800`, `1/60s shutter` are noise. Lens focal length as a *look reference* ("85mm portrait," "anamorphic") is fine. Frame rate is fine when it carries a look ("deep slow-motion," "gentle overcrank") but not as a precise number unless meaningful.
- Stacked effects: list them. Three things at once = name all three.
- Transitions are beats. Whip pans, autofocus snaps, crowd cheer swells, focus pulls — write them in.
- Signature moments — 5–10s gets 1, 10–15s gets 1–2. Mark each `(SIGNATURE)` at the end of the block.
- Describe the visual *result*, not the editing software step.

## Cinematic vocabulary

Use this language explicitly inside beats — Seedance 2.0 responds to it.

**Camera movement:** dolly-in / pull-out, push-in, truck (lateral), pan, tilt, crane, jib, orbit, arc, gimbal, handheld, steadicam, whip pan, locked-off, parallax dolly, rack focus, phone-POV.

**Camera behaviour (UGC register):** auto-exposure hunt, autofocus pull (snap-focus), foreground occlusion, micro-zoom (operator pushes phone forward), reframe up/down, bumped-by-crowd jolt, phone held vertically at chest height.

**Lens look:** 14mm ultra-wide (visible distortion), 24mm wide, 35mm normal-wide, 50mm normal, 85mm portrait (extremely shallow DOF), 100mm macro, 135mm tele, anamorphic (oval bokeh, horizontal flares), tilt-shift. Focal length as look reference — avoid f-stop notation (Seedance treats it as noise).

**Camera body / aesthetic:** ARRI ALEXA aesthetic, ARRI 35, Sony Venice, Sony FX3 / FX6, RED Komodo, RED V-Raptor, Blackmagic Pocket, iPhone-shot, GoPro POV, Bolex 16mm (organic grain), Super 8 (heavy grain, gate weave), Hi8 / VHS camcorder (90s home-video), MiniDV (early 2000s indie), DSLR (Canon 5D Mark II — early-YouTube look). Seedance has learned these aesthetics during training — naming the body shifts the look in noticeable ways.

**Film stock / grain:** 35mm film grain, 16mm grain (looser, dirtier), Super 8 grain, clean digital, filmic halation, bleach-bypass.

**Lighting:** golden hour, blue hour, overcast soft, hard noon, tungsten practicals, neon practicals, single key, rim / backlight, motivated, hard / soft, key-to-fill ratio, slight bloom on glass, specular highlight roll.

**Grade / look:** teal-orange, desaturated, milky lifted blacks, high-contrast, bleach-bypass, warm clean, cold clinical, filmic halation.

**Pacing & frame rate (descriptive):** slow steady push-in, deep slow-motion, gentle overcrank, snap into stillness, held breath, rapid release, sudden cut. When citing frame rate, use it for a *look* ("deep slow-motion overcrank") — Seedance responds to descriptive pacing better than precise numbers.

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
2. **Signature moments matter.** Every video gets at least one — a 15s piece can carry up to two. Mark each `(SIGNATURE)`.
3. **Transitions are beats.** Whip pans, autofocus snaps, crowd cheer swells, focus pulls — write them in.
4. **Specificity in the right register.** Numbers, lenses, grades for cinematic; behavioural camera language for UGC. Don't mix.
5. **Anchor what models drift on.** Detail wardrobe and body language. Use negative directives. Reason about scale and continuity. Write audio. These four are where generic output comes from — leave none to chance.
6. **Speak Seedance's dialect.** Cinematic descriptors > technical specs. Camera body aesthetics ("ARRI ALEXA," "Sony Venice") shift the look. Avoid f-stop/ISO notation. Avoid the unqualified word "fast" (a known Seedance degrader — use "rapid," "snap," "sudden"). Always close the prompt with the relevant `CONSTRAINTS:` stabilizer line.
7. **Energy resolves.** No matter how intense the open, the close should feel intentional, not like the budget ran out.

## Duration calibration

**Seedance 2.0 caps at 15 seconds per generation.** Calibrate within that ceiling:

- 5–8s: 4–6 beats, lean, 1 signature.
- 8–12s: 6–10 beats, 1–2 signatures.
- 12–15s: 10–14 beats, 1–2 signatures (the upper limit — the espresso reference is 11 beats × 15s).

If the user doesn't specify, default to 15s. **If the brief asks for longer than 15s, don't try to fit it into one prompt.** Tell the user, then generate multiple ≤15s prompts that stitch together in editing — each one a self-contained beat-by-beat timeline ending in its own `CONSTRAINTS:` footer.

## Tone

Director's beat notes. Direct, prose-rich, no hype. Trust the reader.
