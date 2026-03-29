# Concatenating multiple same-format audio files into one using ffmpeg.

The cleanest way is to use ffmpeg's concat demuxer. Here's how:

## 1- Create file list:

In your folder, run:
```
for f in *.mp3; do echo "file '$f'" >> filelist.txt; done
```
## 2. Concatenate with ffmpeg demuxer:
```
ffmpeg -f concat -safe 0 -i filelist.txt -c copy output.mp3
```

* -f concat — uses the concat demuxer
* -safe 0 — allows relative paths in the file list
* -c copy — copies streams without re-encoding (fast, lossless)
* output.mp3 — your final combined file

## Tips:

* If your files are numbered (e.g. chapter01.mp3, chapter02.mp3), the glob *.mp3 will naturally sort them correctly on most systems.
* If order matters and isn't guaranteed alphabetically, sort explicitly: ls -v *.mp3 or specify files manually in filelist.txt.
* The -c copy flag only works cleanly when all files share the same codec, sample rate, and channel layout — which is your case since they're the same format.
