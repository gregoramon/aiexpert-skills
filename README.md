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

### ChatGPT (web / desktop)

OpenAI adopted the open Skills format in December 2025, so the same `shotcraft.skill` file works in ChatGPT too.

1. Download **[`shotcraft.skill`](https://github.com/gregoramon/aiexpert-skills/raw/main/shotcraft.skill)** (the same file as for Claude).
2. Open ChatGPT → **Skills page** → **New skill** → **Upload from your computer**.
3. Select `shotcraft.skill`. (If your ChatGPT version requires a plain `.zip` extension, rename the file to `shotcraft.zip` first — the contents are identical.)
4. Save. Try a brief like *"15-second cinematic espresso macro film."*

### Codex (OpenAI CLI)

Codex reads skills from `~/.codex/skills/`. Either drop the unzipped `shotcraft/` folder there, or use OpenAI's skill loader with the same `.skill` bundle.

### Anthropic API / Claude Agent SDK

Skills load programmatically by pointing the SDK at a folder (not a `.skill` zip). Clone this repo and reference:

```
plugins/shotcraft/skills/shotcraft/
```

See your SDK's skill-loading docs for the exact configuration call.

### Mobile apps (iOS / Android)

Custom skill upload may not be available yet on mobile depending on your app version. Check **Settings → Capabilities → Skills** in your app to see whether upload is supported. If it isn't, the skill still works in any conversation that started on web or desktop with Shotcraft enabled.

### Gemini CLI / Copilot CLI / other tools — manual install

Skills are an open standard. For any CLI that supports them:

1. Download `shotcraft.skill` and unzip, or clone this repo.
2. Copy `plugins/shotcraft/skills/shotcraft/` into your CLI's skills directory (commonly `~/.gemini/skills/` for Gemini CLI; check your tool's docs for the exact path).
3. Restart the CLI.

The skill is self-contained: one `SKILL.md` plus a `references/` folder. No dependencies, no tool calls, no platform lock-in.

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
