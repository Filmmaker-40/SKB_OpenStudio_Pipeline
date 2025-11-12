[README.md](https://github.com/user-attachments/files/23492548/README.md)
# SKB Open Studio Pipeline

A version-controlled, open-source–friendly filmmaking workspace for **SKBproductions, LLC**.

This repo organizes scripts, AI prompts, images, motion tests, audio, marketing, and release assets across your three flagship projects: **Borsalino-Style**, **The 25th Dynasty**, and **Night Time People**.

---

## 📦 Structure

```
SKB_OpenStudio_Pipeline/
├─ projects/
│  ├─ Borsalino-Style/        # Noir series: Duke, Ava, Chicago 1940s
│  ├─ The-25th-Dynasty/       # King Kushta, Piye, desert epics
│  └─ Night-Time-People/      # Urban crime drama, nightclub owners
├─ assets/                    # Reusable images, prompts, LUTs, fonts, refs
├─ audio/                     # VO, music, SFX
├─ video/                     # Sources, proxies, renders
├─ marketing/                 # Thumbnails, pitch decks
├─ templates/                 # Prompt + checklist templates
├─ automation/                # Scripts or notes for Huginn/GitHub Actions
├─ docs/                      # Notes, tutorials, pipeline diagrams
└─ scripts/                   # Utility scripts (e.g., renamers, converters)
```

> Tip: Keep **heavy media** (e.g., `.mp4`, `.wav`) managed via **Git LFS**. See below.

---

## 🚀 Quick Start

1. Create a new GitHub repo named **`SKB_OpenStudio_Pipeline`**.
2. Click **Add file → Upload files** and drag everything from this folder.
3. (Optional) Initialize **Git LFS** locally for large files:
   ```bash
   git lfs install
   git lfs track "*.mp4" "*.mov" "*.wav" "*.flac" "*.png" "*.jpg"
   git add .gitattributes
   git commit -m "chore: enable Git LFS for media"
   git push
   ```

---

## 🎬 Standard 16:9 Cinematic Workflow

**Script → Storyboarder → DiffusionBee/ComfyUI → Blender (camera/lighting) → AnimateDiff / Runway / Pika → Kdenlive/DaVinci → Audacity/Ardour → HandBrake → YouTube + Pinterest**

- Maintain **dramatic lighting** for interiors.
- Prefer **full-body framing** unless a specific shot is called out.
- Keep character looks **consistent** across episodes (see `/templates/prompt_templates`).

---

## 🗂 Folder Conventions

- Filenames: `PROJECT_scene-shot_ver.ext` (e.g., `BORS_s01-a03_v2.png`)
- Prompts: keep both **prompt text** and **seed/params** in a paired `.txt` or `.json` next to the image.
- Thumbnails: store in `/thumbnails/16x9` and `/thumbnails/9x16` with ≤2 MB targets.

---

## 🔊 Subtitles & Localization

Use **Whisper** to transcribe and generate SRTs:
```bash
whisper input_audio.wav --model medium --language en --task translate --output_format srt
```
Store subtitles in `/subtitles/{lang}/` (e.g., `subtitles/es/episode2.srt`).

---

## 🤖 Automation (Optional)

- **Huginn**: cross-posting or watch-folder automations.
- **GitHub Actions**: lint prompts, validate folder names, publish docs site.

---

## ⚖️ License

Default license is **MIT** for your *code/configs*. Your **media (images/audio/video)** remains **All Rights Reserved** by SKBproductions unless you state otherwise. See `/templates/licenses/`.

---

_Last updated: 2025-11-11_
