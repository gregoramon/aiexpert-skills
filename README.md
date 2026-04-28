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
