# image-ppt-maker

`image-ppt-maker` is a Codex skill for turning a presentation idea into a polished set of PPT-style images, a playable 16:9 HTML slideshow, and final speaker notes.

It is designed for people who want the visual impact of a slide deck without spending hours manually shaping storylines, prompts, layouts, and presenter scripts.

[中文说明](README.zh-CN.md)

## Why Use It

- **McKinsey-style storyline**: turns vague requirements into an answer-first master outline and page-by-page logic.
- **Human-in-the-loop checkpoints**: asks for confirmation at key moments instead of rushing into image generation.
- **Context-aware visual direction**: recommends suitable styles such as training, executive report, illustration-heavy, chart-heavy, tech, or brand-clean.
- **Prompt consistency**: locks one deck-wide visual style so generated slides feel like one coherent deck.
- **Image-first output**: generates one 16:9 image per slide, suitable for sharing, embedding, or presenting.
- **Playable HTML deck**: automatically assembles generated images into an interactive 16:9 HTML player with keyboard navigation, click zones, progress, and fullscreen support.
- **Final speaker notes**: writes natural, friendly, oral talk tracks after seeing the final generated slides.

## Workflow

1. Clarify the brief, audience, duration, slide count, density, source constraints, and optional top-corner LOGO space.
2. Draft a McKinsey-style master outline and page-by-page outline.
3. Expand each page with richer content, examples, and visual emphasis.
4. Ask the user to choose a visual style, with recommendations based on context.
5. Generate unified image prompts internally and proceed directly to image generation without a prompt-approval step.
6. Generate one 16:9 slide image per page, then review the completed images with the user.
7. After image approval, automatically create a playable 16:9 HTML slideshow.
8. Write duration-aware, directly readable speaker notes based on the approved outline and final images.

For later single-slide changes, the skill rebuilds and confirms that slide's logic, content, examples, and visual emphasis before regenerating its image. It reuses the approved deck style and does not ask for prompt approval.

## Requirements

This skill depends on an image-generation model available in your Codex environment. The model should be good at:

- following detailed layout instructions;
- generating readable slide-like text;
- keeping a consistent visual style across multiple images;
- producing or exporting local image files for HTML assembly.

Recommended model families:

- **OpenAI GPT Image / ChatGPT image generation** for strong instruction following and slide-like composition. See [OpenAI image generation docs](https://platform.openai.com/docs/guides/image-generation).
- **Google Gemini image generation / Nano Banana / Imagen** for multimodal image generation and iteration. See [Gemini image generation docs](https://ai.google.dev/gemini-api/docs/image-generation) and [Google DeepMind Imagen](https://deepmind.google/models/imagen/).
- Any comparable image model that can reliably create 16:9 presentation pages with readable text and consistent style.

Model names and availability change over time. Check your provider's current documentation before relying on a specific model ID.

## Installation

### Option 1: Install from ClawHub (OpenClaw)

Install into the current OpenClaw workspace:

```bash
openclaw skills install @callmexhj/image-ppt-maker
```

Install globally for all local OpenClaw agents:

```bash
openclaw skills install @callmexhj/image-ppt-maker --global
```

Update the globally installed skill later:

```bash
openclaw skills update @callmexhj/image-ppt-maker --global
```

This method is for OpenClaw. For Codex, use one of the manual installation methods below.

### Option 2: Clone Directly Into Codex Skills

PowerShell:

```powershell
git clone https://github.com/callmexhj/image-ppt-maker.git "$env:USERPROFILE\.codex\skills\image-ppt-maker"
```

macOS/Linux:

```bash
git clone https://github.com/callmexhj/image-ppt-maker.git ~/.codex/skills/image-ppt-maker
```

### Option 3: Download ZIP

1. Download this repository as a ZIP from GitHub.
2. Extract it.
3. Rename the extracted folder to `image-ppt-maker`.
4. Move it into your Codex skills directory:
   - Windows: `%USERPROFILE%\.codex\skills\image-ppt-maker`
   - macOS/Linux: `~/.codex/skills/image-ppt-maker`

### Option 4: Copy From a Local Checkout

PowerShell:

```powershell
Copy-Item -LiteralPath . -Destination "$env:USERPROFILE\.codex\skills\image-ppt-maker" -Recurse -Force
```

macOS/Linux:

```bash
cp -R . ~/.codex/skills/image-ppt-maker
```

## Usage

Invoke the skill in Codex:

```text
$image-ppt-maker
```

Example request:

```text
$image-ppt-maker 帮我做一套面向管理层的 AI 应用培训分享，10 分钟左右，偏培训风，最后生成可播放的 HTML。
```

## Output

The skill can produce:

- confirmed brief and assumptions;
- master outline and page-by-page outline;
- expanded page content and visual emphasis;
- image-generation prompts;
- 16:9 slide images;
- playable HTML slideshow;
- final oral speaker notes.

## Notes

- This skill does not assemble `.pptx` files.
- HTML assembly requires local slide image files.
- For best results, provide source facts, brand constraints, target audience, duration, and preferred tone.

