# Davinci Resolve won't play most video formats on Linux
## Fixin video format with ffmpeg:

For a single file : `ffmpeg -i old.m4v -vcodec mjpeg -q:v 2 -acodec pcm_s16be -q:a 0 -f mov new.mov`

For a batch of files in a folder:

```bash
for file in /path/to/directory/*.TS.mp4; do ffmpeg -i "$file" -vcodec mjpeg -q:v 2 -acodec pcm_s16be -q:a 0 -f mov "${file%.TS.mp4}.mov"; done
```
