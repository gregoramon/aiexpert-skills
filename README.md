# AI Expert Skills

Opinionated skills for video, content, and creative AI workflows — by [AI Expert](https://aiexpert.ae).

## Available skills

### `shotcraft`

Generate copy-paste-ready Seedance 2.0 video prompts from a creative brief. Output is a clean beat-by-beat timeline written in cinematic language — visual, camera, lighting, audio, timing — ready to paste into Seedance.

Built for product films, commercials, social vertical, cinematic interviews, and UGC.

---

## Install

### Claude Code (one-liner)

```text
/plugin marketplace add gregoramon/aiexpert-skills
/plugin install shotcraft@aiexpert
```

If skills don't appear right away, run `/reload-plugins` and restart Claude Code.

### Claude.ai (web) and Claude Desktop (Mac / Windows)

1. Download the skill bundle: **[`shotcraft.skill`](https://github.com/gregoramon/aiexpert-skills/raw/main/shotcraft.skill)**. Upload this file as-is — do not unzip it; the `.skill` file *is* the bundle (a zip of `SKILL.md` + `references/`).
2. Open Claude → **Settings → Capabilities → Skills**.
3. Click **Upload custom skill** and select `shotcraft.skill`.
4. The skill is now available in your conversations — just describe a video brief and Claude will use Shotcraft to write the prompt.

### Codex (OpenAI CLI)

OpenAI's Codex CLI is the place to use Shotcraft on the OpenAI side — skills aren't supported in the ChatGPT consumer app (only Codex).

1. Download **[`shotcraft.skill`](https://github.com/gregoramon/aiexpert-skills/raw/main/shotcraft.skill)** and unzip — you'll get a `SKILL.md` and a `references/` folder.
2. Place those inside a `shotcraft/` folder and copy that into `~/.codex/skills/`:
   ```text
   ~/.codex/skills/shotcraft/
     ├── SKILL.md
     └── references/
   ```
3. Restart Codex. The skill auto-loads.

### Anthropic API / Claude Agent SDK

Skills load programmatically by pointing the SDK at a folder (not a `.skill` zip). Clone this repo and reference:

```text
plugins/shotcraft/skills/shotcraft/
```

See your SDK's skill-loading docs for the exact configuration call.

### Mobile apps (iOS / Android)

Custom skill upload may not be available yet on mobile depending on your app version. Check **Settings → Capabilities → Skills** in your app to see whether upload is supported. If it isn't, the skill may still be available in conversations that were started on web or desktop with Shotcraft enabled — but cross-app behaviour can vary, so confirm in your app before relying on it.

### Gemini CLI / Copilot CLI / other tools — manual install

Skills are an open standard. For any CLI that supports them, you need a `shotcraft/` directory containing `SKILL.md` and `references/` placed in the CLI's skills directory (commonly `~/.gemini/skills/` for Gemini CLI; check your tool's docs for the exact path).

Two ways to get that directory:

- **From the `.skill` zip:** download [`shotcraft.skill`](https://github.com/gregoramon/aiexpert-skills/raw/main/shotcraft.skill), unzip it (you'll get `SKILL.md` + `references/` at the root of the zip), then place those two items inside a folder named `shotcraft/` and copy that folder into the skills directory.
- **From this repo:** clone the repo and copy `plugins/shotcraft/skills/shotcraft/` directly into the skills directory.

Then restart the CLI.

The skill is self-contained: one `SKILL.md` plus a `references/` folder. No dependencies, no tool calls, no platform lock-in.

---

## Usage

Once installed, just ask:

- *"Write me a Seedance prompt for a 15-second espresso macro film."*
- *"Build a shot list for a 20-second sports car commercial, golden hour, anamorphic."*
- *"Plan a 12-second cinematic interview opening for a founder talking about AI."*
- *"UGC-style 8-second product reveal for a perfume bottle."*

Shotcraft will pick the right cinematic register, write a beat-by-beat timeline, and output it ready to paste into Seedance 2.0.

---

## What you get

A single output: a beat-by-beat timeline. No effects inventory, no density map, no commentary — just the prompt, ready to paste.

Example beat block:

```text
BEAT 3 (00:03-00:04) — Grinder Burst
• EFFECT: 240fps deep slow-motion + radial motion blur + speed ramp on exit
• VISUAL: Coffee grounds explode outward from the grinder chute in a fine cloud, individual grains visible against pure black. The cloud has structure — a denser core, a lighter halo, fine particles drifting outward in slow arcs. No environmental detail in the background, just void.
• CAMERA: 85mm portrait look, extremely shallow depth of field, locked-off, framed dead-centre with negative space top and bottom. Sony Venice aesthetic — deep blacks, rich amber roll-off.
• LIGHT + GRADE: single hard top-light, rim light from behind through the cloud — the rim defines the edge of every grain. High-contrast, near-bleach-bypass; grounds read as warm against black.
• AUDIO: the grinder's mechanical whirr drops to subsonic as the speed ramps; a low score note enters — a single sustained tone, not melody.
• TIMING: 240fps overcrank — the slowest moment in the film — ramping up to 24fps as the grounds settle.
• EXIT: speed ramp into Beat 4; the cloud snaps to stillness.
• (SIGNATURE) — the burst.
```

Eleven of those, plus a closing `CONSTRAINTS:` line, and you have a 15-second prompt.

---

## License

MIT. See [LICENSE](LICENSE).

---

Made by [AI Expert](https://aiexpert.ae) — Gregor Amon.
