# AI Expert Skills

Opinionated skills for video, content, and creative AI workflows — by [AI Expert](https://aiexpert.ae).

## Available skills

### `shotcraft`

Generate copy-paste-ready Seedance 2.0 video prompts from a creative brief. Output is a clean shot-by-shot timeline written in cinematic language — lens, movement, lighting, grade, framerate — ready to paste into Seedance.

Built for product films, commercials, social vertical, cinematic interviews, and UGC.

---

## Install

### Claude Code (one-liner)

```
/plugin marketplace add gregoramon/aiexpert-skills
/plugin install shotcraft@aiexpert
```

If skills don't appear right away, run `/reload-plugins` and restart Claude Code.

### Claude.ai (web) and Claude Desktop (Mac / Windows)

1. Download the skill bundle: **[`shotcraft.skill`](https://github.com/gregoramon/aiexpert-skills/raw/main/shotcraft.skill)** (a zipped `SKILL.md` + `references/`).
2. Open Claude → **Settings → Capabilities → Skills**.
3. Click **Upload custom skill** and select `shotcraft.skill`.
4. The skill is now available in your conversations — just describe a video brief and Claude will use Shotcraft to write the prompt.

### ChatGPT (Custom GPTs)

ChatGPT doesn't accept `.skill` zips, but Custom GPTs work great.

1. Download **[`shotcraft-gpt.md`](https://github.com/gregoramon/aiexpert-skills/raw/main/shotcraft-gpt.md)** — a single combined file with the skill instructions and the worked-example reference.
2. Open ChatGPT → **Explore GPTs → Create a GPT**.
3. In the **Configure** tab → **Instructions** field, paste this short block:
   > *You are Shotcraft, an AI Expert tool that turns a creative brief into a copy-paste-ready Seedance 2.0 video prompt — a beat-by-beat timeline. Before generating, read the attached `shotcraft-gpt.md` knowledge file in full to calibrate output structure, vocabulary, and constraints. Output only the beat-by-beat timeline — no preamble, no commentary.*
4. In the **Knowledge** section, upload `shotcraft-gpt.md`.
5. Save. Try a brief like *"15-second cinematic espresso macro film."*

The header of `shotcraft-gpt.md` repeats these steps and offers an alternative route if your tier supports long Instructions.

### Anthropic API / Claude Agent SDK

Skills load programmatically by pointing the SDK at a folder (not a `.skill` zip). Clone this repo and reference:

```
plugins/shotcraft/skills/shotcraft/
```

See your SDK's skill-loading docs for the exact configuration call.

### Mobile apps (iOS / Android)

Custom skill upload may not be available yet on mobile depending on your app version. Check **Settings → Capabilities → Skills** in your app to see whether upload is supported. If it isn't, the skill still works in any conversation that started on web or desktop with Shotcraft enabled.

### Codex (OpenAI CLI), Gemini CLI, Copilot CLI — manual install

The skill format is portable — Shotcraft is a writing skill that doesn't depend on Claude-Code-specific tools, so it ports cleanly to any CLI that supports skills.

1. Clone or download this repo:
   ```
   git clone https://github.com/gregoramon/aiexpert-skills.git
   ```
2. Copy the skill folder into your CLI's skills directory:
   ```
   plugins/shotcraft/skills/shotcraft/  →  <your-cli-skills-directory>/shotcraft/
   ```
   Common locations:
   - **Codex:** check the Codex docs for the current skills path.
   - **Gemini CLI:** `~/.gemini/skills/` (or wherever your GEMINI.md points).
   - **Copilot CLI:** check the Copilot CLI docs for the current skills path.
3. Restart your CLI.

The skill is self-contained: a single `SKILL.md` plus a `references/` folder. No dependencies, no tool calls, no platform lock-in.

---

## Usage

Once installed, just ask:

- *"Write me a Seedance prompt for a 15-second espresso macro film."*
- *"Build a shot list for a 20-second sports car commercial, golden hour, anamorphic."*
- *"Plan a 12-second cinematic interview opening for a founder talking about AI."*
- *"UGC-style 8-second product reveal for a perfume bottle."*

Shotcraft will pick the right cinematic register, write a shot-by-shot timeline, and output it ready to paste into Seedance 2.0.

---

## What you get

A single output: a shot-by-shot timeline. No effects inventory, no density map, no commentary — just the prompt, ready to paste.

Example shot block:

```
SHOT 3 (00:03-00:04) — Grinder Burst (SIGNATURE)
• EFFECT: 240fps deep slow-motion + radial motion blur + speed ramp on exit
• Coffee grounds explode outward from the grinder chute in a fine cloud, individual grains visible against a dark backdrop
• Camera: 85mm at f/2, locked-off, framed dead-centre with negative space top and bottom
• Light: single hard top-light, rim light from behind through the cloud
• Grade: high-contrast, near-bleach-bypass; grounds read as warm against black
• Speed: 240fps overcrank — the slowest moment in the film — ramping up to 24fps as the grounds settle
• Exit: speed ramp into Shot 4; the cloud snaps to stillness
```

Eleven of those, and you have a 15-second prompt.

---

## License

MIT. See [LICENSE](LICENSE).

---

Made by [AI Expert](https://aiexpert.ae) — Gregor Amon.
