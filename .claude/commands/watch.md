---
allowed-tools: Bash, Read, AskUserQuestion
description: Analyze a video by downloading it, extracting frames, and transcribing audio
---

# /watch — Claude watches a video

Given `$ARGUMENTS` (a video URL or local file path, plus an optional question), analyze the video:

1. Run preflight check:
   ```
   python3 ~/.claude/skills/watch/scripts/setup.py --check
   ```
   If it fails (exit non-zero), run the full installer and follow its output before continuing.

2. Run the video pipeline:
   ```
   python3 ~/.claude/skills/watch/scripts/watch.py <source> [--max-frames N] [--resolution W] [--start T] [--end T] [--no-whisper]
   ```

3. Read each frame path listed in the report using the Read tool to view the images.

4. Answer the user's question grounded in the frames and transcript.

If no arguments are provided, use AskUserQuestion to ask for a video URL or local file path before proceeding.

The work directory printed in the report should be deleted with `rm -rf <work-dir>` when analysis is complete.
