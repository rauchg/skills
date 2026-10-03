# skills

Agent skills by [@rauchg](https://github.com/rauchg). Each folder in [`skills/`](skills) is self-contained: a `SKILL.md` with the instructions, plus the scripts and assets it needs.

## Install

```bash
npx skills add rauchg/skills
```

Or copy a skill folder into your agent's skills directory (for example `~/.claude/skills/` or `~/.fx/skills/`).

## Skills

### [ui-recording-timeline](skills/ui-recording-timeline)

Turns a screen recording of a UI (page load, navigation, redirect or auth flow, app startup) into an interactive paint timeline page:

- the video fills the window, with a thin timeline of every visual paint (timestamps, how long each screen was shown, phase colors, hover thumbnails, scrubbing)
- at each paint, what was painted flashes pink and what only moved slides in blue
- painted regions are snapped to whole layout elements, not pixel noise; moves are detected by template matching, and the mouse cursor is learned from the recording and ignored
- the output is a static folder (`index.html` plus the video), easy to open locally or deploy

The agent does the judgment parts: which frame changes are real paints, labels, phases, metrics. One script (`scripts/timeline.py`, run with `uv`) does the rest: extracting frames, contact sheets for review, the move-aware diff, check sheets, and building the page.

Requirements: `ffmpeg`, `uv`, and optionally Chrome or Chromium for headless previews.

## License

MIT
